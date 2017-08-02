---
title: "C&#243;mo: Crear y modificar propiedades personalizadas para documentos"
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
  - "propiedades de documento personalizadas"
  - "documentos [desarrollo de Office en Visual Studio], propiedades"
  - "propiedades del documento [desarrollo de Office en Visual Studio]"
ms.assetid: 99d9dfaf-891f-4f3b-a580-67362afdaf34
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# C&#243;mo: Crear y modificar propiedades personalizadas para documentos
  Las aplicaciones de Microsoft Office enumeradas anteriormente proporcionan propiedades integradas que se almacenan con los documentos. Además, puede crear y modificar propiedades de documento personalizadas si hay información adicional que desea almacenar con el documento.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Use la propiedad CustomDocumentProperties de un documento para trabajar con propiedades personalizadas. Por ejemplo, en un proyecto de nivel de documento para Microsoft Office Excel, use la propiedad <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> de la clase `ThisWorkbook`. En un proyecto de complemento de VSTO para Excel, use la propiedad <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> de un objeto <xref:Microsoft.Office.Interop.Excel.Workbook>. Estas propiedades devuelven un objeto <xref:Microsoft.Office.Core.DocumentProperties>, que es una colección de objetos <xref:Microsoft.Office.Core.DocumentProperty>. Puede usar la propiedad `Item` de la colección para recuperar una propiedad determinada, ya sea por nombre o por índice dentro de la colección.  
  
 En el ejemplo siguiente se muestra cómo agregar una propiedad personalizada en una personalización de nivel de documento para Excel y asignarle un valor.  
  
 ![vínculo a vídeo](~/docs/data-tools/media/playvideo.gif "vínculo a vídeo") Para ver una demostración en vídeo relacionada, consulte [Cómo obtener acceso a las propiedades personalizadas de un documento y manipularlas en Microsoft Word](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## Ejemplo  
 [!code-csharp[Trin_VstcoreProgramming#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#6)]
 [!code-vb[Trin_VstcoreProgramming#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#6)]  
  
## Programación eficaz  
 Si se intenta acceder a la propiedad `Value` para propiedades sin definir, se produce una excepción.  
  
## Vea también  
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Cómo: Leer y escribir en propiedades de un documento](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  