---
title: Obtener mensajes sin leer de la bandeja de entrada mediante programación
description: Obtenga información sobre cómo puede usar Visual Studio para recuperar mediante programación mensajes sin leer de la bandeja de entrada de Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], unread mail
- Outlook [Office development in Visual Studio], unread mail
- unread e-mail
- mail items [Office development in Visual Studio], unread mail
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 82bd595b76a03ee730995e546fd9c4e827c95a53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953856"
---
# <a name="how-to-programmatically-retrieve-unread-messages-from-the-inbox"></a>Cómo: recuperar mensajes sin leer de la bandeja de entrada mediante programación
  En este ejemplo se recuperan los mensajes de correo electrónico sin leer de la **bandeja de entrada** de Outlook y se muestra el número de elementos.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-vb[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_UnreadItems/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_UnreadItems/thisaddin.cs#1)]

## <a name="see-also"></a>Vea también
- [Trabajar con elementos de correo](../vsto/working-with-mail-items.md)
- [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Cómo: crear un elemento de correo electrónico mediante programación](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Cómo: enviar correo electrónico mediante programación](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Cómo: realizar acciones al recibir un mensaje de correo electrónico mediante programación](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
