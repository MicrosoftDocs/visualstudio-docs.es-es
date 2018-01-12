---
title: "Cómo: determinar mediante programación el elemento de Outlook actual | Documentos de Microsoft"
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
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: de17e299e98a46a82547bc38dfecd17a9f5aea58
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Cómo: Determinar el elemento actual de Outlook mediante programación
  En este ejemplo se utiliza el evento Explorer.SelectionChange para mostrar el nombre de la carpeta actual y alguna información sobre el elemento seleccionado. El código, a continuación, muestra el elemento seleccionado.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Cita, póngase en contacto con y elementos de correo electrónico en Microsoft Office Outlook.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)   
 [Cómo: recuperar una carpeta por su nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Cómo: Buscar un contacto específico mediante programación](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  