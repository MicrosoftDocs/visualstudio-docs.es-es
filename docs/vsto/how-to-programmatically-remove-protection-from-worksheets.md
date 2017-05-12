---
title: "C&#243;mo: Desproteger hojas de c&#225;lculo mediante programaci&#243;n"
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
  - "hojas de cálculo, desproteger"
  - "documentos [desarrollo de Office en Visual Studio], protección de documentos"
  - "protección de documento, quitar de las hojas de cálculo"
  - "Unprotect (método)"
ms.assetid: 034688d2-eda7-4b4a-bcc2-d0999ff879a4
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# C&#243;mo: Desproteger hojas de c&#225;lculo mediante programaci&#243;n
  Puede quitar mediante programación la protección de una hoja de cálculo de Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 En el ejemplo siguiente se usa la variable `getPasswordFromUser`, que contiene una contraseña obtenida del usuario.  
  
### Para desproteger una hoja de cálculo en una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> de la hoja de cálculo y pase la contraseña, si es necesario. En este ejemplo se da por supuesto que está trabajando con una hoja de cálculo denominada `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#28)]  
  
### Para desproteger una hoja de cálculo en un complemento VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> de la hoja de cálculo activa y pase la contraseña, si es necesario.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#18)]  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Proteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Cómo: Proteger libros mediante programación](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Cómo: Ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  