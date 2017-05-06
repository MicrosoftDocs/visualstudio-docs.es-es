---
title: "C&#243;mo: Agregar filas y columnas a tablas de Word mediante programaci&#243;n"
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
  - "columnas [desarrollo de Office en Visual Studio], agregar a las tablas de Word"
  - "filas [desarrollo de Office en Visual Studio], agregar a las tablas de Word"
  - "tablas [desarrollo de Office en Visual Studio], agregar filas y columnas"
ms.assetid: 01a9b6ca-1373-4a6e-b9e6-2225a1321daf
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# C&#243;mo: Agregar filas y columnas a tablas de Word mediante programaci&#243;n
  En una tabla de Microsoft Office Word, las celdas se organizan en filas y columnas.  Puede usar el método <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> del objeto <xref:Microsoft.Office.Interop.Word.Rows> para agregar filas a la tabla y el método <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> del objeto <xref:Microsoft.Office.Interop.Word.Columns> para agregar columnas.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Ejemplos de personalización de nivel de documento  
 Los siguientes ejemplos de código se pueden usar en una personalización de nivel de documento.  Para usar estos ejemplos, ejecútelos desde la clase `ThisDocument` del proyecto.  Estos ejemplos suponen que el documento asociado a su personalización ya tiene al menos una tabla.  
  
> [!IMPORTANT]  
>  Este código solo se ejecuta en proyectos creados mediante cualquiera de las siguientes plantillas de proyecto:  
>   
>  -   Documento de Word 2013  
> -   Plantilla de Word 2013  
> -   Documento de Word 2010  
> -   Plantilla de Word 2010  
>   
>  Si desea llevar a cabo esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia al ensamblado **Microsoft.Office.Interop.Word** y, después, debe usar las clases de dicho ensamblado para agregar filas y columnas a las tablas.  Para obtener más información, vea [Cómo: Apuntar a las aplicaciones de Office mediante los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) y [Referencia de ensamblado de interoperabilidad primario de Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### Para agregar una fila a una tabla  
  
1.  Use el método <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> para agregar una fila a la tabla.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomation#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#95)]  
  
#### Para agregar una columna a una tabla  
  
1.  Use el método <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> y, a continuación, use el método <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> para hacer que todas las columnas tengan el mismo ancho.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomation#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#96)]  
  
## Ejemplos para complementos de VSTO  
 Los siguientes ejemplos de código se pueden usar en un complemento de VSTO.  Para usar los ejemplos, ejecútelos desde la clase `ThisAddIn` del proyecto.  Estos ejemplos suponen que el documento activo ya tiene al menos una tabla.  
  
> [!IMPORTANT]  
>  Este código solo se ejecuta en proyectos creados mediante plantillas de complemento de VSTO de Word.  
>   
>  Si desea llevar a cabo esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia al ensamblado **Microsoft.Office.Interop.Word** y, después, debe usar las clases de dicho ensamblado para agregar filas y columnas a las tablas.  Para obtener más información, vea [Cómo: Apuntar a las aplicaciones de Office mediante los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) y [Referencia de ensamblado de interoperabilidad primario de Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### Para agregar una fila a una tabla  
  
1.  Use el método <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> para agregar una fila a la tabla.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#95)]  
  
#### Para agregar una columna a una tabla  
  
1.  Use el método <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> y, a continuación, use el método <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> para hacer que todas las columnas tengan el mismo ancho.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#96)]  
  
## Vea también  
 [Cómo: Crear tablas de Word mediante programación](../vsto/how-to-programmatically-create-word-tables.md)   
 [Cómo: Agregar texto y formato a celdas de tablas de Word mediante programación](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Cómo: Rellenar tablas de Word con propiedades de documento mediante programación](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  