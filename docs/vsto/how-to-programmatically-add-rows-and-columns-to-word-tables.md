---
title: 'Cómo: Agregar filas y columnas a tablas de Word mediante programación'
description: Obtenga información sobre cómo puede usar el método Add del objeto Rows para agregar filas a la tabla. También puede usar el método Add del objeto Columns para agregar columnas.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7cac3e11f73e53441f1bcf20c67dd5659a49a1b0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828428"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Cómo: Agregar filas y columnas a tablas de Word mediante programación
  En una tabla de Microsoft Office Word, las celdas se organizan en filas y columnas. Puede usar el método <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> del objeto <xref:Microsoft.Office.Interop.Word.Rows> para agregar filas a la tabla y el método <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> del objeto <xref:Microsoft.Office.Interop.Word.Columns> para agregar columnas.

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Ejemplos de personalización de nivel de documento
 Los siguientes ejemplos de código se pueden usar en una personalización de nivel de documento. Para usar estos ejemplos, ejecútelos desde la clase `ThisDocument` del proyecto. Estos ejemplos suponen que el documento asociado a su personalización ya tiene al menos una tabla.

> [!IMPORTANT]
> Este código solo se ejecuta en proyectos creados mediante cualquiera de las siguientes plantillas de proyecto:
>
> - Documento de Word 2013
> - Plantilla de Word 2013
> - Documento de Word 2010
> - Plantilla de Word 2010
>
>   Si desea realizar esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia al ensamblado **Microsoft.Office.Interop.Word** y, a continuación, debe usar clases de ese ensamblado para agregar filas y columnas a las tablas. Para obtener más información, [vea Cómo:](how-to-target-office-applications-through-primary-interop-assemblies.md) Dirigir aplicaciones de Office a través de ensamblados de interoperabilidad primarios y Referencia de ensamblados de [interoperabilidad primarios de Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>Para agregar una fila a una tabla

1. Use el método <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> para agregar una fila a la tabla.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet95":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet95":::

### <a name="to-add-a-column-to-a-table"></a>Para agregar una columna a una tabla

1. Use el método <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> y, a continuación, use el método <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> para hacer que todas las columnas tengan el mismo ancho.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet96":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet96":::

## <a name="vsto-add-in-examples"></a>Ejemplos de complementos de VSTO
 Los siguientes ejemplos de código se pueden usar en un complemento de VSTO. Para usar los ejemplos, ejecútelos desde la clase `ThisAddIn` del proyecto. Estos ejemplos suponen que el documento activo ya tiene al menos una tabla.

> [!IMPORTANT]
> Este código solo se ejecuta en proyectos creados mediante plantillas de complemento de VSTO de Word.
>
> Si desea realizar esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia al ensamblado **Microsoft.Office.Interop.Word** y, a continuación, debe usar clases de ese ensamblado para agregar filas y columnas a las tablas. Para obtener más información, [vea Cómo:](how-to-target-office-applications-through-primary-interop-assemblies.md) Dirigir aplicaciones de Office a través de ensamblados de interoperabilidad primarios y Referencia de ensamblados de [interoperabilidad primarios de Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>Para agregar una fila a una tabla

1. Use el método <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> para agregar una fila a la tabla.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet95":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet95":::

### <a name="to-add-a-column-to-a-table"></a>Para agregar una columna a una tabla

1. Use el método <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> y, a continuación, use el método <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> para hacer que todas las columnas tengan el mismo ancho.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet96":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet96":::

## <a name="see-also"></a>Consulte también
- [Cómo: Crear tablas de Word mediante programación](how-to-programmatically-create-word-tables.md)
- [Cómo: Agregar texto y formato a celdas de tablas de Word mediante programación](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Cómo: Rellenar tablas de Word mediante programación con propiedades de documento](how-to-programmatically-populate-word-tables-with-document-properties.md)
