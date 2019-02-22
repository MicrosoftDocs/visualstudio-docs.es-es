---
title: Filtrar Agregar imágenes y dibujos de Word a documentos mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3e1d181c67628db52aa8e4f135109f1446a34816
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617917"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Filtrar Agregar imágenes y dibujos de Word a documentos mediante programación
  Puede agregar imágenes y objetos de dibujo a los documentos en tiempo de diseño o en tiempo de ejecución. WordArt permite agregar texto decorativo a documentos de Microsoft Office Word. Estos efectos de texto especiales son objetos de dibujo que se pueden personalizar e insertar en el documento.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Agregar una imagen en tiempo de diseño
 Si está desarrollando una personalización de nivel de documento, puede agregar una imagen al documento en tiempo de diseño.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Para agregar una imagen a un documento de Word en tiempo de diseño

1.  Coloque el cursor donde desea insertar la imagen en el documento.

2.  Haga clic en el **insertar** pestaña de la cinta de opciones.

3.  En el **ilustraciones** grupo, haga clic en **imagen**.

4.  En el **Insertar imagen** cuadro de diálogo, navegue a la imagen que desea insertar y haga clic en **insertar**.

     La imagen se agrega al documento en la ubicación actual del cursor.

## <a name="add-a-picture-at-runtime"></a>Agregar una imagen en tiempo de ejecución
 Puede insertar una imagen en un documento en la ubicación actual del cursor.

### <a name="to-add-a-picture-at-the-cursor-location"></a>Para agregar una imagen en la ubicación del cursor

1.  Llame al método <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> de la colección <xref:Microsoft.Office.Interop.Word.InlineShapes> y pase el nombre del archivo.

     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]

## <a name="add-wordart-at-design-time"></a>Agregar WordArt en tiempo de diseño
 Si está desarrollando una personalización de nivel de documento, puede agregar WordArt al documento en tiempo de diseño.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Para agregar WordArt a un documento de Word en tiempo de diseño

1.  Coloque el cursor donde desea insertar el elemento de WordArt en el documento.

2.  Haga clic en el **insertar** pestaña de la cinta de opciones.

3.  En el **texto** grupo, haga clic en **WordArt**y, a continuación, seleccione un estilo de WordArt.

4.  Agregue el texto que desea que aparezca en el documento hasta el **editar texto de WordArt** cuadro de diálogo y haga clic en **Aceptar**.

     El texto se agrega al documento con el estilo de WordArt que seleccionó aplicado.

## <a name="add-wordart-at-runtime"></a>Agregar WordArt en tiempo de ejecución
 Puede insertar WordArt en un documento en la ubicación actual del cursor. El procedimiento es diferente para las personalizaciones de nivel de documento y los complementos de VSTO.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Para agregar WordArt en la ubicación del cursor en una personalización de nivel de documento

1.  Obtenga la posición izquierda y superior de la ubicación actual del cursor.

     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]

2.  Llame al método <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> del objeto <xref:Microsoft.Office.Interop.Word.Shapes> en el documento.

     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Para agregar WordArt en la ubicación del cursor en un complemento de VSTO

1.  Obtenga la posición izquierda y superior de la ubicación actual del cursor.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]

2.  Llame al método <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> del objeto <xref:Microsoft.Office.Interop.Word.Shapes> del documento activo (u otro documento que especifique).

     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]

## <a name="compile-the-code"></a>Compilar el código

-   Una imagen denominada *SamplePicture.jpg* debe existir en la unidad C.

## <a name="see-also"></a>Vea también
- [Cómo: Abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)
- [Cómo: Insertar texto en documentos de Word mediante programación](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Cómo: Restaurar selecciones después de realizar búsquedas mediante programación](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Cómo: Guardar documentos mediante programación](../vsto/how-to-programmatically-save-documents.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
