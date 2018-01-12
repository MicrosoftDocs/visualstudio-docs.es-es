---
title: "Cómo: agregar texto y formato a las celdas de las tablas de Word mediante programación | Documentos de Microsoft"
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
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2742215f01065fb90d8a312eaa324e0cecccb57b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Cómo: Agregar texto y formato a celdas de tablas de Word mediante programación
  Cada tabla consta de una colección de celdas. Cada objeto <xref:Microsoft.Office.Interop.Word.Cell> individual representa una celda de la tabla. Se hace referencia a cada celda mediante su ubicación en la tabla. Este ejemplo hace referencia a la celda ubicada en la primera fila y la primera columna de la tabla, le añade texto y le aplica formato.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-add-text-and-formatting-to-cells"></a>Para agregar texto y formato a celdas  
  
1.  Haga referencia a la celda por su ubicación en la tabla, agregue texto a la celda y aplique el formato.  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento. Para usar este ejemplo, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]  
  
     El siguiente ejemplo de código se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo. Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear tablas de Word mediante programación](../vsto/how-to-programmatically-create-word-tables.md)   
 [Cómo: agregar mediante programación filas y columnas a las tablas de Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Cómo: Rellenar tablas de Word con propiedades de documento mediante programación](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  