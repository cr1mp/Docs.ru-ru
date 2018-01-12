---
uid: web-forms/overview/ajax-control-toolkit/collapsiblepanel/collapsing-and-expanding-a-panel-from-javascript-vb
title: "Свертывание и развертывание панели из кода JavaScript (VB) | Документы Microsoft"
author: wenz
description: "Предоставляет ему возможность свернуть его содержимое и разверните его и расширяет их возможности панели управления CollapsiblePanel в наборе элементов управления ASP.NET AJAX..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/02/2008
ms.topic: article
ms.assetid: 298789b4-2964-49f5-a0a8-d4dbeb9ff2c2
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/collapsiblepanel/collapsing-and-expanding-a-panel-from-javascript-vb
msc.type: authoredcontent
ms.openlocfilehash: 6adca6771042cad71139977496f985cb8dac63aa
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2017
---
<a name="collapsing-and-expanding-a-panel-from-javascript-vb"></a><span data-ttu-id="4cfa7-103">Свертывание и развертывание панели из кода JavaScript (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cfa7-103">Collapsing and Expanding a Panel from JavaScript (VB)</span></span>
====================
<span data-ttu-id="4cfa7-104">по [Кристиан Wenz](https://github.com/wenz)</span><span class="sxs-lookup"><span data-stu-id="4cfa7-104">by [Christian Wenz](https://github.com/wenz)</span></span>

<span data-ttu-id="4cfa7-105">[Загрузить код](http://download.microsoft.com/download/8/a/a/8aab3c3e-de6f-463f-805c-5fda567eef6e/CollapsiblePanel1.vb.zip) или [скачать PDF](http://download.microsoft.com/download/b/6/a/b6ae89ee-df69-4c87-9bfb-ad1eb2b23373/collapsiblepanel1VB.pdf)</span><span class="sxs-lookup"><span data-stu-id="4cfa7-105">[Download Code](http://download.microsoft.com/download/8/a/a/8aab3c3e-de6f-463f-805c-5fda567eef6e/CollapsiblePanel1.vb.zip) or [Download PDF](http://download.microsoft.com/download/b/6/a/b6ae89ee-df69-4c87-9bfb-ad1eb2b23373/collapsiblepanel1VB.pdf)</span></span>

> <span data-ttu-id="4cfa7-106">CollapsiblePanel управления в наборе элементов управления ASP.NET AJAX расширяет панели и предоставляет ему возможность свернуть его содержимое и развернуть его снова.</span><span class="sxs-lookup"><span data-stu-id="4cfa7-106">The CollapsiblePanel control in the ASP.NET AJAX Control Toolkit extends a panel and provides it with the capability to collapse its contents and expand it again.</span></span> <span data-ttu-id="4cfa7-107">Эти два действия могут также инициироваться из пользовательского кода JavaScript.</span><span class="sxs-lookup"><span data-stu-id="4cfa7-107">These two actions can also be triggered from custom JavaScript code.</span></span>


## <a name="overview"></a><span data-ttu-id="4cfa7-108">Обзор</span><span class="sxs-lookup"><span data-stu-id="4cfa7-108">Overview</span></span>

<span data-ttu-id="4cfa7-109">CollapsiblePanel управления в наборе элементов управления ASP.NET AJAX расширяет панели и предоставляет ему возможность свернуть его содержимое и развернуть его снова.</span><span class="sxs-lookup"><span data-stu-id="4cfa7-109">The CollapsiblePanel control in the ASP.NET AJAX Control Toolkit extends a panel and provides it with the capability to collapse its contents and expand it again.</span></span> <span data-ttu-id="4cfa7-110">Эти два действия могут также инициироваться из пользовательского кода JavaScript.</span><span class="sxs-lookup"><span data-stu-id="4cfa7-110">These two actions can also be triggered from custom JavaScript code.</span></span>

## <a name="steps"></a><span data-ttu-id="4cfa7-111">Шаги</span><span class="sxs-lookup"><span data-stu-id="4cfa7-111">Steps</span></span>

<span data-ttu-id="4cfa7-112">Во-первых, создайте новую страницу ASP.NET и включите `ScriptManager` в пределах одного `<form>` элемента.</span><span class="sxs-lookup"><span data-stu-id="4cfa7-112">First of all, create a new ASP.NET page and include the `ScriptManager` within the one `<form>` element.</span></span> <span data-ttu-id="4cfa7-113">Это загружает библиотеки ASP.NET AJAX, необходимый для набора элементов управления:</span><span class="sxs-lookup"><span data-stu-id="4cfa7-113">This loads the ASP.NET AJAX library which is required by the Control Toolkit:</span></span>

[!code-aspx[Main](collapsing-and-expanding-a-panel-from-javascript-vb/samples/sample1.aspx)]

<span data-ttu-id="4cfa7-114">Затем создайте панель с какой-либо текст, можно увидеть эффект развернут или свернут:</span><span class="sxs-lookup"><span data-stu-id="4cfa7-114">Then, create a panel with some text so that the collapse/expand effect can be seen:</span></span>

[!code-aspx[Main](collapsing-and-expanding-a-panel-from-javascript-vb/samples/sample2.aspx)]

<span data-ttu-id="4cfa7-115">Как видите, панель ссылается на класс CSS, который приведен ниже (и по существу, определяет фоновый цвет и ширину панели):</span><span class="sxs-lookup"><span data-stu-id="4cfa7-115">As you can see, the panel references a CSS class which is shown here (and basically defines a background color and the panel's width):</span></span>

[!code-css[Main](collapsing-and-expanding-a-panel-from-javascript-vb/samples/sample3.css)]

<span data-ttu-id="4cfa7-116">`CollapsiblePanelExtender` Управления требует `TargetControlID` таким образом, набор средств знает, какая панель, чтобы свернуть или развернуть по запросу:</span><span class="sxs-lookup"><span data-stu-id="4cfa7-116">The `CollapsiblePanelExtender` control requires the `TargetControlID` attribute so that the toolkit knows which panel to collapse or expand upon request:</span></span>

[!code-aspx[Main](collapsing-and-expanding-a-panel-from-javascript-vb/samples/sample4.aspx)]

<span data-ttu-id="4cfa7-117">К сожалению расширитель в настоящее время не предоставляет определенный интерфейс API для свертывания и развертывания панели, но некоторые методы недокументированные происходит.</span><span class="sxs-lookup"><span data-stu-id="4cfa7-117">Unfortunately, the extender currently does not expose a specific API for collapsing or expanding the panel, but some undocumented methods will do.</span></span> <span data-ttu-id="4cfa7-118">Во-первых добавьте три кнопки HTML для страницы, которое затем запускает клиентский сценарий JavaScript, чтобы свернуть или развернуть содержимого панели:</span><span class="sxs-lookup"><span data-stu-id="4cfa7-118">First of all, add three HTML buttons to the page which will then trigger the client-side JavaScript to collapse or expand the panel's contents:</span></span>

[!code-aspx[Main](collapsing-and-expanding-a-panel-from-javascript-vb/samples/sample5.aspx)]

<span data-ttu-id="4cfa7-119">В код JavaScript на стороне клиента (работы с `<script type="text/javascript">`), `$find()` метод должен использоваться для доступа к `CollapsiblePanelExtender`.</span><span class="sxs-lookup"><span data-stu-id="4cfa7-119">In the client-side JavaScript code (started with `<script type="text/javascript">`), the `$find()` method needs to be used to access the `CollapsiblePanelExtender`.</span></span> <span data-ttu-id="4cfa7-120">`$find("cpe")`Возвращает ссылку на него.</span><span class="sxs-lookup"><span data-stu-id="4cfa7-120">`$find("cpe")` will return a reference to it.</span></span> <span data-ttu-id="4cfa7-121">Оттуда на определенных методов будет решения поставленной задачи.</span><span class="sxs-lookup"><span data-stu-id="4cfa7-121">From there on, specific methods will solve the task at hand.</span></span>

<span data-ttu-id="4cfa7-122">Метод для открытия (расширение) называется панели `_doOpen()`; в следующем коде реализуется `doOpen()` функция, вызываемая при нажатии кнопки первой:</span><span class="sxs-lookup"><span data-stu-id="4cfa7-122">The method for opening (expanding) the panel is called `_doOpen()`; the following code implements the `doOpen()` function called when the first button is clicked:</span></span>

[!code-javascript[Main](collapsing-and-expanding-a-panel-from-javascript-vb/samples/sample6.js)]

<span data-ttu-id="4cfa7-123">Для закрытия или свертывания панели, `_doClose()` метод должен быть выполнен.</span><span class="sxs-lookup"><span data-stu-id="4cfa7-123">For closing, or collapsing the panel, the `_doClose()` method needs to be executed.</span></span> <span data-ttu-id="4cfa7-124">Поэтому при щелчке вторая кнопка называется следующий код JavaScript:</span><span class="sxs-lookup"><span data-stu-id="4cfa7-124">So when the user clicks on the second button, the following JavaScript code is called:</span></span>

[!code-javascript[Main](collapsing-and-expanding-a-panel-from-javascript-vb/samples/sample7.js)]

<span data-ttu-id="4cfa7-125">Третья кнопка переключает состояние панели: из свернуть, чтобы развернуть и наоборот.</span><span class="sxs-lookup"><span data-stu-id="4cfa7-125">The third button toggles the state of the panel: from collapsed to expanded, and vice versa.</span></span> <span data-ttu-id="4cfa7-126">`CollapsiblePanelExtender` Предоставляет `toggle()` метод, который делает именно это: изменяет состояние панели.</span><span class="sxs-lookup"><span data-stu-id="4cfa7-126">The `CollapsiblePanelExtender` exposes the `toggle()` method which does exactly that: reverses the state of the panel.</span></span> <span data-ttu-id="4cfa7-127">Однако есть еще один подход (который внутренне используется для `toggle()` метод): `get_Collapsed()` метод `CollapsiblePanelExtender()` сообщает, свернута ли панель или нет.</span><span class="sxs-lookup"><span data-stu-id="4cfa7-127">However there is also another approach (which is internally used by the `toggle()` method): The `get_Collapsed()` method of the `CollapsiblePanelExtender()` tells us whether the panel is collapsed or not.</span></span> <span data-ttu-id="4cfa7-128">В зависимости от возвращаемого значения функции, является панели, то либо разворачивать (`_doOpen()` метод) и в свернутом виде (`_doClose()`) метод:</span><span class="sxs-lookup"><span data-stu-id="4cfa7-128">Depending on the return value of this function, the panel is then either expanded (`_doOpen()` method) or collapsed (`_doClose()`) method:</span></span>

[!code-javascript[Main](collapsing-and-expanding-a-panel-from-javascript-vb/samples/sample8.js)]


<span data-ttu-id="4cfa7-129">[![Третья кнопка изменяет состояние панели: из свернуть, чтобы развернутые и назад](collapsing-and-expanding-a-panel-from-javascript-vb/_static/image2.png)](collapsing-and-expanding-a-panel-from-javascript-vb/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="4cfa7-129">[![The third button changes the state of the panel: from collapsed to expanded and back](collapsing-and-expanding-a-panel-from-javascript-vb/_static/image2.png)](collapsing-and-expanding-a-panel-from-javascript-vb/_static/image1.png)</span></span>

<span data-ttu-id="4cfa7-130">Третья кнопка изменяет состояние панели: из свернуть, чтобы развернутые и задней ([Просмотр полноразмерное изображение](collapsing-and-expanding-a-panel-from-javascript-vb/_static/image3.png))</span><span class="sxs-lookup"><span data-stu-id="4cfa7-130">The third button changes the state of the panel: from collapsed to expanded and back ([Click to view full-size image](collapsing-and-expanding-a-panel-from-javascript-vb/_static/image3.png))</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="4cfa7-131">Назад</span><span class="sxs-lookup"><span data-stu-id="4cfa7-131">Previous</span></span>](collapsing-and-expanding-a-panel-from-javascript-cs.md)