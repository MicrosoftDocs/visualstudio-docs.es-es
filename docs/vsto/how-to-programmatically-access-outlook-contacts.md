---
title: 'Cómo: obtener acceso mediante programación a los contactos de Outlook | Documentos de Microsoft'
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
ms.openlocfilehash: c48a58a4215ce73bcc6e9f4593819cbbdbed1693
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Cómo: Obtener acceso a los contactos de Outlook mediante programación
  Este ejemplo busca todos los contactos cuyos apellidos contengan una cadena de búsqueda especificado.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Contactos cuyos apellidos contengan la cadena "**Na"** (por ejemplo, Tzipi Butnaru) en el **contactos** carpeta.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con contactos](../vsto/working-with-contact-items.md)   
 [Cómo: agregar una entrada mediante programación a los contactos de Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Cómo: buscar un contacto específico mediante programación](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Cómo: buscar una dirección de correo electrónico en los contactos mediante programación](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Cómo: Eliminar contactos de Outlook mediante programación](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  