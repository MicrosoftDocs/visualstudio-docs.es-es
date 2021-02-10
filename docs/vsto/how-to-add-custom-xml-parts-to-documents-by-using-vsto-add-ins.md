---
title: Agregar elementos XML personalizados a documentos mediante complementos de VSTO
description: Obtenga información sobre cómo almacenar datos XML en los siguientes tipos de documentos creando un elemento XML personalizado en un complemento de VSTO.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fbba5c629807815a306221368d00b7d759dcc294
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954233"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Cómo: agregar elementos XML personalizados a documentos mediante complementos de VSTO
  Puede almacenar datos XML en los siguientes tipos de documentos creando un elemento XML personalizado en un complemento de VSTO:

- Un libro de Microsoft Office Excel.

- Un documento de Microsoft Office Word.

- Una presentación de Microsoft Office PowerPoint.

  Para obtener más información, vea [información general sobre los elementos XML personalizados](../vsto/custom-xml-parts-overview.md).

  **Aplicación:** la información de este tema se aplica a los proyectos de nivel de aplicación de Excel, PowerPoint y Word. Para obtener más información, consulte [características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Para agregar un elemento XML personalizado a un libro de Excel

1. Agregue un nuevo objeto <xref:Microsoft.Office.Core.CustomXMLPart> a la colección <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> del libro. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la cadena XML que desea almacenar en el libro.

     En el ejemplo de código siguiente se agrega un elemento XML personalizado al libro especificado.

     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]

2. Agregue el `AddCustomXmlPartToWorkbook` método a la `ThisAddIn` clase en un proyecto de complemento de VSTO para Excel.

3. Llame al método desde otro código del proyecto. Por ejemplo, para crear el elemento XML personalizado cuando el usuario abre un libro, llame al método desde un controlador de eventos para el evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> .

## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Para agregar un elemento XML personalizado a un documento de Word

1. Agregue un nuevo objeto <xref:Microsoft.Office.Core.CustomXMLPart> a la colección <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> del documento. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la cadena XML que desea almacenar en el documento.

     En el ejemplo de código siguiente se agrega un elemento XML personalizado al documento especificado.

     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]

2. Agregue el `AddCustomXmlPartToDocument` método a la `ThisAddIn` clase en un proyecto de complemento de VSTO para Word.

3. Llame al método desde otro código del proyecto. Por ejemplo, para crear el elemento XML personalizado cuando el usuario abre un documento, llame al método desde un controlador de eventos para el evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Para agregar un elemento XML personalizado a una presentación de PowerPoint

1. Agregue un nuevo <xref:Microsoft.Office.Core.CustomXMLPart> objeto a la colección [Microsoft.Office.Interop.PowerPoint._Presentation. CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29) en la presentación. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la cadena XML que desea almacenar en la presentación.

     En el ejemplo de código siguiente se agrega un elemento XML personalizado a la presentación especificada.

     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]

2. Agregue el `AddCustomXmlPartToPresentation` método a la `ThisAddIn` clase en un proyecto de complemento de VSTO para PowerPoint.

3. Llame al método desde otro código del proyecto. Por ejemplo, para crear el elemento XML personalizado cuando el usuario abre una presentación, llame al método desde un controlador de eventos para el evento [Microsoft.Office.Interop.PowerPoint.EApplication_Event. AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v=office.14)) .

## <a name="robust-programming"></a>Programación sólida
 Para simplificar, este ejemplo usa una cadena XML que se define como una variable local en el método. Normalmente, debe obtener el XML desde un origen externo, como un archivo o una base de datos.

## <a name="see-also"></a>Vea también
- [Información general sobre los elementos XML personalizados](../vsto/custom-xml-parts-overview.md)
- [Cómo: agregar elementos XML personalizados a personalizaciones de nivel de documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
