---
title: 'Cómo: responder a cambios en un modelo UML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eff43f3c7547a46b75885448999335637e9fbc62
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609805"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Cómo: Responder a cambios en un modelo UML
Es posible escribir código que se ejecute cada vez que se produzca un cambio en un modelo UML en Visual Studio. Responderá igualmente a los cambios realizados directamente por el usuario y por otras extensiones de Visual Studio. Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!WARNING]
> Estas técnicas son non compatible con la API de UML. Es posible no funcionen en futuras versiones de Visual Studio.

 El código de ejemplo está disponible en [UML: responder a los cambios en un modelo UML mediante el uso de eventos y reglas](http://code.msdn.microsoft.com/UML-Responding-to-changes-c024cd4b)

## <a name="see-also"></a>Vea también
 [Navegar por los controladores de eventos del modelo UML](../modeling/navigate-the-uml-model.md) [propagar los cambios fuera del modelo de](../modeling/event-handlers-propagate-changes-outside-the-model.md) [ejemplo: color por estereotipo](http://go.microsoft.com/fwlink/?LinkId=213841)