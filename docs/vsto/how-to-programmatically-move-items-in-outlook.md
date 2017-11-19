---
title: "Cómo: mover elementos mediante programación en Outlook | Documentos de Microsoft"
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
helpviewer_keywords: Outlook folders [Office development in Visual Studio], moving items
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fc7afe28e435e0dcdd58c7403f6282ebf3609a23
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Cómo: Mover elementos en Outlook mediante programación
  Este ejemplo mueve mensajes de correo electrónico no leídos desde el **Bandeja de entrada** en una carpeta denominada **prueba**. En el ejemplo se mueve únicamente los mensajes que tienen la palabra **prueba** en el `Subject` campo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Una carpeta de correo electrónico de Outlook con el nombre **prueba**.  
  
-   Un mensaje de correo electrónico que llega con la palabra **prueba** en el `Subject` campo.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con carpetas](../vsto/working-with-folders.md)   
 [Cómo: recuperar una carpeta por su nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Cómo: buscar en una carpeta específica mediante programación](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Cómo: Realizar acciones al recibir un mensaje de correo mediante programación](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  