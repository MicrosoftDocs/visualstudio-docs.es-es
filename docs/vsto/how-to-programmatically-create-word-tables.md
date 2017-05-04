---
title: "C&#243;mo: Crear tablas de Word mediante programaci&#243;n | Microsoft Docs"
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
  - "documentos [desarrollo de Office en Visual Studio], agregar tablas"
  - "tablas [desarrollo de Office en Visual Studio], agregar a documentos"
ms.assetid: fe1f9143-9622-45e8-b0a5-511336d99ad1
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# C&#243;mo: Crear tablas de Word mediante programaci&#243;n
  La colección <xref:Microsoft.Office.Interop.Word.Tables> es un miembro de las clases <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection> y <xref:Microsoft.Office.Interop.Word.Range>, lo que significa que puede crear una tabla en cualquiera de estos contextos.  Use el método <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> de la colección <xref:Microsoft.Office.Interop.Word.Tables> para agregar una tabla al intervalo especificado.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Crear tablas en personalizaciones de nivel de documento  
  
#### Para agregar una tabla sencilla a un documento  
  
-   Use el método <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> para agregar una tabla que conste de tres filas y cuatro columnas al principio del documento.  
  
     Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomation#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#86)]  
  
 Al crear una tabla, se agrega automáticamente a la colección <xref:Microsoft.Office.Interop.Word.Tables> del elemento host <xref:Microsoft.Office.Tools.Word.Document>.  Después, puede hacer referencia a la tabla por su número de elemento usando la propiedad <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, como se muestra en el código siguiente.  
  
#### Para hacer referencia a una tabla por su número de elemento  
  
1.  Use la propiedad <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> y proporcione el número de elemento de la tabla a la que desee hacer referencia.  
  
     Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomation#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#87)]  
  
 Cada objeto <xref:Microsoft.Office.Interop.Word.Table> tiene también una propiedad <xref:Microsoft.Office.Interop.Word.Table.Range%2A> que le permite establecer atributos de formato.  
  
#### Para aplicar un estilo a una tabla  
  
1.  Use la propiedad <xref:Microsoft.Office.Interop.Word.Table.Style%2A> para aplicar a una tabla uno de los estilos integrados en Word.  
  
     Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomation#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#88)]  
  
## Crear tablas en complementos de VSTO  
  
#### Para agregar una tabla sencilla a un documento  
  
-   Use el método <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> para agregar una tabla que conste de tres filas y cuatro columnas al principio del documento.  
  
     En el siguiente ejemplo de código se agrega una tabla al documento activo.  Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#86)]  
  
 Al crear una tabla, se agrega automáticamente a la colección <xref:Microsoft.Office.Interop.Word.Tables> del <xref:Microsoft.Office.Interop.Word.Document>.  Después, puede hacer referencia a la tabla por su número de elemento usando la propiedad <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, como se muestra en el código siguiente.  
  
#### Para hacer referencia a una tabla por su número de elemento  
  
1.  Use la propiedad <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> y proporcione el número de elemento de la tabla a la que desee hacer referencia.  
  
     En el siguiente ejemplo de código se usa el documento activo.  Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#87)]  
  
 Cada objeto <xref:Microsoft.Office.Interop.Word.Table> tiene también una propiedad <xref:Microsoft.Office.Interop.Word.Table.Range%2A> que le permite establecer atributos de formato.  
  
#### Para aplicar un estilo a una tabla  
  
1.  Use la propiedad <xref:Microsoft.Office.Interop.Word.Table.Style%2A> para aplicar a una tabla uno de los estilos integrados en Word.  
  
     En el siguiente ejemplo de código se usa el documento activo.  Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#88)]  
  
## Vea también  
 [Cómo: Agregar texto y formato a celdas de tablas de Word mediante programación](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Cómo: Agregar filas y columnas a tablas de Word mediante programación](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Cómo: Rellenar tablas de Word con propiedades de documento mediante programación](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  