---
title: Buscar una dirección de correo electrónico en contactos mediante programación
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a4a9d52ae16b77b40461a314c6008f8cdd741bcd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537649"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Cómo: buscar una dirección de correo electrónico en contactos mediante programación
  En este ejemplo se busca en una carpeta de contactos los contactos que tienen el nombre de dominio **ejemplo.com** en sus direcciones de correo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo se necesita:

- Contactos que tengan el nombre de dominio **ejemplo.com** en sus direcciones de correo (por ejemplo, `somebody@example.com`) y que tengan nombres y apellidos.

## <a name="see-also"></a>Vea también
- [Trabajar con elementos de contacto](../vsto/working-with-contact-items.md)
- [Cómo: enviar correo electrónico mediante programación](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Cómo: obtener acceso a los contactos de Outlook mediante programación](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Cómo: agregar una entrada a contactos de Outlook mediante programación](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
