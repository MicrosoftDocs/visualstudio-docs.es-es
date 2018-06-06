---
title: Limitaciones de programación de elementos host y controles host
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0b7e45ed9ba8e9fcd42d57a1cc6aaf34ce3e3711
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693388"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Limitaciones de programación de elementos host y controles host
  Los elementos y controles host están diseñados para comportarse como los objetos de Microsoft Office Word o Microsoft Office Excel nativos correspondientes, pero con funcionalidad adicional. Sin embargo, hay algunas diferencias fundamentales entre el comportamiento de los elementos y los controles host y los objetos nativos de Office en tiempo de ejecución.  
  
 Para obtener información general sobre elementos host y controles host, vea [elementos Host y hospedar información general sobre controles](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="programmatically-create-host-items"></a>Crear elementos host mediante programación  
 Cuando se crea o se abre mediante programación un documento, un libro o una hoja de cálculo en tiempo de ejecución usando el modelo de objetos de Word o Excel, el elemento no es un elemento host, sino que el nuevo objeto es un objeto de Office nativo. Por ejemplo, si usa el método <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> para crear un nuevo documento de Word en tiempo de ejecución, será un objeto <xref:Microsoft.Office.Interop.Word.Document> nativo en lugar de un elemento host <xref:Microsoft.Office.Tools.Word.Document> . De forma similar, cuando crea una nueva hoja de cálculo en tiempo de ejecución mediante el método <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> , obtiene un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo en lugar de un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> .  
  
 En los proyectos de nivel de documento, no se puede crear elementos host en tiempo de ejecución. Los elementos host pueden crearse solo en tiempo de diseño en proyectos de nivel de documento. Para obtener más información, consulte [elemento host Document](../vsto/document-host-item.md), [elemento host Workbook](../vsto/workbook-host-item.md), y [elemento host Worksheet](../vsto/worksheet-host-item.md).  
  
 En proyectos de complemento de VSTO, puede crear <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, o <xref:Microsoft.Office.Tools.Excel.Worksheet> hospedar elementos en tiempo de ejecución. Para obtener más información, consulte [documentos de Word extender y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="programmatically-create-host-controls"></a>Crear mediante programación controles host  
 Puede agregar mediante programación controles host a un <xref:Microsoft.Office.Tools.Word.Document> o <xref:Microsoft.Office.Tools.Excel.Worksheet> elemento host en tiempo de ejecución. Para obtener más información, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 No se pueden agregar controles host a <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Worksheet>nativo.  
  
> [!NOTE]  
>  Los controles host siguientes no se pueden agregar mediante programación a hojas de cálculo ni documentos: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>y <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Diferencias de tipo entre los objetos nativos de Office, los elementos host y controles host  
 Existe un objeto nativo subyacente de Microsoft Office Word o Microsoft Office Excel por cada elemento y control host. Tener acceso al objeto subyacente mediante la propiedad InnerObject del elemento host o control host. Sin embargo, no hay forma de convertir un objeto nativo de Office en el elemento o control host correspondiente. Si se intenta convertir un objeto nativo de Office en el tipo de un elemento o control host, se produce una <xref:System.InvalidCastException> .  
  
 Hay varios escenarios donde las diferencias entre los tipos de elementos y controles host y los objetos nativos de Office subyacentes pueden afectar al código.  
  
### <a name="pass-host-controls-to-methods-and-properties"></a>Pasar controles host a métodos y propiedades  
 En Word, no se puede pasar un control host a un método o una propiedad que requiera un objeto nativo de Word como parámetro. Debe utilizar la propiedad InnerObject del control host para devolver el objeto nativo subyacente de Word. Por ejemplo, puede pasar un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> a un método pasando la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> del control host <xref:Microsoft.Office.Tools.Word.Bookmark> al método.  
  
 En Excel, debe utilizar la propiedad InnerObject del control host para pasar el control host a un método o propiedad cuando el método o la propiedad espera el objeto subyacente de Excel.  
  
 En el ejemplo siguiente se crea un control <xref:Microsoft.Office.Tools.Excel.NamedRange> para pasarlo al método <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> . El código usa la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> del rango con nombre para devolver el <xref:Microsoft.Office.Interop.Excel.Range> subyacente de Office necesario para el método <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> .  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]  
  
### <a name="return-types-of-native-office-methods-and-properties"></a>Devolver tipos de propiedades y métodos nativos de Office  
 La mayoría de los métodos y propiedades de lo elementos host devuelven el objeto de Office nativo subyacente en el que se basa el elemento host. Por ejemplo, la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> de un control host <xref:Microsoft.Office.Tools.Excel.NamedRange> en Excel devuelve un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> en lugar de un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> . De igual forma, la propiedad <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> de un control host <xref:Microsoft.Office.Tools.Word.RichTextContentControl> en Word devuelve un objeto <xref:Microsoft.Office.Interop.Word.Document> en lugar de un elemento host <xref:Microsoft.Office.Tools.Word.Document> .  
  
### <a name="access-collections-of-host-controls"></a>Colecciones de acceso de los controles host  
 El [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] no proporciona colecciones individuales para cada tipo de control host. En su lugar, utilice la propiedad de los controles de un elemento host para recorrer en iteración todos los controles administrados (controles host y controles de formularios Windows Forms) en el documento o la hoja de cálculo y, a continuación, busque elementos que coinciden con el tipo del control host que le interesen. En el siguiente ejemplo de código se examina cada control en un documento de Word y se determina si el control es un control <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]  
  
 Para obtener más información acerca de la propiedad de los controles de elementos host, vea [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Los modelos de objetos de Word y Excel incluyen propiedades que exponen colecciones de controles nativos en los documentos y las hojas de cálculo. No se puede acceder a los controles administrados mediante estas propiedades. Por ejemplo, no es posible enumerar cada control host <xref:Microsoft.Office.Tools.Word.Bookmark> en un documento mediante la propiedad <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Document> o la propiedad <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> de un objeto <xref:Microsoft.Office.Tools.Word.Document>. Estas propiedades incluyen solo los controles <xref:Microsoft.Office.Interop.Word.Bookmark> del documento; no contienen los controles host <xref:Microsoft.Office.Tools.Word.Bookmark> del documento.  
  
## <a name="see-also"></a>Vea también  
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Elemento host Workbook](../vsto/workbook-host-item.md)   
 [Elemento host Document](../vsto/document-host-item.md)  
  
  