---
title: 'Cómo: enviar correo electrónico mediante programación'
description: Use Visual Studio para enviar un correo electrónico desde Microsoft Outlook mediante programación. En este ejemplo se envía un mensaje de correo electrónico a los contactos que tienen el nombre de dominio example.com.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5f31fdb92a5acff16b1d6e8001ea88931a9a22ab
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525380"
---
# <a name="how-to-programmatically-send-email"></a>Cómo: enviar correo electrónico mediante programación
  En este ejemplo se envía un mensaje de correo electrónico a los contactos que tienen el nombre de dominio **example.com** en sus direcciones de correo electrónico.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo se necesita:

- Contactos que tienen el nombre de dominio **example.com** en sus direcciones de correo electrónico.

## <a name="robust-programming"></a>Programación sólida
 No quite el código de filtro que busca el nombre de dominio **example.com**. La solución enviará mensajes de correo electrónico a todos los contactos si quita el filtro.

## <a name="see-also"></a>Consulte también
- [Trabajar con elementos de correo](../vsto/working-with-mail-items.md)
- [Cómo: crear un elemento de correo electrónico mediante programación](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Cómo: obtener acceso a los contactos de Outlook mediante programación](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Cómo: realizar acciones al recibir un mensaje de correo electrónico mediante programación](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
