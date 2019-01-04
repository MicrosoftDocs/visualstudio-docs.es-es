---
title: Procedimiento Almacenar datos en caché en un documento protegido por contraseña
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: c47f76c2371737b10c5eb58566cef388aff5fcd7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968422"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Procedimiento Almacenar datos en caché en un documento protegido por contraseña
  Si agrega datos a la caché de datos en un documento o libro que está protegido con una contraseña, no se guardan los cambios realizados en los datos en caché automáticamente. Puede guardar los cambios a los datos almacenados en caché mediante el reemplazo de dos métodos en el proyecto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>Almacenamiento en caché en documentos de Word  
  
### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Para almacenar datos en un documento de Word que está protegido con una contraseña  
  
1.  En el `ThisDocument` class, marcar un campo público o una propiedad en la memoria caché. Para obtener más información, consulte [almacenar en caché datos](../vsto/caching-data.md).  
  
2.  Invalidar el <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> método en el `ThisDocument` clase y quitar la protección del documento.  
  
     Cuando se guarda el documento, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para darle una oportunidad para desproteger el documento. Esto permite realizar cambios en los datos en caché se guarden.  
  
3.  Invalidar el <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> método en el `ThisDocument` clase y volver a aplicar la protección al documento.  
  
     Después de guardar el documento, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para darle la oportunidad de volver a aplicar la protección al documento.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente muestra cómo almacenar en caché datos en un documento de Word que está protegido con una contraseña. Antes de que el código quita la protección en el <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> método, guarda actual <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> valor, por lo que se pueda aplicar el mismo tipo de protección en el <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> método.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compile-the-code"></a>Compilar el código  
 Agregue este código a la `ThisDocument` clase del proyecto. Este código supone que la contraseña se almacena en un campo denominado `securelyStoredPassword`.  
  
## <a name="cache-in-excel-workbooks"></a>Almacenar en caché en los libros de Excel  
 En los proyectos de Excel, este procedimiento sólo es necesario cuando proteger el libro completo con una contraseña mediante la <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> método. Este procedimiento no es necesario si protege solo una hoja de cálculo específico con una contraseña mediante el uso de la <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> método.  
  
### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Para almacenar datos en un libro de Excel que está protegido con una contraseña  
  
1.  En el `ThisWorkbook` clase o una de las `Sheet` *n* clases, marcar un campo público o una propiedad en la memoria caché. Para obtener más información, consulte [almacenar en caché datos](../vsto/caching-data.md).  
  
2.  Invalidar el <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> método en el `ThisWorkbook` clase y quitar la protección del libro.  
  
     Cuando se guarda el libro, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para darle una oportunidad para desproteger el libro. Esto permite realizar cambios en los datos en caché se guarden.  
  
3.  Invalidar el <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> método en el `ThisWorkbook` clase y volver a aplicar la protección al documento.  
  
     Una vez guardado el libro, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para darle la oportunidad de volver a aplicar la protección en el libro.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente muestra cómo almacenar en caché datos en un libro de Excel que está protegido con una contraseña. Antes de que el código quita la protección en el <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> método, guarda actual <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> y <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> valores, para que se puede aplicar el mismo tipo de protección en el <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> método.  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compile-the-code"></a>Compilar el código  
 Agregue este código a la `ThisWorkbook` clase del proyecto. Este código supone que la contraseña se almacena en un campo denominado `securelyStoredPassword`.  
  
## <a name="see-also"></a>Vea también  
 [Almacenar datos en caché](../vsto/caching-data.md)   
 [Cómo: Almacenar en caché datos para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Cómo: Almacenar en caché mediante programación un origen de datos en un documento de Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
