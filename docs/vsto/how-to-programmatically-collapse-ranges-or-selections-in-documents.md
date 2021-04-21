---
title: Contraer rangos o selecciones en documentos mediante programación
description: Aprenda que si está trabajando con un objeto Range o Selection, puede que quiera cambiar la selección a un punto de inserción antes de insertar texto.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5d1fb41943690da5144fb06245ed7f4aa70250aa
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828649"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Cómo: Contraer rangos o selecciones en documentos mediante programación
  Si está trabajando con un objeto <xref:Microsoft.Office.Interop.Word.Range> o <xref:Microsoft.Office.Interop.Word.Selection> , puede que desee cambiar la selección a un punto de inserción antes de insertar el texto, para no sobrescribir el texto existente. Los objetos <xref:Microsoft.Office.Interop.Word.Range> y tienen un método <xref:Microsoft.Office.Interop.Word.Selection> Collapse, que usa los valores de <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> enumeración :

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> contrae la selección hasta el principio de la selección. Esta es la opción predeterminada si no especifica un valor de enumeración.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> contrae la selección hasta el final de la selección.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>Para contraer un rango e insertar texto nuevo

1. Cree un objeto <xref:Microsoft.Office.Interop.Word.Range> formado por el primer párrafo del documento.

    El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet46":::

    El siguiente ejemplo de código se puede usar en un complemento de VSTO. Este código usa el documento activo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet46":::

2. Utilice el valor de enumeración <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> para contraer el rango.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet47":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet47":::

3. Inserte el texto nuevo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet48":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet48":::

4. Seleccione <xref:Microsoft.Office.Interop.Word.Range>.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet49":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet49":::

   Si usa el valor de enumeración <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> , el texto se inserta al principio del párrafo siguiente.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet50":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet50":::

   Puede que espere que al insertar una nueva frase, se inserte antes del marcador de párrafo, pero esto no ocurre porque el rango original incluye la marca de párrafo. Para obtener más información, [vea Cómo: Excluir mediante programación marcas de párrafo al crear intervalos](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).

## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Para contraer un intervalo en una personalización de nivel de documento

1. En el siguiente ejemplo se muestra el método completo de una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet45":::

## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Para contraer un intervalo en un complemento de VSTO

1. En el ejemplo siguiente se muestra el método completo para un complemento de VSTO. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet45":::

## <a name="see-also"></a>Consulte también
- [Cómo: Insertar texto mediante programación en documentos de Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: Recuperar mediante programación caracteres iniciales y finales en intervalos](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Cómo: Excluir marcas de párrafo mediante programación al crear intervalos](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Cómo: Ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Cómo: Restablecer intervalos en documentos de Word mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
