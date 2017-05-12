---
title: "C&#243;mo: Definir y seleccionar intervalos en documentos mediante programaci&#243;n"
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
  - "documentos [desarrollo de Office en Visual Studio], intervalos"
  - "documentos [desarrollo de Office en Visual Studio], seleccionar frases"
  - "intervalos, definir en documentos"
  - "intervalos, seleccionar en documentos"
  - "frases, seleccionar en documentos"
ms.assetid: 0727c1cb-d44c-4f1c-a699-4365dd13be5d
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# C&#243;mo: Definir y seleccionar intervalos en documentos mediante programaci&#243;n
  Puede definir un intervalo en un documento de Microsoft Office Word mediante un objeto <xref:Microsoft.Office.Interop.Word.Range>.  Puede seleccionar todo el documento de varias maneras, por ejemplo, mediante el método <xref:Microsoft.Office.Interop.Word.Range.Select%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range> o usando la propiedad Content de la clase <xref:Microsoft.Office.Tools.Word.Document> \(en una personalización de nivel de documento\) o la clase <xref:Microsoft.Office.Interop.Word.Document> \(en un complemento de VSTO\).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Definir un intervalo  
 En el siguiente ejemplo se muestra cómo crear un nuevo objeto <xref:Microsoft.Office.Interop.Word.Range> que incluya los siete primeros caracteres del documento activo, incluidos los caracteres no imprimibles.  A continuación, selecciona el texto dentro del intervalo.  
  
#### Para definir un intervalo en una personalización de nivel de documento  
  
1.  Agregue el intervalo al documento pasando un carácter inicial y final al método <xref:Microsoft.Office.Tools.Word.Document.Range%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document>.  Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomation#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#18)]  
  
#### Para definir un intervalo mediante un complemento de VSTO  
  
1.  Agregue el intervalo al documento pasando un carácter inicial y final al método <xref:Microsoft.Office.Interop.Word._Document.Range%2A> de la clase <xref:Microsoft.Office.Interop.Word.Document>.  En el siguiente ejemplo de código se agrega un intervalo al documento activo.  Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#18)]  
  
## Seleccionar un intervalo en una personalización de nivel de documento  
 Los siguientes ejemplos muestran cómo seleccionar todo el documento mediante el método <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Range> o usando la propiedad <xref:Microsoft.Office.Tools.Word.Document.Content%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document>.  
  
#### Para seleccionar todo el documento como un intervalo mediante el método Select  
  
1.  Use el método <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de un <xref:Microsoft.Office.Interop.Word.Range> que contenga todo el documento.  Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomation#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#19)]  
  
#### Para seleccionar todo el documento como un intervalo mediante la propiedad Content  
  
1.  Use la propiedad <xref:Microsoft.Office.Tools.Word.Document.Content%2A> para definir un intervalo que abarque todo el documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomation#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#20)]  
  
 También puede usar los métodos y propiedades de otros objetos para definir un intervalo.  
  
#### Para seleccionar una frase en el documento activo  
  
1.  Establezca el intervalo usando la colección <xref:Microsoft.Office.Interop.Word.Sentences>.  Use el índice de la frase que desea seleccionar.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomation#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#21)]  
  
 Otra forma de seleccionar una frase es establecer manualmente los valores inicial y final del intervalo.  
  
#### Para seleccionar una frase estableciendo manualmente los valores inicial y final  
  
1.  Cree una variable de intervalo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomation#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#23)]  
  
2.  Compruebe si hay al menos dos frases en el documento, establezca los argumentos *Start* y *End* del intervalo y, a continuación, seleccione el intervalo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomation#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#24)]  
  
## Seleccionar un intervalo mediante un complemento de VSTO  
 Los siguientes ejemplos muestran cómo seleccionar todo el documento mediante el método <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Range> o usando la propiedad <xref:Microsoft.Office.Interop.Word._Document.Content%2A> de la clase <xref:Microsoft.Office.Interop.Word.Document>.  
  
#### Para seleccionar todo el documento como un intervalo mediante el método Select  
  
1.  Use el método <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de un <xref:Microsoft.Office.Interop.Word.Range> que contenga todo el documento.  En el siguiente ejemplo de código se selecciona el contenido del documento activo.  Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
#### Para seleccionar todo el documento como un intervalo mediante la propiedad Content  
  
1.  Use la propiedad <xref:Microsoft.Office.Interop.Word._Document.Content%2A> para definir un intervalo que abarque todo el documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
 También puede usar los métodos y propiedades de otros objetos para definir un intervalo.  
  
#### Para seleccionar una frase en el documento activo  
  
1.  Establezca el intervalo usando la colección <xref:Microsoft.Office.Interop.Word.Sentences>.  Use el índice de la frase que desea seleccionar.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#21)]  
  
 Otra forma de seleccionar una frase es establecer manualmente los valores inicial y final del intervalo.  
  
#### Para seleccionar una frase estableciendo manualmente los valores inicial y final  
  
1.  Cree una variable de intervalo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
2.  Compruebe si hay al menos dos frases en el documento, establezca los argumentos *Start* y *End* del intervalo y, a continuación, seleccione el intervalo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## Vea también  
 [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Cómo: ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Cómo: Recuperar los caracteres inicial y final de los intervalos mediante programación](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Cómo: ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Cómo: Restablecer intervalos en documentos de Word mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Cómo: Contraer intervalos o selecciones en documentos mediante programación](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Cómo: Excluir marcas de párrafo al crear intervalos mediante programación](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  