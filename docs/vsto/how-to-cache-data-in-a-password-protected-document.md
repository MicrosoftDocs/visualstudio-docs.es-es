---
title: 'Cómo: Almacenar en caché datos en un documento protegido con contraseña'
description: Aprenda que si agrega datos a la caché de datos en un documento o libro protegido con una contraseña, puede guardar los cambios en los datos almacenados en caché invalidando dos métodos en el proyecto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ccdb906022d4dcfc321af294eec59afa36832773
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824190"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Cómo: Almacenar en caché datos en un documento protegido con contraseña
  Si agrega datos a la caché de datos en un documento o libro que está protegido con una contraseña, los cambios en los datos almacenados en caché no se guardan automáticamente. Puede guardar los cambios en los datos almacenados en caché reemplazando dos métodos en el proyecto.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Almacenamiento en caché en documentos de Word

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Para almacenar en caché datos en un documento de Word protegido con una contraseña

1. En la `ThisDocument` clase , marque un campo o propiedad públicos que se almacenarán en caché. Para obtener más información, vea Almacenar [en caché los datos](../vsto/caching-data.md).

2. Invalide <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> el método de la clase y quite la protección del `ThisDocument` documento.

     Cuando se guarda el documento, llama a este método para darle la oportunidad [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] de desproteger el documento. Esto permite guardar los cambios en los datos almacenados en caché.

3. Invalide <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> el método de la clase y vuelva a aplicar la protección al `ThisDocument` documento.

     Una vez guardado el documento, llama a este método para darle la oportunidad de volver a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aplicar la protección al documento.

### <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo almacenar en caché los datos de un documento de Word que está protegido con una contraseña. Antes de que el código quite la protección del método , guarda el valor actual, de modo que se pueda volver a aplicar el mismo tipo <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> de protección en el método <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb" id="Snippet1":::

### <a name="compile-the-code"></a>Compilar el código
 Agregue este código a la `ThisDocument` clase del proyecto. Este código supone que la contraseña se almacena en un campo denominado `securelyStoredPassword` .

## <a name="cache-in-excel-workbooks"></a>Caché en libros de Excel
 En los proyectos de Excel, este procedimiento solo es necesario cuando se protege todo el libro con una contraseña mediante el <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> método . Este procedimiento no es necesario si protege solo una hoja de cálculo específica con una contraseña mediante el <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> método .

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Para almacenar en caché los datos de un libro de Excel protegido con una contraseña

1. En la `ThisWorkbook` clase o en una de las clases `Sheet` *n,* marque un campo o propiedad públicos que se almacenarán en caché. Para obtener más información, vea Almacenar [en caché los datos](../vsto/caching-data.md).

2. Invalide <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> el método de la clase y quite la protección del `ThisWorkbook` libro.

     Cuando se guarda el libro, llama a este método para darle la oportunidad [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] de desproteger el libro. Esto permite guardar los cambios en los datos almacenados en caché.

3. Invalide <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> el método de la clase y vuelva a aplicar la protección al `ThisWorkbook` documento.

     Una vez guardado el libro, llama a este método para darle la oportunidad de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] volver a aplicar la protección al libro.

### <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo almacenar en caché los datos de un libro de Excel protegido con una contraseña. Antes de que el código quite la protección en el método , guarda los valores actuales y , de modo que se pueda volver a aplicar el mismo tipo <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> de protección en el método <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs" id="Snippet1":::

### <a name="compile-the-code"></a>Compilar el código
 Agregue este código a la `ThisWorkbook` clase del proyecto. Este código supone que la contraseña se almacena en un campo denominado `securelyStoredPassword` .

## <a name="see-also"></a>Consulte también
- [Datos de caché](../vsto/caching-data.md)
- [Cómo: Almacenar en caché datos para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Cómo: Almacenar en caché mediante programación un origen de datos en un documento de Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
