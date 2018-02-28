---
title: "Cómo: buscar en una carpeta específica mediante programación | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 71b9da77857bb82a27f6bd6ae057a1df1fca8a1d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Cómo: Buscar en una carpeta específica mediante programación
  Este ejemplo de código se utiliza el `Find` y `FindNext` métodos para buscar texto en el campo de asunto de mensajes de correo electrónico que se encuentran en el **Bandeja de entrada**. Este método utiliza un filtro de cadena para comprobar la letra T como la letra inicial de la `Subject` texto.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con carpetas](../vsto/working-with-folders.md)   
 [Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)   
 [Cómo: Recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  