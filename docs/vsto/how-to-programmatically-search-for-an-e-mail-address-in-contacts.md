---
title: 'Cómo: buscar una dirección de correo electrónico en los contactos mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e7b9c4c7d02f3cd1564e6733c46cb821eade7f54
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675488"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Cómo: buscar una dirección de correo electrónico en los contactos mediante programación
  En este ejemplo se busca en una carpeta de contactos los contactos que tienen el nombre de dominio **ejemplo.com** en sus direcciones de correo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Contactos que tengan el nombre de dominio **ejemplo.com** en sus direcciones de correo (por ejemplo, `somebody@example.com`) y que tengan nombres y apellidos.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con elementos de contacto](../vsto/working-with-contact-items.md)   
 [Cómo: enviar correo electrónico](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Cómo: obtener acceso mediante programación a los contactos de Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Cómo: agregar una entrada a los contactos de Outlook mediante programación](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  