---
title: "C&#243;mo: Cerrar documentos mediante programaci&#243;n | Microsoft Docs"
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
  - "documentos [desarrollo de Office en Visual Studio], cerrar"
  - "Word [desarrollo de Office en Visual Studio], cerrar documentos"
ms.assetid: d5bee1dc-63d1-4307-828f-b7b077e20fb9
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# C&#243;mo: Cerrar documentos mediante programaci&#243;n
  Puede cerrar el documento activo o especificar el documento que se va a cerrar.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Cerrar el documento activo  
 Hay dos procedimientos para cerrar el documento activo: uno para las personalizaciones de nivel de documento y uno para los complementos de VSTO.  
  
#### Para cerrar el documento activo en una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Word.Document.Close%2A> de la clase `ThisDocument` del proyecto para cerrar el documento asociado a la personalización. Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument`.  
  
    > [!NOTE]  
    >  Este ejemplo pasa el valor <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parámetro *SaveChanges* para cerrar sin guardar los cambios ni preguntar al usuario.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomation#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#3)]  
  
#### Para cerrar el documento activo en un complemento de VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Word._Document.Close%2A> de la propiedad <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> para cerrar el documento activo. Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
    > [!NOTE]  
    >  Este ejemplo pasa el valor <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parámetro *SaveChanges* para cerrar sin guardar los cambios ni preguntar al usuario.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Cerrar un documento que se especifica por el nombre  
 La manera en que se cierra un documento que se especifica por nombre es el mismo para las personalizaciones de nivel de documento y las de complemento de VSTO.  
  
#### Para cerrar un documento que se especifica por el nombre  
  
1.  Especifique el nombre del documento como argumento para la colección <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> y, después, llame al método <xref:Microsoft.Office.Interop.Word._Document.Close%2A>. En el siguiente ejemplo de código, se supone que un documento llamado **NewDocument** está abierto en Word.  
  
    > [!NOTE]  
    >  Este ejemplo pasa el valor <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parámetro *SaveChanges* para cerrar sin guardar los cambios ni preguntar al usuario.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreWordAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#4)]  
  
## Vea también  
 [Cómo: Abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Cómo: Guardar documentos mediante programación](../vsto/how-to-programmatically-save-documents.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  