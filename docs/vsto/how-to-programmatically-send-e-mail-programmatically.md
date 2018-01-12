---
title: "Cómo: enviar correo electrónico | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f8681fecf8dc2d4c3a26aeaeb372faeb57e54094
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-send-e-mail"></a>Cómo: enviar un correo electrónico mediante programación  
  Este ejemplo envía un mensaje de correo electrónico a los contactos que tienen el nombre de dominio **ejemplo.com** en sus direcciones de correo electrónico.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Contactos que tienen el nombre de dominio **ejemplo.com** en sus direcciones de correo electrónico.  
  
## <a name="robust-programming"></a>Programación sólida  
 No quite el código de filtro que busca el nombre de dominio **ejemplo.com**. La solución enviará mensajes de correo electrónico a todos los contactos si quita el filtro.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con elementos de correo](../vsto/working-with-mail-items.md)   
 [Cómo: crear un elemento de correo electrónico mediante programación](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Cómo: obtener acceso mediante programación a los contactos de Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Cómo: Realizar acciones al recibir un mensaje de correo mediante programación](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  