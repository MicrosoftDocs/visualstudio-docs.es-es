---
title: Realizar acciones mediante programación si se recibe un mensaje de correo electrónico
description: Obtenga información sobre cómo puede usar Visual Studio para realizar acciones personalizadas mediante programación si se recibe un correo electrónico en Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d0909b94f00b344383c2b042ec1e143f9294ee8d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888711"
---
# <a name="how-to-programmatically-perform-actions-when-an-email-message-is-received"></a>Cómo: realizar acciones al recibir un mensaje de correo electrónico mediante programación
  Este ejemplo realiza acciones personalizadas cuando el usuario recibe un mensaje de correo electrónico.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-vb[Trin_Outlook_RL_PerformActions#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_PerformActions/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_PerformActions#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_PerformActions/thisaddin.cs#1)]

## <a name="see-also"></a>Vea también
- [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Trabajar con elementos de correo](../vsto/working-with-mail-items.md)
- [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
