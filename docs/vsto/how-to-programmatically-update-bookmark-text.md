---
title: "C&#243;mo: Actualizar texto de marcador mediante programaci&#243;n"
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
  - "Bookmark (control), actualizar contenido"
  - "marcadores, actualizar texto"
  - "texto [desarrollo de Office en Visual Studio], actualizar en marcadores"
ms.assetid: 2324164d-2538-4695-9aaf-7285ce403be3
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# C&#243;mo: Actualizar texto de marcador mediante programaci&#243;n
  Puede insertar texto en un marcador de marcador de posición de un documento de Microsoft Office Word para poder recuperar el texto posteriormente o reemplazar el texto de un marcador.  Si está desarrollando una personalización de nivel de documento, también puede actualizar el texto de un control <xref:Microsoft.Office.Tools.Word.Bookmark> que está enlazado a datos.  Para obtener más información, consulte [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 El objeto de marcador puede ser de uno de los dos tipos indicados a continuación:  
  
-   Un control host <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Los controles <xref:Microsoft.Office.Tools.Word.Bookmark> amplían los objetos nativos <xref:Microsoft.Office.Interop.Word.Bookmark> habilitando el enlace de datos y exponiendo los eventos.  Para obtener más información acerca de los controles host, vea [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
-   Un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo.  
  
     Los objetos <xref:Microsoft.Office.Interop.Word.Bookmark> no tienen capacidades de enlace de datos o eventos.  
  
 Cuando se asigna texto a un marcador, el comportamiento entre un <xref:Microsoft.Office.Interop.Word.Bookmark> y un <xref:Microsoft.Office.Tools.Word.Bookmark> es diferente.  Para obtener más información, vea [Bookmark &#40;Control&#41;](../vsto/bookmark-control.md).  
  
## Usar controles host  
  
#### Para actualizar el contenido del marcador usando un control Bookmark  
  
1.  Cree un procedimiento que tome un argumento `bookmark` para el nombre del marcador y un argumento `newText` para la cadena que se va a asignar a la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>.  
  
    > [!NOTE]  
    >  Asignar texto a la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> o <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> de un control <xref:Microsoft.Office.Tools.Word.Bookmark> no hace que se elimine el marcador.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#63)]
     [!code-vb[Trin_VstcoreWordAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#63)]  
  
2.  Asigne la cadena *newText* a la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> del <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#64)]
     [!code-vb[Trin_VstcoreWordAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#64)]  
  
## Usar objetos de Word  
  
#### Para actualizar el contenido del marcador usando un objeto Bookmark de Word  
  
1.  Cree un procedimiento que tenga un argumento `bookmark` para el nombre del <xref:Microsoft.Office.Interop.Word.Bookmark> y un argumento `newText` para la cadena que se va a asignar a la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> del marcador.  
  
    > [!NOTE]  
    >  Si se asigna texto a un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo de Word, se elimina el marcador.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#65](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#65)]
     [!code-vb[Trin_VstcoreWordAutomation#65](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#65)]  
  
2.  Asigne la cadena *newText* a la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> del marcador, lo cual elimina automáticamente el marcador.  A continuación, vuelva a agregar el marcador a la colección <xref:Microsoft.Office.Interop.Word.Bookmarks>.  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomation#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#66)]  
  
     El siguiente ejemplo de código se puede usar en un complemento de VSTO.  En este ejemplo se usa el documento activo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#66)]  
  
## Vea también  
 [Cómo: Insertar texto en documentos de Word mediante programación](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Bookmark &#40;Control&#41;](../vsto/bookmark-control.md)  
  
  