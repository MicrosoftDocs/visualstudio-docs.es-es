---
title: "C&#243;mo: Proteger documentos y partes de documentos mediante programaci&#243;n | Microsoft Docs"
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
  - "protección de documentos"
  - "documentos [desarrollo de Office en Visual Studio], protección de documentos"
  - "documentos de Word, protección"
ms.assetid: af8390fc-c4c7-48c7-94b8-4fedbaac0757
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# C&#243;mo: Proteger documentos y partes de documentos mediante programaci&#243;n
  Puede agregar protección a documentos de Microsoft Office Word para impedir que los usuarios realicen cualquier modificación en el documento.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 También puede marcar determinadas áreas del documento como excepciones para que los usuarios especificados pueden modificar solo dichas áreas del documento. Por ejemplo, puede que desee proteger todo el documento excepto un marcador determinado. Opcionalmente, puede agregar una contraseña para que los usuarios no puedan quitar la protección del documento, a menos que conozcan la contraseña.  
  
> [!NOTE]  
>  El ejemplo siguiente no utiliza protección con contraseña; sin embargo, es recomendable considerar el uso de una contraseña al agregar protección al documento. Para obtener más información, vea el ejemplo de Document Protector en [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 También puede usar los controles de contenido para proteger elementos de documentos. Para obtener más información, consulta [Cómo: Proteger elementos de documentos mediante controles de contenido](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## Proteger un documento que forma parte de una personalización de nivel de documento  
  
#### Para proteger un documento que forma parte de una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> de la clase `ThisDocument` en su proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
#### Para excluir un control de marcador de la protección de documento  
  
1.  Proteja todo el documento mediante el método <xref:Microsoft.Office.Tools.Word.Document.Protect%2A>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
2.  Excluya `Bookmark1` de la protección del documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#112](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#112)]
     [!code-vb[Trin_VstcoreWordAutomation#112](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#112)]  
  
### Compilar el código  
 Para usar estos ejemplos de código, ejecútelos desde la clase `ThisDocument` del proyecto. Estos ejemplos de código suponen que dispone de un control <xref:Microsoft.Office.Tools.Word.Bookmark> existente denominado `Bookmark1` en el documento en el que aparece este código.  
  
## Proteger un documento mediante un complemento de VSTO  
  
#### Para proteger un documento mediante un complemento de VSTO de nivel de aplicación  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> del <xref:Microsoft.Office.Interop.Word.Document> que quiere proteger.  
  
     El siguiente ejemplo de código protege el documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#111)]  
  
## Vea también  
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)   
 [Cómo: Permitir que el código se ejecute en documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Cómo: Agregar controles Bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  