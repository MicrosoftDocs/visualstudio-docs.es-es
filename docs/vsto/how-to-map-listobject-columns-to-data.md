---
title: "C&#243;mo: Asignar columnas ListObject a datos"
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
  - "datos [desarrollo de Office en Visual Studio], asignar a columna ListObject"
  - "Control ListObject, asignar datos"
ms.assetid: 2108d0c3-d595-410e-a0ae-3dd53bf6bcc7
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# C&#243;mo: Asignar columnas ListObject a datos
  Al enlazar un control <xref:Microsoft.Office.Tools.Excel.ListObject> a un <xref:System.Data.DataTable>, puede que no desee mostrar todas las columnas de una lista o puede que tenga algunas columnas que no están enlazadas a datos. Puede asignar las columnas que desea que aparezca en <xref:Microsoft.Office.Tools.Excel.ListObject> al llamar al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A>.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![vínculo a vídeo](~/docs/data-tools/media/playvideo.gif "vínculo a vídeo") Para una demostración en vídeo relacionada, vea [Cómo: crear una lista de Excel conectada a una lista de SharePoint](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
## Asignar columnas  
  
#### Para asignar una tabla de datos a columnas en una lista  
  
1.  Cree la <xref:System.Data.DataTable> en el nivel de clase.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#16)]  
  
2.  Agregue columnas de ejemplo y datos en el controlador de eventos `Startup` de la clase `Sheet1` \(en un proyecto de nivel de documento\) o una clase `ThisAddIn` \(en un proyecto de complemento de VSTO\).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#17)]  
  
3.  Llame al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> y pase los nombres de columna en el orden en que deben aparecer. El objeto de lista se enlazará a los <xref:System.Data.DataTable> recientemente creados, pero el orden de las columnas en el objeto de lista diferirá del orden en que aparecen en <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#18)]  
  
## Especificar columnas no asignadas  
 Al asignar columnas a un <xref:System.Data.DataTable>, también puede especificar que algunas columnas no se enlacen a datos pasando una cadena vacía. A continuación, se agrega al control <xref:Microsoft.Office.Tools.Excel.ListObject> una nueva columna que no esté enlazada a datos.  
  
#### Para especificar una columna no asignada al asignar columnas ListObject  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> y pase los nombres de columna en el orden en que deben aparecer. Use una cadena vacía para indicar dónde se agrega una columna no asignada; en este caso, entre la columna de título y la última columna de nombre.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#19)]  
  
## Compilar el código  
 Este ejemplo de código supone que dispone de un <xref:Microsoft.Office.Tools.Excel.ListObject> existente denominado `list1` en la hoja de cálculo en la que aparece este código.  
  
## Vea también  
 [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Cómo: Rellenar los controles ListObject con datos](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject &#40;Control&#41;](../vsto/listobject-control.md)  
  
  