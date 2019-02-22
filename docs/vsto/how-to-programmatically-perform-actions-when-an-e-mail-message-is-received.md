---
title: Filtrar Realizar acciones mediante programación cuando se recibe un mensaje de correo electrónico
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], actions when e-mail is received
- NewMail event
- mail items [Office development in Visual Studio], custom actions
- e-mail [Office development in Visual Studio], custom actions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 31f195d6b83a93363c3b2ef3bfa7d829f5fc822d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612353"
---
# <a name="how-to-programmatically-perform-actions-when-an-email-message-is-received"></a>Filtrar Realizar acciones mediante programación cuando se recibe un mensaje de correo electrónico
  En este ejemplo realiza acciones personalizadas cuando el usuario recibe un mensaje de correo electrónico.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-vb[Trin_Outlook_RL_PerformActions#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_PerformActions/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_PerformActions#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_PerformActions/thisaddin.cs#1)]

## <a name="see-also"></a>Vea también
- [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Trabajar con elementos de correo](../vsto/working-with-mail-items.md)
- [Empezar a programar complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
