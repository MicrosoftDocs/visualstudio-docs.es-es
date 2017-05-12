---
title: "C&#243;mo: Leer y escribir en propiedades de un documento"
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
  - "Word [desarrollo de Office en Visual Studio], propiedades del documento"
  - "documentos [desarrollo de Office en Visual Studio], propiedades"
  - "propiedades del documento [desarrollo de Office en Visual Studio]"
  - "Excel [desarrollo de Office en Visual Studio], propiedades del documento"
ms.assetid: e9ef9fa3-36b9-48fb-8148-f5152463c03c
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# C&#243;mo: Leer y escribir en propiedades de un documento
  Puede almacenar propiedades de documento junto con un documento. Las aplicaciones de Office proporcionan una serie de propiedades integradas, como author, title y subject. En este tema se muestra cómo establecer las propiedades de documento en Microsoft Office Excel y Microsoft Office Word.  
  
 ![vínculo a vídeo](../vsto/media/playvideo.png "vínculo a vídeo") Para ver una demostración en vídeo relacionada, consulte [Cómo obtener acceso a las propiedades personalizadas de un documento y manipularlas en Microsoft Word](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## Establecer las propiedades de un documento en Excel  
 Para trabajar con las propiedades integradas de Excel, use las siguientes propiedades:  
  
-   En un proyecto de nivel de documento, use la propiedad <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> de la clase `ThisWorkbook`.  
  
-   En un proyecto de complemento de VSTO, use la propiedad <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> de un objeto <xref:Microsoft.Office.Interop.Excel.Workbook>.  
  
 Estas propiedades devuelven un objeto <xref:Microsoft.Office.Core.DocumentProperties>, que es una colección de objetos <xref:Microsoft.Office.Core.DocumentProperty>. Puede usar la propiedad `Item` de la colección para recuperar una propiedad determinada, ya sea por nombre o por índice dentro de la colección.  
  
 En el siguiente ejemplo de código se muestra cómo cambiar la propiedad integrada **Revision Number** en un proyecto de nivel de documento.  
  
#### Para cambiar la propiedad Revision Number en Excel  
  
1.  Asigne las propiedades integradas del documento a una variable.  
  
     [!code-csharp[Trin_VstcoreProgramming#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#7)]
     [!code-vb[Trin_VstcoreProgramming#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#7)]  
  
2.  Incremente la propiedad `Revision Number` en uno.  
  
     [!code-csharp[Trin_VstcoreProgramming#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#8)]
     [!code-vb[Trin_VstcoreProgramming#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#8)]  
  
## Establecer las propiedades de un documento en Word  
 Para trabajar con las propiedades integradas de Word, use las siguientes propiedades:  
  
-   En un proyecto de nivel de documento, use la propiedad <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> de la clase `ThisDocument`.  
  
-   En un proyecto de complemento de VSTO, use la propiedad <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Document>.  
  
 Estas propiedades devuelven un objeto <xref:Microsoft.Office.Core.DocumentProperties>, que es una colección de objetos <xref:Microsoft.Office.Core.DocumentProperty>. Puede usar la propiedad `Item` de la colección para recuperar una propiedad determinada, ya sea por nombre o por índice dentro de la colección.  
  
 En el siguiente ejemplo de código se muestra cómo cambiar la propiedad integrada **Subject** en un proyecto de nivel de documento.  
  
#### Para cambiar la propiedad Subject  
  
1.  Asigne las propiedades integradas del documento a una variable.  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#1)]  
  
2.  Cambie la propiedad `Subject` a «Whitepaper».  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#2)]  
  
## Programación eficaz  
 En los ejemplos se supone que ha escrito el código de la clase `ThisWorkbook` en un proyecto de nivel de documento para Excel y la clase `ThisDocument` en un proyecto de nivel de documento para Word.  
  
 Aunque trabaje con Word y Excel y sus objetos, Microsoft Office proporciona una lista de propiedades de documento integradas. Si se intenta tener acceso a una propiedad sin definir, se produce una excepción.  
  
## Vea también  
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Cómo: Crear y modificar propiedades personalizadas para documentos](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  