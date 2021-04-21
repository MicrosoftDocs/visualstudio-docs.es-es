---
title: 'Cómo: Acceder a los contactos de Outlook mediante programación'
description: Obtenga información sobre cómo puede acceder a los contactos de Outlook mediante programación. En este ejemplo se buscan todos los contactos cuyos apellidos contienen una cadena de búsqueda especificada.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 08e9d9ea69985a26a9688152f5c3b028caf75300
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828909"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Cómo: Acceder a los contactos de Outlook mediante programación
  En este ejemplo se buscan todos los contactos cuyos apellidos contienen una cadena de búsqueda especificada.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb" id="Snippet1":::


## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo se necesita:

- Contactos cuyos apellidos contienen la cadena **"Na"** (por ejemplo, Tzipi Butnuz) en la **carpeta Contactos.**

## <a name="see-also"></a>Consulte también
- [Trabajar con elementos de contacto](../vsto/working-with-contact-items.md)
- [Cómo: Agregar mediante programación una entrada a contactos de Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Cómo: Buscar mediante programación un contacto específico](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Cómo: Buscar mediante programación una dirección de correo electrónico en los contactos](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Cómo: Eliminar contactos de Outlook mediante programación](../vsto/how-to-programmatically-delete-outlook-contacts.md)
