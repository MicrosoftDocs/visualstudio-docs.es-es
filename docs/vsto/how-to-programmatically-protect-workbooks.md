---
title: "C&#243;mo: Proteger libros mediante programaci&#243;n | Microsoft Docs"
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
  - "protección de documentos, agregar a los libros"
  - "protección de documentos, quitar de los libros"
  - "documentos [desarrollo de Office en Visual Studio], protección de documentos"
  - "libros, contraseñas"
  - "libros, proteger"
  - "libros, desproteger"
ms.assetid: 553c67b9-e2a4-46b6-878c-5b4b4efa4589
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# C&#243;mo: Proteger libros mediante programaci&#243;n
  Puede proteger un libro de Microsoft Office Excel para que los usuarios no puedan agregar ni eliminar hojas de cálculo, y también puede desproteger el libro mediante programación.  Opcionalmente, puede especificar una contraseña, indicar si desea que se proteja la estructura \(para que los usuarios no puedan mover las hojas\) y si desea que estén protegidas las ventanas del libro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 El hecho de que un libro esté protegido no impide a los usuarios editar las celdas.  Para proteger los datos, debe proteger las hojas de cálculo.  Para obtener más información, vea [Cómo: Proteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-protect-worksheets.md).  
  
 En el siguiente código de ejemplo se utiliza una variable que contiene una contraseña que se ha obtenido del usuario.  
  
## Proteger un libro que forma parte de una personalización en el nivel del documento  
  
#### Para proteger un libro  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> del libro e incluya una contraseña.  Para utilizar el ejemplo de código siguiente, ejecútelo en la clase `ThisWorkbook`, no en una clase Sheet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#10)]  
  
#### Para desproteger un libro  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A>, pasando una contraseña si es necesario.  Para utilizar el ejemplo de código siguiente, ejecútelo en la clase `ThisWorkbook`, no en una clase Sheet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#11)]  
  
## Proteger un libro mediante un complemento en el nivel de la aplicación  
  
#### Para proteger un libro  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> del libro e incluya una contraseña.  En este ejemplo de código se usa el libro activo.  Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
#### Para desproteger un libro  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> del libro activo y pase una contraseña si es necesario.  Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [Cómo: Proteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Cómo: Ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  