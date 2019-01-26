---
title: Procedimiento Asociar una página web a una carpeta de Outlook mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c60ac58c59adaacd66a7c56b4c394d596cfd6b24
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871278"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Procedimiento Asociar una página web a una carpeta de Outlook mediante programación
  En este ejemplo se comprueba una carpeta denominada `HtmlView` en Microsoft Office Outlook. Si la carpeta no existe, el código crea la carpeta y le asigna una página Web. Si la carpeta no existe, el código muestra el contenido de la carpeta.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con carpetas](../vsto/working-with-folders.md)   
 [Cómo: Recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Cómo: Crear elementos de carpeta personalizados mediante programación](../vsto/how-to-programmatically-create-custom-folder-items.md)  
