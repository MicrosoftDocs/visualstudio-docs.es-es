---
title: 'Cómo: crear tablas de Word mediante programación | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f77b6ee70d56c12b6c1a6b9c88de36a9adb7d92e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-create-word-tables"></a>Cómo: Crear tablas de Word mediante programación
  La colección <xref:Microsoft.Office.Interop.Word.Tables> es un miembro de las clases <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection> y <xref:Microsoft.Office.Interop.Word.Range>, lo que significa que puede crear una tabla en cualquiera de estos contextos. Use el método <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> de la colección <xref:Microsoft.Office.Interop.Word.Tables> para agregar una tabla al intervalo especificado.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="creating-tables-in-document-level-customizations"></a>Crear tablas en personalizaciones de nivel de documento  
  
#### <a name="to-add-a-simple-table-to-a-document"></a>Para agregar una tabla sencilla a un documento  
  
-   Use el método <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> para agregar una tabla que conste de tres filas y cuatro columnas al principio del documento.  
  
     Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]  
  
 Al crear una tabla, se agrega automáticamente a la colección <xref:Microsoft.Office.Interop.Word.Tables> del elemento host <xref:Microsoft.Office.Tools.Word.Document>. Después, puede hacer referencia a la tabla por su número de elemento usando la propiedad <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, como se muestra en el código siguiente.  
  
#### <a name="to-refer-to-a-table-by-item-number"></a>Para hacer referencia a una tabla por su número de elemento  
  
1.  Use la propiedad <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> y proporcione el número de elemento de la tabla a la que desee hacer referencia.  
  
     Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]  
  
 Cada objeto <xref:Microsoft.Office.Interop.Word.Table> tiene también una propiedad <xref:Microsoft.Office.Interop.Word.Table.Range%2A> que le permite establecer atributos de formato.  
  
#### <a name="to-apply-a-style-to-a-table"></a>Para aplicar un estilo a una tabla  
  
1.  Use la propiedad <xref:Microsoft.Office.Interop.Word.Table.Style%2A> para aplicar a una tabla uno de los estilos integrados en Word.  
  
     Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]  
  
## <a name="creating-tables-in-vsto-add-ins"></a>Crear tablas en complementos de VSTO  
  
#### <a name="to-add-a-simple-table-to-a-document"></a>Para agregar una tabla sencilla a un documento  
  
-   Use el método <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> para agregar una tabla que conste de tres filas y cuatro columnas al principio del documento.  
  
     En el siguiente ejemplo de código se agrega una tabla al documento activo. Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]  
  
 Al crear una tabla, se agrega automáticamente a la colección <xref:Microsoft.Office.Interop.Word.Tables> del <xref:Microsoft.Office.Interop.Word.Document>. Después, puede hacer referencia a la tabla por su número de elemento usando la propiedad <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, como se muestra en el código siguiente.  
  
#### <a name="to-refer-to-a-table-by-item-number"></a>Para hacer referencia a una tabla por su número de elemento  
  
1.  Use la propiedad <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> y proporcione el número de elemento de la tabla a la que desee hacer referencia.  
  
     En el siguiente ejemplo de código se usa el documento activo. Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]  
  
 Cada objeto <xref:Microsoft.Office.Interop.Word.Table> tiene también una propiedad <xref:Microsoft.Office.Interop.Word.Table.Range%2A> que le permite establecer atributos de formato.  
  
#### <a name="to-apply-a-style-to-a-table"></a>Para aplicar un estilo a una tabla  
  
1.  Use la propiedad <xref:Microsoft.Office.Interop.Word.Table.Style%2A> para aplicar a una tabla uno de los estilos integrados en Word.  
  
     En el siguiente ejemplo de código se usa el documento activo. Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: agregar texto y formato a las celdas de las tablas de Word mediante programación](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Cómo: agregar mediante programación filas y columnas a las tablas de Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Cómo: rellenar mediante programación las tablas de Word con propiedades de documento](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  