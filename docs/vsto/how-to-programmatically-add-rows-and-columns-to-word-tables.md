---
title: 'Cómo: agregar filas y columnas a las tablas de Word mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fca44524c3a7c7f10e855eaf62e8b77dc225ae01
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818684"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Cómo: agregar filas y columnas a las tablas de Word mediante programación
  En una tabla de Microsoft Office Word, las celdas se organizan en filas y columnas. Puede usar el método <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> del objeto <xref:Microsoft.Office.Interop.Word.Rows> para agregar filas a la tabla y el método <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> del objeto <xref:Microsoft.Office.Interop.Word.Columns> para agregar columnas.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customization-examples"></a>Ejemplos de personalización de nivel de documento  
 Los siguientes ejemplos de código se pueden usar en una personalización de nivel de documento. Para usar estos ejemplos, ejecútelos desde la clase `ThisDocument` del proyecto. Estos ejemplos suponen que el documento asociado a su personalización ya tiene al menos una tabla.  
  
> [!IMPORTANT]
>  Este código solo se ejecuta en proyectos creados mediante cualquiera de las siguientes plantillas de proyecto:  
> 
> - Documento de Word 2013  
> - Plantilla de Word 2013  
> - Documento de Word 2010  
> - Plantilla de Word 2010  
> 
>   Si desea realizar esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia a la **Microsoft.Office.Interop.Word** ensamblado y, a continuación, debe usar clases de dicho ensamblado para agregar filas y columnas a las tablas. Para obtener más información, consulte [Cómo: las aplicaciones de Office de destino a través de los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) y [referencia de ensamblado de interoperabilidad primario de Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
### <a name="to-add-a-row-to-a-table"></a>Para agregar una fila a una tabla  
  
1.  Use el método <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> para agregar una fila a la tabla.  
  
     [!code-vb[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]  
  
### <a name="to-add-a-column-to-a-table"></a>Para agregar una columna a una tabla  
  
1.  Use el método <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> y, a continuación, use el método <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> para hacer que todas las columnas tengan el mismo ancho.  
  
     [!code-vb[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]  
  
## <a name="vsto-add-in-examples"></a>Ejemplos de complementos de VSTO  
 Los siguientes ejemplos de código se pueden usar en un complemento de VSTO. Para usar los ejemplos, ejecútelos desde la clase `ThisAddIn` del proyecto. Estos ejemplos suponen que el documento activo ya tiene al menos una tabla.  
  
> [!IMPORTANT]  
>  Este código solo se ejecuta en proyectos creados mediante plantillas de complemento de VSTO de Word.  
>   
>  Si desea realizar esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia a la **Microsoft.Office.Interop.Word** ensamblado y, a continuación, debe usar clases de dicho ensamblado para agregar filas y columnas a las tablas. Para obtener más información, consulte [Cómo: las aplicaciones de Office de destino a través de los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) y [referencia de ensamblado de interoperabilidad primario de Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
### <a name="to-add-a-row-to-a-table"></a>Para agregar una fila a una tabla  
  
1.  Use el método <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> para agregar una fila a la tabla.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]  
  
### <a name="to-add-a-column-to-a-table"></a>Para agregar una columna a una tabla  
  
1.  Use el método <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> y, a continuación, use el método <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> para hacer que todas las columnas tengan el mismo ancho.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear tablas de Word mediante programación](../vsto/how-to-programmatically-create-word-tables.md)   
 [Cómo: agregar texto y formato a celdas de tablas de Word mediante programación](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Cómo: rellenar tablas de Word con propiedades de documento mediante programación](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  