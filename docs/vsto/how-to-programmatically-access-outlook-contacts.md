---
title: 'Cómo: obtener acceso a los contactos de Outlook mediante programación'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 2f6d64512af660392c10082e3bcd3c26b6bc6885
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520101"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Cómo: obtener acceso a los contactos de Outlook mediante programación
  Este ejemplo busca todos los contactos cuyos nombres contienen una cadena de búsqueda especificada.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo se necesita:

- Contactos cuyos apellidos contienen la cadena "**na"** (por ejemplo, Tzipi Butnaru) en la carpeta **contactos** .

## <a name="see-also"></a>Consulte también
- [Trabajar con elementos de contacto](../vsto/working-with-contact-items.md)
- [Cómo: agregar una entrada a contactos de Outlook mediante programación](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Cómo: buscar un contacto específico mediante programación](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Cómo: buscar una dirección de correo electrónico en contactos mediante programación](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Cómo: eliminar contactos de Outlook mediante programación](../vsto/how-to-programmatically-delete-outlook-contacts.md)
