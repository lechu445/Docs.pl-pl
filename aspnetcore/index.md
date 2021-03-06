---
title: Wprowadzenie do platformy ASP.NET Core
author: rick-anderson
description: Zapoznaj się z wprowadzeniem do rozwiązania ASP.NET Core, czyli międzyplatformowej struktury typu open source o wysokiej wydajności służącej do tworzenia nowoczesnych aplikacji internetowych opartych na chmurze.
ms.author: riande
ms.custom: mvc
ms.date: 01/15/2019
uid: index
ms.openlocfilehash: e7c81ff82e5206a5aca217417f6cb1c339d72e89
ms.sourcegitcommit: 42a8164b8aba21f322ffefacb92301bdfb4d3c2d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54341410"
---
# <a name="introduction-to-aspnet-core"></a>Wprowadzenie do platformy ASP.NET Core

[Daniel Roth](https://github.com/danroth27), [Rick Anderson](https://twitter.com/RickAndMSFT) i [Shaun Luttin](https://twitter.com/dicshaunary)

ASP.NET Core to międzyplatformowa struktura typu [open source](https://github.com/aspnet/home) o wysokiej wydajności służąca do tworzenia nowoczesnych aplikacji internetowych opartych na chmurze. Platforma ASP.NET Core umożliwia:

* Kompilowanie aplikacji i usług internetowych, aplikacji [IoT](https://www.microsoft.com/internet-of-things/) i zapleczy mobilnych.
* Używanie ulubionych narzędzi programistycznych w systemach Windows, macOS i Linux.
* Wdrażanie w chmurze lub lokalnie.
* Uruchamianie aplikacji na platformie [.NET Core lub .NET Framework](/dotnet/articles/standard/choosing-core-framework-server).

## <a name="why-use-aspnet-core"></a>Dlaczego warto korzystać z platformy ASP.NET Core?

Miliony deweloperów korzystają z platformy [ASP.NET 4.x](/aspnet/overview) do tworzenia aplikacji internetowych. ASP.NET Core to przeprojektowana platforma ASP.NET 4.x, w której wprowadzono zmiany architektoniczne w celu stworzenia bardziej zwartej i modułowej struktury.

[!INCLUDE[](~/includes/benefits.md)]

## <a name="build-web-apis-and-web-ui-using-aspnet-core-mvc"></a>Tworzenie internetowego interfejsu użytkownika i internetowych interfejsów API przy użyciu wzorca MVC platformy ASP.NET Core

Platforma ASP.NET Core MVC udostępnia funkcje, które umożliwiają tworzenie [internetowych interfejsów API](xref:tutorials/first-web-api) i [aplikacji](xref:tutorials/razor-pages/index):

* Wzorzec [MVC (Model View Controller)](xref:mvc/overview) umożliwia testowanie internetowych interfejsów API i aplikacji.
* [Razor Pages](xref:razor-pages/index) to oparty na stronach model programowania, który umożliwia łatwiejsze i bardziej wydajne tworzenie internetowego interfejsu użytkownika.
* [Składnia Razor](xref:mvc/views/razor) zapewnia wydajny język dla [stron Razor](xref:razor-pages/index) i [widoków MVC](xref:mvc/views/overview).
* Specjalne funkcje pomocnicze (tzw. [pomocnicy tagów](xref:mvc/views/tag-helpers/intro)) umożliwiają tworzenie i renderowanie elementów HTML w plikach Razor z użyciem kodu po stronie serwera.
* Wbudowana obsługa [wielu formatów danych i negocjacji zawartości](xref:web-api/advanced/formatting) umożliwia internetowym interfejsom API nawiązywanie połączeń z szeroką gamą klientów (dotyczy to m.in. przeglądarek i urządzeń przenośnych).
* [Powiązanie modelu](xref:mvc/models/model-binding) automatycznie mapuje dane z żądań HTTP na parametry metod akcji.
* [Walidacja modelu](xref:mvc/models/validation) automatycznie przeprowadza walidację po stronie klienta i serwera.

## <a name="client-side-development"></a>Programowanie po stronie klienta

Platforma ASP.NET Core bezproblemowo integruje się z popularnymi strukturami i bibliotekami po stronie klienta, takimi jak [Angular](xref:spa/angular), [React](xref:spa/react) czy [Bootstrap](https://getbootstrap.com/). Aby uzyskać więcej informacji, zobacz [Programowanie po stronie klienta](xref:client-side/index).

<a name="target-framework"></a>

## <a name="aspnet-core-targeting-net-framework"></a>Platforma ASP.NET Core ukierunkowana na .NET Framework

Platforma ASP.NET Core 2.x umożliwia obsługę aplikacji dedykowanych rozwiązaniom .NET Core lub .NET Framework. Aplikacje platformy ASP.NET Core ukierunkowane na rozwiązanie .NET Framework nie są wieloplatformowe &mdash; działają tylko w systemie Windows. Ogólnie rzecz biorąc, platforma ASP.NET Core 2.x jest zbudowana z bibliotek [.NET Standard](/dotnet/standard/net-standard). Aplikacje napisane przy użyciu platformy .NET Standard 2.0 działają wszędzie tam, gdzie obsługiwana jest platforma .NET Standard 2.0.

Platforma ASP.NET Core 2.x jest obsługiwana w wersjach .NET Framework zgodnych z .NET Standard 2.0:

* Zdecydowanie zaleca się wersję .NET Framework 4.7.1 lub nowszą.
* Platforma .NET Framework 4.6.1 lub nowsza.

Platforma ASP.NET Core 3.0 i nowsze wersje będą działać tylko na platformie .NET Core. Aby uzyskać więcej informacji o tej zmianie, zobacz [A first look at changes coming in ASP.NET Core 3.0](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0/) (Pierwsze spojrzenie na zmiany wprowadzane na platformie ASP.NET Core 3.0).

Tworzenie rozwiązań ukierunkowanych na .NET Core jest korzystne z wielu względów, a przewaga tej platformy rośnie z każdym wydaniem. Oto niektóre z czynników wpływających na przewagę platformy .NET Core nad .NET Framework:

* Wieloplatformowość. Działanie w systemach macOS, Linux i Windows.
* Większa wydajność
* Równoległa obsługa różnych wersji
* Nowe interfejsy API
* Kod open source

Ciężko pracujemy nad zlikwidowaniem rozbieżności między interfejsami API platform .NET Framework i .NET Core. Pakiet [Windows Compatibility Pack](/dotnet/core/porting/windows-compat-pack) udostępnił tysiące interfejsów API specyficznych dla systemu Windows na platformie .NET Core. Te interfejsy API nie były dostępne na platformie .NET Core 1.x.

## <a name="how-to-download-a-sample"></a>Instrukcje: pobieranie pliku

Wiele artykułów i samouczków zawiera linki do przykładów kodu.

1. [Pobierz plik zip repozytorium ASP.NET](https://codeload.github.com/aspnet/Docs/zip/master).
1. Rozpakuj plik *Docs-master.zip*.
1. Przejdź do katalogu przykładu, korzystając z adresu URL linku przykładu.

### <a name="preprocessor-directives-in-sample-code"></a>Dyrektywy preprocesora w przykładowym kodzie

Aby zademonstrować wiele scenariuszy, przykładowe aplikacje używają instrukcji `#define` i `#if-#else/#elif-#endif` języka C# do selektywnego kompilowania i uruchamiania różnych sekcji przykładowego kodu. Jeśli chcesz skorzystać z tej możliwości w tych przykładach, ustaw instrukcję `#define` w górnej części plików języka C# na symbol skojarzony ze scenariuszem, który chcesz uruchomić. Niektóre przykłady mogą wymagać ustawienia symbolu w górnej części wielu plików, aby umożliwić uruchomienie scenariusza.

Na przykład następująca lista symboli `#define` wskazuje, że są dostępne cztery scenariusze (jeden scenariusz na symbol). Aktualna konfiguracja przykładu powoduje uruchomienie scenariusza `TemplateCode`:

```csharp
#define TemplateCode // or LogFromMain or ExpandDefault or FilterInCode
```

Aby zmienić przykład w celu uruchomienia scenariusza `ExpandDefault`, zdefiniuj symbol `ExpandDefault` i pozostaw pozostałe symbole jako przekształcone w komentarz:

```csharp
#define ExpandDefault // TemplateCode or LogFromMain or FilterInCode
```

Więcej informacji na temat używania [ dyrektyw preprocesora języka C#](/dotnet/csharp/language-reference/preprocessor-directives/) do selektywnego kompilowania sekcji kodu można znaleźć w tematach [#define (C# Reference)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-define) (#define (dokumentacja języka C#)) i [#if (C# Reference)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) (#if (dokumentacja języka C#)).

### <a name="regions-in-sample-code"></a>Regiony w przykładowym kodzie

Niektóre przykładowe aplikacje zawierają sekcje kodu ujęte w instrukcje [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) i [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) języka C#. System tworzenia dokumentacji wstawia te regiony do renderowanych tematów dokumentacji.  

Nazwy regionów zwykle zawierają wyraz „snippet”. W poniższym przykładzie pokazano region o nazwie `snippet_FilterInCode`:

```csharp
#region snippet_FilterInCode
WebHost.CreateDefaultBuilder(args)
    .UseStartup<Startup>()
    .ConfigureLogging(logging =>
        logging.AddFilter("System", LogLevel.Debug)
            .AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Trace))
            .Build();
#endregion
```

Wcześniejszy fragment kodu w języku C# jest przywoływany w pliku markdown tematu za pomocą następującego wiersza:

```
[!code-csharp[](sample/SampleApp/Program.cs?name=snippet_FilterInCode)]
```

Możesz bezpiecznie zignorować (lub usunąć) instrukcje `#region` i `#endregion` otaczające kod. Jeśli planujesz uruchamiać przykładowy scenariusz opisany w temacie, nie zmieniaj kodu między tymi instrukcjami. Kod możesz swobodnie modyfikować, eksperymentując z innymi scenariuszami.

Aby uzyskać więcej informacji, zobacz [Współtworzenie dokumentacji platformy ASP.NET: fragmenty kodu](https://github.com/aspnet/Docs/blob/master/CONTRIBUTING.md#code-snippets).

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji, zobacz następujące zasoby:

* [Wprowadzenie do korzystania ze stron Razor](xref:tutorials/razor-pages/razor-pages-start)
* <xref:tutorials/publish-to-azure-webapp-using-vs>
* [Platforma ASP.NET Core — podstawy](xref:fundamentals/index)
* [Cotygodniowe podsumowanie ASP.NET Community Standup](https://live.asp.net/) zawiera aktualności o postępach i planach zespołu. Zawiera też informacje o polecanych blogach i oprogramowaniu innych firm.
