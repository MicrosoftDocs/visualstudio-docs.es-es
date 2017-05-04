---
title: "C&#243;mo: Insertar texto en documentos de Word mediante programaci&#243;n | Microsoft Docs"
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
  - "rangos, insertar texto en documentos"
  - "texto [desarrollo de Office en Visual Studio], insertar en documentos"
  - "rangos, reemplazar texto en documentos"
  - "documentos [desarrollo de Office en Visual Studio], insertar texto"
  - "texto [desarrollo de Office en Visual Studio], reemplazar"
ms.assetid: 405d7442-8ba3-4fcc-b17e-7b289ffd3967
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# C&#243;mo: Insertar texto en documentos de Word mediante programaci&#243;n
  Existen tres maneras principales de insertar texto en documentos de Microsoft Office Word:  
  
-   Insertar texto en un intervalo.  
  
-   Reemplazar texto en un intervalo con texto nuevo.  
  
-   Usar el método <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Selection> para insertar texto en el cursor o la selección.  
  
> [!NOTE]  
>  También puede insertar texto en controles de contenido y marcadores. Para obtener más información, consulte [Controles de contenido](../vsto/content-controls.md) y [Bookmark &#40;Control&#41;](../vsto/bookmark-control.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Insertar texto en un intervalo  
 Use la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Range> para insertar texto en un documento.  
  
#### Para insertar texto en un intervalo  
  
1.  Especifique un intervalo al principio de un documento e inserte el texto **New Text**.  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#51)]
     [!code-vb[Trin_VstcoreWordAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#51)]  
  
     El siguiente ejemplo de código se puede usar en un complemento de VSTO. Este código usa el documento activo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#51)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#51)]  
  
2.  Seleccione el objeto <xref:Microsoft.Office.Interop.Word.Range>, que se ha ampliado de un carácter a la longitud del texto insertado.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#52)]
     [!code-vb[Trin_VstcoreWordAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#52)]  
  
## Reemplazar texto en un intervalo  
 Si el intervalo especificado contiene texto, se reemplaza todo el texto en el intervalo por el texto insertado.  
  
#### Para reemplazar texto en un intervalo  
  
1.  Cree un objeto <xref:Microsoft.Office.Interop.Word.Range> que consista de los 12 primeros caracteres del documento.  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#53)]
     [!code-vb[Trin_VstcoreWordAutomation#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#53)]  
  
     El siguiente ejemplo de código se puede usar en un complemento de VSTO. Este código usa el documento activo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#53)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#53)]  
  
2.  Reemplace esos caracteres por la cadena **New Text**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#54](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#54)]
     [!code-vb[Trin_VstcoreWordAutomation#54](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#54)]  
  
3.  Seleccione el intervalo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#55](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#55)]
     [!code-vb[Trin_VstcoreWordAutomation#55](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#55)]  
  
## Insertar texto usando TypeText  
 El método <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> inserta texto en la selección.<xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> se comporta de forma distinta según las opciones establecidas en el equipo del usuario. El código en el siguiente procedimiento declara una variable de objeto <xref:Microsoft.Office.Interop.Word.Selection> y desactiva la opción **Overtype** si está activada. Si la opción **Overtype** está activada, se sobrescribe cualquier texto situado junto al cursor.  
  
#### Para insertar texto mediante el método TypeText  
  
1.  Declare una variable de objeto <xref:Microsoft.Office.Interop.Word.Selection>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#57)]
     [!code-vb[Trin_VstcoreWordAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#57)]  
  
2.  Desactive la opción **Overtype** si está activada.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#58)]
     [!code-vb[Trin_VstcoreWordAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#58)]  
  
3.  Compruebe si la selección actual es un punto de inserción.  
  
     Si lo es, el código inserta una frase usando <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> y, a continuación, una marca de párrafo usando el método <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#59)]
     [!code-vb[Trin_VstcoreWordAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#59)]  
  
4.  El código del bloque **ElseIf** comprueba si la selección es una selección normal. Si lo es, otro bloque **If** comprueba si la opción **ReplaceSelection** está activada. Si es así, el código usa el método <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> de la selección para contraer la selección hasta un punto de inserción al principio del bloque de texto seleccionado. Inserte el texto y una marca de párrafo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#60)]
     [!code-vb[Trin_VstcoreWordAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#60)]  
  
5.  Si la selección no es un punto de inserción o un bloque de texto seleccionado, el código del bloque **Else** no hace nada.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#61)]
     [!code-vb[Trin_VstcoreWordAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#61)]  
  
 También puede usar el método <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> del objeto <xref:Microsoft.Office.Interop.Word.Selection>, que imita la funcionalidad de la tecla Retroceso del teclado. Sin embargo, cuando se trata de insertar y manipular texto, el objeto <xref:Microsoft.Office.Interop.Word.Range> ofrece un mayor control.  
  
 El ejemplo siguiente muestra el código completo: Para usar este ejemplo, ejecute el código desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#56](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#56)]
 [!code-vb[Trin_VstcoreWordAutomation#56](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#56)]  
  
## Vea también  
 [Cómo: Dar formato al texto en documentos mediante programación](../vsto/how-to-programmatically-format-text-in-documents.md)   
 [Cómo: Definir y seleccionar intervalos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Cómo: ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)  
  
  