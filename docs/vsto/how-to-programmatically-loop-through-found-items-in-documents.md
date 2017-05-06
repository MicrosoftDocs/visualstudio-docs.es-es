---
title: "C&#243;mo: Recorrer los elementos encontrados en documentos mediante programaci&#243;n"
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
  - "bucles, a través de los elementos encontrados en documentos"
  - "documentos [desarrollo de Office en Visual Studio], buscar"
  - "texto [desarrollo de Office en Visual Studio], buscar en documentos"
ms.assetid: 68dc41b1-eb96-4697-ac93-1a88c862ebad
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# C&#243;mo: Recorrer los elementos encontrados en documentos mediante programaci&#243;n
  La clase <xref:Microsoft.Office.Interop.Word.Find> tiene una propiedad <xref:Microsoft.Office.Interop.Word.Find.Found%2A> que devuelve el valor **true** cada vez que se encuentra el elemento buscado. Puede recorrer todas las instancias que se encuentran en un objeto <xref:Microsoft.Office.Interop.Word.Range> mediante el método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Para recorrer los elementos encontrados  
  
1.  Declare un objeto <xref:Microsoft.Office.Interop.Word.Range>.  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#79)]
     [!code-vb[Trin_VstcoreWordAutomation#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#79)]  
  
     El siguiente ejemplo de código se puede usar en un complemento VSTO. En este ejemplo se usa el documento activo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#79)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#79)]  
  
2.  Use la propiedad <xref:Microsoft.Office.Interop.Word.Find.Found%2A> en un bucle para buscar todas las repeticiones de la cadena en el documento, e incremente en 1 una variable entera cada vez que se encuentre esa cadena.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#80](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#80)]
     [!code-vb[Trin_VstcoreWordAutomation#80](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#80)]  
  
3.  Muestre el número de veces que se encontró la cadena en un cuadro de mensaje.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#81](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#81)]
     [!code-vb[Trin_VstcoreWordAutomation#81](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#81)]  
  
 En el siguiente ejemplo se muestra el método completo.  
  
## Ejemplo de personalización de nivel de documento  
  
#### Recorrer los elementos en una personalización de nivel de documento  
  
1.  En el siguiente ejemplo se muestra el código completo de una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#78)]
     [!code-vb[Trin_VstcoreWordAutomation#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#78)]  
  
## Ejemplo para complemento de VSTO  
  
#### Recorrer los elementos en un complemento VSTO  
  
1.  En el siguiente ejemplo se muestra el código completo de un complemento de VSTO. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#78)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#78)]  
  
## Vea también  
 [Cómo: Buscar y reemplazar texto en documentos mediante programación](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Cómo: Establecer opciones de búsqueda en Word mediante programación](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Cómo: Definir y seleccionar intervalos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Cómo: Restaurar selecciones después de realizar búsquedas mediante programación](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  