---
title: 'Cómo: crear tablas de Word mediante programación'
description: Aprenda a usar el método Add de la colección tables para agregar una tabla en el intervalo especificado en un documento de Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f2d31f656f0f383ec63fb50f10b19ee26fe2509e
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523935"
---
# <a name="how-to-programmatically-create-word-tables"></a>Cómo: crear tablas de Word mediante programación
  La colección <xref:Microsoft.Office.Interop.Word.Tables> es un miembro de las clases <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection> y <xref:Microsoft.Office.Interop.Word.Range>, lo que significa que puede crear una tabla en cualquiera de estos contextos. Use el método <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> de la colección <xref:Microsoft.Office.Interop.Word.Tables> para agregar una tabla al intervalo especificado.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="create-tables-in-document-level-customizations"></a>Crear tablas en personalizaciones de nivel de documento

### <a name="to-add-a-table-to-a-document"></a>Para agregar una tabla a un documento

- Use el método <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> para agregar una tabla que conste de tres filas y cuatro columnas al principio del documento.

   Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

   [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]

  Al crear una tabla, se agrega automáticamente a la colección <xref:Microsoft.Office.Interop.Word.Tables> del elemento host <xref:Microsoft.Office.Tools.Word.Document>. Después, puede hacer referencia a la tabla por su número de elemento usando la propiedad <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, como se muestra en el código siguiente.

### <a name="to-refer-to-a-table-by-item-number"></a>Para hacer referencia a una tabla por su número de elemento

1. Use la propiedad <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> y proporcione el número de elemento de la tabla a la que desee hacer referencia.

    Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

    [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]

   Cada objeto <xref:Microsoft.Office.Interop.Word.Table> tiene también una propiedad <xref:Microsoft.Office.Interop.Word.Table.Range%2A> que le permite establecer atributos de formato.

### <a name="to-apply-a-style-to-a-table"></a>Para aplicar un estilo a una tabla

1. Use la propiedad <xref:Microsoft.Office.Interop.Word.Table.Style%2A> para aplicar a una tabla uno de los estilos integrados en Word.

     Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]

## <a name="create-tables-in-vsto-add-ins"></a>Crear tablas en complementos de VSTO

### <a name="to-add-a-table-to-a-document"></a>Para agregar una tabla a un documento

- Use el método <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> para agregar una tabla que conste de tres filas y cuatro columnas al principio del documento.

   En el siguiente ejemplo de código se agrega una tabla al documento activo. Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.

   [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]

  Al crear una tabla, se agrega automáticamente a la colección <xref:Microsoft.Office.Interop.Word.Tables> del <xref:Microsoft.Office.Interop.Word.Document>. Después, puede hacer referencia a la tabla por su número de elemento usando la propiedad <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, como se muestra en el código siguiente.

### <a name="to-refer-to-a-table-by-item-number"></a>Para hacer referencia a una tabla por su número de elemento

1. Use la propiedad <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> y proporcione el número de elemento de la tabla a la que desee hacer referencia.

    En el siguiente ejemplo de código se usa el documento activo. Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]

   Cada objeto <xref:Microsoft.Office.Interop.Word.Table> tiene también una propiedad <xref:Microsoft.Office.Interop.Word.Table.Range%2A> que le permite establecer atributos de formato.

### <a name="to-apply-a-style-to-a-table"></a>Para aplicar un estilo a una tabla

1. Use la propiedad <xref:Microsoft.Office.Interop.Word.Table.Style%2A> para aplicar a una tabla uno de los estilos integrados en Word.

     En el siguiente ejemplo de código se usa el documento activo. Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]

## <a name="see-also"></a>Consulte también
- [Cómo: agregar texto y formato a celdas de tablas de Word mediante programación](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Cómo: Agregar filas y columnas a tablas de Word mediante programación](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Cómo: rellenar tablas de Word con propiedades de documento mediante programación](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
