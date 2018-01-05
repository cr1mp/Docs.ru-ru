---
uid: web-api/overview/advanced/configuring-aspnet-web-api
title: "Настройка ASP.NET Web API 2 | Документы Microsoft"
author: MikeWasson
description: 
ms.author: aspnetcontent
manager: wpickett
ms.date: 03/31/2014
ms.topic: article
ms.assetid: 9e10a700-8d91-4d2e-a31e-b8b569fe867c
ms.technology: dotnet-webapi
ms.prod: .net-framework
msc.legacyurl: /web-api/overview/advanced/configuring-aspnet-web-api
msc.type: authoredcontent
ms.openlocfilehash: 1c007c4c327b7cde6ff52c6b0022acdff3c9b137
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2017
---
<a name="configuring-aspnet-web-api-2"></a><span data-ttu-id="daf1f-102">Настройка ASP.NET Web API 2</span><span class="sxs-lookup"><span data-stu-id="daf1f-102">Configuring ASP.NET Web API 2</span></span>
====================
<span data-ttu-id="daf1f-103">по [Mike Wasson](https://github.com/MikeWasson)</span><span class="sxs-lookup"><span data-stu-id="daf1f-103">by [Mike Wasson](https://github.com/MikeWasson)</span></span>

<span data-ttu-id="daf1f-104">В этом разделе описываются способы настройки веб-API ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="daf1f-104">This topic describes how to configure ASP.NET Web API.</span></span>

- [<span data-ttu-id="daf1f-105">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="daf1f-105">Configuration Settings</span></span>](#settings)
- [<span data-ttu-id="daf1f-106">Настройка веб-API с размещением ASP.NET</span><span class="sxs-lookup"><span data-stu-id="daf1f-106">Configuring Web API with ASP.NET Hosting</span></span>](#webhost)
- [<span data-ttu-id="daf1f-107">Настройка веб-API с резидентной OWIN</span><span class="sxs-lookup"><span data-stu-id="daf1f-107">Configuring Web API with OWIN Self-Hosting</span></span>](#selfhost)
- [<span data-ttu-id="daf1f-108">Глобальные веб-API службы</span><span class="sxs-lookup"><span data-stu-id="daf1f-108">Global Web API Services</span></span>](#services)
- [<span data-ttu-id="daf1f-109">Настройка контроллера</span><span class="sxs-lookup"><span data-stu-id="daf1f-109">Per-Controller Configuration</span></span>](#percontrollerconfig)

<a id="settings"></a>
## <a name="configuration-settings"></a><span data-ttu-id="daf1f-110">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="daf1f-110">Configuration Settings</span></span>

<span data-ttu-id="daf1f-111">Определенные параметры конфигурации веб-API в [HttpConfiguration](https://msdn.microsoft.com/en-us/library/system.web.http.httpconfiguration.aspx) класса.</span><span class="sxs-lookup"><span data-stu-id="daf1f-111">Web API configuration setttings are defined in the [HttpConfiguration](https://msdn.microsoft.com/en-us/library/system.web.http.httpconfiguration.aspx) class.</span></span>

| <span data-ttu-id="daf1f-112">Член</span><span class="sxs-lookup"><span data-stu-id="daf1f-112">Member</span></span> | <span data-ttu-id="daf1f-113">Описание</span><span class="sxs-lookup"><span data-stu-id="daf1f-113">Description</span></span> |
| --- | --- |
| <span data-ttu-id="daf1f-114">**DependencyResolver**</span><span class="sxs-lookup"><span data-stu-id="daf1f-114">**DependencyResolver**</span></span> | <span data-ttu-id="daf1f-115">Позволяет внедрения зависимостей для контроллеров.</span><span class="sxs-lookup"><span data-stu-id="daf1f-115">Enables dependency injection for controllers.</span></span> <span data-ttu-id="daf1f-116">В разделе [с помощью сопоставителя зависимостей веб-API](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-116">See [Using the Web API Dependency Resolver](dependency-injection.md).</span></span> |
| <span data-ttu-id="daf1f-117">**Фильтры**</span><span class="sxs-lookup"><span data-stu-id="daf1f-117">**Filters**</span></span> | <span data-ttu-id="daf1f-118">Фильтры действий.</span><span class="sxs-lookup"><span data-stu-id="daf1f-118">Action filters.</span></span> |
| <span data-ttu-id="daf1f-119">**Модули форматирования**</span><span class="sxs-lookup"><span data-stu-id="daf1f-119">**Formatters**</span></span> | <span data-ttu-id="daf1f-120">[Модули форматирования типа мультимедиа](../formats-and-model-binding/media-formatters.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-120">[Media-type formatters](../formats-and-model-binding/media-formatters.md).</span></span> |
| <span data-ttu-id="daf1f-121">**IncludeErrorDetailPolicy**</span><span class="sxs-lookup"><span data-stu-id="daf1f-121">**IncludeErrorDetailPolicy**</span></span> | <span data-ttu-id="daf1f-122">Указывает, должен ли сервер включать сведения об ошибке, например сообщения исключений и трассировки стека в сообщений ответов HTTP.</span><span class="sxs-lookup"><span data-stu-id="daf1f-122">Specifies whether the server should include error details, such as exception messages and stack traces, in HTTP response messages.</span></span> <span data-ttu-id="daf1f-123">В разделе [IncludeErrorDetailPolicy](https://msdn.microsoft.com/en-us/library/system.web.http.includeerrordetailpolicy(v=vs.108)).</span><span class="sxs-lookup"><span data-stu-id="daf1f-123">See [IncludeErrorDetailPolicy](https://msdn.microsoft.com/en-us/library/system.web.http.includeerrordetailpolicy(v=vs.108)).</span></span> |
| <span data-ttu-id="daf1f-124">**Инициализатор**</span><span class="sxs-lookup"><span data-stu-id="daf1f-124">**Initializer**</span></span> | <span data-ttu-id="daf1f-125">Функция, которая выполняет окончательной инициализации **HttpConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="daf1f-125">A function that performs final initialization of the **HttpConfiguration**.</span></span> |
| <span data-ttu-id="daf1f-126">**MessageHandlers**</span><span class="sxs-lookup"><span data-stu-id="daf1f-126">**MessageHandlers**</span></span> | <span data-ttu-id="daf1f-127">[Обработчики сообщений HTTP](http-message-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-127">[HTTP message handlers](http-message-handlers.md).</span></span> |
| <span data-ttu-id="daf1f-128">**ParameterBindingRules**</span><span class="sxs-lookup"><span data-stu-id="daf1f-128">**ParameterBindingRules**</span></span> | <span data-ttu-id="daf1f-129">Коллекции правил привязки параметров действий контроллера.</span><span class="sxs-lookup"><span data-stu-id="daf1f-129">A collection of rules for binding parameters on controller actions.</span></span> |
| <span data-ttu-id="daf1f-130">**Свойства**</span><span class="sxs-lookup"><span data-stu-id="daf1f-130">**Properties**</span></span> | <span data-ttu-id="daf1f-131">Универсальное хранилище свойств.</span><span class="sxs-lookup"><span data-stu-id="daf1f-131">A generic property bag.</span></span> |
| <span data-ttu-id="daf1f-132">**Маршруты**</span><span class="sxs-lookup"><span data-stu-id="daf1f-132">**Routes**</span></span> | <span data-ttu-id="daf1f-133">Коллекция маршрутов.</span><span class="sxs-lookup"><span data-stu-id="daf1f-133">The collection of routes.</span></span> <span data-ttu-id="daf1f-134">В разделе [маршрутизации в ASP.NET Web API](../web-api-routing-and-actions/routing-in-aspnet-web-api.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-134">See [Routing in ASP.NET Web API](../web-api-routing-and-actions/routing-in-aspnet-web-api.md).</span></span> |
| <span data-ttu-id="daf1f-135">**Службы**</span><span class="sxs-lookup"><span data-stu-id="daf1f-135">**Services**</span></span> | <span data-ttu-id="daf1f-136">Коллекция служб.</span><span class="sxs-lookup"><span data-stu-id="daf1f-136">The collection of services.</span></span> <span data-ttu-id="daf1f-137">В разделе [службы](#services).</span><span class="sxs-lookup"><span data-stu-id="daf1f-137">See [Services](#services).</span></span> |


## <a name="prerequisites"></a><span data-ttu-id="daf1f-138">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="daf1f-138">Prerequisites</span></span>

<span data-ttu-id="daf1f-139">[Visual Studio 2017 г](https://www.visualstudio.com/vs/) Community, Professional или Enterprise Edition.</span><span class="sxs-lookup"><span data-stu-id="daf1f-139">[Visual Studio 2017](https://www.visualstudio.com/vs/) Community, Professional, or Enterprise Edition.</span></span>

<a id="webhost"></a>
## <a name="configuring-web-api-with-aspnet-hosting"></a><span data-ttu-id="daf1f-140">Настройка веб-API с размещением ASP.NET</span><span class="sxs-lookup"><span data-stu-id="daf1f-140">Configuring Web API with ASP.NET Hosting</span></span>

<span data-ttu-id="daf1f-141">В приложении ASP.NET настроить веб-API путем вызова [GlobalConfiguration.Configure](https://msdn.microsoft.com/en-us/library/system.web.http.globalconfiguration.configure.aspx) в **приложения\_запустить** метод.</span><span class="sxs-lookup"><span data-stu-id="daf1f-141">In an ASP.NET application, configure Web API by calling [GlobalConfiguration.Configure](https://msdn.microsoft.com/en-us/library/system.web.http.globalconfiguration.configure.aspx) in the **Application\_Start** method.</span></span> <span data-ttu-id="daf1f-142">**Настройка** метод принимает делегат с одним параметром типа **HttpConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="daf1f-142">The **Configure** method takes a delegate with a single parameter of type **HttpConfiguration**.</span></span> <span data-ttu-id="daf1f-143">Выполните все вашей конфигурации внутри делегата.</span><span class="sxs-lookup"><span data-stu-id="daf1f-143">Perform all of your configuation inside the delegate.</span></span>

<span data-ttu-id="daf1f-144">Ниже приведен пример использования анонимного делегата:</span><span class="sxs-lookup"><span data-stu-id="daf1f-144">Here is an example using an anonymous delegate:</span></span>

[!code-csharp[Main](configuring-aspnet-web-api/samples/sample1.cs)]

<span data-ttu-id="daf1f-145">В Visual Studio 2017 г., шаблон проекта «Веб-приложение ASP.NET» автоматически настраивает код конфигурации, если выбрать «Веб-API» в **новый проект ASP.NET** диалогового окна.</span><span class="sxs-lookup"><span data-stu-id="daf1f-145">In Visual Studio 2017, the "ASP.NET Web Application" project template automatically sets up the configuration code, if you select "Web API" in the **New ASP.NET Project** dialog.</span></span>

[![](configuring-aspnet-web-api/_static/image2.png)](configuring-aspnet-web-api/_static/image1.png)

<span data-ttu-id="daf1f-146">Шаблон проекта создает файл с именем WebApiConfig.cs внутри приложения\_Начальная папка.</span><span class="sxs-lookup"><span data-stu-id="daf1f-146">The project template creates a file named WebApiConfig.cs inside the App\_Start folder.</span></span> <span data-ttu-id="daf1f-147">Этот файл код определяет делегат, где следует поместить код конфигурации веб-API.</span><span class="sxs-lookup"><span data-stu-id="daf1f-147">This code file defines the delegate where you should put your Web API configuration code.</span></span>

![](configuring-aspnet-web-api/_static/image3.png)

[!code-csharp[Main](configuring-aspnet-web-api/samples/sample2.cs?highlight=12)]

<span data-ttu-id="daf1f-148">Шаблон проекта также добавляет код, который вызывает делегат из **приложения\_запустить**.</span><span class="sxs-lookup"><span data-stu-id="daf1f-148">The project template also adds the code that calls the delegate from **Application\_Start**.</span></span>

[!code-csharp[Main](configuring-aspnet-web-api/samples/sample3.cs?highlight=5)]

<a id="selfhost"></a>
## <a name="configuring-web-api-with-owin-self-hosting"></a><span data-ttu-id="daf1f-149">Настройка веб-API с резидентной OWIN</span><span class="sxs-lookup"><span data-stu-id="daf1f-149">Configuring Web API with OWIN Self-Hosting</span></span>

<span data-ttu-id="daf1f-150">Если резидентного размещения с OWIN, создайте новый **HttpConfiguration** экземпляра.</span><span class="sxs-lookup"><span data-stu-id="daf1f-150">If you are self-hosting with OWIN, create a new **HttpConfiguration** instance.</span></span> <span data-ttu-id="daf1f-151">Выполнить настройки в данном экземпляре, а затем передайте экземпляр для **Owin.UseWebApi** метода расширения.</span><span class="sxs-lookup"><span data-stu-id="daf1f-151">Perform any configuration on this instance, and then pass the instance to the **Owin.UseWebApi** extension method.</span></span>

[!code-csharp[Main](configuring-aspnet-web-api/samples/sample4.cs)]

<span data-ttu-id="daf1f-152">Учебник [OWIN используйте Self-Host ASP.NET Web API 2](../hosting-aspnet-web-api/use-owin-to-self-host-web-api.md) показывает все шаги.</span><span class="sxs-lookup"><span data-stu-id="daf1f-152">The tutorial [Use OWIN to Self-Host ASP.NET Web API 2](../hosting-aspnet-web-api/use-owin-to-self-host-web-api.md) shows the complete steps.</span></span>

<a id="services"></a>
## <a name="global-web-api-services"></a><span data-ttu-id="daf1f-153">Глобальные веб-API службы</span><span class="sxs-lookup"><span data-stu-id="daf1f-153">Global Web API Services</span></span>

<span data-ttu-id="daf1f-154">**HttpConfiguration.Services** коллекция содержит набор глобальных служб, используемых для выполнения различных задач, таких как контроллер согласования выделения и содержимое веб-API.</span><span class="sxs-lookup"><span data-stu-id="daf1f-154">The **HttpConfiguration.Services** collection contains a set of global services that Web API uses to perform various tasks, such as controller selection and content negotiation.</span></span>

> [!NOTE]
> <span data-ttu-id="daf1f-155">**Служб** коллекции не является универсального механизма для внесения обнаружения или зависимостей службы.</span><span class="sxs-lookup"><span data-stu-id="daf1f-155">The **Services** collection is not a general-purpose mechanism for service discovery or dependency injection.</span></span> <span data-ttu-id="daf1f-156">Она только хранит типы служб, которые заведомо платформа веб-API.</span><span class="sxs-lookup"><span data-stu-id="daf1f-156">It only stores service types that are known to the Web API framework.</span></span>


<span data-ttu-id="daf1f-157">**Служб** коллекция инициализирована со стандартным набором служб, и можно задать собственные пользовательские реализации.</span><span class="sxs-lookup"><span data-stu-id="daf1f-157">The **Services** collection is initialized with a default set of services, and you can provide your own custom implementations.</span></span> <span data-ttu-id="daf1f-158">Некоторые службы поддержки нескольких экземпляров, а другие могут иметь только один экземпляр.</span><span class="sxs-lookup"><span data-stu-id="daf1f-158">Some services support multiple instances, while others can have only one instance.</span></span> <span data-ttu-id="daf1f-159">(Тем не менее, можно также предоставить службы на уровне контроллера; см. раздел [-контроллер конфигурации](#percontrollerconfig).</span><span class="sxs-lookup"><span data-stu-id="daf1f-159">(However, you can also provide services at the controller level; see [Per-Controller Configuration](#percontrollerconfig).</span></span>

<span data-ttu-id="daf1f-160">Один экземпляр службы</span><span class="sxs-lookup"><span data-stu-id="daf1f-160">Single-Instance Services</span></span>


| <span data-ttu-id="daf1f-161">Служба</span><span class="sxs-lookup"><span data-stu-id="daf1f-161">Service</span></span> | <span data-ttu-id="daf1f-162">Описание</span><span class="sxs-lookup"><span data-stu-id="daf1f-162">Description</span></span> |
| --- | --- |
| <span data-ttu-id="daf1f-163">**IActionValueBinder**</span><span class="sxs-lookup"><span data-stu-id="daf1f-163">**IActionValueBinder**</span></span> | <span data-ttu-id="daf1f-164">Возвращает привязку для параметра.</span><span class="sxs-lookup"><span data-stu-id="daf1f-164">Gets a binding for a parameter.</span></span> |
| <span data-ttu-id="daf1f-165">**IApiExplorer**</span><span class="sxs-lookup"><span data-stu-id="daf1f-165">**IApiExplorer**</span></span> | <span data-ttu-id="daf1f-166">Получает описания API-интерфейсы, предоставляемые приложением.</span><span class="sxs-lookup"><span data-stu-id="daf1f-166">Gets descriptions of the APIs exposed by the application.</span></span> <span data-ttu-id="daf1f-167">В разделе [Создание страницы справки для веб-API](../getting-started-with-aspnet-web-api/creating-api-help-pages.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-167">See [Creating a Help Page for a Web API](../getting-started-with-aspnet-web-api/creating-api-help-pages.md).</span></span> |
| <span data-ttu-id="daf1f-168">**IAssembliesResolver**</span><span class="sxs-lookup"><span data-stu-id="daf1f-168">**IAssembliesResolver**</span></span> | <span data-ttu-id="daf1f-169">Возвращает список сборок для приложения.</span><span class="sxs-lookup"><span data-stu-id="daf1f-169">Gets a list of the assemblies for the application.</span></span> <span data-ttu-id="daf1f-170">В разделе [Маршрутизация и выбор действий](../web-api-routing-and-actions/routing-and-action-selection.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-170">See [Routing and Action Selection](../web-api-routing-and-actions/routing-and-action-selection.md).</span></span> |
| <span data-ttu-id="daf1f-171">**IBodyModelValidator**</span><span class="sxs-lookup"><span data-stu-id="daf1f-171">**IBodyModelValidator**</span></span> | <span data-ttu-id="daf1f-172">Проверяет модель, которая считывается в тексте запроса модуль форматирования типа мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="daf1f-172">Validates a model that is read from the request body by a media-type formatter.</span></span> |
| <span data-ttu-id="daf1f-173">**IContentNegotiator**</span><span class="sxs-lookup"><span data-stu-id="daf1f-173">**IContentNegotiator**</span></span> | <span data-ttu-id="daf1f-174">Выполняет согласование содержимого.</span><span class="sxs-lookup"><span data-stu-id="daf1f-174">Performs content negotiation.</span></span> |
| <span data-ttu-id="daf1f-175">**IDocumentationProvider**</span><span class="sxs-lookup"><span data-stu-id="daf1f-175">**IDocumentationProvider**</span></span> | <span data-ttu-id="daf1f-176">Предоставляет документацию для API-интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="daf1f-176">Provides documentation for APIs.</span></span> <span data-ttu-id="daf1f-177">Значение по умолчанию — **null**.</span><span class="sxs-lookup"><span data-stu-id="daf1f-177">The default is **null**.</span></span> <span data-ttu-id="daf1f-178">В разделе [Создание страницы справки для веб-API](../getting-started-with-aspnet-web-api/creating-api-help-pages.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-178">See [Creating a Help Page for a Web API](../getting-started-with-aspnet-web-api/creating-api-help-pages.md).</span></span> |
| <span data-ttu-id="daf1f-179">**IHostBufferPolicySelector**</span><span class="sxs-lookup"><span data-stu-id="daf1f-179">**IHostBufferPolicySelector**</span></span> | <span data-ttu-id="daf1f-180">Указывает, является ли узел буферизовать текст сущности сообщений HTTP.</span><span class="sxs-lookup"><span data-stu-id="daf1f-180">Indicates whether the host should buffer HTTP message entity bodies.</span></span> |
| <span data-ttu-id="daf1f-181">**IHttpActionInvoker**</span><span class="sxs-lookup"><span data-stu-id="daf1f-181">**IHttpActionInvoker**</span></span> | <span data-ttu-id="daf1f-182">Вызывает действие контроллера.</span><span class="sxs-lookup"><span data-stu-id="daf1f-182">Invokes a controller action.</span></span> <span data-ttu-id="daf1f-183">В разделе [Маршрутизация и выбор действий](../web-api-routing-and-actions/routing-and-action-selection.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-183">See [Routing and Action Selection](../web-api-routing-and-actions/routing-and-action-selection.md).</span></span> |
| <span data-ttu-id="daf1f-184">**IHttpActionSelector**</span><span class="sxs-lookup"><span data-stu-id="daf1f-184">**IHttpActionSelector**</span></span> | <span data-ttu-id="daf1f-185">Выбирает действие контроллера.</span><span class="sxs-lookup"><span data-stu-id="daf1f-185">Selects a controller action.</span></span> <span data-ttu-id="daf1f-186">В разделе [Маршрутизация и выбор действий](../web-api-routing-and-actions/routing-and-action-selection.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-186">See [Routing and Action Selection](../web-api-routing-and-actions/routing-and-action-selection.md).</span></span> |
| <span data-ttu-id="daf1f-187">**IHttpControllerActivator**</span><span class="sxs-lookup"><span data-stu-id="daf1f-187">**IHttpControllerActivator**</span></span> | <span data-ttu-id="daf1f-188">Активирует контроллера.</span><span class="sxs-lookup"><span data-stu-id="daf1f-188">Activates a controller.</span></span> <span data-ttu-id="daf1f-189">В разделе [Маршрутизация и выбор действий](../web-api-routing-and-actions/routing-and-action-selection.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-189">See [Routing and Action Selection](../web-api-routing-and-actions/routing-and-action-selection.md).</span></span> |
| <span data-ttu-id="daf1f-190">**IHttpControllerSelector**</span><span class="sxs-lookup"><span data-stu-id="daf1f-190">**IHttpControllerSelector**</span></span> | <span data-ttu-id="daf1f-191">Выбирает контроллер.</span><span class="sxs-lookup"><span data-stu-id="daf1f-191">Selects a controller.</span></span> <span data-ttu-id="daf1f-192">В разделе [Маршрутизация и выбор действий](../web-api-routing-and-actions/routing-and-action-selection.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-192">See [Routing and Action Selection](../web-api-routing-and-actions/routing-and-action-selection.md).</span></span> |
| <span data-ttu-id="daf1f-193">**IHttpControllerTypeResolver**</span><span class="sxs-lookup"><span data-stu-id="daf1f-193">**IHttpControllerTypeResolver**</span></span> | <span data-ttu-id="daf1f-194">Содержит список типов контроллера веб-API в приложении.</span><span class="sxs-lookup"><span data-stu-id="daf1f-194">Provides a list of the Web API controller types in the application.</span></span> <span data-ttu-id="daf1f-195">В разделе [Маршрутизация и выбор действий](../web-api-routing-and-actions/routing-and-action-selection.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-195">See [Routing and Action Selection](../web-api-routing-and-actions/routing-and-action-selection.md).</span></span> |
| <span data-ttu-id="daf1f-196">**ITraceManager**</span><span class="sxs-lookup"><span data-stu-id="daf1f-196">**ITraceManager**</span></span> | <span data-ttu-id="daf1f-197">Инициализирует платформы трассировки.</span><span class="sxs-lookup"><span data-stu-id="daf1f-197">Initializes the tracing framework.</span></span> <span data-ttu-id="daf1f-198">В разделе [трассировки в ASP.NET Web API](../testing-and-debugging/tracing-in-aspnet-web-api.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-198">See [Tracing in ASP.NET Web API](../testing-and-debugging/tracing-in-aspnet-web-api.md).</span></span> |
| <span data-ttu-id="daf1f-199">**ITraceWriter**</span><span class="sxs-lookup"><span data-stu-id="daf1f-199">**ITraceWriter**</span></span> | <span data-ttu-id="daf1f-200">Предоставляет модуль записи трассировки.</span><span class="sxs-lookup"><span data-stu-id="daf1f-200">Provides a trace writer.</span></span> <span data-ttu-id="daf1f-201">Значение по умолчанию — модуль записи трассировки «холостой».</span><span class="sxs-lookup"><span data-stu-id="daf1f-201">The default is a "no-op" trace writer.</span></span> <span data-ttu-id="daf1f-202">В разделе [трассировки в ASP.NET Web API](../testing-and-debugging/tracing-in-aspnet-web-api.md).</span><span class="sxs-lookup"><span data-stu-id="daf1f-202">See [Tracing in ASP.NET Web API](../testing-and-debugging/tracing-in-aspnet-web-api.md).</span></span> |
| <span data-ttu-id="daf1f-203">**IModelValidatorCache**</span><span class="sxs-lookup"><span data-stu-id="daf1f-203">**IModelValidatorCache**</span></span> | <span data-ttu-id="daf1f-204">Предоставляет кэш средств проверки модели.</span><span class="sxs-lookup"><span data-stu-id="daf1f-204">Provides a cache of model validators.</span></span> |

<span data-ttu-id="daf1f-205">Нескольких экземпляров служб</span><span class="sxs-lookup"><span data-stu-id="daf1f-205">Multiple-Instance Services</span></span>


| <span data-ttu-id="daf1f-206">Служба</span><span class="sxs-lookup"><span data-stu-id="daf1f-206">Service</span></span> | <span data-ttu-id="daf1f-207">Описание</span><span class="sxs-lookup"><span data-stu-id="daf1f-207">Description</span></span> |
| --- | --- |
| <span data-ttu-id="daf1f-208">**IFilterProvider**</span><span class="sxs-lookup"><span data-stu-id="daf1f-208">**IFilterProvider**</span></span> | <span data-ttu-id="daf1f-209">Возвращает список фильтров для действия контроллера.</span><span class="sxs-lookup"><span data-stu-id="daf1f-209">Returns a list of filters for a controller action.</span></span> |
| <span data-ttu-id="daf1f-210">**ModelBinderProvider**</span><span class="sxs-lookup"><span data-stu-id="daf1f-210">**ModelBinderProvider**</span></span> | <span data-ttu-id="daf1f-211">Возвращает связыватель модели для данного типа.</span><span class="sxs-lookup"><span data-stu-id="daf1f-211">Returns a model binder for a given type.</span></span> |
| <span data-ttu-id="daf1f-212">**ModelMetadataProvider**</span><span class="sxs-lookup"><span data-stu-id="daf1f-212">**ModelMetadataProvider**</span></span> | <span data-ttu-id="daf1f-213">Предоставляет метаданные для модели.</span><span class="sxs-lookup"><span data-stu-id="daf1f-213">Provides metadata for a model.</span></span> |
| <span data-ttu-id="daf1f-214">**ModelValidatorProvider**</span><span class="sxs-lookup"><span data-stu-id="daf1f-214">**ModelValidatorProvider**</span></span> | <span data-ttu-id="daf1f-215">Предоставляет проверяющий элемент управления для модели.</span><span class="sxs-lookup"><span data-stu-id="daf1f-215">Provides a validator for a model.</span></span> |
| <span data-ttu-id="daf1f-216">**ValueProviderFactory**</span><span class="sxs-lookup"><span data-stu-id="daf1f-216">**ValueProviderFactory**</span></span> | <span data-ttu-id="daf1f-217">Создает поставщик значений.</span><span class="sxs-lookup"><span data-stu-id="daf1f-217">Creates a value provider.</span></span> <span data-ttu-id="daf1f-218">Дополнительные сведения см. в разделе блога Майк стол [Создание поставщика пользовательских значений в WebAPI](https://blogs.msdn.com/b/jmstall/archive/2012/04/23/how-to-create-a-custom-value-provider-in-webapi.aspx)</span><span class="sxs-lookup"><span data-stu-id="daf1f-218">For more information, see Mike Stall's blog post [How to create a custom value provider in WebAPI](https://blogs.msdn.com/b/jmstall/archive/2012/04/23/how-to-create-a-custom-value-provider-in-webapi.aspx)</span></span> |<span data-ttu-id="daf1f-219">.</span><span class="sxs-lookup"><span data-stu-id="daf1f-219">.</span></span>

<span data-ttu-id="daf1f-220">Чтобы добавить пользовательскую реализацию нескольких экземпляров службы, вызовите **добавить** или **вставить** на **служб** коллекции:</span><span class="sxs-lookup"><span data-stu-id="daf1f-220">To add a custom implementation to a multi-instance service, call **Add** or **Insert** on the **Services** collection:</span></span>

[!code-csharp[Main](configuring-aspnet-web-api/samples/sample5.cs)]

<span data-ttu-id="daf1f-221">Чтобы заменить одного экземпляра службы с пользовательской реализацией, вызовите **заменить** на **служб** коллекции:</span><span class="sxs-lookup"><span data-stu-id="daf1f-221">To replace a single-instance service with a custom implementation, call **Replace** on the **Services** collection:</span></span>

[!code-csharp[Main](configuring-aspnet-web-api/samples/sample6.cs)]

<a id="percontrollerconfig"></a>
## <a name="per-controller-configuration"></a><span data-ttu-id="daf1f-222">Настройка контроллера</span><span class="sxs-lookup"><span data-stu-id="daf1f-222">Per-Controller Configuration</span></span>

<span data-ttu-id="daf1f-223">Можно переопределить отдельно для каждого контроллера следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="daf1f-223">You can override the following settings on a per-controller basis:</span></span>

- <span data-ttu-id="daf1f-224">Модули форматирования типа мультимедиа</span><span class="sxs-lookup"><span data-stu-id="daf1f-224">Media-type formatters</span></span>
- <span data-ttu-id="daf1f-225">Параметр привязки правил</span><span class="sxs-lookup"><span data-stu-id="daf1f-225">Parameter binding rules</span></span>
- <span data-ttu-id="daf1f-226">Службы</span><span class="sxs-lookup"><span data-stu-id="daf1f-226">Services</span></span>

<span data-ttu-id="daf1f-227">Для этого нужно определить настраиваемый атрибут, реализующий **IControllerConfiguration** интерфейса.</span><span class="sxs-lookup"><span data-stu-id="daf1f-227">To do so, define a custom attribute that implements the **IControllerConfiguration** interface.</span></span> <span data-ttu-id="daf1f-228">Затем примените атрибут к контроллеру.</span><span class="sxs-lookup"><span data-stu-id="daf1f-228">Then apply the attribute to the controller.</span></span>

<span data-ttu-id="daf1f-229">Следующий пример заменяет пользовательский модуль форматирования по умолчанию модули форматирования типа мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="daf1f-229">The following example replaces the default media-type formatters with a custom formatter.</span></span>

[!code-csharp[Main](configuring-aspnet-web-api/samples/sample7.cs)]

<span data-ttu-id="daf1f-230">**IControllerConfiguration.Initialize** метод принимает два параметра:</span><span class="sxs-lookup"><span data-stu-id="daf1f-230">The **IControllerConfiguration.Initialize** method takes two parameters:</span></span>

- <span data-ttu-id="daf1f-231">**HttpControllerSettings** объекта</span><span class="sxs-lookup"><span data-stu-id="daf1f-231">An **HttpControllerSettings** object</span></span>
- <span data-ttu-id="daf1f-232">**HttpControllerDescriptor** объекта</span><span class="sxs-lookup"><span data-stu-id="daf1f-232">An **HttpControllerDescriptor** object</span></span>

<span data-ttu-id="daf1f-233">**HttpControllerDescriptor** содержит описание контроллера, который можно просмотреть в ознакомительных целях (скажем, для различения двух контроллеров).</span><span class="sxs-lookup"><span data-stu-id="daf1f-233">The **HttpControllerDescriptor** contains a description of the controller, which you can examine for informational purposes (say, to distinguish between two controllers).</span></span>

<span data-ttu-id="daf1f-234">Используйте **HttpControllerSettings** объекта, чтобы настроить контроллер.</span><span class="sxs-lookup"><span data-stu-id="daf1f-234">Use the **HttpControllerSettings** object to configure the controller.</span></span> <span data-ttu-id="daf1f-235">Этот объект содержит подмножество параметров конфигурации, которые можно переопределить отдельно для каждого контроллера.</span><span class="sxs-lookup"><span data-stu-id="daf1f-235">This object contains the subset of configuration parameters that you can override on a per-controller basis.</span></span> <span data-ttu-id="daf1f-236">По умолчанию все параметры, которые не изменяются на глобальную **HttpConfiguration** объекта.</span><span class="sxs-lookup"><span data-stu-id="daf1f-236">Any settings that you don't change default to the global **HttpConfiguration** object.</span></span>