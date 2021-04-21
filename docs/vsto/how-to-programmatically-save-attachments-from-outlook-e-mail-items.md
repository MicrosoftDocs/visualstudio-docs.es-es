---
title: Guardar datos adjuntos de elementos de correo electrónico de Outlook mediante programación
description: Obtenga información sobre cómo puede usar Visual Studio guardar los datos adjuntos de los elementos de correo electrónico de Microsoft Outlook mediante programación.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ad64593f91e14bcfd993929420764869a8359e3e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826699"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Cómo: Guardar datos adjuntos de elementos de correo electrónico de Outlook mediante programación

En este ejemplo se guardan los datos adjuntos al correo electrónico en una carpeta específica cuando el correo se recibe en la bandeja de entrada.

> [!IMPORTANT]
> Este ejemplo solo funciona si agrega una carpeta denominada **TestFileSave** en la raíz del directorio C.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo

:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Consulte también

- [Trabajar con elementos de correo](../vsto/working-with-mail-items.md)
- [Cómo: Recuperar mediante programación una carpeta por nombre](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Cómo: Realizar acciones mediante programación cuando se recibe un mensaje de correo electrónico](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Cómo: Buscar mediante programación dentro de una carpeta específica](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
