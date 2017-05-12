---
title: "C&#243;mo: Copiar hojas de c&#225;lculo mediante programaci&#243;n"
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
  - "Excel [desarrollo de Office en Visual Studio], copiar hojas de cálculo"
  - "hojas de cálculo, copiar"
ms.assetid: e49e03f5-7b2f-416b-b5fe-0965336c47e1
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# C&#243;mo: Copiar hojas de c&#225;lculo mediante programaci&#243;n
  Puede crear una copia de una hoja de cálculo e insertarla antes o después de otra hoja existente en el libro.  Si no especifica dónde insertarla, Excel crea un nuevo libro para la nueva hoja de cálculo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Tanto si copia la hoja de cálculo mediante programación como si el usuario final copia la hoja de cálculo manualmente, no hay ningún código detrás de la nueva hoja de cálculo y los controles de la nueva hoja de cálculo no funcionan.  Esto se debe a que la hoja de cálculo recién copiada es un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> y no un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>.  Los controles de Windows Forms y los controles host solo pueden agregarse a elementos host.  Para obtener más información, consulte [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### Para agregar una hoja de cálculo copiada a un libro en una personalización de nivel de documento  
  
1.  Use el método <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> para copiar la primera hoja de cálculo en el libro actual y colocarla tras la tercera hoja.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#16)]  
  
### Para agregar una hoja de cálculo copiada a un libro en un complemento de VSTO  
  
1.  Use el método <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> para copiar la primera hoja de cálculo en el libro actual y colocarla tras la tercera hoja.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Cómo: Agregar nuevas hojas de cálculo a libros mediante programación](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Cómo: Eliminar hojas de cálculo de libros mediante programación](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Cómo: Seleccionar hojas de cálculo mediante programación](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  