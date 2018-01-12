---
title: "Cómo: guardar mediante programación los datos adjuntos de elementos de correo electrónico de Outlook | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: f87b05b45fafab3ad28a6da6a98391b8d121be7e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-save-attachments-from-outlook-e-mail-items"></a>Cómo: Guardar datos adjuntos de elementos de correo electrónico de Outlook mediante programación
  En este ejemplo se guardan los datos adjuntos al correo electrónico en una carpeta específica cuando el correo se recibe en la bandeja de entrada.  
  
> [!IMPORTANT]  
>  En este ejemplo solo funciona si se agrega una carpeta denominada **TestFileSave** en la raíz del directorio c.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con elementos de correo](../vsto/working-with-mail-items.md)   
 [Cómo: recuperar una carpeta por su nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Cómo: realizar acciones mediante programación cuando se recibe un mensaje de correo electrónico](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [Cómo: Buscar en una carpeta específica mediante programación](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  