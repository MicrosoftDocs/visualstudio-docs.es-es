---
title: 'Cómo: guardar mediante programación los datos adjuntos de elementos de correo electrónico de Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd564b71622ad5f9ee6500ddc3864bad0b21686b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674455"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Cómo: guardar mediante programación los datos adjuntos de elementos de correo electrónico de Outlook
  En este ejemplo se guardan los datos adjuntos al correo electrónico en una carpeta específica cuando el correo se recibe en la bandeja de entrada.  
  
> [!IMPORTANT]  
>  En este ejemplo solo funciona si agregar una carpeta denominada **TestFileSave** en la raíz del directorio c.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con elementos de correo](../vsto/working-with-mail-items.md)   
 [Cómo: recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Cómo: realizar acciones mediante programación cuando se recibe un mensaje de correo electrónico](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [Cómo: buscar en una carpeta específica mediante programación](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  