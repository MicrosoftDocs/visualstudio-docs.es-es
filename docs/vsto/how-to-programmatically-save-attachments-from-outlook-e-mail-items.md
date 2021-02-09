---
title: Guardar datos adjuntos de elementos de correo electrónico de Outlook mediante programación
description: Obtenga información sobre cómo puede usar Visual Studio para guardar datos adjuntos de los elementos de correo electrónico de Microsoft Outlook mediante programación.
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
ms.openlocfilehash: 516b6b680b8718747490a8afd9cdd2f823e996e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880468"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Cómo: guardar datos adjuntos de elementos de correo electrónico de Outlook mediante programación

En este ejemplo se guardan los datos adjuntos al correo electrónico en una carpeta específica cuando el correo se recibe en la bandeja de entrada.

> [!IMPORTANT]
> Este ejemplo solo funciona si agrega una carpeta denominada **TestFileSave** en la raíz del directorio C.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo

[!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>Vea también

- [Trabajar con elementos de correo](../vsto/working-with-mail-items.md)
- [Cómo: recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Cómo: realizar acciones al recibir un mensaje de correo electrónico mediante programación](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Cómo: buscar en una carpeta específica mediante programación](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
