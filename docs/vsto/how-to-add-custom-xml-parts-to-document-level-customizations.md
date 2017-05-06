---
title: "C&#243;mo: Agregar elementos XML personalizados a personalizaciones de nivel de documento"
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
  - "personalizaciones de nivel de documento [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "documentos de Office [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "Word [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "Excel [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "elementos XML personalizados [desarrollo de Office en Visual Studio], agregar"
  - "documentos [desarrollo de Office en Visual Studio], elementos XML personalizados"
ms.assetid: e305a3d6-3a0e-4e72-ab8c-6a87a3590068
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# C&#243;mo: Agregar elementos XML personalizados a personalizaciones de nivel de documento
  Puede almacenar datos XML en un libro de Microsoft Office Excel o un documento de Microsoft Office Word creando un elemento XML personalizado en una personalización de nivel de documento. Para obtener más información, consulta [Información general sobre los elementos XML personalizados](../vsto/custom-xml-parts-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Visual Studio no ofrece proyectos de nivel de documento para Microsoft Office PowerPoint. Para obtener información sobre cómo agregar un elemento XML personalizado a una presentación de PowerPoint con un complemento de VSTO, consulte [Cómo: Agregar elementos XML personalizados a documentos mediante complementos de VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
### Para agregar un elemento XML personalizado a un libro de Excel  
  
1.  Agregue un nuevo objeto <xref:Microsoft.Office.Core.CustomXMLPart> a la colección <xref:Microsoft.Office.Core.CustomXMLParts> del libro.<xref:Microsoft.Office.Core.CustomXMLPart> contiene la cadena XML que desea almacenar en el libro.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelDocLevel/CS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelDocLevel/VB/ThisWorkbook.vb#1)]  
  
2.  Agregue el método `AddCustomXmlPartToWorkbook` a la clase `ThisWorkbook` en un proyecto de nivel de documento para Excel.  
  
3.  Llame al método desde otro código del proyecto. Por ejemplo, para crear el elemento XML personalizado cuando el usuario abre el libro, llame al método desde un controlador de eventos `ThisWorkbook_Startup`.  
  
### Para agregar un elemento XML personalizado a un documento de Word  
  
1.  Agregue un nuevo objeto <xref:Microsoft.Office.Core.CustomXMLPart> a la colección <xref:Microsoft.Office.Core.CustomXMLParts> del documento.<xref:Microsoft.Office.Core.CustomXMLPart> contiene la cadena XML que desea almacenar en el documento.  
  
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordDocLevel/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordDocLevel/VB/ThisDocument.vb#1)]  
  
2.  Agregue el método `AddCustomXmlPartToDocument` a la clase `ThisDocument` en un proyecto de nivel de documento para Word.  
  
3.  Llame al método desde otro código del proyecto. Por ejemplo, para crear el elemento XML personalizado cuando el usuario abre el documento, llame al método desde un controlador de eventos `ThisDocument_Startup`.  
  
## Programación eficaz  
 Para simplificar, este ejemplo usa una cadena XML que se define como una variable local en el método. Normalmente, debe obtener el XML desde un origen externo, como un archivo o una base de datos.  
  
## Vea también  
 [Información general sobre los elementos XML personalizados](../vsto/custom-xml-parts-overview.md)   
 [Cómo: Agregar elementos XML personalizados a documentos mediante complementos de VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
  