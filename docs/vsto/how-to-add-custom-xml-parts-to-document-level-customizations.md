---
title: Procedimiento Agregar elementos XML personalizados a personalizaciones de nivel de documento
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb87650156f5ed0060170b0b9f809924d2326fce
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868032"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Procedimiento Agregar elementos XML personalizados a personalizaciones de nivel de documento
  Puede almacenar datos XML en un libro de Microsoft Office Excel o un documento de Microsoft Office Word creando un elemento XML personalizado en una personalización de nivel de documento. Para obtener más información, consulte [información general de elementos XML personalizados](../vsto/custom-xml-parts-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Visual Studio no ofrece proyectos de nivel de documento para Microsoft Office PowerPoint. Para obtener información sobre cómo agregar un elemento XML personalizado a una presentación de PowerPoint mediante el uso de un complemento de VSTO, consulte [Cómo: Agregar elementos XML personalizados a documentos mediante complementos VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Para agregar un elemento XML personalizado a un libro de Excel  
  
1.  Agregue un nuevo objeto <xref:Microsoft.Office.Core.CustomXMLPart> a la colección <xref:Microsoft.Office.Core.CustomXMLParts> del libro. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la cadena XML que desea almacenar en el libro.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb#1)]  
  
2.  Agregue el método `AddCustomXmlPartToWorkbook` a la clase `ThisWorkbook` en un proyecto de nivel de documento para Excel.  
  
3.  Llame al método desde otro código del proyecto. Por ejemplo, para crear el elemento XML personalizado cuando el usuario abre el libro, llame al método desde un controlador de eventos `ThisWorkbook_Startup` .  
  
### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Para agregar un elemento XML personalizado a un documento de Word  
  
1.  Agregue un nuevo objeto <xref:Microsoft.Office.Core.CustomXMLPart> a la colección <xref:Microsoft.Office.Core.CustomXMLParts> del documento. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la cadena XML que desea almacenar en el documento.  
  
     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs#1)]  
  
2.  Agregue el método `AddCustomXmlPartToDocument` a la clase `ThisDocument` en un proyecto de nivel de documento para Word.  
  
3.  Llame al método desde otro código del proyecto. Por ejemplo, para crear el elemento XML personalizado cuando el usuario abre el documento, llame al método desde un controlador de eventos `ThisDocument_Startup` .  
  
## <a name="robust-programming"></a>Programación sólida  
 Para simplificar, este ejemplo usa una cadena XML que se define como una variable local en el método. Normalmente, debe obtener el XML desde un origen externo, como un archivo o una base de datos.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre elementos XML personalizados](../vsto/custom-xml-parts-overview.md)   
 [Cómo: Agregar elementos XML personalizados a documentos mediante complementos de VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
