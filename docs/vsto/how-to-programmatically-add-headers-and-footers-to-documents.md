---
title: "C&#243;mo: Agregar encabezados y pies de p&#225;gina a documentos mediante programaci&#243;n"
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
  - "documentos [desarrollo de Office en Visual Studio], agregar pies de página"
  - "documentos [desarrollo de Office en Visual Studio], agregar encabezados"
  - "pies de página, agregar a documentos"
  - "encabezados, agregar a documentos de Office"
ms.assetid: c7a5cc8a-d8c0-48e9-81d3-108aa6bfbb74
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# C&#243;mo: Agregar encabezados y pies de p&#225;gina a documentos mediante programaci&#243;n
  Puede agregar texto a los encabezados y pies de página del documento mediante las propiedades <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> y <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> de la <xref:Microsoft.Office.Interop.Word.Section>.  Cada sección de un documento contiene tres encabezados y pies de página:  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
 Los procedimientos son diferentes para las personalizaciones de nivel de documento y los complementos de VSTO.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Personalizaciones de nivel de documento  
 Para usar los siguientes ejemplos de código, ejecútelos desde la clase `ThisDocument` del proyecto.  
  
#### Para agregar texto a los pies de página en el documento  
  
1.  En el siguiente ejemplo de código se establece la fuente del texto que se va a insertar en el pie de página principal de cada sección del documento y, después, se inserta un texto en el pie de página.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#114](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#114)]
     [!code-vb[Trin_VstcoreWordAutomation#114](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#114)]  
  
#### Para agregar texto a los encabezados del documento  
  
1.  En el siguiente ejemplo de código se agrega un campo para mostrar el número de página en cada encabezado del documento y, después, se establece la alineación del párrafo para que el texto se alinee a la derecha del encabezado.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#116](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#116)]
     [!code-vb[Trin_VstcoreWordAutomation#116](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#116)]  
  
## Complementos de VSTO  
 Para usar los siguientes ejemplos de código, ejecútelos desde la clase `ThisAddIn` del proyecto.  
  
#### Para agregar texto a los pies de página de un documento  
  
1.  En el siguiente ejemplo de código se establece la fuente del texto que se va a insertar en el pie de página principal de cada sección del documento y, después, se inserta un texto en el pie de página.  Este ejemplo de código usa el documento activo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#114)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#114)]  
  
#### Para agregar texto a los encabezados del documento  
  
1.  En el siguiente ejemplo de código se agrega un campo para mostrar el número de página en cada encabezado del documento y, después, se establece la alineación del párrafo para que el texto se alinee a la derecha del encabezado.  Este ejemplo de código usa el documento activo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#116)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#116)]  
  
## Vea también  
 [Cómo: Crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md)   
 [Cómo: ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Cómo: Recorrer los elementos encontrados en documentos mediante programación](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
  
  