---
title: Buscar una dirección de correo electrónico en contactos mediante programación
description: Obtenga información sobre cómo puede usar Visual Studio para buscar mediante programación una dirección de correo electrónico en los contactos de Microsoft Outlook.
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
ms.openlocfilehash: cd977840cd75081d87011540ca00675fb84cee36
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828948"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Cómo: Buscar mediante programación una dirección de correo electrónico en contactos
  En este ejemplo se busca en una carpeta de contactos los contactos que tienen el nombre de dominio **ejemplo.com** en sus direcciones de correo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo se necesita:

- Contactos que tengan el nombre de dominio **ejemplo.com** en sus direcciones de correo (por ejemplo, `somebody@example.com`) y que tengan nombres y apellidos.

## <a name="see-also"></a>Consulte también
- [Trabajar con elementos de contacto](../vsto/working-with-contact-items.md)
- [Cómo: Enviar correo electrónico mediante programación](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Cómo: Acceder a contactos de Outlook mediante programación](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Cómo: Agregar mediante programación una entrada a contactos de Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
