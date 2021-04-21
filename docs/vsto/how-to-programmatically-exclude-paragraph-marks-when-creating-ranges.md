---
title: Excluir marcas de párrafo al crear intervalos mediante programación
description: Obtenga información sobre cómo puede excluir marcas de párrafo mediante programación al crear intervalos en un documento de Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c0929ccf3bb2567099dc7f3b795ad2257da0edb3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825802"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Cómo: Excluir marcas de párrafo mediante programación al crear intervalos
  Siempre que se crea un objeto <xref:Microsoft.Office.Interop.Word.Range> basado en un párrafo, todos los caracteres no imprimibles (como las marcas de párrafo), se incluirán en el intervalo. Es posible que desee insertar el texto de un párrafo de origen en un párrafo de destino. Si no desea dividir el párrafo de destino en párrafos independientes, en primer lugar, tendrá que quitar la marca de párrafo del párrafo de origen. Además, dado que la información de formato de párrafo se almacena en la marca de párrafo, es posible que no desee incluirla cuando inserte el intervalo en un párrafo existente.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 El siguiente procedimiento de ejemplo declara dos variables de cadena, recupera el contenido del primer y del segundo párrafo del documento activo y, a continuación, intercambia su contenido. A continuación, el ejemplo muestra cómo se elimina la marca de párrafo del intervalo mediante el método <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> , y cómo se inserta el texto dentro del párrafo.

## <a name="to-control-paragraph-structure-when-inserting-text"></a>Controlar la estructura de un párrafo cuando se inserta texto

1. Cree dos variables de intervalo para los párrafos primero y segundo y recupere su contenido mediante la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> .

     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet27":::

     El siguiente ejemplo de código se puede usar en un complemento VSTO de nivel de aplicación. Este código usa el documento activo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet27":::

2. Asigne la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> , intercambiando el texto entre los dos párrafos.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet28":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet28":::

3. Seleccione los intervalos por turnos y haga una pausa para mostrar los resultados en un cuadro de mensaje.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet29":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet29":::

4. Ajuste `firstRange` con el método <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> , de forma que la marca de párrafo deje de formar parte del elemento `firstRange`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet30":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet30":::

5. Sustituya el resto del texto del primer párrafo, asignando una cadena nueva a la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> del intervalo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet31":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet31":::

6. Sustituya el texto en `secondRange`, incluyendo la marca de párrafo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet32":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet32":::

7. Seleccione `firstRange` y haga una pausa para mostrar los resultados en un cuadro de mensaje. A continuación, proceda de igual forma con `secondRange`.

     Dado que `firstRange` se ha redefinido para excluir la marca de párrafo, el formato original del párrafo se conserva. Sin embargo, se insertó una frase sobre la marca de párrafo en `secondRange`, lo cual elimina el párrafo independiente.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet33":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet33":::

     El contenido original de los dos intervalos se guardó como cadenas, lo que permite restaurar el estado original del documento.

8. Readjust `firstRange` para incluir la marca de párrafo mediante el método para la posición de un <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> carácter.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet34":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet34":::

9. Elimine `secondRange`. De esta forma se restablece la posición original del tercer párrafo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet35":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet35":::

10. Restaure el texto del párrafo original en `firstRange`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet36":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet36":::

11. Use el método <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range> para insertar el contenido del segundo párrafo original después de `firstRange`y, a continuación, seleccione `firstRange`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet37":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet37":::

## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento

### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Controlar la estructura de un párrafo cuando se inserta texto en las personalizaciones de nivel de documento

1. En el siguiente ejemplo se muestra el método completo de una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet26":::

## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO

### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>Para controlar la estructura de párrafos al insertar texto en un complemento de VSTO

1. En el ejemplo siguiente se muestra el método completo para un complemento de VSTO. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet26":::

## <a name="see-also"></a>Consulte también
- [Cómo: Ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Cómo: Contraer rangos o selecciones en documentos mediante programación](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Cómo: Insertar texto mediante programación en documentos de Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Cómo: Restablecer rangos en documentos de Word mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
