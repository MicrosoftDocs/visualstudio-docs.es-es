---
title: 'Cómo: Enviar correo electrónico mediante programación'
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fa6a45a199d4edce924f0e36a971026726d96eca
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824801"
---
# <a name="how-to-programmatically-send-email"></a>Cómo: Enviar correo electrónico mediante programación
  En este ejemplo se envía un mensaje de correo electrónico a los contactos que tienen el nombre **de dominio example.com** en sus direcciones de correo electrónico.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Ejemplo
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo se necesita:

- Los contactos que tienen el nombre de **dominio example.com** en sus direcciones de correo electrónico.

## <a name="robust-programming"></a>Programación sólida
 No quite el código de filtro que busca el nombre de dominio **example.com**. La solución enviará mensajes de correo electrónico a todos los contactos si quita el filtro.

## <a name="see-also"></a>Consulte también
- [Trabajar con elementos de correo](../vsto/working-with-mail-items.md)
- [Cómo: Crear mediante programación un elemento de correo electrónico](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Cómo: Acceder a los contactos de Outlook mediante programación](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Cómo: Realizar acciones mediante programación cuando se recibe un mensaje de correo electrónico](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
