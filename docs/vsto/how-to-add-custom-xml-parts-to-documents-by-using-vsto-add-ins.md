---
title: "C&#243;mo: Agregar elementos XML personalizados a documentos mediante complementos de VSTO"
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
  - "complementos [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "documentos de Office [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "Word [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "PowerPoint [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "Excel [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "elementos XML personalizados [desarrollo de Office en Visual Studio], agregar"
  - "documentos [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio], elementos XML personalizados"
ms.assetid: 872d2beb-193b-49f9-9a7b-dcebab91a73b
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# C&#243;mo: Agregar elementos XML personalizados a documentos mediante complementos de VSTO
  Puede almacenar datos XML en los siguientes tipos de documentos creando un elemento XML personalizado en un complemento de VSTO:  
  
-   Un libro de Microsoft Office Excel.  
  
-   Un documento de Microsoft Office Word.  
  
-   Una presentación de Microsoft Office PowerPoint.  
  
 Para obtener más información, consulta [Información general sobre los elementos XML personalizados](../vsto/custom-xml-parts-overview.md).  
  
 **Aplicación:** la información de este tema se aplica a los proyectos de nivel de aplicación de Excel, PowerPoint y Word. Para obtener más información, consulta [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
### Para agregar un elemento XML personalizado a un libro de Excel  
  
1.  Agregue un nuevo objeto <xref:Microsoft.Office.Core.CustomXMLPart> a la colección <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> del libro.<xref:Microsoft.Office.Core.CustomXMLPart> contiene la cadena XML que desea almacenar en el libro.  
  
     En el ejemplo de código siguiente se agrega un elemento XML personalizado al libro especificado.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Agregue el método `AddCustomXmlPartToWorkbook` a la clase `ThisAddIn` en un proyecto de complemento VSTO para Excel.  
  
3.  Llame al método desde otro código del proyecto. Por ejemplo, para crear el elemento XML personalizado cuando el usuario abre un libro, llame al método desde un controlador de eventos para el evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen>.  
  
### Para agregar un elemento XML personalizado a un documento de Word  
  
1.  Agregue un nuevo objeto <xref:Microsoft.Office.Core.CustomXMLPart> a la colección <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> del documento.<xref:Microsoft.Office.Core.CustomXMLPart> contiene la cadena XML que desea almacenar en el documento.  
  
     En el ejemplo de código siguiente se agrega un elemento XML personalizado al documento especificado.  
  
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Agregue el método `AddCustomXmlPartToDocument` a la clase `ThisAddIn` en un proyecto de complemento VSTO para Word.  
  
3.  Llame al método desde otro código del proyecto. Por ejemplo, para crear el elemento XML personalizado cuando el usuario abre un documento, llame al método desde un controlador de eventos para el evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
### Para agregar un elemento XML personalizado a una presentación de PowerPoint  
  
1.  Agregue un nuevo objeto <xref:Microsoft.Office.Core.CustomXMLPart> a la colección <xref:Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts%2A> de la presentación.<xref:Microsoft.Office.Core.CustomXMLPart> contiene la cadena XML que desea almacenar en la presentación.  
  
     En el ejemplo de código siguiente se agrega un elemento XML personalizado a la presentación especificada.  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartPowerPointAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartPowerPointAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Agregue el método `AddCustomXmlPartToPresentation` a la clase `ThisAddIn` en un proyecto de complemento VSTO para PowerPoint.  
  
3.  Llame al método desde otro código del proyecto. Por ejemplo, para crear el elemento XML personalizado cuando el usuario abre una presentación, llame al método desde un controlador de eventos para el evento <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen>.  
  
## Programación eficaz  
 Para simplificar, este ejemplo usa una cadena XML que se define como una variable local en el método. Normalmente, debe obtener el XML desde un origen externo, como un archivo o una base de datos.  
  
## Vea también  
 [Información general sobre los elementos XML personalizados](../vsto/custom-xml-parts-overview.md)   
 [Cómo: Agregar elementos XML personalizados a personalizaciones de nivel de documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  