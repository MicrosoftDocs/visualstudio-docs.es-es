---
title: 'Cómo: crear y modificar propiedades de documento personalizadas'
description: Obtenga información acerca de cómo puede crear y modificar propiedades de documento personalizadas si hay información adicional que desea almacenar con el documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4897008f102600bd222a21761237acc4bcb62a30
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844301"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Cómo: crear y modificar propiedades de documento personalizadas
  Las aplicaciones de Microsoft Office enumeradas anteriormente proporcionan propiedades integradas que se almacenan con los documentos. Además, puede crear y modificar propiedades de documento personalizadas si hay información adicional que desea almacenar con el documento.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Use la propiedad CustomDocumentProperties de un documento para trabajar con propiedades personalizadas. Por ejemplo, en un proyecto de nivel de documento para Microsoft Office Excel, use la propiedad <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> de la clase `ThisWorkbook` . En un proyecto de complemento de VSTO para Excel, use la propiedad <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> de un objeto <xref:Microsoft.Office.Interop.Excel.Workbook> . Estas propiedades devuelven un objeto <xref:Microsoft.Office.Core.DocumentProperties> , que es una colección de objetos <xref:Microsoft.Office.Core.DocumentProperty> . Puede usar la propiedad `Item` de la colección para recuperar una propiedad determinada, ya sea por nombre o por índice dentro de la colección.

 En el ejemplo siguiente se muestra cómo agregar una propiedad personalizada en una personalización de nivel de documento para Excel y asignarle un valor.

## <a name="example"></a>Ejemplo
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]

## <a name="robust-programming"></a>Programación sólida
 Si se intenta acceder a la propiedad `Value` para propiedades sin definir, se produce una excepción.

## <a name="see-also"></a>Vea también
- [Complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md)
- [Personalizaciones de nivel de documento de programa](../vsto/programming-document-level-customizations.md)
- [Cómo: leer y escribir en propiedades de documento](../vsto/how-to-read-from-and-write-to-document-properties.md)
