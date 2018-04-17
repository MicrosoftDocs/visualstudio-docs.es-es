---
title: 'Cómo: almacenar en caché datos en un documento protegido por contraseña | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 71ce65cd253ea6473a07a98542449a1e47ae9d7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Cómo: Almacenar datos en caché en un documento protegido por contraseña
  Si agrega datos a la caché de datos en un documento o un libro que está protegido con una contraseña, los cambios en los datos almacenados en caché no se guardan automáticamente. Puede guardar los cambios a los datos almacenados en memoria caché al invalidar los dos métodos en el proyecto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>Almacenamiento en caché de documentos de Word  
  
#### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Para almacenar datos en un documento de Word que está protegido con una contraseña  
  
1.  En la `ThisDocument` clase, marque un campo público o una propiedad en la memoria caché. Para obtener más información, consulta [Caching Data](../vsto/caching-data.md).  
  
2.  Invalidar el <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> método en la `ThisDocument` clase y quite la protección del documento.  
  
     Cuando se guarda el documento, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para darle la oportunidad de desproteger el documento. Esto permite realizar cambios en los datos almacenados en memoria caché se guarden.  
  
3.  Invalidar el <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> método en la `ThisDocument` clase y volver a aplicar la protección al documento.  
  
     Después de guarda el documento, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para darle la oportunidad de volver a aplicar la protección al documento.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo almacenar en caché datos en un documento de Word que está protegido con una contraseña. Antes de que el código quita la protección en el <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> método, guarda actual <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> valor, por lo que puede volver a aplicar el mismo tipo de protección en el <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> método.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compiling-the-code"></a>Compilar el código  
 Agregue este código a la `ThisDocument` clase en su proyecto. Este código supone que la contraseña se almacena en un campo denominado `securelyStoredPassword`.  
  
## <a name="caching-in-excel-workbooks"></a>Almacenamiento en caché en los libros de Excel  
 En los proyectos de Excel, este procedimiento sólo es necesario cuando se protege el libro completo con una contraseña mediante el <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> método. Este procedimiento no es necesario si sólo una hoja de cálculo específico con una contraseña que proteja mediante el <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> método.  
  
#### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Para almacenar datos en un libro de Excel que está protegido con una contraseña  
  
1.  En el `ThisWorkbook` clase o uno de los `Sheet` *n* clases, marcar un campo público o una propiedad en la memoria caché. Para obtener más información, consulta [Caching Data](../vsto/caching-data.md).  
  
2.  Invalidar el <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> método en la `ThisWorkbook` clase y quite la protección del libro.  
  
     Cuando se guarda el libro, la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para darle la oportunidad de desproteger el libro. Esto permite realizar cambios en los datos almacenados en memoria caché se guarden.  
  
3.  Invalidar el <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> método en la `ThisWorkbook` clase y volver a aplicar la protección al documento.  
  
     Después de guarda el libro, la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para darle la oportunidad de volver a aplicar la protección al libro.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo almacenar en caché datos en un libro de Excel que está protegido con una contraseña. Antes de que el código quita la protección en el <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> método, guarda actual <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> y <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> los valores, por lo que puede volver a aplicar el mismo tipo de protección en el <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> método.  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compiling-the-code"></a>Compilar el código  
 Agregue este código a la `ThisWorkbook` clase en su proyecto. Este código supone que la contraseña se almacena en un campo denominado `securelyStoredPassword`.  
  
## <a name="see-also"></a>Vea también  
 [Almacenar datos en caché](../vsto/caching-data.md)   
 [Cómo: almacenar en caché datos para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Cómo: Almacenar en caché un origen de datos de un documento de Office mediante programación](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  