---
title: "Limitaciones de programaci&#243;n de elementos y controles Host"
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
  - "documentos de Office [desarrollo de Office en Visual Studio], controles host"
  - "desarrollo de aplicaciones [desarrollo de Office en Visual Studio], elementos host"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], elementos host"
  - "elementos host [desarrollo de Office en Visual Studio], limitaciones de programación"
  - "Excel [desarrollo de Office en Visual Studio], elementos host"
  - "controles host [desarrollo de Office en Visual Studio], crear"
  - "personalizaciones de nivel de documento [desarrollo de Office en Visual Studio], controles host"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], controles host"
  - "documentos [desarrollo de Office en Visual Studio], controles host"
  - "controles [desarrollo de Office en Visual Studio], controles host"
  - "controles host [desarrollo de Office en Visual Studio], pasar a métodos y propiedades"
  - "desarrollo de aplicaciones [desarrollo de Office en Visual Studio], controles host"
  - "Excel [desarrollo de Office en Visual Studio], controles host"
  - "controles host [desarrollo de Office en Visual Studio], limitaciones de programación"
  - "documentos [desarrollo de Office en Visual Studio], elementos host"
  - "documentos de Office [desarrollo de Office en Visual Studio], elementos host"
  - "Word [desarrollo de Office en Visual Studio], elementos host"
  - "personalizaciones de nivel de documento [desarrollo de Office en Visual Studio], elementos host"
  - "Word [desarrollo de Office en Visual Studio], controles host"
ms.assetid: 88487946-6f3d-4ea6-8de0-dd219b8002df
caps.latest.revision: 67
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# Limitaciones de programaci&#243;n de elementos y controles Host
  Los elementos y controles host están diseñados para comportarse como los objetos de Microsoft Office Word o Microsoft Office Excel nativos correspondientes, pero con funcionalidad adicional. Sin embargo, hay algunas diferencias fundamentales entre el comportamiento de los elementos y los controles host y los objetos nativos de Office en tiempo de ejecución.  
  
 Para obtener más información sobre los elementos host y los controles host, consulte [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Crear elementos host mediante programación  
 Cuando se crea o se abre mediante programación un documento, un libro o una hoja de cálculo en tiempo de ejecución usando el modelo de objetos de Word o Excel, el elemento no es un elemento host, sino que el nuevo objeto es un objeto de Office nativo. Por ejemplo, si usa el método <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> para crear un nuevo documento de Word en tiempo de ejecución, será un objeto <xref:Microsoft.Office.Interop.Word.Document> nativo en lugar de un elemento host <xref:Microsoft.Office.Tools.Word.Document>. De forma similar, cuando crea una nueva hoja de cálculo en tiempo de ejecución mediante el método <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A>, obtiene un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo en lugar de un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>.  
  
 En los proyectos de nivel de documento, no es posible crear elementos host en tiempo de ejecución. Los elementos host pueden crearse solo en tiempo de diseño en proyectos de nivel de documento. Para obtener más información, vea [Elemento host Document](../vsto/document-host-item.md), [Elemento host Workbook](../vsto/workbook-host-item.md) y [Elemento host Worksheet](../vsto/worksheet-host-item.md).  
  
 En los proyectos de complemento de VSTO, se puede crear los elementos host <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook> o <xref:Microsoft.Office.Tools.Excel.Worksheet> en tiempo de ejecución. Para obtener más información, consulta [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Crear controles host mediante programación  
 Puede agregar mediante programación controles host a un elemento host <xref:Microsoft.Office.Tools.Word.Document> o <xref:Microsoft.Office.Tools.Excel.Worksheet> en tiempo de ejecución. Para obtener más información, consulta [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 No se pueden agregar controles host a <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo.  
  
> [!NOTE]  
>  Los controles host siguientes no se pueden agregar mediante programación a hojas de cálculo ni documentos: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode> y <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## Diferencias de tipos entre elementos host, controles host y objetos de Office nativos  
 Existe un objeto nativo subyacente de Microsoft Office Word o Microsoft Office Excel por cada elemento y control host. Para obtener acceso al objeto subyacente, use la propiedad InnerObject del elemento host o el control host. Sin embargo, no hay forma de convertir un objeto nativo de Office en el elemento o control host correspondiente. Si se intenta convertir un objeto nativo de Office en el tipo de un elemento o control host, se produce una <xref:System.InvalidCastException>.  
  
 Hay varios escenarios donde las diferencias entre los tipos de elementos y controles host y los objetos nativos de Office subyacentes pueden afectar al código.  
  
### Pasar controles host a métodos y propiedades  
 En Word, no se puede pasar un control host a un método o una propiedad que requiera un objeto nativo de Word como parámetro. Es necesario usar la propiedad InnerObject del control host para devolver el objeto nativo subyacente de Word. Por ejemplo, puede pasar un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> a un método pasando la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> del control host <xref:Microsoft.Office.Tools.Word.Bookmark> al método.  
  
 En Excel, debe usar la propiedad InnerObject del control host para pasar el control host a un método o una propiedad cuando el método o la propiedad espera el objeto subyacente de Excel.  
  
 En el ejemplo siguiente se crea un control <xref:Microsoft.Office.Tools.Excel.NamedRange> para pasarlo al método <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>. El código usa la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> del rango con nombre para devolver el <xref:Microsoft.Office.Interop.Excel.Range> subyacente de Office necesario para el método <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>.  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#28)]  
  
### Devolver tipos de métodos y propiedades nativos de Office  
 La mayoría de los métodos y propiedades de lo elementos host devuelven el objeto de Office nativo subyacente en el que se basa el elemento host. Por ejemplo, la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> de un control host <xref:Microsoft.Office.Tools.Excel.NamedRange> en Excel devuelve un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> en lugar de un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>. De igual forma, la propiedad <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> de un control host <xref:Microsoft.Office.Tools.Word.RichTextContentControl> en Word devuelve un objeto <xref:Microsoft.Office.Interop.Word.Document> en lugar de un elemento host <xref:Microsoft.Office.Tools.Word.Document>.  
  
### Acceder a colecciones de controles host  
 El [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] no proporciona colecciones individuales para cada tipo de control host. En su lugar, use la propiedad Controls de un elemento host para iterar por todos los controles administrados \(controles host y controles de Windows Forms\) en el documento o la hoja de cálculo y luego busque elementos que coincidan con el tipo de control host de su interés. En el siguiente ejemplo de código se examina cada control en un documento de Word y se determina si el control es un control <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#10)]  
  
 Para obtener más información sobre la propiedad Controls de los elementos host, consulte [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Los modelos de objetos de Word y Excel incluyen propiedades que exponen colecciones de controles nativos en los documentos y las hojas de cálculo. No se puede acceder a los controles administrados mediante estas propiedades. Por ejemplo, no es posible enumerar cada control host <xref:Microsoft.Office.Tools.Word.Bookmark> en un documento mediante la propiedad <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Document> o la propiedad <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> de un objeto <xref:Microsoft.Office.Tools.Word.Document>. Estas propiedades incluyen solo los controles <xref:Microsoft.Office.Interop.Word.Bookmark> del documento; no contienen los controles host <xref:Microsoft.Office.Tools.Word.Bookmark> del documento.  
  
## Vea también  
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Elemento host Workbook](../vsto/workbook-host-item.md)   
 [Elemento host Document](../vsto/document-host-item.md)  
  
  