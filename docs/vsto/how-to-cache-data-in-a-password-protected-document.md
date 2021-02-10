---
title: 'Cómo: almacenar datos en caché en un documento protegido mediante contraseña'
description: Sepa que si agrega datos a la memoria caché de datos en un documento o libro protegido con una contraseña, puede guardar los cambios en los datos almacenados en caché invalidando dos métodos en el proyecto.
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
ms.openlocfilehash: cd7efe4aa2aa14cb94a68f0729bc7fe3535888ee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954038"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Cómo: almacenar datos en caché en un documento protegido mediante contraseña
  Si agrega datos a la memoria caché de datos en un documento o libro protegido con una contraseña, los cambios en los datos almacenados en caché no se guardan automáticamente. Puede guardar los cambios en los datos almacenados en caché invalidando dos métodos en el proyecto.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Almacenar en caché en documentos de Word

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Para almacenar en caché los datos de un documento de Word que está protegido con una contraseña

1. En la `ThisDocument` clase, marque un campo público o una propiedad que se va a almacenar en caché. Para obtener más información, vea [almacenar datos en caché](../vsto/caching-data.md).

2. Invalide el <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> método en la `ThisDocument` clase y quite la protección del documento.

     Cuando se guarda el documento, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para darle la oportunidad de desproteger el documento. Esto permite guardar los cambios realizados en los datos almacenados en caché.

3. Invalide el <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> método en la `ThisDocument` clase y vuelva a aplicar la protección al documento.

     Una vez guardado el documento, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para darle la oportunidad de volver a aplicar la protección al documento.

### <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo almacenar en caché los datos de un documento de Word que está protegido con una contraseña. Antes de que el código Quite la protección en el <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> método, guarda el <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> valor actual, de modo que se pueda volver a aplicar el mismo tipo de protección en el <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> método.

 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]

### <a name="compile-the-code"></a>Compilar el código
 Agregue este código a la `ThisDocument` clase en el proyecto. En este código se supone que la contraseña se almacena en un campo denominado `securelyStoredPassword` .

## <a name="cache-in-excel-workbooks"></a>Almacenar en caché en libros de Excel
 En los proyectos de Excel, este procedimiento solo es necesario cuando se protege todo el libro con una contraseña mediante el <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> método. Este procedimiento no es necesario si se protege una determinada hoja de cálculo con una contraseña mediante el <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> método.

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Para almacenar en caché los datos de un libro de Excel que está protegido con una contraseña

1. En la `ThisWorkbook` clase o en una de las `Sheet` clases *n* , marque una propiedad o campo público que se va a almacenar en caché. Para obtener más información, vea [almacenar datos en caché](../vsto/caching-data.md).

2. Invalide el <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> método en la `ThisWorkbook` clase y quite la protección del libro.

     Cuando se guarda el libro, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para darle la oportunidad de desproteger el libro. Esto permite guardar los cambios realizados en los datos almacenados en caché.

3. Invalide el <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> método en la `ThisWorkbook` clase y vuelva a aplicar la protección al documento.

     Una vez guardado el libro, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para darle la oportunidad de volver a aplicar la protección al libro.

### <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo almacenar en caché los datos de un libro de Excel que está protegido con una contraseña. Antes de que el código Quite la protección en el <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> método, guarda los <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> valores y actuales <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> , de modo que se pueda volver a aplicar el mismo tipo de protección en el <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> método.

 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]

### <a name="compile-the-code"></a>Compilar el código
 Agregue este código a la `ThisWorkbook` clase en el proyecto. En este código se supone que la contraseña se almacena en un campo denominado `securelyStoredPassword` .

## <a name="see-also"></a>Vea también
- [Datos de caché](../vsto/caching-data.md)
- [Cómo: almacenar datos en caché para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Cómo: almacenar en caché un origen de datos en un documento de Office mediante programación](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
