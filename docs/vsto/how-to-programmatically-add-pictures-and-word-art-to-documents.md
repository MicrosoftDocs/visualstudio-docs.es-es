---
title: "C&#243;mo: Agregar im&#225;genes y dibujos de Word a documentos mediante programaci&#243;n"
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
  - "documentos [desarrollo de Office en Visual Studio], agregar imágenes"
  - "gráficos, agregar a los documentos de Word"
  - "documentos de Word, agregar imágenes"
  - "documentos de Word, agregar dibujos de Word"
  - "dibujos de Word, agregar a documentos"
ms.assetid: 944e1858-bc7c-471f-b5e7-adf3b0fa574d
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# C&#243;mo: Agregar im&#225;genes y dibujos de Word a documentos mediante programaci&#243;n
  Puede agregar imágenes y objetos de dibujo a los documentos en tiempo de diseño o en tiempo de ejecución.  WordArt permite agregar texto decorativo a documentos de Microsoft Office Word.  Estos efectos de texto especiales son objetos de dibujo que se pueden personalizar e insertar en el documento.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Agregar una imagen en tiempo de diseño  
 Si está desarrollando una personalización de nivel de documento, puede agregar una imagen al documento en tiempo de diseño.  
  
#### Para agregar una imagen a un documento de Word en tiempo de diseño  
  
1.  Coloque el cursor donde desea insertar la imagen en el documento.  
  
2.  En la cinta de opciones, haga clic en la pestaña **Insertar**.  
  
3.  En el grupo **Ilustraciones**, haga clic en **Imagen**.  
  
4.  En el cuadro de diálogo **Insertar imagen**, navegue a la imagen que desea insertar y haga clic en **Insertar**.  
  
     La imagen se agrega al documento en la ubicación actual del cursor.  
  
## Agregar una imagen en tiempo de ejecución  
 Puede insertar una imagen en un documento en la ubicación actual del cursor.  
  
#### Para agregar una imagen en la ubicación del cursor  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> de la colección <xref:Microsoft.Office.Interop.Word.InlineShapes> y pase el nombre del archivo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#108](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#108)]
     [!code-vb[Trin_VstcoreWordAutomation#108](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#108)]  
  
## Agregar WordArt en tiempo de diseño  
 Si está desarrollando una personalización de nivel de documento, puede agregar WordArt al documento en tiempo de diseño.  
  
#### Para agregar WordArt a un documento de Word en tiempo de diseño  
  
1.  Coloque el cursor donde desea insertar el elemento de WordArt en el documento.  
  
2.  En la cinta de opciones, haga clic en la pestaña **Insertar**.  
  
3.  En el grupo **Texto**, haga clic en **WordArt** y seleccione un estilo de WordArt.  
  
4.  Agregue el texto que desea que aparezca en el documento en el cuadro de diálogo **Editar texto de WordArt** y haga clic en **Aceptar**.  
  
     El texto se agrega al documento con el estilo de WordArt que seleccionó aplicado.  
  
## Agregar WordArt en tiempo de ejecución  
 Puede insertar WordArt en un documento en la ubicación actual del cursor.  El procedimiento es diferente para las personalizaciones de nivel de documento y los complementos de VSTO.  
  
#### Para agregar WordArt en la ubicación del cursor en una personalización de nivel de documento  
  
1.  Obtenga la posición izquierda y superior de la ubicación actual del cursor.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomation#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#109)]  
  
2.  Llame al método <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> del objeto <xref:Microsoft.Office.Interop.Word.Shapes> en el documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomation#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#110)]  
  
#### Para agregar WordArt en la ubicación del cursor en un complemento de VSTO  
  
1.  Obtenga la posición izquierda y superior de la ubicación actual del cursor.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#109)]  
  
2.  Llame al método <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> del objeto <xref:Microsoft.Office.Interop.Word.Shapes> del documento activo \(u otro documento que especifique\).  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#110)]  
  
## Compilar el código  
  
-   Debe existir en la unidad C una imagen llamada **SamplePicture.jpg**.  
  
## Vea también  
 [Cómo: Abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Cómo: Insertar texto en documentos de Word mediante programación](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Cómo: Restaurar selecciones después de realizar búsquedas mediante programación](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Cómo: Guardar documentos mediante programación](../vsto/how-to-programmatically-save-documents.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  