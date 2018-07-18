---
title: 'Cómo: obtener acceso mediante programación a los contactos de Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6ee09e0d0a51675bc00b19aedd0508276cb0cb09
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255946"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Cómo: obtener acceso mediante programación a los contactos de Outlook
  Este ejemplo busca todos los contactos cuyos apellidos contengan una cadena de búsqueda especificado.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compile-the-code"></a>Compile el código  
 Para este ejemplo se necesita:  
  
-   Contactos cuyos apellidos contengan la cadena "**Na"** (por ejemplo, Tzipi Butnaru) en el **contactos** carpeta.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con elementos de contacto](../vsto/working-with-contact-items.md)   
 [Cómo: agregar una entrada a los contactos de Outlook mediante programación](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Cómo: buscar un contacto específico mediante programación](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Cómo: buscar una dirección de correo electrónico en los contactos mediante programación](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Cómo: eliminar contactos de Outlook mediante programación](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  