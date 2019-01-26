---
title: Procedimiento Acceso mediante programación a los contactos de Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b47d90eef38c5aff055b7ba2a05e39f8de17269
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873670"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Procedimiento Acceso mediante programación a los contactos de Outlook
  Este ejemplo busca todos los contactos cuyos apellidos contengan una cadena de búsqueda especificado.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compile-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Contactos cuyos apellidos contengan la cadena "**Na"** (por ejemplo, Tzipi Butnaru) en el **contactos** carpeta.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con elementos de contacto](../vsto/working-with-contact-items.md)   
 [Cómo: Agregar una entrada a los contactos de Outlook mediante programación](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Cómo: Buscar un contacto específico mediante programación](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Cómo: Buscar una dirección de correo electrónico en los contactos mediante programación](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Cómo: Eliminar contactos de Outlook mediante programación](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
