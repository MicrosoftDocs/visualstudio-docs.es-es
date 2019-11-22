---
title: 'How to: Respond to Changes in a UML Model | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9eaaa1406591bc950dbbf95aff8dcd732eef3448
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293399"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Cómo: Responder a cambios en un modelo UML
Es posible escribir código que se ejecute cada vez que se produzca un cambio en un modelo UML en Visual Studio. Responderá igualmente a los cambios realizados directamente por el usuario y por otras extensiones de Visual Studio. Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!WARNING]
> Estas técnicas son non compatible con la API de UML. Es posible no funcionen en futuras versiones de Visual Studio.

## <a name="see-also"></a>Vea también
 [Navigate the UML model](../modeling/navigate-the-uml-model.md) [Event Handlers Propagate Changes Outside the Model](../modeling/event-handlers-propagate-changes-outside-the-model.md) [Sample: Color by Stereotype](https://go.microsoft.com/fwlink/?LinkId=213841)