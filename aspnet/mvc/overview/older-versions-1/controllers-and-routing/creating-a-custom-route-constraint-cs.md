---
uid: mvc/overview/older-versions-1/controllers-and-routing/creating-a-custom-route-constraint-cs
title: Создание пользовательского ограничения маршрута (C#) | Документация Майкрософт
author: StephenWalther
description: Стивен Вальтер демонстрирует, как можно создать ограничение настраиваемый маршрут. Мы реализуем простой пользовательский ограничение, которое запрещает маршрут соответствует w...
ms.author: riande
ms.date: 02/16/2009
ms.assetid: a4f4bf4e-abcc-4650-8f43-527e48b52fe6
msc.legacyurl: /mvc/overview/older-versions-1/controllers-and-routing/creating-a-custom-route-constraint-cs
msc.type: authoredcontent
ms.openlocfilehash: 0a0b6b706fdb212a745346ffaefc118e85c2a245
ms.sourcegitcommit: 45ac74e400f9f2b7dbded66297730f6f14a4eb25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "41829608"
---
<a name="creating-a-custom-route-constraint-c"></a>Создание пользовательского ограничения маршрута (C#)
====================
по [Стивен Вальтер](https://github.com/StephenWalther)

> Стивен Вальтер демонстрирует, как можно создать ограничение настраиваемый маршрут. Мы реализуем простой пользовательский ограничение, которое предотвращает маршрут соответствует при запрос браузера с удаленного компьютера.


Целью данного учебника — продемонстрировать, как можно создать ограничение настраиваемый маршрут. Настраиваемый маршрут ограничение позволяет предотвратить маршрут соответствует, если только некоторые пользовательские условия.

В этом руководстве мы создадим ограничения маршрута Localhost. Ограничения маршрута Localhost соответствует только запросы, поступающие с локального компьютера. Удаленные запросы из Интернета не совпадают.

Реализуйте ограничение настраиваемый маршрут, реализовав интерфейс IRouteConstraint. Это очень простой интерфейс, который описывает один метод:

[!code-csharp[Main](creating-a-custom-route-constraint-cs/samples/sample1.cs)]

Метод возвращает значение типа Boolean. Если вы возвращаете false, маршрут, связанный с ограничением не будет соответствовать запрос браузера.

Ограничение Localhost содержится в листинге 1.

**В листинге 1 - LocalhostConstraint.cs**

[!code-csharp[Main](creating-a-custom-route-constraint-cs/samples/sample2.cs)]

Ограничение в листинге 1 использует свойство IsLocal класса HttpRequest. Это свойство возвращает значение true, если IP-адрес запроса является либо 127.0.0.1 или если IP-адрес запроса совпадает с IP-адрес сервера.

Можно использовать пользовательские ограничения маршрута, указанным в файле Global.asax. Файл Global.asax в листинге 2 использует ограничение Localhost, чтобы запретить запросе страницы администрирования, если только они сделать запрос с локального сервера. Например запрос /Admin/DeleteAll завершится ошибкой при внесении с удаленного сервера.

**В листинге 2 - Global.asax**

[!code-csharp[Main](creating-a-custom-route-constraint-cs/samples/sample3.cs)]

Ограничение Localhost используется в определении маршрута администратора. Этот маршрут, не будет соответствовать запроса удаленного обозревателя. Учтите, тем не менее, что другие маршруты, указанные в файле Global.asax может соответствовать тот же запрос. Важно понимать, что ограничение предотвращает сопоставление запроса определенного маршрута, и не все маршруты, определенные в файле Global.asax.

Обратите внимание на то, что маршрут по умолчанию был закомментирован из файла Global.asax в листинге 2. Если маршрут по умолчанию, маршрут по умолчанию будет соответствовать запросы для администратора контроллера. В этом случае удаленные пользователи по-прежнему может заставить действия администратора контроллера, несмотря на то, что их запросы не соответствуют маршруту администратора.

> [!div class="step-by-step"]
> [Назад](creating-a-route-constraint-cs.md)
> [Вперед](asp-net-mvc-controller-overview-vb.md)
