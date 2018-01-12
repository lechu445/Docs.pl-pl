---
uid: signalr/overview/getting-started/introduction-to-signalr
title: Wprowadzenie do SignalR | Dokumentacja firmy Microsoft
author: pfletcher
description: "W tym artykule opisano, co to jest SignalR i niektóre rozwiązania, który został zaprojektowany do utworzenia."
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/10/2014
ms.topic: article
ms.assetid: 0fab5e35-8c1f-43d4-8635-b8aba8766a71
ms.technology: dotnet-signalr
ms.prod: .net-framework
msc.legacyurl: /signalr/overview/getting-started/introduction-to-signalr
msc.type: authoredcontent
ms.openlocfilehash: 27150d314b6861f1098e6ef4a7de94e7b371a78e
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2017
---
<a name="introduction-to-signalr"></a><span data-ttu-id="f516c-103">Wprowadzenie do SignalR</span><span class="sxs-lookup"><span data-stu-id="f516c-103">Introduction to SignalR</span></span>
====================
<span data-ttu-id="f516c-104">przez [Patrick Fletcher](https://github.com/pfletcher)</span><span class="sxs-lookup"><span data-stu-id="f516c-104">by [Patrick Fletcher](https://github.com/pfletcher)</span></span>

> <span data-ttu-id="f516c-105">W tym artykule opisano, co to jest SignalR i niektóre rozwiązania, który został zaprojektowany do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="f516c-105">This article describes what SignalR is, and some of the solutions it was designed to create.</span></span> 
> 
> ## <a name="questions-and-comments"></a><span data-ttu-id="f516c-106">Pytania i komentarze</span><span class="sxs-lookup"><span data-stu-id="f516c-106">Questions and comments</span></span>
> 
> <span data-ttu-id="f516c-107">Wystaw opinię na jak zbędne tego samouczka i jakie firma Microsoft może poprawić w komentarze u dołu strony.</span><span class="sxs-lookup"><span data-stu-id="f516c-107">Please leave feedback on how you liked this tutorial and what we could improve in the comments at the bottom of the page.</span></span> <span data-ttu-id="f516c-108">Jeśli masz pytania, które nie są bezpośrednio związane z tego samouczka możesz zamieścić je do [forum ASP.NET SignalR](https://forums.asp.net/1254.aspx/1?ASP+NET+SignalR) lub [StackOverflow.com](http://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="f516c-108">If you have questions that are not directly related to the tutorial, you can post them to the [ASP.NET SignalR forum](https://forums.asp.net/1254.aspx/1?ASP+NET+SignalR) or [StackOverflow.com](http://stackoverflow.com/).</span></span>


## <a name="what-is-signalr"></a><span data-ttu-id="f516c-109">Co to jest SignalR?</span><span class="sxs-lookup"><span data-stu-id="f516c-109">What is SignalR?</span></span>

<span data-ttu-id="f516c-110">Biblioteka SignalR platformy ASP.NET to biblioteka dla deweloperów platformy ASP.NET, które upraszcza proces dodawania funkcji sieci web w czasie rzeczywistym do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f516c-110">ASP.NET SignalR is a library for ASP.NET developers that simplifies the process of adding real-time web functionality to applications.</span></span> <span data-ttu-id="f516c-111">Funkcje sieci web w czasie rzeczywistym jest możliwość server przekazywanie zawartości przez kod do połączonych klientów natychmiast po jej udostępnieniu, zamiast serwera, poczekaj, aż klientowi żądanie nowych danych.</span><span class="sxs-lookup"><span data-stu-id="f516c-111">Real-time web functionality is the ability to have server code push content to connected clients instantly as it becomes available, rather than having the server wait for a client to request new data.</span></span>

<span data-ttu-id="f516c-112">SignalR można dodać dowolny rodzaj funkcji "w czasie rzeczywistym" sieci web do aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f516c-112">SignalR can be used to add any sort of "real-time" web functionality to your ASP.NET application.</span></span> <span data-ttu-id="f516c-113">Podczas rozmowy jest często używana jako przykład, możesz zrobić wiele więcej.</span><span class="sxs-lookup"><span data-stu-id="f516c-113">While chat is often used as an example, you can do a whole lot more.</span></span> <span data-ttu-id="f516c-114">Wszystkie razem, kiedy użytkownik odświeża strony sieci web, aby zobaczyć nowe dane, lub implementuje stronę [długiego sondowania](http://en.wikipedia.org/wiki/Push_technology#Long_polling) można pobrać nowe dane, jest kandydatem do przy użyciu SignalR.</span><span class="sxs-lookup"><span data-stu-id="f516c-114">Any time a user refreshes a web page to see new data, or the page implements [long polling](http://en.wikipedia.org/wiki/Push_technology#Long_polling) to retrieve new data, it is a candidate for using SignalR.</span></span> <span data-ttu-id="f516c-115">Przykłady obejmują pulpitów nawigacyjnych i monitorowania aplikacji, współpracy aplikacji (takich jak jednoczesne edytowanie dokumentów), zadań, aktualizacje postępu i formularzy w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="f516c-115">Examples include dashboards and monitoring applications, collaborative applications (such as simultaneous editing of documents), job progress updates, and real-time forms.</span></span>

<span data-ttu-id="f516c-116">SignalR umożliwia również całkowicie nowych typów aplikacji sieci web, które wymagają wysokiej częstotliwości aktualizacji z serwera, na przykład w czasie rzeczywistym gier.</span><span class="sxs-lookup"><span data-stu-id="f516c-116">SignalR also enables completely new types of web applications that require high frequency updates from the server, for example, real-time gaming.</span></span> <span data-ttu-id="f516c-117">Na dużą przykład tego, zobacz [ShootR gier.](http://shootr.signalr.net/)</span><span class="sxs-lookup"><span data-stu-id="f516c-117">For a great example of this, see the [ShootR game.](http://shootr.signalr.net/)</span></span>

<span data-ttu-id="f516c-118">Biblioteka SignalR udostępnia prosty interfejs API do tworzenia klienta serwera zdalnych wywołań procedur (RPC) które wywołują funkcje JavaScript w kliencie w przeglądarkach (i innych platform klienta), z kodu .NET po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="f516c-118">SignalR provides a simple API for creating server-to-client remote procedure calls (RPC) that call JavaScript functions in client browsers (and other client platforms) from server-side .NET code.</span></span> <span data-ttu-id="f516c-119">Biblioteka SignalR zawiera też interfejs API umożliwiający zarządzanie połączeniami (na przykład nawiązywanie i zakańczanie zdarzeń) i grupowanie połączeń.</span><span class="sxs-lookup"><span data-stu-id="f516c-119">SignalR also includes API for connection management (for instance, connect and disconnect events), and grouping connections.</span></span>

![Wywoływanie metody z SignalR](introduction-to-signalr/_static/image1.png)

<span data-ttu-id="f516c-121">SignalR automatycznie obsługuje zarządzanie połączeniami i umożliwia komunikatów rozgłaszanych do wszystkich klientów podłączonych równocześnie, takich jak pokoju rozmów.</span><span class="sxs-lookup"><span data-stu-id="f516c-121">SignalR handles connection management automatically, and lets you broadcast messages to all connected clients simultaneously, like a chat room.</span></span> <span data-ttu-id="f516c-122">Można również wysyłać wiadomości do określonych klientów.</span><span class="sxs-lookup"><span data-stu-id="f516c-122">You can also send messages to specific clients.</span></span> <span data-ttu-id="f516c-123">Połączenie między klientem a serwerem jest trwała, w przeciwieństwie do klasycznego połączenia HTTP, nawiązane ponownie dla każdego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f516c-123">The connection between the client and server is persistent, unlike a classic HTTP connection, which is re-established for each communication.</span></span>

<span data-ttu-id="f516c-124">SignalR obsługuje funkcje "serwera wypychania", w którym kod serwera, można umieszczać kod klienta w przeglądarce, za pomocą zdalnego wywołania procedury (RPC), zamiast wspólnego modelu żądań i odpowiedzi w sieci web dzisiaj.</span><span class="sxs-lookup"><span data-stu-id="f516c-124">SignalR supports "server push" functionality, in which server code can call out to client code in the browser using Remote Procedure Calls (RPC), rather than the request-response model common on the web today.</span></span>

<span data-ttu-id="f516c-125">Aplikacji SignalR można skalować w poziomie do tysięcy klientów przy użyciu usługi Service Bus, programu SQL Server lub [Redis](http://redis.io).</span><span class="sxs-lookup"><span data-stu-id="f516c-125">SignalR applications can scale out to thousands of clients using Service Bus, SQL Server or [Redis](http://redis.io).</span></span>

<span data-ttu-id="f516c-126">SignalR to open source, dostępny za pośrednictwem [GitHub](https://github.com/signalr).</span><span class="sxs-lookup"><span data-stu-id="f516c-126">SignalR is open-source, accessible through [GitHub](https://github.com/signalr).</span></span>

## <a name="signalr-and-websocket"></a><span data-ttu-id="f516c-127">SignalR i protokołu WebSocket</span><span class="sxs-lookup"><span data-stu-id="f516c-127">SignalR and WebSocket</span></span>

<span data-ttu-id="f516c-128">SignalR używa nowego transportu protokołu WebSocket, jeśli jest on dostępny i powraca do starszych transporty w miarę potrzeby.</span><span class="sxs-lookup"><span data-stu-id="f516c-128">SignalR uses the new WebSocket transport where available, and falls back to older transports where necessary.</span></span> <span data-ttu-id="f516c-129">Podczas pisania można pewnością aplikacji bezpośrednio za pomocą protokołu WebSocket, używając SignalR oznacza, że wiele dodatkowe funkcje, które należy zaimplementować będzie już zostały wykonane dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="f516c-129">While you could certainly write your application using WebSocket directly, using SignalR means that a lot of the extra functionality you would need to implement will already have been done for you.</span></span> <span data-ttu-id="f516c-130">Co najważniejsze oznacza to, że można kodu aplikacji, aby móc korzystać z protokołu WebSocket bez konieczności martwić tworzenia ścieżki kodu oddzielne starszych klientów.</span><span class="sxs-lookup"><span data-stu-id="f516c-130">Most importantly, this means that you can code your application to take advantage of WebSocket without having to worry about creating a separate code path for older clients.</span></span> <span data-ttu-id="f516c-131">SignalR również osłony można z martwiąc się o aktualizacje protokołu WebSocket, ponieważ SignalR nadal będzie zostać zaktualizowany do obsługi zmian w podstawowym transportu aplikacji spójny interfejs między wersjami protokołu WebSocket.</span><span class="sxs-lookup"><span data-stu-id="f516c-131">SignalR also shields you from having to worry about updates to WebSocket, since SignalR will continue to be updated to support changes in the underlying transport, providing your application a consistent interface across versions of WebSocket.</span></span>

<span data-ttu-id="f516c-132">Na pewno może tworzyć rozwiązania za pomocą protokołu WebSocket wyłącznie, SignalR zawiera wszystkie funkcje, należy zapisać użytkownika, takie jak powrotu do innego transportu i modyfikowania aplikacji w celu aktualizacji do implementacji protokołu WebSocket.</span><span class="sxs-lookup"><span data-stu-id="f516c-132">While you could certainly create a solution using WebSocket alone, SignalR provides all of the functionality you would need to write yourself, such as fallback to other transports and revising your application for updates to WebSocket implementations.</span></span>

<a id="transports"></a>

## <a name="transports-and-fallbacks"></a><span data-ttu-id="f516c-133">Transporty i przejścia</span><span class="sxs-lookup"><span data-stu-id="f516c-133">Transports and fallbacks</span></span>

<span data-ttu-id="f516c-134">SignalR to Abstrakcja przez niektóre transportów, które są wymagane do pracy w czasie rzeczywistym między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="f516c-134">SignalR is an abstraction over some of the transports that are required to do real-time work between client and server.</span></span> <span data-ttu-id="f516c-135">Połączenia SignalR rozpoczyna się jako HTTP, a następnie jest podwyższany do połączenia obiektu WebSocket, jeśli jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="f516c-135">A SignalR connection starts as HTTP, and is then promoted to a WebSocket connection if it is available.</span></span> <span data-ttu-id="f516c-136">Protokół WebSocket jest idealny transportu dla biblioteki SignalR, ponieważ sprawia, że najbardziej efektywne wykorzystanie pamięci serwera, ma ona uzyskać najmniejsze opóźnienia i ma większość funkcji (na przykład pełnego dupleksu komunikacji między klientem i serwerem), ale ma także najbardziej rygorystyczne wymagania dotyczące: WebSocket wymaga serwera z systemem Windows Server 2012 lub Windows 8 i .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="f516c-136">WebSocket is the ideal transport for SignalR, since it makes the most efficient use of server memory, has the lowest latency, and has the most underlying features (such as full duplex communication between client and server), but it also has the most stringent requirements: WebSocket requires the server to be using Windows Server 2012 or Windows 8, and .NET Framework 4.5.</span></span> <span data-ttu-id="f516c-137">Jeśli te wymagania nie są spełnione, SignalR spróbuje Użyj innego transportu, aby wprowadzić jego połączenia.</span><span class="sxs-lookup"><span data-stu-id="f516c-137">If these requirements are not met, SignalR will attempt to use other transports to make its connections.</span></span>

### <a name="html-5-transports"></a><span data-ttu-id="f516c-138">Transporty HTML 5</span><span class="sxs-lookup"><span data-stu-id="f516c-138">HTML 5 transports</span></span>

<span data-ttu-id="f516c-139">Transporty te są zależne od obsługę [HTML 5](http://en.wikipedia.org/wiki/HTML5).</span><span class="sxs-lookup"><span data-stu-id="f516c-139">These transports depend on support for [HTML 5](http://en.wikipedia.org/wiki/HTML5).</span></span> <span data-ttu-id="f516c-140">Jeśli przeglądarka klienta nie obsługuje standardu HTML 5, będą używane starsze transportów.</span><span class="sxs-lookup"><span data-stu-id="f516c-140">If the client browser does not support the HTML 5 standard, older transports will be used.</span></span>

- <span data-ttu-id="f516c-141">**Protokół WebSocket** (Jeśli serwer i przeglądarki wskazują one obsługi protokołu Websocket).</span><span class="sxs-lookup"><span data-stu-id="f516c-141">**WebSocket** (if the both the server and browser indicate they can support Websocket).</span></span> <span data-ttu-id="f516c-142">Protokół WebSocket jest tylko transport, który określa wartość true, trwałe, dwukierunkowe połączenie między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="f516c-142">WebSocket is the only transport that establishes a true persistent, two-way connection between client and server.</span></span> <span data-ttu-id="f516c-143">Jednak WebSocket ma wymagania najbardziej rygorystyczne; jest w pełni obsługiwana tylko w najnowszej wersji programu Microsoft Internet Explorer i Google Chrome, Mozilla Firefox i zawiera tylko częściowe wdrożenie w innych przeglądarkach, takie jak Opera i Safari.</span><span class="sxs-lookup"><span data-stu-id="f516c-143">However, WebSocket also has the most stringent requirements; it is fully supported only in the latest versions of Microsoft Internet Explorer, Google Chrome, and Mozilla Firefox, and only has a partial implementation in other browsers such as Opera and Safari.</span></span>
- <span data-ttu-id="f516c-144">**Zdarzenia wysyłane serwera**, znanej również jako źródła zdarzeń (Jeśli przeglądarka obsługuje wysyłane zdarzeń serwera, który jest zasadniczo wszystkie przeglądarki, z wyjątkiem programu Internet Explorer).</span><span class="sxs-lookup"><span data-stu-id="f516c-144">**Server Sent Events**, also known as EventSource (if the browser supports Server Sent Events, which is basically all browsers except Internet Explorer.)</span></span>

### <a name="comet-transports"></a><span data-ttu-id="f516c-145">Transporty kometa</span><span class="sxs-lookup"><span data-stu-id="f516c-145">Comet transports</span></span>

<span data-ttu-id="f516c-146">Następujące transportu są oparte na [kometa](http://en.wikipedia.org/wiki/Comet_(programming)) modelu aplikacji sieci web, w którym przeglądarki lub inne klienta obsługuje żądania HTTP przechowywane przez długi, którym serwer w szczególności wypychanie danych do klienta bez klienta programu żąda go.</span><span class="sxs-lookup"><span data-stu-id="f516c-146">The following transports are based on the [Comet](http://en.wikipedia.org/wiki/Comet_(programming)) web application model, in which a browser or other client maintains a long-held HTTP request, which the server can use to push data to the client without the client specifically requesting it.</span></span>

- <span data-ttu-id="f516c-147">**Nieskończona ramki** (dla programu Internet Explorer tylko).</span><span class="sxs-lookup"><span data-stu-id="f516c-147">**Forever Frame** (for Internet Explorer only).</span></span> <span data-ttu-id="f516c-148">Nieskończona ramki tworzy ukryte IFrame, dzięki czemu żądanie do punktu końcowego na serwerze, który nie zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="f516c-148">Forever Frame creates a hidden IFrame which makes a request to an endpoint on the server that does not complete.</span></span> <span data-ttu-id="f516c-149">Serwer następnie stale wysyła skryptu do klienta, który natychmiast zostanie wykonany, zapewniając połączenia jednokierunkowe w czasie rzeczywistym z serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="f516c-149">The server then continually sends script to the client which is immediately executed, providing a one-way realtime connection from server to client.</span></span> <span data-ttu-id="f516c-150">Połączenie z klienta do serwera używa oddzielnego połączenia z serwera do klienta połączenia i jak standardowe żądania HTTP, nowe połączenie jest tworzony dla każdego elementu danych, który ma być wysyłane.</span><span class="sxs-lookup"><span data-stu-id="f516c-150">The connection from client to server uses a separate connection from the server to client connection, and like a standard HTTP request, a new connection is created for each piece of data that needs to be sent.</span></span>
- <span data-ttu-id="f516c-151">**Długie sondowania AJAX**.</span><span class="sxs-lookup"><span data-stu-id="f516c-151">**Ajax long polling**.</span></span> <span data-ttu-id="f516c-152">Sondowanie długo nie tworzy trwałe połączenie, ale zamiast tego odpytuje serwer z żądaniem pozostanie otwarty, dopóki serwer odpowiada, w którym połączenie zostanie zamknięte i natychmiast zażądano nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="f516c-152">Long polling does not create a persistent connection, but instead polls the server with a request that stays open until the server responds, at which point the connection closes, and a new connection is requested immediately.</span></span> <span data-ttu-id="f516c-153">Może to powodować pewnego opóźnienia przesyłania podczas resetuje połączenie.</span><span class="sxs-lookup"><span data-stu-id="f516c-153">This may introduce some latency while the connection resets.</span></span>

<span data-ttu-id="f516c-154">Aby uzyskać więcej informacji na jakie transportu są obsługiwane w jakich konfiguracjach, zobacz [obsługiwane platformy](supported-platforms.md).</span><span class="sxs-lookup"><span data-stu-id="f516c-154">For more information on what transports are supported under which configurations, see [Supported Platforms](supported-platforms.md).</span></span>

### <a name="transport-selection-process"></a><span data-ttu-id="f516c-155">Procesu wyboru transportu</span><span class="sxs-lookup"><span data-stu-id="f516c-155">Transport selection process</span></span>

<span data-ttu-id="f516c-156">Na poniższej liście przedstawiono kroki, które używa SignalR, aby zdecydować, które transportu do użycia.</span><span class="sxs-lookup"><span data-stu-id="f516c-156">The following list shows the steps that SignalR uses to decide which transport to use.</span></span>

1. <span data-ttu-id="f516c-157">Jeśli zainstalowano przeglądarkę Internet Explorer 8 lub wcześniej, używany jest długa sondowania.</span><span class="sxs-lookup"><span data-stu-id="f516c-157">If the browser is Internet Explorer 8 or earlier, Long Polling is used.</span></span>
2. <span data-ttu-id="f516c-158">Jeśli skonfigurowano JSONP (oznacza to, `jsonp` parametr ma wartość `true` po uruchomieniu połączenia), długi sondowania jest używany.</span><span class="sxs-lookup"><span data-stu-id="f516c-158">If JSONP is configured (that is, the `jsonp` parameter is set to `true` when the connection is started), Long Polling is used.</span></span>
3. <span data-ttu-id="f516c-159">Jeśli między domenami jest nawiązywane połączenie (jeśli SignalR punktu końcowego nie jest w tej samej domenie co hostingu strony), następnie protokołu WebSocket zostaną użyte, jeśli są spełnione poniższe kryteria:</span><span class="sxs-lookup"><span data-stu-id="f516c-159">If a cross-domain connection is being made (that is, if the SignalR endpoint is not in the same domain as the hosting page), then WebSocket will be used if the following criteria are met:</span></span>

    - <span data-ttu-id="f516c-160">Klient obsługuje CORS (Cross-Origin Resource Sharing).</span><span class="sxs-lookup"><span data-stu-id="f516c-160">The client supports CORS (Cross-Origin Resource Sharing).</span></span> <span data-ttu-id="f516c-161">Aby uzyskać szczegółowe informacje, na których klienci obsługi mechanizmu CORS, zobacz [CORS w caniuse.com](http://www.caniuse.com/CORS).</span><span class="sxs-lookup"><span data-stu-id="f516c-161">For details on which clients support CORS, see [CORS at caniuse.com](http://www.caniuse.com/CORS).</span></span>
    - <span data-ttu-id="f516c-162">Klient obsługuje protokół WebSocket</span><span class="sxs-lookup"><span data-stu-id="f516c-162">The client supports WebSocket</span></span>
    - <span data-ttu-id="f516c-163">Serwer obsługuje protokół WebSocket</span><span class="sxs-lookup"><span data-stu-id="f516c-163">The server supports WebSocket</span></span>

    <span data-ttu-id="f516c-164">Jeśli którekolwiek z tych kryteriów nie są spełnione, będą używane długie sondowania.</span><span class="sxs-lookup"><span data-stu-id="f516c-164">If any of these criteria are not met, Long Polling will be used.</span></span> <span data-ttu-id="f516c-165">Aby uzyskać więcej informacji dotyczących połączeń między domenami, zobacz [jak nawiązać połączenie między domenami](../guide-to-the-api/hubs-api-guide-javascript-client.md#crossdomain).</span><span class="sxs-lookup"><span data-stu-id="f516c-165">For more information on cross-domain connections, see [How to establish a cross-domain connection](../guide-to-the-api/hubs-api-guide-javascript-client.md#crossdomain).</span></span>
4. <span data-ttu-id="f516c-166">Jeśli nie skonfigurowano JSONP i nie jest połączeniem między domenami, protokołu WebSocket zostaną użyte, jeśli klient i serwer jego obsługi.</span><span class="sxs-lookup"><span data-stu-id="f516c-166">If JSONP is not configured and the connection is not cross-domain, WebSocket will be used if both the client and server support it.</span></span>
5. <span data-ttu-id="f516c-167">Jeśli klient lub serwer nie obsługują protokołu WebSocket, zdarzenia wysyłane serwera jest używany, jeśli jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="f516c-167">If either the client or server do not support WebSocket, Server Sent Events is used if it is available.</span></span>
6. <span data-ttu-id="f516c-168">Jeśli zdarzenia wysyłane serwera nie jest dostępna, nastąpiła nieskończona ramki.</span><span class="sxs-lookup"><span data-stu-id="f516c-168">If Server Sent Events is not available, Forever Frame is attempted.</span></span>
7. <span data-ttu-id="f516c-169">Długie sondowania jest używany w przypadku niepowodzenia nieskończona ramki.</span><span class="sxs-lookup"><span data-stu-id="f516c-169">If Forever Frame fails, Long Polling is used.</span></span>

<a id="MonitoringTransports"></a>
### <a name="monitoring-transports"></a><span data-ttu-id="f516c-170">Transporty monitorowania</span><span class="sxs-lookup"><span data-stu-id="f516c-170">Monitoring transports</span></span>

<span data-ttu-id="f516c-171">Można określić transportu używa aplikacji przez włączenie rejestrowania w Centrum i otwieranie okna konsoli w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="f516c-171">You can determine what transport your application is using by enabling logging on your hub, and opening the console window in your browser.</span></span>

<span data-ttu-id="f516c-172">Aby włączyć rejestrowanie zdarzeń w Centrum w przeglądarce, Dodaj następujące polecenie do aplikacji klienta:</span><span class="sxs-lookup"><span data-stu-id="f516c-172">To enable logging for your hub's events in a browser, add the following command to your client application:</span></span>

`$.connection.hub.logging = true;`

- <span data-ttu-id="f516c-173">W programie Internet Explorer Otwórz narzędzia deweloperskie, naciskając klawisz F12 i kliknij kartę konsoli.</span><span class="sxs-lookup"><span data-stu-id="f516c-173">In Internet Explorer, open the developer tools by pressing F12, and click the Console tab.</span></span>

    ![Konsola programu Microsoft Internet Explorer](introduction-to-signalr/_static/image2.png)
- <span data-ttu-id="f516c-175">W przeglądarce Chrome Otwórz konsolę, naciskając klawisze Ctrl + Shift + J.</span><span class="sxs-lookup"><span data-stu-id="f516c-175">In Chrome, open the console by pressing Ctrl+Shift+J.</span></span>

    ![Konsoli programu Google Chrome](introduction-to-signalr/_static/image3.png)

<span data-ttu-id="f516c-177">Otwórz konsolę i włączone rejestrowanie będziesz mieć możliwość Zobacz transport, który jest używany przez SignalR.</span><span class="sxs-lookup"><span data-stu-id="f516c-177">With the console open and logging enabled, you'll be able to see which transport is being used by SignalR.</span></span>

![Konsoli w programie Internet Explorer przedstawiający protokołu WebSocket transportu](introduction-to-signalr/_static/image4.png)

### <a name="specifying-a-transport"></a><span data-ttu-id="f516c-179">Określanie transportu</span><span class="sxs-lookup"><span data-stu-id="f516c-179">Specifying a transport</span></span>

<span data-ttu-id="f516c-180">Transportu do negocjowania musi upłynąć trochę czasu i klient/serwer zasobów.</span><span class="sxs-lookup"><span data-stu-id="f516c-180">Negotiating a transport takes a certain amount of time and client/server resources.</span></span> <span data-ttu-id="f516c-181">Jeśli funkcje klienta są znane, transport można określić po uruchomieniu połączenia klienta.</span><span class="sxs-lookup"><span data-stu-id="f516c-181">If the client capabilities are known, then a transport can be specified when the client connection is started.</span></span> <span data-ttu-id="f516c-182">Poniższy fragment kodu przedstawia uruchamianie połączenie przy użyciu transportu sondowania długi Ajax, jak mają być używane, jeśli nosiła ona, że klient nie obsługuje żadnego innego protokołu:</span><span class="sxs-lookup"><span data-stu-id="f516c-182">The following code snippet demonstrates starting a connection using the Ajax Long Polling transport, as would be used if it was known that the client did not support any other protocol:</span></span>

`connection.start({ transport: 'longPolling' });`

<span data-ttu-id="f516c-183">Jeśli klient próby transportów określonych w kolejności, można określić rezerwowy order.</span><span class="sxs-lookup"><span data-stu-id="f516c-183">You can specify a fallback order if you want a client to try specific transports in order.</span></span> <span data-ttu-id="f516c-184">Poniższy fragment kodu przedstawia WebSocket w trakcie i awarii, który, przejście bezpośrednio do sondowania długo.</span><span class="sxs-lookup"><span data-stu-id="f516c-184">The following code snippet demonstrates trying WebSocket, and failing that, going directly to Long Polling.</span></span>

`connection.start({ transport: ['webSockets','longPolling'] });`

<span data-ttu-id="f516c-185">Stałe typu string służący do określania transportu są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f516c-185">The string constants for specifying transports are defined as follows:</span></span>

- `webSockets`
- `foreverFrame`
- `serverSentEvents`
- `longPolling`

## <a name="connections-and-hubs"></a><span data-ttu-id="f516c-186">Połączeniami i koncentratorami</span><span class="sxs-lookup"><span data-stu-id="f516c-186">Connections and Hubs</span></span>

<span data-ttu-id="f516c-187">Interfejs API SignalR zawiera dwa modele komunikacji między klientami a serwerami: stałe połączeniami i koncentratorami.</span><span class="sxs-lookup"><span data-stu-id="f516c-187">The SignalR API contains two models for communicating between clients and servers: Persistent Connections and Hubs.</span></span>

<span data-ttu-id="f516c-188">Połączenie reprezentuje proste punktu końcowego do wysyłania wiadomości jednego adresata, grupowanych lub emisji.</span><span class="sxs-lookup"><span data-stu-id="f516c-188">A Connection represents a simple endpoint for sending single-recipient, grouped, or broadcast messages.</span></span> <span data-ttu-id="f516c-189">Umożliwia trwałe połączenie interfejsu API (reprezentowane przez klasę klasy PersistentConnection w kodu platformy .NET), deweloper bezpośredni dostęp do protokołu komunikacyjnego niskiego poziomu, który ujawnia SignalR.</span><span class="sxs-lookup"><span data-stu-id="f516c-189">The Persistent Connection API (represented in .NET code by the PersistentConnection class) gives the developer direct access to the low-level communication protocol that SignalR exposes.</span></span> <span data-ttu-id="f516c-190">Przy użyciu modelu komunikacji połączenia jest znane deweloperom, którzy użyli API opartego na połączeniach, takie jak Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="f516c-190">Using the Connections communication model will be familiar to developers who have used connection-based APIs such as Windows Communication Foundation.</span></span>

<span data-ttu-id="f516c-191">Koncentrator jest bardziej ogólne potoku wbudowane w system API połączenia, który pozwala klienta i serwera, bezpośrednie wywoływanie metod na siebie.</span><span class="sxs-lookup"><span data-stu-id="f516c-191">A Hub is a more high-level pipeline built upon the Connection API that allows your client and server to call methods on each other directly.</span></span> <span data-ttu-id="f516c-192">SignalR obsługuje wysyłki poza granicami maszyny tak, jakby przez magic, co pozwala klientom wywoływać metod na serwerze jako łatwo jako metody lokalne i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="f516c-192">SignalR handles the dispatching across machine boundaries as if by magic, allowing clients to call methods on the server as easily as local methods, and vice versa.</span></span> <span data-ttu-id="f516c-193">Przy użyciu modelu komunikacji koncentratory jest znane deweloperom, którzy użyli zdalnego wywoływania interfejsów API, takich jak .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="f516c-193">Using the Hubs communication model will be familiar to developers who have used remote invocation APIs such as .NET Remoting.</span></span> <span data-ttu-id="f516c-194">Przy użyciu koncentratora umożliwia również przekazywanie jednoznacznie parametrów do metod, włączanie wiązania modelu.</span><span class="sxs-lookup"><span data-stu-id="f516c-194">Using a Hub also allows you to pass strongly typed parameters to methods, enabling model binding.</span></span>

### <a name="architecture-diagram"></a><span data-ttu-id="f516c-195">diagram architektury</span><span class="sxs-lookup"><span data-stu-id="f516c-195">Architecture diagram</span></span>

<span data-ttu-id="f516c-196">Na poniższym diagramie przedstawiono relację między koncentratorów, połączeń trwałych i podstawowych technologii używanych dla transportu.</span><span class="sxs-lookup"><span data-stu-id="f516c-196">The following diagram shows the relationship between Hubs, Persistent Connections, and the underlying technologies used for transports.</span></span>

![Diagram architektury SignalR przedstawiający interfejsów API transportu i klientów](introduction-to-signalr/_static/image5.png)

### <a name="how-hubs-work"></a><span data-ttu-id="f516c-198">Jak działają centrów</span><span class="sxs-lookup"><span data-stu-id="f516c-198">How Hubs work</span></span>

<span data-ttu-id="f516c-199">Gdy kod po stronie serwera wywołuje metodę dla klienta, pakiet są wysyłane przez aktywny transport, który zawiera nazwy i parametry metody do wywołania (gdy obiekt jest wysyłany jako parametr metody, jego jest zserializowanym przy użyciu JSON).</span><span class="sxs-lookup"><span data-stu-id="f516c-199">When server-side code calls a method on the client, a packet is sent across the active transport that contains the name and parameters of the method to be called (when an object is sent as a method parameter, it is serialized using JSON).</span></span> <span data-ttu-id="f516c-200">Następnie klient dopasowuje Nazwa metody do metody zdefiniowane w kodzie po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="f516c-200">The client then matches the method name to methods defined in client-side code.</span></span> <span data-ttu-id="f516c-201">Jeśli istnieje dopasowanie, metody klientów będą wykonywane przy użyciu danych parametru zdeserializowany.</span><span class="sxs-lookup"><span data-stu-id="f516c-201">If there is a match, the client method will be executed using the deserialized parameter data.</span></span>

<span data-ttu-id="f516c-202">Wywołanie metody można monitorować za pomocą takich narzędzi jak [Fiddler.](http://fiddler2.com/)</span><span class="sxs-lookup"><span data-stu-id="f516c-202">The method call can be monitored using tools like [Fiddler.](http://fiddler2.com/)</span></span> <span data-ttu-id="f516c-203">Na poniższej ilustracji przedstawiono wywołania metody wysłanych z serwera SignalR klient przeglądarki sieci web w okienku Dzienniki narzędzia Fiddler.</span><span class="sxs-lookup"><span data-stu-id="f516c-203">The following image shows a method call sent from a SignalR server to a web browser client in the Logs pane of Fiddler.</span></span> <span data-ttu-id="f516c-204">Wywołanie metody wysyłanych z koncentratora o nazwie `MoveShapeHub`, i jest wywoływana metoda jest wywoływana `updateShape`.</span><span class="sxs-lookup"><span data-stu-id="f516c-204">The method call is being sent from a hub called `MoveShapeHub`, and the method being invoked is called `updateShape`.</span></span>

![Widok pokazujący ruchu SignalR dziennika Fiddler](introduction-to-signalr/_static/image6.png)

<span data-ttu-id="f516c-206">W tym przykładzie nazwy Centrum jest identyfikowany przy `H` parametru; metody nazwa jest oznaczone symbolem `M` określono parametr, a dane są wysyłane do metody z `A` parametru.</span><span class="sxs-lookup"><span data-stu-id="f516c-206">In this example, the hub name is identified with the `H` parameter; the method name is identified with the `M` parameter, and the data being sent to the method is identified with the `A` parameter.</span></span> <span data-ttu-id="f516c-207">Aplikacji, która wygenerowała ten komunikat jest tworzony w [wysokiej częstotliwości w czasie rzeczywistym](tutorial-high-frequency-realtime-with-signalr.md) samouczka.</span><span class="sxs-lookup"><span data-stu-id="f516c-207">The application that generated this message is created in the [High-Frequency Realtime](tutorial-high-frequency-realtime-with-signalr.md) tutorial.</span></span>

### <a name="choosing-a-communication-model"></a><span data-ttu-id="f516c-208">Wybieranie modelu komunikacji</span><span class="sxs-lookup"><span data-stu-id="f516c-208">Choosing a communication model</span></span>

<span data-ttu-id="f516c-209">Większość aplikacji należy używać interfejsu API koncentratorów.</span><span class="sxs-lookup"><span data-stu-id="f516c-209">Most applications should use the Hubs API.</span></span> <span data-ttu-id="f516c-210">Interfejs API połączeń mogła zostać użyta w następujących okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="f516c-210">The Connections API could be used in the following circumstances:</span></span>

- <span data-ttu-id="f516c-211">Format rzeczywiste wysłano wiadomość musi być określony.</span><span class="sxs-lookup"><span data-stu-id="f516c-211">The format of the actual message sent needs to be specified.</span></span>
- <span data-ttu-id="f516c-212">Deweloper preferuje do pracy z modelem obsługi wiadomości i wysyłania, a nie modelu zdalnego wywoływania.</span><span class="sxs-lookup"><span data-stu-id="f516c-212">The developer prefers to work with a messaging and dispatching model rather than a remote invocation model.</span></span>
- <span data-ttu-id="f516c-213">Istniejących aplikacji, która używa modelu obsługi wiadomości jest są przenoszone do użycia SignalR.</span><span class="sxs-lookup"><span data-stu-id="f516c-213">An existing application that uses a messaging model is being ported to use SignalR.</span></span>