---
title: Публикация ASP.NET Core приложений SignalR на веб-приложение Azure
author: rachelappel
description: Публикация ASP.NET Core приложений SignalR на веб-приложение Azure
manager: wpickett
monikerRange: '>= aspnetcore-2.1'
ms.author: rachelap
ms.custom: mvc
ms.date: 04/20/2018
ms.prod: aspnet-core
ms.technology: aspnet
ms.topic: article
uid: signalr/publish-to-azure-web-app
ms.openlocfilehash: 8612824cc9d4a9ace1c214411c44754350100f06
ms.sourcegitcommit: 7e87671fea9a5f36ca516616fe3b40b537f428d2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35341812"
---
# <a name="publish-an-aspnet-core-signalr-app-to-an-azure-web-app"></a><span data-ttu-id="47137-103">Публикация ASP.NET Core приложений SignalR на веб-приложение Azure</span><span class="sxs-lookup"><span data-stu-id="47137-103">Publish an ASP.NET Core SignalR app to an Azure Web App</span></span>

<span data-ttu-id="47137-104">[Azure веб-приложения](/azure/app-service/app-service-web-overview) — [Microsoft облачные вычисления](https://azure.microsoft.com/) платформы службы для размещения веб-приложений, включая ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="47137-104">[Azure Web App](/azure/app-service/app-service-web-overview) is a [Microsoft cloud computing](https://azure.microsoft.com/) platform service for hosting web apps, including ASP.NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="47137-105">В этой статье относится к публикации приложения ASP.NET Core SignalR из Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="47137-105">This article refers to publishing an ASP.NET Core SignalR app from Visual Studio.</span></span> <span data-ttu-id="47137-106">Посетите [SignalR службы для Azure](https://azure.microsoft.com/en-gb/services/signalr-service?) Дополнительные сведения об использовании SignalR в Azure.</span><span class="sxs-lookup"><span data-stu-id="47137-106">Visit [SignalR service for Azure](https://azure.microsoft.com/en-gb/services/signalr-service?) for more information about using SignalR on Azure.</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="47137-107">Публикация приложения</span><span class="sxs-lookup"><span data-stu-id="47137-107">Publish the app</span></span>

<span data-ttu-id="47137-108">Visual Studio предоставляет встроенные средства для публикации для веб-приложение Azure.</span><span class="sxs-lookup"><span data-stu-id="47137-108">Visual Studio provides built-in tools for publishing to an Azure Web App.</span></span> <span data-ttu-id="47137-109">Можно использовать Visual Studio код пользователя [Azure CLI](/cli/azure) команд для публикации приложения в Azure.</span><span class="sxs-lookup"><span data-stu-id="47137-109">Visual Studio Code user can use [Azure CLI](/cli/azure) commands to publish apps to Azure.</span></span> <span data-ttu-id="47137-110">В этой статье рассказывается о публикации с использованием средства в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="47137-110">This article covers publishing using the tools in Visual Studio.</span></span> <span data-ttu-id="47137-111">Чтобы опубликовать приложение с помощью Azure CLI, в разделе [публикации приложения ASP.NET Core в Azure с помощью средства командной строки](xref:tutorials/publish-to-azure-webapp-using-cli).</span><span class="sxs-lookup"><span data-stu-id="47137-111">To publish an app using Azure CLI, see [Publish an ASP.NET Core app to Azure with command line tools](xref:tutorials/publish-to-azure-webapp-using-cli).</span></span>

<span data-ttu-id="47137-112">Правой кнопкой мыши проект в **обозревателе решений** и выберите **публикации**.</span><span class="sxs-lookup"><span data-stu-id="47137-112">Right-click on the project in **Solution Explorer** and select **Publish**.</span></span> <span data-ttu-id="47137-113">Убедитесь, что **создать новый** возврата **выбрать место назначения публикации** диалогового окна, а затем выберите **публикации**.</span><span class="sxs-lookup"><span data-stu-id="47137-113">Confirm that **Create new** is checked in the **Pick a publish target** dialog, and select **Publish**.</span></span>

![Подбор публикации целевой](publish-to-azure-web-app/_static/pick-publish-target-dialog.png)

<span data-ttu-id="47137-115">Введите следующие сведения в **Создание приложения службы** диалоговое окно и выбрать **создать**.</span><span class="sxs-lookup"><span data-stu-id="47137-115">Enter the following information in the **Create App Service** dialog and select **Create**.</span></span>

| <span data-ttu-id="47137-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="47137-116">Item</span></span> | <span data-ttu-id="47137-117">Описание:</span><span class="sxs-lookup"><span data-stu-id="47137-117">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="47137-118">**Имя приложения**</span><span class="sxs-lookup"><span data-stu-id="47137-118">**App name**</span></span> | <span data-ttu-id="47137-119">Уникальное имя приложения.</span><span class="sxs-lookup"><span data-stu-id="47137-119">A unique name of the app.</span></span> |
| <span data-ttu-id="47137-120">**Подписки**</span><span class="sxs-lookup"><span data-stu-id="47137-120">**Subscription**</span></span> | <span data-ttu-id="47137-121">Подписка Azure, который использует приложение.</span><span class="sxs-lookup"><span data-stu-id="47137-121">The Azure subscription that the app uses.</span></span> |
| <span data-ttu-id="47137-122">**Группа ресурсов**</span><span class="sxs-lookup"><span data-stu-id="47137-122">**Resource Group**</span></span> | <span data-ttu-id="47137-123">Группа связанных ресурсов, к которым принадлежит приложения.</span><span class="sxs-lookup"><span data-stu-id="47137-123">The group of related resources to which the app belongs.</span></span>  |
| <span data-ttu-id="47137-124">**План размещения**</span><span class="sxs-lookup"><span data-stu-id="47137-124">**Hosting Plan**</span></span> | <span data-ttu-id="47137-125">Ценовой план для веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="47137-125">The pricing plan for the web app.</span></span> |

![Создание приложения службы](publish-to-azure-web-app/_static/create-app-service-dialog.png)

<span data-ttu-id="47137-127">Visual Studio выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="47137-127">Visual Studio completes the following tasks:</span></span>

* <span data-ttu-id="47137-128">Создает профиль публикации содержащего параметры публикации.</span><span class="sxs-lookup"><span data-stu-id="47137-128">Creates a Publish Profile containing publish settings.</span></span>
* <span data-ttu-id="47137-129">Создает или использует существующий *веб-приложения Azure* с помощью указанных сведений.</span><span class="sxs-lookup"><span data-stu-id="47137-129">Creates or uses an existing *Azure Web App* with the provided details.</span></span>
* <span data-ttu-id="47137-130">Публикация приложения.</span><span class="sxs-lookup"><span data-stu-id="47137-130">Publishes the app.</span></span>
* <span data-ttu-id="47137-131">Запускает браузер с загружен опубликованных веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="47137-131">Launches a browser, with the published web app loaded.</span></span>

<span data-ttu-id="47137-132">Обратите внимание на формат URL-адреса для приложения является *.azurewebsites {имя приложения} .net*.</span><span class="sxs-lookup"><span data-stu-id="47137-132">Notice the format of the URL for the app is *{app name}.azurewebsites.net*.</span></span> <span data-ttu-id="47137-133">Например, приложение с именем `SignalRChattR` URL-адрес, который выглядит как `https://signalrchattr.azurewebsites.net`.</span><span class="sxs-lookup"><span data-stu-id="47137-133">For example, an app named `SignalRChattR` has a URL that looks like `https://signalrchattr.azurewebsites.net`.</span></span>

<span data-ttu-id="47137-134">См. в случае ошибки HTTP 502.2 [развертывание ASP.NET Core предварительного выпуска в службу приложений Azure](xref:host-and-deploy/azure-apps/index) ее устранения.</span><span class="sxs-lookup"><span data-stu-id="47137-134">If an HTTP 502.2 error occurs, see [Deploy ASP.NET Core preview release to Azure App Service](xref:host-and-deploy/azure-apps/index) to resolve it.</span></span>

## <a name="configure-signalr-web-app"></a><span data-ttu-id="47137-135">Настройка SignalR веб-приложения</span><span class="sxs-lookup"><span data-stu-id="47137-135">Configure SignalR web app</span></span>

<span data-ttu-id="47137-136">Приложения ASP.NET Core SignalR, которые опубликованы как веб-приложение Azure должно быть [сходства ARR](https://en.wikipedia.org/wiki/Application_Request_Routing) включена.</span><span class="sxs-lookup"><span data-stu-id="47137-136">ASP.NET Core SignalR apps that are published as an Azure Web App must have [ARR Affinity](https://en.wikipedia.org/wiki/Application_Request_Routing) enabled.</span></span> <span data-ttu-id="47137-137">[WebSockets](xref:fundamentals/websockets) для должна быть включена, разрешить передачи WebSockets функции.</span><span class="sxs-lookup"><span data-stu-id="47137-137">[WebSockets](xref:fundamentals/websockets) should be enabled, to allow the WebSockets transport to function.</span></span>

<span data-ttu-id="47137-138">На портале Azure перейдите к **параметры приложения** для веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="47137-138">In the Azure portal, navigate to **App Settings** for your web app.</span></span> <span data-ttu-id="47137-139">Задать **WebSockets** для **на**и проверьте **сходства ARR** — **на**.</span><span class="sxs-lookup"><span data-stu-id="47137-139">Set **WebSockets** to **On**, and verify **ARR Affinity** is **On**.</span></span>

![Параметры Azure веб-приложения на портале Azure](publish-to-azure-web-app/_static/azure-web-app-settings.png)

 <span data-ttu-id="47137-141">WebSockets и других транспортов [ограничены зависят от того, план служб приложений](/azure/azure-subscription-service-limits#app-service-limits).</span><span class="sxs-lookup"><span data-stu-id="47137-141">WebSockets and other transports [are limited based on the App Service Plan](/azure/azure-subscription-service-limits#app-service-limits).</span></span>

## <a name="related-resources"></a><span data-ttu-id="47137-142">Связанные ресурсы</span><span class="sxs-lookup"><span data-stu-id="47137-142">Related resources</span></span>

* [<span data-ttu-id="47137-143">Публикация приложения ASP.NET Core в Azure с помощью средств командной строки</span><span class="sxs-lookup"><span data-stu-id="47137-143">Publish an ASP.NET Core app to Azure with command line tools</span></span>](xref:tutorials/publish-to-azure-webapp-using-cli?tabs=windows)
* [<span data-ttu-id="47137-144">Публикация приложения ASP.NET Core в Azure с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="47137-144">Publish an ASP.NET Core app to Azure with Visual Studio</span></span>](xref:tutorials/publish-to-azure-webapp-using-vs)
* [<span data-ttu-id="47137-145">Размещать и развертывать приложения ASP.NET Core Preview в Azure</span><span class="sxs-lookup"><span data-stu-id="47137-145">Host and deploy ASP.NET Core Preview apps on Azure</span></span>](xref:host-and-deploy/azure-apps/index#deploy-aspnet-core-preview-release-to-azure-app-service)