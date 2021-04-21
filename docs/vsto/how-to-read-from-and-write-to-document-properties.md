---
title: 'Cómo: Leer y escribir en las propiedades del documento'
description: Obtenga información sobre cómo puede usar Visual Studio para obtener o establecer propiedades de documento en Microsoft Excel y Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3474d86a7408e841d383c82e5ab38da90253dbbf
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826686"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Cómo: Leer y escribir en las propiedades del documento
  Puede almacenar propiedades de documento junto con un documento. Las aplicaciones de Office proporcionan una serie de propiedades integradas, como author, title y subject. En este tema se muestra cómo establecer las propiedades de documento en Microsoft Office Excel y Microsoft Office Word.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

## <a name="set-document-properties-in-excel"></a>Establecimiento de propiedades de documento en Excel
 Para trabajar con las propiedades integradas de Excel, use las siguientes propiedades:

- En un proyecto de nivel de documento, use la propiedad <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> de la clase `ThisWorkbook` .

- En un proyecto de complemento de VSTO, use la propiedad <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> de un objeto <xref:Microsoft.Office.Interop.Excel.Workbook> .

  Estas propiedades devuelven un objeto <xref:Microsoft.Office.Core.DocumentProperties> , que es una colección de objetos <xref:Microsoft.Office.Core.DocumentProperty> . Puede usar la propiedad `Item` de la colección para recuperar una propiedad determinada, ya sea por nombre o por índice dentro de la colección.

  En el siguiente ejemplo de código se muestra cómo cambiar la propiedad integrada **Revision Number** en un proyecto de nivel de documento.

### <a name="to-change-the-revision-number-property-in-excel"></a>Para cambiar la propiedad Revision Number en Excel

1. Asigne las propiedades integradas del documento a una variable.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet7":::

2. Incremente la propiedad `Revision Number` en uno.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet8":::

## <a name="set-document-properties-in-word"></a>Establecimiento de propiedades de documento en Word
 Para trabajar con las propiedades integradas de Word, use las siguientes propiedades:

- En un proyecto de nivel de documento, use la propiedad <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> de la clase `ThisDocument` .

- En un proyecto de complemento de VSTO, use la propiedad <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Document> .

  Estas propiedades devuelven un objeto <xref:Microsoft.Office.Core.DocumentProperties> , que es una colección de objetos <xref:Microsoft.Office.Core.DocumentProperty> . Puede usar la propiedad `Item` de la colección para recuperar una propiedad determinada, ya sea por nombre o por índice dentro de la colección.

  En el siguiente ejemplo de código se muestra cómo cambiar la propiedad integrada **Subject** en un proyecto de nivel de documento.

### <a name="to-change-the-subject-property"></a>Para cambiar la propiedad Subject

1. Asigne las propiedades integradas del documento a una variable.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb" id="Snippet1":::

2. Cambie la propiedad `Subject` a «Whitepaper».

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb" id="Snippet2":::

## <a name="robust-programming"></a>Programación sólida
 En los ejemplos se supone que ha escrito el código de la clase `ThisWorkbook` en un proyecto de nivel de documento para Excel y la clase `ThisDocument` en un proyecto de nivel de documento para Word.

 Aunque trabaje con Word y Excel y sus objetos, Microsoft Office proporciona una lista de propiedades de documento integradas. Si se intenta tener acceso a una propiedad sin definir, se produce una excepción.

## <a name="see-also"></a>Consulte también
- [Programas de complementos VSTO](../vsto/programming-vsto-add-ins.md)
- [Personalizaciones de nivel de documento del programa](../vsto/programming-document-level-customizations.md)
- [Cómo: Crear y modificar propiedades de documento personalizadas](../vsto/how-to-create-and-modify-custom-document-properties.md)
