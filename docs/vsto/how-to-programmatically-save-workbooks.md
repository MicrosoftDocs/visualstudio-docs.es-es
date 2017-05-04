---
title: "C&#243;mo: Guardar libros mediante programaci&#243;n | Microsoft Docs"
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
  - "libros, guardar"
  - "libros, guardar copias de seguridad"
  - "libros, guardar en formato XML"
ms.assetid: 991ccf9b-5213-4094-9030-284ec167bdcc
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# C&#243;mo: Guardar libros mediante programaci&#243;n
  Existen varias formas de guardar un libro.  Puede guardar un libro sin cambiar la ruta de acceso.  Si el libro nunca se guardó, debe guardarlo especificando una ruta de acceso.  Sin una ruta de acceso explícita, Microsoft Office Excel guarda el archivo en la carpeta actual con el nombre que se especificó cuando se creó.  También puede guardar una copia del libro sin modificar el libro abierto en memoria.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Guardar un libro sin cambiar la ruta de acceso  
  
#### Para guardar un libro asociado a una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> de la clase ThisWorkbook.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#4)]  
  
#### Para guardar el libro activo en un complemento de VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> para guardar el libro activo.  Para usar el ejemplo de código siguiente, ejecútelo en la clase `ThisAddIn` en un proyecto de complemento de VSTO para Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Guardar un libro con una nueva ruta de acceso  
 Puede guardar el libro especificado en una ubicación nueva o con un nombre nuevo, especificando opcionalmente un formato de archivo, una contraseña y un modo de acceso, entre otras cosas.  
  
> [!NOTE]  
>  Tal vez desee establecer la propiedad <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> en **False** antes de guardar el libro con una nueva ruta de acceso, ya que guardar en algunos formatos requiere interacción.  Si esta propiedad se establece en **False**, Excel usa todos los valores predeterminados.  
  
#### Para guardar un libro asociado a una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> de la clase `ThisWorkbook`.  Para usar el siguiente ejemplo de código, ejecútelo en la clase `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#5)]  
  
#### Para guardar el libro activo en un complemento de VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> para guardar el libro activo en una nueva ruta de acceso.  Para usar el ejemplo de código siguiente, ejecútelo en la clase `ThisAddIn` en un proyecto de complemento de VSTO para Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## Guardar una copia del libro  
 Puede guardar una copia del libro en un archivo sin modificar el libro abierto en memoria.  Esto es útil cuando se desea crear una copia de seguridad sin modificar la ubicación del libro.  
  
#### Para guardar un libro asociado a una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> de la clase `ThisWorkbook`.  Para usar el siguiente ejemplo de código, ejecútelo en la clase `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#6)]  
  
#### Para guardar el libro activo en un complemento de VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> para guardar una copia del libro activo.  Para usar el ejemplo de código siguiente, ejecútelo en la clase `ThisAddIn` en un proyecto de complemento de VSTO para Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## Programación eficaz  
 Si se cancela interactivamente cualquiera de los métodos que guardan o copian el libro se produce un error en tiempo de ejecución en el código.  Por ejemplo, si el procedimiento llama al método <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> pero no deshabilita los mensajes de Excel y el usuario hace clic en **Cancelar** cuando se le pide, Excel genera un error en tiempo de ejecución.  
  
## Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [Elemento host Workbook](../vsto/workbook-host-item.md)   
 [Cómo: Cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
  