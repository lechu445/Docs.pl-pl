---
title: "Stron razor podstawowych EF - aktualizacji powiązanych danych - 7, 8"
author: rick-anderson
description: "W tym samouczku będziesz aktualizacji powiązanych danych, aktualizując pól klucza obcego i właściwości nawigacji."
keywords: "Tworzy sprzężenie platformy ASP.NET Core Entity Framework Core, powiązane dane"
ms.author: riande
manager: wpickett
ms.date: 11/15/2017
ms.topic: get-started-article
ms.technology: aspnet
ms.prod: asp.net-core
uid: data/ef-rp/update-related-data
ms.openlocfilehash: f07a33c19ba1be623fae14228f8fbc909d766816
ms.sourcegitcommit: 6e46abd65973dea796d364a514de9ec2e3e1c1ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="updating-related-data---ef-core-razor-pages-7-of-8"></a><span data-ttu-id="7bb00-104">Aktualizowanie danych powiązanych - stron Razor EF Core (7, 8)</span><span class="sxs-lookup"><span data-stu-id="7bb00-104">Updating related data - EF Core Razor Pages (7 of 8)</span></span>

<span data-ttu-id="7bb00-105">Przez [Dykstra Tomasz](https://github.com/tdykstra), i [Rick Anderson](https://twitter.com/RickAndMSFT)</span><span class="sxs-lookup"><span data-stu-id="7bb00-105">By [Tom Dykstra](https://github.com/tdykstra), and [Rick Anderson](https://twitter.com/RickAndMSFT)</span></span>

[!INCLUDE[about the series](../../includes/RP-EF/intro.md)]

<span data-ttu-id="7bb00-106">Ten samouczek pokazuje, aktualizowanie powiązanych danych.</span><span class="sxs-lookup"><span data-stu-id="7bb00-106">This tutorial demonstrates updating related data.</span></span> <span data-ttu-id="7bb00-107">Jeśli wystąpiły problemy, nie można rozwiązać, Pobierz [ukończonej aplikacji dla tego etapu](https://github.com/aspnet/Docs/tree/master/aspnetcore/data/ef-rp/intro/samples/StageSnapShots/cu-part7).</span><span class="sxs-lookup"><span data-stu-id="7bb00-107">If you run into problems you can't solve, download the [completed app for this stage](https://github.com/aspnet/Docs/tree/master/aspnetcore/data/ef-rp/intro/samples/StageSnapShots/cu-part7).</span></span>

<span data-ttu-id="7bb00-108">Poniższych ilustracjach przedstawiono niektóre ukończone stron.</span><span class="sxs-lookup"><span data-stu-id="7bb00-108">The following illustrations shows some of the completed pages.</span></span>

<span data-ttu-id="7bb00-109">![Kursu edycji strony](update-related-data/_static/course-edit.png)
![instruktora edytowanie strony](update-related-data/_static/instructor-edit-courses.png)</span><span class="sxs-lookup"><span data-stu-id="7bb00-109">![Course Edit page](update-related-data/_static/course-edit.png)
![Instructor Edit page](update-related-data/_static/instructor-edit-courses.png)</span></span>

<span data-ttu-id="7bb00-110">Sprawdź i przetestować, tworzenie i edytowanie ciągu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-110">Examine and test the Create and Edit course pages.</span></span> <span data-ttu-id="7bb00-111">Utwórz nowy plan.</span><span class="sxs-lookup"><span data-stu-id="7bb00-111">Create a new course.</span></span> <span data-ttu-id="7bb00-112">Dział został wybrany za pomocą klucza podstawowego (liczba całkowita), nie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="7bb00-112">The department is selected by its primary key (an integer), not its name.</span></span> <span data-ttu-id="7bb00-113">Edytuj nowego kursu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-113">Edit the new course.</span></span> <span data-ttu-id="7bb00-114">Po zakończeniu testowania Usuń nowego kursu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-114">When you have finished testing, delete the new course.</span></span>

## <a name="create-a-base-class-to-share-common-code"></a><span data-ttu-id="7bb00-115">Utwórz klasę podstawową, aby udostępnić typowy kod</span><span class="sxs-lookup"><span data-stu-id="7bb00-115">Create a base class to share common code</span></span>

<span data-ttu-id="7bb00-116">Kursy/Utwórz kursy i edytowanie strony i każdego muszą listę nazw działów.</span><span class="sxs-lookup"><span data-stu-id="7bb00-116">The Courses/Create and Courses/Edit pages each need a list of department names.</span></span> <span data-ttu-id="7bb00-117">Utwórz *Pages/Courses/DepartmentNamePageModel.cshtml.cs* klasę podstawową dla tworzenie i edytowanie strony:</span><span class="sxs-lookup"><span data-stu-id="7bb00-117">Create the *Pages/Courses/DepartmentNamePageModel.cshtml.cs* base class for the Create and Edit pages:</span></span>

[!code-csharp[Main](intro/samples/cu/Pages/Courses/DepartmentNamePageModel.cshtml.cs?highlight=9,11,20-21)]

<span data-ttu-id="7bb00-118">Poprzedni kod tworzy [SelectList](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.rendering.selectlist?view=aspnetcore-2.0) zawierać listę nazw działu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-118">The preceding code creates a [SelectList](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.rendering.selectlist?view=aspnetcore-2.0) to contain the list of department names.</span></span> <span data-ttu-id="7bb00-119">Jeśli `selectedDepartment` określono, że dział został wybrany w `SelectList`.</span><span class="sxs-lookup"><span data-stu-id="7bb00-119">If `selectedDepartment` is specified, that department is selected in the `SelectList`.</span></span>

<span data-ttu-id="7bb00-120">Klasy modeli tworzenie i edytowanie strony będzie dziedziczyć `DepartmentNamePageModel`.</span><span class="sxs-lookup"><span data-stu-id="7bb00-120">The Create and Edit page model classes will derive from `DepartmentNamePageModel`.</span></span>

## <a name="customize-the-courses-pages"></a><span data-ttu-id="7bb00-121">Dostosowywanie stron kursy</span><span class="sxs-lookup"><span data-stu-id="7bb00-121">Customize the Courses Pages</span></span>

<span data-ttu-id="7bb00-122">Po utworzeniu nowego obiektu kursu musi mieć relacji z istniejących działu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-122">When a new course entity is created, it must have a relationship to an existing department.</span></span> <span data-ttu-id="7bb00-123">Dział podczas tworzenia kursu, klasę podstawową dla tworzenie i edytowanie zawiera listy rozwijanej wyboru działu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-123">To add a department while creating a course, the base class for Create and Edit contains a drop-down list for selecting the department.</span></span> <span data-ttu-id="7bb00-124">Ustawia listy rozwijanej `Course.DepartmentID` właściwości klucza obcego (klucz OBCY).</span><span class="sxs-lookup"><span data-stu-id="7bb00-124">The drop-down list sets the `Course.DepartmentID` foreign key (FK) property.</span></span> <span data-ttu-id="7bb00-125">Używa EF Core `Course.DepartmentID` klucz OBCY załadować `Department` właściwości nawigacji.</span><span class="sxs-lookup"><span data-stu-id="7bb00-125">EF Core uses the `Course.DepartmentID` FK to load the `Department` navigation property.</span></span>

![Utwórz plan](update-related-data/_static/ddl.png)

<span data-ttu-id="7bb00-127">Aktualizacja modelu strony Utwórz następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7bb00-127">Update the Create page model with the following code:</span></span>

[!code-csharp[Main](intro/samples/cu/Pages/Courses/Create.cshtml.cs?highlight=7,18,32-)]

<span data-ttu-id="7bb00-128">Poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="7bb00-128">The preceding code:</span></span>

* <span data-ttu-id="7bb00-129">Pochodną `DepartmentNamePageModel`.</span><span class="sxs-lookup"><span data-stu-id="7bb00-129">Derives from `DepartmentNamePageModel`.</span></span>
* <span data-ttu-id="7bb00-130">Używa `TryUpdateModelAsync` zapobiegające [overposting](xref:data/ef-rp/crud#overposting).</span><span class="sxs-lookup"><span data-stu-id="7bb00-130">Uses `TryUpdateModelAsync` to prevent [overposting](xref:data/ef-rp/crud#overposting).</span></span>
* <span data-ttu-id="7bb00-131">Zastępuje `ViewData["DepartmentID"]` z `DepartmentNameSL` (od klasy podstawowej).</span><span class="sxs-lookup"><span data-stu-id="7bb00-131">Replaces `ViewData["DepartmentID"]` with `DepartmentNameSL` (from the base class).</span></span>

<span data-ttu-id="7bb00-132">`ViewData["DepartmentID"]`zastępuje z silnie typizowaną `DepartmentNameSL`.</span><span class="sxs-lookup"><span data-stu-id="7bb00-132">`ViewData["DepartmentID"]` is replaced with the strongly typed `DepartmentNameSL`.</span></span> <span data-ttu-id="7bb00-133">Modele jednoznacznie są preferowane za pośrednictwem lekko wpisany.</span><span class="sxs-lookup"><span data-stu-id="7bb00-133">Strongly typed models are preferred over weakly typed.</span></span> <span data-ttu-id="7bb00-134">Aby uzyskać więcej informacji, zobacz [lekko typu danych (ViewData i obiekt ViewBag)](xref:mvc/views/overview#VD_VB).</span><span class="sxs-lookup"><span data-stu-id="7bb00-134">For more information, see [Weakly typed data (ViewData and ViewBag)](xref:mvc/views/overview#VD_VB).</span></span>

### <a name="update-the-courses-create-page"></a><span data-ttu-id="7bb00-135">Zaktualizuj strony tworzenia kursów</span><span class="sxs-lookup"><span data-stu-id="7bb00-135">Update the Courses Create page</span></span>

<span data-ttu-id="7bb00-136">Aktualizacja *Pages/Courses/Create.cshtml* z następujący kod:</span><span class="sxs-lookup"><span data-stu-id="7bb00-136">Update *Pages/Courses/Create.cshtml* with the following markup:</span></span>

[!code-cshtml[Main](intro/samples/cu/Pages/Courses/Create.cshtml?highlight=29-34)]

<span data-ttu-id="7bb00-137">Poprzedni kod znaczników wprowadza następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="7bb00-137">The preceding markup makes the following changes:</span></span>

* <span data-ttu-id="7bb00-138">Zmienia podpisu z **DepartmentID** do **działu**.</span><span class="sxs-lookup"><span data-stu-id="7bb00-138">Changes the caption from **DepartmentID** to **Department**.</span></span>
* <span data-ttu-id="7bb00-139">Zastępuje `"ViewBag.DepartmentID"` z `DepartmentNameSL` (od klasy podstawowej).</span><span class="sxs-lookup"><span data-stu-id="7bb00-139">Replaces `"ViewBag.DepartmentID"` with `DepartmentNameSL` (from the base class).</span></span>
* <span data-ttu-id="7bb00-140">Dodaje opcję "Wybierz dział".</span><span class="sxs-lookup"><span data-stu-id="7bb00-140">Adds the "Select Department" option.</span></span> <span data-ttu-id="7bb00-141">Ta zmiana powoduje "Wybierz dział" zamiast pierwszy działu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-141">This change renders "Select Department" rather than the first department.</span></span>
* <span data-ttu-id="7bb00-142">Dodaje komunikat dotyczący sprawdzania poprawności, gdy nie wybrano działu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-142">Adds a validation message when the department is not selected.</span></span>

<span data-ttu-id="7bb00-143">Strona Razor używa [wybierz pomocnika tagów](xref:mvc/views/working-with-forms#the-select-tag-helper):</span><span class="sxs-lookup"><span data-stu-id="7bb00-143">The Razor Page uses the [Select Tag Helper](xref:mvc/views/working-with-forms#the-select-tag-helper):</span></span>

[!code-cshtml[Main](intro/samples/cu/Pages/Courses/Create.cshtml?range=28-35&highlight=3-6)]

<span data-ttu-id="7bb00-144">Przetestuj tworzenia strony.</span><span class="sxs-lookup"><span data-stu-id="7bb00-144">Test the Create page.</span></span> <span data-ttu-id="7bb00-145">Utwórz stronę Wyświetla nazwę działu zamiast identyfikatora działu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-145">The Create page displays the department name rather than the department ID.</span></span>

### <a name="update-the-courses-edit-page"></a><span data-ttu-id="7bb00-146">Zaktualizuj strony Edytuj kursy.</span><span class="sxs-lookup"><span data-stu-id="7bb00-146">Update the Courses Edit page.</span></span>

<span data-ttu-id="7bb00-147">Aktualizacja modelu strony Edytuj następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7bb00-147">Update the edit page model with the following code:</span></span>

[!code-csharp[Main](intro/samples/cu/Pages/Courses/Edit.cshtml.cs?highlight=8,28,35,36,40,47-)]

<span data-ttu-id="7bb00-148">Zmiany są podobne do tych wprowadzone w modelu strony Utwórz.</span><span class="sxs-lookup"><span data-stu-id="7bb00-148">The changes are similar to those made in the Create page model.</span></span> <span data-ttu-id="7bb00-149">W powyższym kodzie `PopulateDepartmentsDropDownList` przebiegów w identyfikatorze działu, które dział określonych na liście rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="7bb00-149">In the preceding code, `PopulateDepartmentsDropDownList` passes in the department ID, which select the department specified in the drop-down list.</span></span>

<span data-ttu-id="7bb00-150">Aktualizacja *Pages/Courses/Edit.cshtml* z następujący kod:</span><span class="sxs-lookup"><span data-stu-id="7bb00-150">Update *Pages/Courses/Edit.cshtml* with the following markup:</span></span>

[!code-cshtml[Main](intro/samples/cu/Pages/Courses/Edit.cshtml?highlight=17-20,32-35)]

<span data-ttu-id="7bb00-151">Poprzedni kod znaczników wprowadza następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="7bb00-151">The preceding markup makes the following changes:</span></span>

* <span data-ttu-id="7bb00-152">Wyświetla identyfikator kursu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-152">Displays the course ID.</span></span> <span data-ttu-id="7bb00-153">Ogólnie rzecz biorąc podstawowego klucza (PK) z jednostki nie jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="7bb00-153">Generally the Primary Key (PK) of an entity is not displayed.</span></span> <span data-ttu-id="7bb00-154">PKs są zazwyczaj bezużyteczne dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="7bb00-154">PKs are usually meaningless to users.</span></span> <span data-ttu-id="7bb00-155">W takim przypadku PK jest to liczba kursu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-155">In this case, the PK is the course number.</span></span>
* <span data-ttu-id="7bb00-156">Zmienia podpisu z **DepartmentID** do **działu**.</span><span class="sxs-lookup"><span data-stu-id="7bb00-156">Changes the caption from **DepartmentID** to **Department**.</span></span>
* <span data-ttu-id="7bb00-157">Zastępuje `"ViewBag.DepartmentID"` z `DepartmentNameSL` (od klasy podstawowej).</span><span class="sxs-lookup"><span data-stu-id="7bb00-157">Replaces `"ViewBag.DepartmentID"` with `DepartmentNameSL` (from the base class).</span></span>
* <span data-ttu-id="7bb00-158">Dodaje opcję "Wybierz dział".</span><span class="sxs-lookup"><span data-stu-id="7bb00-158">Adds the "Select Department" option.</span></span> <span data-ttu-id="7bb00-159">Ta zmiana powoduje "Wybierz dział" zamiast pierwszy działu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-159">This change renders "Select Department" rather than the first department.</span></span>
* <span data-ttu-id="7bb00-160">Dodaje komunikat dotyczący sprawdzania poprawności, gdy nie wybrano działu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-160">Adds a validation message when the department is not selected.</span></span>

<span data-ttu-id="7bb00-161">Strona zawiera pola ukrytego (`<input type="hidden">`) dla porach numeru.</span><span class="sxs-lookup"><span data-stu-id="7bb00-161">The page contains a hidden field (`<input type="hidden">`) for the course number.</span></span> <span data-ttu-id="7bb00-162">Dodawanie `<label>` pomocnika za pomocą tagów `asp-for="Course.CourseID"` nie eliminuje potrzebę stosowania ukryte pole.</span><span class="sxs-lookup"><span data-stu-id="7bb00-162">Adding a `<label>` tag helper with `asp-for="Course.CourseID"` doesn't eliminate the need for the hidden field.</span></span> <span data-ttu-id="7bb00-163">`<input type="hidden">`jest wymagany dla numeru kursu mają zostać uwzględnione w przesłane dane, gdy użytkownik kliknie **zapisać**.</span><span class="sxs-lookup"><span data-stu-id="7bb00-163">`<input type="hidden">` is required for the course number to be included in the posted data when the user clicks **Save**.</span></span>

<span data-ttu-id="7bb00-164">Przetestuj zaktualizowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-164">Test the updated code.</span></span> <span data-ttu-id="7bb00-165">Tworzenie, edytowanie i usuwanie kursu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-165">Create, edit, and delete a course.</span></span>

## <a name="add-asnotracking-to-the-details-and-delete-page-models"></a><span data-ttu-id="7bb00-166">Dodaj AsNoTracking do szczegółów i usuń modele strony</span><span class="sxs-lookup"><span data-stu-id="7bb00-166">Add AsNoTracking to the Details and Delete page models</span></span>

<span data-ttu-id="7bb00-167">[AsNoTracking](https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.entityframeworkqueryableextensions.asnotracking?view=efcore-2.0#Microsoft_EntityFrameworkCore_EntityFrameworkQueryableExtensions_AsNoTracking__1_System_Linq_IQueryable___0__) może poprawić wydajność podczas śledzenia nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="7bb00-167">[AsNoTracking](https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.entityframeworkqueryableextensions.asnotracking?view=efcore-2.0#Microsoft_EntityFrameworkCore_EntityFrameworkQueryableExtensions_AsNoTracking__1_System_Linq_IQueryable___0__) can improve performance when tracking is not required.</span></span> <span data-ttu-id="7bb00-168">Dodaj `AsNoTracking` do modelu strony Delete i szczegóły.</span><span class="sxs-lookup"><span data-stu-id="7bb00-168">Add `AsNoTracking` to the Delete and Details page model.</span></span> <span data-ttu-id="7bb00-169">Poniższy kod przedstawia w zaktualizowanym modelu. Usuń strony:</span><span class="sxs-lookup"><span data-stu-id="7bb00-169">The following code shows the updated Delete page model:</span></span>

[!code-csharp[Main](intro/samples/cu/Pages/Courses/Delete.cshtml.cs?name=snippet&highlight=21,23,40,41)]

<span data-ttu-id="7bb00-170">Aktualizacja `OnGetAsync` metody w *Pages/Courses/Details.cshtml.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="7bb00-170">Update the `OnGetAsync` method in the *Pages/Courses/Details.cshtml.cs* file:</span></span>

[!code-csharp[Main](intro/samples/cu/Pages/Courses/Details.cshtml.cs?name=snippet)]

### <a name="modify-the-delete-and-details-pages"></a><span data-ttu-id="7bb00-171">Modyfikowanie stron Delete i szczegóły</span><span class="sxs-lookup"><span data-stu-id="7bb00-171">Modify the Delete and Details pages</span></span>

<span data-ttu-id="7bb00-172">Zaktualizuj strony Usuń Razor o następujący kod:</span><span class="sxs-lookup"><span data-stu-id="7bb00-172">Update the Delete Razor page with the following markup:</span></span>

[!code-cshtml[Main](intro/samples/cu/Pages/Courses/Delete.cshtml?highlight=15-20)]

<span data-ttu-id="7bb00-173">Wprowadzenie identycznych zmian do strony szczegółów.</span><span class="sxs-lookup"><span data-stu-id="7bb00-173">Make the same changes to the Details page.</span></span>

### <a name="test-the-course-pages"></a><span data-ttu-id="7bb00-174">Kursu stron w teście</span><span class="sxs-lookup"><span data-stu-id="7bb00-174">Test the Course pages</span></span>

<span data-ttu-id="7bb00-175">Test tworzenia, edytowania, uzyskać szczegółowe informacje i usuwania.</span><span class="sxs-lookup"><span data-stu-id="7bb00-175">Test create, edit, details, and delete.</span></span>

## <a name="update-the-instructor-pages"></a><span data-ttu-id="7bb00-176">Aktualizowanie stron instruktora</span><span class="sxs-lookup"><span data-stu-id="7bb00-176">Update the instructor pages</span></span>

<span data-ttu-id="7bb00-177">Poniższe sekcje aktualizacji instruktora stron.</span><span class="sxs-lookup"><span data-stu-id="7bb00-177">The following sections update the instructor pages.</span></span>

### <a name="add-office-location"></a><span data-ttu-id="7bb00-178">Dodaj lokalizację pakietu office</span><span class="sxs-lookup"><span data-stu-id="7bb00-178">Add office location</span></span>

<span data-ttu-id="7bb00-179">Edytowanie rekordu instruktora, można zaktualizować przypisania office instruktora.</span><span class="sxs-lookup"><span data-stu-id="7bb00-179">When editing an instructor record, you may want to update the instructor's office assignment.</span></span> <span data-ttu-id="7bb00-180">`Instructor` Jednostka ma relacji jeden do zero lub jeden z `OfficeAssignment` jednostki.</span><span class="sxs-lookup"><span data-stu-id="7bb00-180">The `Instructor` entity has a one-to-zero-or-one relationship with the `OfficeAssignment` entity.</span></span> <span data-ttu-id="7bb00-181">Kod instruktora musi obsługiwać:</span><span class="sxs-lookup"><span data-stu-id="7bb00-181">The instructor code must handle:</span></span>

* <span data-ttu-id="7bb00-182">Jeśli użytkownik usuwa przypisanie pakietu office, Usuń `OfficeAssignment` jednostki.</span><span class="sxs-lookup"><span data-stu-id="7bb00-182">If the user clears the office assignment, delete the `OfficeAssignment` entity.</span></span>
* <span data-ttu-id="7bb00-183">Jeśli użytkownik wprowadzi przypisania pakietu office i był on pusty, Utwórz nową `OfficeAssignment` jednostki.</span><span class="sxs-lookup"><span data-stu-id="7bb00-183">If the user enters an office assignment and it was empty, create a new `OfficeAssignment` entity.</span></span>
* <span data-ttu-id="7bb00-184">Jeśli użytkownik zmieni przypisania pakietu office, należy zaktualizować `OfficeAssignment` jednostki.</span><span class="sxs-lookup"><span data-stu-id="7bb00-184">If the user changes the office assignment, update the `OfficeAssignment` entity.</span></span>

<span data-ttu-id="7bb00-185">Aktualizacja modelu strony Edytuj instruktorów następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7bb00-185">Update the instructors Edit page model with the following code:</span></span>

[!code-csharp[Main](intro/samples/cu/Pages/Instructors/Edit1.cshtml.cs?name=snippet&highlight=20-23,32,39-)]

<span data-ttu-id="7bb00-186">Poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="7bb00-186">The preceding code:</span></span>

- <span data-ttu-id="7bb00-187">Pobiera bieżący `Instructor` jednostki z bazy danych przy użyciu wczesny ładowania dla `OfficeAssignment` właściwości nawigacji.</span><span class="sxs-lookup"><span data-stu-id="7bb00-187">Gets the current `Instructor` entity from the database using eager loading for the `OfficeAssignment` navigation property.</span></span>
- <span data-ttu-id="7bb00-188">Aktualizuje pobranej `Instructor` jednostki wartościami z integratora modelu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-188">Updates the retrieved `Instructor` entity with values from the model binder.</span></span> <span data-ttu-id="7bb00-189">`TryUpdateModel`Zapobiega [overposting](xref:data/ef-rp/crud#overposting).</span><span class="sxs-lookup"><span data-stu-id="7bb00-189">`TryUpdateModel` prevents [overposting](xref:data/ef-rp/crud#overposting).</span></span>
- <span data-ttu-id="7bb00-190">Jeśli w lokalizacji biura jest puste, ustawia `Instructor.OfficeAssignment` na wartość null.</span><span class="sxs-lookup"><span data-stu-id="7bb00-190">If the office location is blank, sets `Instructor.OfficeAssignment` to null.</span></span> <span data-ttu-id="7bb00-191">Gdy `Instructor.OfficeAssignment` jest null, powiązane wiersza w `OfficeAssignment` usunięcia tabeli.</span><span class="sxs-lookup"><span data-stu-id="7bb00-191">When `Instructor.OfficeAssignment` is null, the related row in the `OfficeAssignment` table is deleted.</span></span>

### <a name="update-the-instructor-edit-page"></a><span data-ttu-id="7bb00-192">Zaktualizuj instruktora edycji strony</span><span class="sxs-lookup"><span data-stu-id="7bb00-192">Update the instructor Edit page</span></span>

<span data-ttu-id="7bb00-193">Aktualizacja *Pages/Instructors/Edit.cshtml* z lokalizacji pakietu office:</span><span class="sxs-lookup"><span data-stu-id="7bb00-193">Update *Pages/Instructors/Edit.cshtml* with the office location:</span></span>

[!code-cshtml[Main](intro/samples/cu/Pages/Instructors/Edit1.cshtml?highlight=29-33)]

<span data-ttu-id="7bb00-194">Sprawdź, czy można zmienić lokalizacji biura instruktorów.</span><span class="sxs-lookup"><span data-stu-id="7bb00-194">Verify you can change an instructors office location.</span></span>

## <a name="add-course-assignments-to-the-instructor-edit-page"></a><span data-ttu-id="7bb00-195">Na stronie edycji instruktora Dodaj kursu przypisania</span><span class="sxs-lookup"><span data-stu-id="7bb00-195">Add Course assignments to the instructor Edit page</span></span>

<span data-ttu-id="7bb00-196">Instruktorów może nauczyć dowolną liczbę kursów.</span><span class="sxs-lookup"><span data-stu-id="7bb00-196">Instructors may teach any number of courses.</span></span> <span data-ttu-id="7bb00-197">W tej sekcji możesz dodać możliwości zmiany przypisania kursu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-197">In this section, you add the ability to change course assignments.</span></span> <span data-ttu-id="7bb00-198">Na poniższej ilustracji przedstawiono zaktualizowane instruktora edycji strony:</span><span class="sxs-lookup"><span data-stu-id="7bb00-198">The following image shows the updated instructor Edit page:</span></span>

![Instruktora edycji strony z kursów](update-related-data/_static/instructor-edit-courses.png)

<span data-ttu-id="7bb00-200">`Course`i `Instructor` ma relację wiele do wielu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-200">`Course` and `Instructor` has a many-to-many relationship.</span></span> <span data-ttu-id="7bb00-201">Aby dodać lub usunąć relacji, dodawania i usuwania jednostek z `CourseAssignments` Dołącz do zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="7bb00-201">To add and remove relationships, you add and remove entities from the `CourseAssignments` join entity set.</span></span>

<span data-ttu-id="7bb00-202">Pola wyboru Włącz zmiany kursów przydzielonej instruktora.</span><span class="sxs-lookup"><span data-stu-id="7bb00-202">Check boxes enable changes to courses an instructor is assigned to.</span></span> <span data-ttu-id="7bb00-203">Pole wyboru jest wyświetlane dla porach co w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="7bb00-203">A check box is displayed for every course in the database.</span></span> <span data-ttu-id="7bb00-204">Kursy przypisane instruktora są sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="7bb00-204">Courses that the instructor is assigned to are checked.</span></span> <span data-ttu-id="7bb00-205">Użytkownika można zaznaczyć lub wyczyścić pola wyboru, aby zmienić przypisania kursu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-205">The user can select or clear check boxes to change course assignments.</span></span> <span data-ttu-id="7bb00-206">Jeśli liczba kursów była większa:</span><span class="sxs-lookup"><span data-stu-id="7bb00-206">If the number of courses were much greater:</span></span>

* <span data-ttu-id="7bb00-207">Interfejs inny użytkownik użyje prawdopodobnie do wyświetlenia kursów.</span><span class="sxs-lookup"><span data-stu-id="7bb00-207">You'd probably use a different user interface to display the courses.</span></span>
* <span data-ttu-id="7bb00-208">Metoda manipulowania jednostki sprzężenia, można utworzyć ani usunąć relacji nie ulegnie zmianie.</span><span class="sxs-lookup"><span data-stu-id="7bb00-208">The method of manipulating a join entity to create or delete relationships would not change.</span></span>

### <a name="add-classes-to-support-create-and-edit-instructor-pages"></a><span data-ttu-id="7bb00-209">Dodawanie klasy do obsługi tworzyć i edytować instruktora strony</span><span class="sxs-lookup"><span data-stu-id="7bb00-209">Add classes to support Create and Edit instructor pages</span></span>

<span data-ttu-id="7bb00-210">Utwórz *SchoolViewModels/AssignedCourseData.cs* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7bb00-210">Create *SchoolViewModels/AssignedCourseData.cs* with the following code:</span></span>

[!code-csharp[Main](intro/samples/cu/Models/SchoolViewModels/AssignedCourseData.cs)]

<span data-ttu-id="7bb00-211">`AssignedCourseData` Klasa zawiera danych, aby utworzyć pól wyboru dla przypisanych kursy przez instruktora.</span><span class="sxs-lookup"><span data-stu-id="7bb00-211">The `AssignedCourseData` class contains data to create the check boxes for assigned courses by an instructor.</span></span>

<span data-ttu-id="7bb00-212">Utwórz *Pages/Instructors/InstructorCoursesPageModel.cshtml.cs* klasy podstawowej:</span><span class="sxs-lookup"><span data-stu-id="7bb00-212">Create the *Pages/Instructors/InstructorCoursesPageModel.cshtml.cs* base class:</span></span>

[!code-csharp[Main](intro/samples/cu/Pages/Instructors/InstructorCoursesPageModel.cshtml.cs)]

<span data-ttu-id="7bb00-213">`InstructorCoursesPageModel` Jest klasą podstawową będzie używane do edycji i tworzenia modeli strony.</span><span class="sxs-lookup"><span data-stu-id="7bb00-213">The `InstructorCoursesPageModel` is the base class you will use for the Edit and Create page models.</span></span> <span data-ttu-id="7bb00-214">`PopulateAssignedCourseData`odczytuje wszystkie `Course` jednostek do wypełnienia `AssignedCourseDataList`.</span><span class="sxs-lookup"><span data-stu-id="7bb00-214">`PopulateAssignedCourseData` reads all `Course` entities to populate `AssignedCourseDataList`.</span></span> <span data-ttu-id="7bb00-215">Dla każdego kursu kod ustawia `CourseID`, tytuł i czy nie jest przypisany do kursu instruktora.</span><span class="sxs-lookup"><span data-stu-id="7bb00-215">For each course, the code sets the `CourseID`, title, and whether or not the instructor is assigned to the course.</span></span> <span data-ttu-id="7bb00-216">A [zestaw HashSet](https://docs.microsoft.com/dotnet/api/system.collections.generic.hashset-1) służy do tworzenia wydajne wyszukiwań.</span><span class="sxs-lookup"><span data-stu-id="7bb00-216">A [HashSet](https://docs.microsoft.com/dotnet/api/system.collections.generic.hashset-1) is used to create efficient lookups.</span></span>

### <a name="instructors-edit-page-model"></a><span data-ttu-id="7bb00-217">Instruktorów edycji strony modelu</span><span class="sxs-lookup"><span data-stu-id="7bb00-217">Instructors Edit page model</span></span>

<span data-ttu-id="7bb00-218">Aktualizacja modelu strony Edytuj instruktora następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7bb00-218">Update the instructor Edit page model with the following code:</span></span>

[!code-csharp[Main](intro/samples/cu/Pages/Instructors/Edit.cshtml.cs?name=snippet&highlight=1,20-24,30,34,41-)]

<span data-ttu-id="7bb00-219">Poprzedni kod obsługi zmian w przypisaniu pakietu office.</span><span class="sxs-lookup"><span data-stu-id="7bb00-219">The preceding code handles office assignment changes.</span></span>

<span data-ttu-id="7bb00-220">Aktualizacja instruktora widoku Razor:</span><span class="sxs-lookup"><span data-stu-id="7bb00-220">Update the instructor Razor View:</span></span>

[!code-cshtml[Main](intro/samples/cu/Pages/Instructors/Edit.cshtml?highlight=34-59)]

<a id="notepad"></a>
> [!NOTE]
> <span data-ttu-id="7bb00-221">Po wklejeniu kodu w programie Visual Studio, podziały wiersza są zmieniane w taki sposób, który dzieli kod.</span><span class="sxs-lookup"><span data-stu-id="7bb00-221">When you paste the code in Visual Studio, line breaks are changed in a way that breaks the code.</span></span> <span data-ttu-id="7bb00-222">Naciśnij klawisze Ctrl + Z jeden raz, aby cofnąć automatycznego formatowania.</span><span class="sxs-lookup"><span data-stu-id="7bb00-222">Press Ctrl+Z one time to undo the automatic formatting.</span></span> <span data-ttu-id="7bb00-223">CTRL + Z rozwiązuje podziały wierszy, dzięki czemu wyglądają tu wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="7bb00-223">Ctrl+Z fixes the line breaks so that they look like what you see here.</span></span> <span data-ttu-id="7bb00-224">Wcięcie nie musi być idealne, ale `@</tr><tr>`, `@:<td>`, `@:</td>`, i `@:</tr>` linie muszą być w jednym wierszu jak pokazano.</span><span class="sxs-lookup"><span data-stu-id="7bb00-224">The indentation doesn't have to be perfect, but the `@</tr><tr>`, `@:<td>`, `@:</td>`, and `@:</tr>` lines must each be on a single line as shown.</span></span> <span data-ttu-id="7bb00-225">Z bloku nowy kod zaznaczone naciśnij klawisz Tab trzykrotnie Aby wyrównać nowy kod z istniejącym kodem.</span><span class="sxs-lookup"><span data-stu-id="7bb00-225">With the block of new code selected, press Tab three times to line up the new code with the existing code.</span></span> <span data-ttu-id="7bb00-226">Głosowania lub sprawdzić stan tej usterki [z tym łączem](https://developercommunity.visualstudio.com/content/problem/147795/razor-editor-malforms-pasted-markup-and-creates-in.html).</span><span class="sxs-lookup"><span data-stu-id="7bb00-226">Vote on or review the status of this bug [with this link](https://developercommunity.visualstudio.com/content/problem/147795/razor-editor-malforms-pasted-markup-and-creates-in.html).</span></span>

<span data-ttu-id="7bb00-227">Poprzedni kod tworzy tabelę HTML, który zawiera trzy kolumny.</span><span class="sxs-lookup"><span data-stu-id="7bb00-227">The preceding code creates an HTML table that has three columns.</span></span> <span data-ttu-id="7bb00-228">Każda kolumna ma postać pola wyboru i podpis zawierający kursu numer i tytuł.</span><span class="sxs-lookup"><span data-stu-id="7bb00-228">Each column has a check box and a caption containing the course number and title.</span></span> <span data-ttu-id="7bb00-229">Wszystkie pola wyboru mają taką samą nazwę ("selectedCourses").</span><span class="sxs-lookup"><span data-stu-id="7bb00-229">The check boxes all have the same name ("selectedCourses").</span></span> <span data-ttu-id="7bb00-230">Przy użyciu tej samej nazwie informuje integratora modelu je traktować jako grupa.</span><span class="sxs-lookup"><span data-stu-id="7bb00-230">Using the same name informs the model binder to treat them as a group.</span></span> <span data-ttu-id="7bb00-231">Ustawiono atrybut wartość każdego pola wyboru `CourseID`.</span><span class="sxs-lookup"><span data-stu-id="7bb00-231">The value attribute of each check box is set to `CourseID`.</span></span> <span data-ttu-id="7bb00-232">Gdy strona jest przesyłana, integratora modelu przekazuje tablicę, która składa się z `CourseID` wartości dla pola wyboru, które są wybrane.</span><span class="sxs-lookup"><span data-stu-id="7bb00-232">When the page is posted, the model binder passes an array that consists of the `CourseID` values for only the check boxes that are selected.</span></span>

<span data-ttu-id="7bb00-233">Gdy pola wyboru początkowo są renderowane, kursy przypisane do instruktora zaznaczono atrybutów.</span><span class="sxs-lookup"><span data-stu-id="7bb00-233">When the check boxes are initially rendered, courses assigned to the instructor have checked attributes.</span></span>

<span data-ttu-id="7bb00-234">Uruchom aplikację i przetestować zaktualizowane instruktorów edycji strony.</span><span class="sxs-lookup"><span data-stu-id="7bb00-234">Run the app and test the updated instructors Edit page.</span></span> <span data-ttu-id="7bb00-235">Zmiana przypisania niektórych kursu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-235">Change some course assignments.</span></span> <span data-ttu-id="7bb00-236">Zmiany zostaną odzwierciedlone na stronie indeksu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-236">The changes are reflected on the Index page.</span></span>

<span data-ttu-id="7bb00-237">Uwaga: w tym miejscu podejście do edytowania danych kursu instruktora dobrze działa w przypadku istnieje ograniczona liczba kursów.</span><span class="sxs-lookup"><span data-stu-id="7bb00-237">Note: The approach taken here to edit instructor course data works well when there is a limited number of courses.</span></span> <span data-ttu-id="7bb00-238">Kolekcje, które są znacznie większe innego interfejsu użytkownika i różne metody aktualizacji będzie bardziej użyteczny i efektywny.</span><span class="sxs-lookup"><span data-stu-id="7bb00-238">For collections that are much larger, a different UI and a different updating method would be more useable and efficient.</span></span>

### <a name="update-the-instructors-create-page"></a><span data-ttu-id="7bb00-239">Aktualizacja instruktorów tworzenia strony</span><span class="sxs-lookup"><span data-stu-id="7bb00-239">Update the instructors Create page</span></span>

<span data-ttu-id="7bb00-240">Aktualizacja modelu strony Utwórz instruktora następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7bb00-240">Update the instructor Create page model with the following code:</span></span>

[!code-csharp[Main](intro/samples/cu/Pages/Instructors/Create.cshtml.cs)]

<span data-ttu-id="7bb00-241">Poprzedni kod jest podobny do *Pages/Instructors/Edit.cshtml.cs* kodu.</span><span class="sxs-lookup"><span data-stu-id="7bb00-241">The preceding code is similar to the *Pages/Instructors/Edit.cshtml.cs* code.</span></span>

<span data-ttu-id="7bb00-242">Zaktualizuj strony tworzenia Razor instruktora o następujący kod:</span><span class="sxs-lookup"><span data-stu-id="7bb00-242">Update the instructor Create Razor page with the following markup:</span></span>

[!code-cshtml[Main](intro/samples/cu/Pages/Instructors/Create.cshtml?highlight=32-62)]

<span data-ttu-id="7bb00-243">Przetestuj instruktora tworzenia strony.</span><span class="sxs-lookup"><span data-stu-id="7bb00-243">Test the instructor Create page.</span></span>

## <a name="update-the-delete-page"></a><span data-ttu-id="7bb00-244">Zaktualizuj strony usuwania</span><span class="sxs-lookup"><span data-stu-id="7bb00-244">Update the Delete page</span></span>

<span data-ttu-id="7bb00-245">Aktualizacja modelu strony Usuń z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7bb00-245">Update the Delete page model with the following code:</span></span>

[!code-csharp[Main](intro/samples/cu/Pages/Instructors/Delete.cshtml.cs?highlight=5,40-)]

<span data-ttu-id="7bb00-246">Poprzedni kod wprowadza następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="7bb00-246">The preceding code makes the following changes:</span></span>

* <span data-ttu-id="7bb00-247">Używa wczesny ładowania dla `CourseAssignments` właściwości nawigacji.</span><span class="sxs-lookup"><span data-stu-id="7bb00-247">Uses eager loading for the `CourseAssignments` navigation property.</span></span> <span data-ttu-id="7bb00-248">`CourseAssignments`muszą być włączone lub nie są one usuwane po usunięciu instruktora.</span><span class="sxs-lookup"><span data-stu-id="7bb00-248">`CourseAssignments` must be included or they aren't deleted when the instructor is deleted.</span></span> <span data-ttu-id="7bb00-249">Aby uniknąć konieczności je odczytać, należy skonfigurować usuwanie kaskadowe w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="7bb00-249">To avoid needing to read them, configure cascade delete in the database.</span></span>

* <span data-ttu-id="7bb00-250">Jeśli instruktora do usunięcia jest przypisany jako administrator działy, usuwa przypisanie instruktora z tych działów.</span><span class="sxs-lookup"><span data-stu-id="7bb00-250">If the instructor to be deleted is assigned as administrator of any departments, removes the instructor assignment from those departments.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="7bb00-251">[Poprzednie](xref:data/ef-rp/read-related-data)
[dalej](xref:data/ef-rp/concurrency)</span><span class="sxs-lookup"><span data-stu-id="7bb00-251">[Previous](xref:data/ef-rp/read-related-data)
[Next](xref:data/ef-rp/concurrency)</span></span>