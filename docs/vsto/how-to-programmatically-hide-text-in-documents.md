---
title: 'Cómo: Ocultar texto en documentos mediante programación'
description: Obtenga información sobre cómo ocultar texto en un documento de Microsoft Word estableciendo la propiedad Hidden de la fuente para un intervalo de texto determinado.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 04ea6b56519656782a3e408892235fa177eef755
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826491"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Cómo: Ocultar texto en documentos mediante programación
  Puede ocultar texto en un documento si establece la propiedad <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> de <xref:Microsoft.Office.Interop.Word.Range.Font%2A> para un determinado rango de texto.

 Por ejemplo, puede ocultar temporalmente el texto dentro de (en una personalización de nivel de documento) o (en un complemento de VSTO) antes de enviar un documento <xref:Microsoft.Office.Tools.Word.Bookmark> <xref:Microsoft.Office.Interop.Word.Bookmark> a una impresora.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Para ocultar el texto de un control Bookmark al imprimir el documento

1. Cree un procedimiento que oculte todo el texto del rango especificado.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet105":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet105":::

2. Cree un procedimiento que muestre todo el texto del rango especificado.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet106":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet106":::

3. Pase el rango de un marcador al método `HideText` , imprima el documento y luego pase el mismo rango al método `UnhideText` .

     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento. Para usar este ejemplo, ejecútelo desde la clase `ThisDocument` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet107":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet107":::

     El siguiente ejemplo de código se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo. Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet107":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet107":::

## <a name="compile-the-code"></a>Compilar el código
 En este ejemplo de código se supone que el documento contiene un control (en una personalización de nivel de documento) o un control (en un complemento <xref:Microsoft.Office.Tools.Word.Bookmark> <xref:Microsoft.Office.Interop.Word.Bookmark> de VSTO) denominado `bookmark1` .

## <a name="see-also"></a>Consulte también
- [Cómo: Imprimir documentos mediante programación](../vsto/how-to-programmatically-print-documents.md)
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: Restablecer rangos en documentos de Word mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Cómo: Actualizar texto de marcador mediante programación](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
