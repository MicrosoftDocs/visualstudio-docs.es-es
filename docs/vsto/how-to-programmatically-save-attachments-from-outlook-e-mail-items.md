---
title: Procedimiento Guardar mediante programación los datos adjuntos de elementos de correo electrónico de Outlook
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d222924e753db1b476a5d7729e2c794a8ab305e2
ms.sourcegitcommit: c6249a8f3054db881ba62f4e80bf006d440f5a2d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2019
ms.locfileid: "66462125"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Procedimiento Guardar mediante programación los datos adjuntos de elementos de correo electrónico de Outlook

En este ejemplo se guardan los datos adjuntos al correo electrónico en una carpeta específica cuando el correo se recibe en la bandeja de entrada.

> [!IMPORTANT]
> En este ejemplo solo funciona si agregar una carpeta denominada **TestFileSave** en la raíz del directorio c.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo

[!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>Vea también

- [Trabajar con elementos de correo](../vsto/working-with-mail-items.md)
- [Cómo: Recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Cómo: Realizar acciones mediante programación cuando se recibe un mensaje de correo electrónico](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Cómo: Buscar en una carpeta específica mediante programación](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
