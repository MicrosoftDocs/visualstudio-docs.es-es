---
title: 'Cómo: asociar una página web a una carpeta de Outlook mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2cb1ef525917288dc44609b899611db884da9073
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256470"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Cómo: asociar una página web a una carpeta de Outlook mediante programación
  En este ejemplo se comprueba una carpeta denominada `HtmlView` en Microsoft Office Outlook. Si la carpeta no existe, el código crea la carpeta y le asigna una página Web. Si la carpeta no existe, el código muestra el contenido de la carpeta.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con carpetas](../vsto/working-with-folders.md)   
 [Cómo: recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Cómo: crear elementos de carpeta personalizados mediante programación](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  