---
title: 'Cómo: agregar y eliminar comentarios en una hoja de cálculo mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fe41fe7f6370697335fa76b468e79e61d6e1269a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673868"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Cómo: agregar y eliminar comentarios en una hoja de cálculo mediante programación
  Puede agregar y eliminar comentarios en las hojas de cálculo de Microsoft Office Excel mediante programación. Los comentarios solo se pueden agregar a celdas individuales y no a intervalos de varias celdas.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Agregar y eliminar un comentario en un proyecto de nivel de documento  
 En los ejemplos siguientes, se da por hecho que hay un control <xref:Microsoft.Office.Tools.Excel.NamedRange> de una sola celda denominado `dateComment` en una hoja de cálculo denominada `Sheet1`.  
  
### <a name="to-add-a-new-comment-to-a-named-range"></a>Agregar un nuevo comentario a un intervalo con nombre  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> del control <xref:Microsoft.Office.Tools.Excel.NamedRange> y escriba el texto del comentario. Este código se debe colocar en la clase `Sheet1` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]  
  
#### <a name="to-delete-a-comment-from-a-named-range"></a>Eliminar un comentario de un intervalo con nombre  
  
1.  Compruebe si en el intervalo hay un comentario y elimínelo. Este código se debe colocar en la clase `Sheet1` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]  
  
## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Agregar y eliminar un comentario en un proyecto de complemento VSTO  
 En los ejemplos siguientes, se da por hecho que hay una sola celda <xref:Microsoft.Office.Interop.Excel.Range> denominada `dateComment` en una hoja de cálculo.  
  
### <a name="to-add-a-new-comment-to-an-excel-range"></a>Agregar un nuevo comentario a un intervalo de Excel  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> de <xref:Microsoft.Office.Interop.Excel.Range> y escriba el texto del comentario.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]  
  
### <a name="to-delete-a-comment-from-an-excel-range"></a>Eliminar un comentario de un intervalo de Excel  
  
1.  Compruebe si en el intervalo hay un comentario y elimínelo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: mostrar mediante programación los comentarios de la hoja de cálculo](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [NamedRange (control)](../vsto/namedrange-control.md)  
  
  