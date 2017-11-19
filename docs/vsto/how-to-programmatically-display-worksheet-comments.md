---
title: "Cómo: mostrar los comentarios de la hoja de cálculo mediante programación | Documentos de Microsoft"
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
- worksheets, comments
- comments, worksheets
ms.assetid: f5ce5e7f-bae4-40b7-951c-0f15b140aaf2
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 20381a6db187536dc729c08bb046152a0489e6a1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Cómo: Mostrar los comentarios de las hojas de cálculo mediante programación
  Puede mostrar y ocultar comentarios en las hojas de cálculo de Microsoft Office Excel mediante programación.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Para mostrar todos los comentarios de una hoja de cálculo en una personalización de nivel de documento  
  
1.  Establezca la propiedad <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> en **true** si desea mostrar los comentarios; en caso contrario, **false**. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Para mostrar todos los comentarios de una hoja de cálculo en un complemento de VSTO de nivel de aplicación  
  
1.  Establezca la propiedad <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> en **true** si desea mostrar los comentarios; en caso contrario, **false**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: agregar mediante programación y eliminar comentarios en una hoja de cálculo](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
  