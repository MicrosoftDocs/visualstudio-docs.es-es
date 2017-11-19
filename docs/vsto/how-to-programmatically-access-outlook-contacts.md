---
title: "Cómo: obtener acceso mediante programación a los contactos de Outlook | Documentos de Microsoft"
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
helpviewer_keywords: contacts [Office development in Visual Studio], searching
ms.assetid: ea2297ea-6802-40e4-af1a-1e511a71ec75
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8ee2c597c1a3b6a7c068c8206a87195779877461
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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
  
  