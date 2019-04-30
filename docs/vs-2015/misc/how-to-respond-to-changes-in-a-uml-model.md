---
title: Procedimiento Responder a los cambios en un modelo UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4d012e3a8c8ef2a3848c4f602bb92e344550f1e1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434987"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Procedimiento Responder a los cambios en un modelo UML
Es posible escribir código que se ejecute cada vez que se produzca un cambio en un modelo UML en Visual Studio. Responderá igualmente a los cambios realizados directamente por el usuario y por otras extensiones de Visual Studio. Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!WARNING]
> Estas técnicas son non compatible con la API de UML. Es posible no funcionen en futuras versiones de Visual Studio.  
  
 Código de ejemplo está disponible en [UML: Responder a los cambios en un modelo UML mediante eventos y reglas](http://code.msdn.microsoft.com/UML-Responding-to-changes-c024cd4b)  
  
## <a name="see-also"></a>Vea también  
 [Navegar por el modelo UML](../modeling/navigate-the-uml-model.md)   
 [Controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [Ejemplo: Color por estereotipo](http://go.microsoft.com/fwlink/?LinkId=213841)