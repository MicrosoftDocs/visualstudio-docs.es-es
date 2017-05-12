---
title: "C&#243;mo: Establecer opciones de b&#250;squeda en Word mediante programaci&#243;n"
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
  - "documentos [desarrollo de Office en Visual Studio], opciones de búsqueda"
  - "buscar, opciones en Word"
  - "configuración, opciones de búsqueda en Word"
  - "Word, opciones de búsqueda"
ms.assetid: 4412b4e8-2868-4afb-a593-983603ef9b02
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# C&#243;mo: Establecer opciones de b&#250;squeda en Word mediante programaci&#243;n
  Hay dos maneras de establecer opciones de búsqueda para las selecciones en documentos de Microsoft Office Word:  
  
-   Establecer propiedades individuales de un objeto <xref:Microsoft.Office.Interop.Word.Find>.  
  
-   Utilice argumentos del método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Find>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Utilizar propiedades de un objeto Find  
 Con el siguiente código se establecen propiedades del objeto <xref:Microsoft.Office.Interop.Word.Find> para buscar texto dentro de la selección actual.  Observe que los criterios de búsqueda, como buscar hacia delante, ajuste del texto y texto de la búsqueda son propiedades del objeto <xref:Microsoft.Office.Interop.Word.Find>.  
  
 No resulta útil establecer todas las propiedades del objeto <xref:Microsoft.Office.Interop.Word.Find> cuando se escribe código en C\#, ya que se deben especificar las mismas propiedades como parámetros en el método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>.  Por consiguiente, este ejemplo sólo contiene código de Visual Basic.  
  
#### Para establecer opciones de búsqueda con un objeto Find  
  
1.  Establezca las propiedades de un objeto <xref:Microsoft.Office.Interop.Word.Find> para buscar hacia delante el texto **find me** en una selección.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#76)]  
  
## Utilizar argumentos del método Execute  
 En el siguiente código se utiliza el método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> del objeto <xref:Microsoft.Office.Interop.Word.Find> para buscar texto dentro de la selección actual.  Observe que los criterios de búsqueda, como buscar hacia delante, ajuste del texto y texto de la búsqueda se pasan como parámetros del método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>.  
  
#### Para establecer opciones de búsqueda con argumentos del método Execute  
  
1.  Pase los criterios de búsqueda como parámetros del método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> para buscar hacia delante el texto **find me** en una selección.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#77](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#77)]
     [!code-vb[Trin_VstcoreWordAutomation#77](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#77)]  
  
## Vea también  
 [Cómo: Buscar y reemplazar texto en documentos mediante programación](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Cómo: Recorrer los elementos encontrados en documentos mediante programación](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Cómo: Restaurar selecciones después de realizar búsquedas mediante programación](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  