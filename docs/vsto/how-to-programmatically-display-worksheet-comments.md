---
title: "C&#243;mo: Mostrar los comentarios de las hojas de c&#225;lculo mediante programaci&#243;n"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "hojas de cálculo, comentarios"
  - "comentarios, hojas de cálculo"
ms.assetid: f5ce5e7f-bae4-40b7-951c-0f15b140aaf2
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# C&#243;mo: Mostrar los comentarios de las hojas de c&#225;lculo mediante programaci&#243;n
  Puede mostrar y ocultar comentarios en las hojas de cálculo de Microsoft Office Excel mediante programación.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Para mostrar todos los comentarios de una hoja de cálculo en una personalización de nivel de documento  
  
1.  Establezca la propiedad <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> en **true** si desea mostrar los comentarios; en caso contrario, **false**. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#31)]  
  
### Para mostrar todos los comentarios de una hoja de cálculo en un complemento de VSTO de nivel de aplicación  
  
1.  Establezca la propiedad <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> en **true** si desea mostrar los comentarios; en caso contrario, **false**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#21)]  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Agregar y eliminar comentarios en una hoja de cálculo mediante programación](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
  