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
ms.openlocfilehash: cf88661f9ec15e1a3a25e7eb6a40bbd82335a7f4
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918719"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Cómo: Responder a cambios en un modelo UML
Es posible escribir código que se ejecute cada vez que se produzca un cambio en un modelo UML en Visual Studio. Responderá igualmente a los cambios realizados directamente por el usuario y por otras extensiones de Visual Studio. Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!WARNING]
> Estas técnicas son non compatible con la API de UML. Es posible no funcionen en futuras versiones de Visual Studio.

## <a name="see-also"></a>Vea también
 [Navegar por los controladores de eventos del modelo UML](../modeling/navigate-the-uml-model.md) [propagar los cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)
 