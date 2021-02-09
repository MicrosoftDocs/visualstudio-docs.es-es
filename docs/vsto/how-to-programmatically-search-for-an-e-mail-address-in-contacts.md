---
title: Buscar una dirección de correo electrónico en contactos mediante programación
description: Obtenga información sobre cómo puede usar Visual Studio para buscar una dirección de correo electrónico en los contactos de Microsoft Outlook mediante programación.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 43baafee82cf38dfd346ebe50e9b348857a3fdc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920461"
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
