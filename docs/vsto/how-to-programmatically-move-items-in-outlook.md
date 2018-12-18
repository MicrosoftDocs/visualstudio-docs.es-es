---
title: 'Cómo: mover elementos en Outlook mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fced6a5e41d2b79d32575f20d224f75053acb988
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257727"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Cómo: mover elementos en Outlook mediante programación
  Este ejemplo mueve los mensajes de correo electrónico no leídos desde el **Bandeja de entrada** en una carpeta denominada **prueba**. El ejemplo mueve sólo los mensajes que tienen la palabra **prueba** en el `Subject` campo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Compile el código  
 Para este ejemplo se necesita:  
  
-   Una carpeta de correo electrónico de Outlook denominada **prueba**.  
  
-   Un mensaje de correo electrónico que llega con la palabra **prueba** en el `Subject` campo.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con carpetas](../vsto/working-with-folders.md)   
 [Cómo: recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Cómo: buscar en una carpeta específica mediante programación](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Cómo: realizar acciones mediante programación cuando se recibe un mensaje de correo electrónico](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  