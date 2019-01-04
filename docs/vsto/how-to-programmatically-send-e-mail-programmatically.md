---
title: Procedimiento Enviar correo electrónico
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 91e59cc8d7bd0115a59c71f13e8e2dc200336b29
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53840426"
---
# <a name="how-to-programmatically-send-email"></a>Procedimiento Enviar correo electrónico  
  Este ejemplo envía un mensaje de correo electrónico a los contactos que tienen el nombre de dominio **ejemplo.com** en sus direcciones de correo electrónico.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Contactos que tienen el nombre de dominio **ejemplo.com** en sus direcciones de correo electrónico.  
  
## <a name="robust-programming"></a>Programación sólida  
 No quite el código de filtro que busca el nombre de dominio **ejemplo.com**. La solución enviará mensajes de correo electrónico a todos los contactos si quita el filtro.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con elementos de correo](../vsto/working-with-mail-items.md)   
 [Cómo: Crear un elemento de correo electrónico mediante programación](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Cómo: Acceso mediante programación a los contactos de Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Cómo: Realizar acciones mediante programación cuando se recibe un mensaje de correo electrónico](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
