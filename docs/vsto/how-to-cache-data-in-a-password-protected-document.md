---
title: "C&#243;mo: Almacenar datos en cach&#233; en un documento protegido por contrase&#241;a | Microsoft Docs"
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
  - "datos [desarrollo de Office en Visual Studio], almacenar en caché"
  - "almacenamiento de datos en caché [desarrollo de Office en Visual Studio], documentos protegidos"
  - "conjuntos de datos [desarrollo de Office en Visual Studio], almacenar en caché"
ms.assetid: 91b865fc-bd01-438f-ac63-2fe3175bc2e8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# C&#243;mo: Almacenar datos en cach&#233; en un documento protegido por contrase&#241;a
  Si se agregan datos a la memoria caché en un documento o libro protegidos con contraseña, los cambios que se hagan en esos datos no se guardarán automáticamente.  Dichos cambios podrán guardarse si se reemplazan dos métodos en el proyecto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Almacenar en memoria caché en documentos de Word  
  
#### Para almacenar en memoria caché los datos de un documento de Word protegido con contraseña  
  
1.  En la clase `ThisDocument`, marque un campo o una propiedad pública que se va a almacenar en la memoria caché.  Para obtener más información, vea [Almacenar datos en caché](../vsto/caching-data.md).  
  
2.  Invalide el método <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> de la clase `ThisDocument` y quite la protección del documento.  
  
     Cuando se guarda el documento, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para que el usuario tenga la oportunidad de desproteger el documento.  Esto permite guardar los cambios efectuados en los datos almacenados en la memoria caché.  
  
3.  Reemplace el método <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> de la clase `ThisDocument` y vuelva a proteger el documento.  
  
     Una vez guardado el documento, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para que el usuario tenga la oportunidad de proteger de nuevo el documento.  
  
### Ejemplo  
 En el ejemplo de código siguiente se muestra cómo almacenar en memoria caché los datos de un documento de Word protegido con contraseña.  Antes de que el código quite la protección en el método <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>, guarda el valor <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> actual para que se pueda volver a aplicar el mismo tipo de protección en el método <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/VB/ThisDocument.vb#1)]  
  
### Compilar el código  
 Agregue este código a la clase `ThisDocument` del proyecto.  Este código da por supuesto que la contraseña está almacenada en un campo denominado `securelyStoredPassword`.  
  
## Almacenar en memoria caché en libros de Excel  
 En los proyectos Excel, este procedimiento solo es necesario cuando se protege el libro completo con contraseña utilizando el método <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>.  Este procedimiento no es necesario si protege una hoja de cálculo concreta con contraseña utilizando el método <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A>.  
  
#### Para almacenar en memoria caché los datos de un libro de Excel protegido con contraseña  
  
1.  En la clase `ThisWorkbook` o en una de las clases `Sheet`*n*, marque el campo o la propiedad pública que se va a almacenar en memoria caché.  Para obtener más información, vea [Almacenar datos en caché](../vsto/caching-data.md).  
  
2.  Invalide el método <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> de la clase `ThisWorkbook` y quite la protección del libro.  
  
     Cuando se guarda el libro, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para que el usuario tenga la oportunidad de desproteger el libro.  Esto permite guardar los cambios efectuados en los datos almacenados en la memoria caché.  
  
3.  Reemplace el método <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> de la clase `ThisWorkbook` y vuelva a proteger el documento.  
  
     Una vez guardado el libro, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama a este método para que el usuario tenga la oportunidad de proteger de nuevo el libro.  
  
### Ejemplo  
 En el ejemplo de código siguiente se muestra cómo almacenar en memoria caché los datos de un libro de Excel protegido con contraseña.  Antes de que el código quite la protección en el método <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>, guarda los valores <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> y <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> actuales para que se pueda volver a aplicar el mismo tipo de protección en el método <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>.  
  
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/VB/ThisWorkbook.vb#1)]  
  
### Compilar el código  
 Agregue este código a la clase `ThisWorkbook` del proyecto.  Este código da por supuesto que la contraseña está almacenada en un campo denominado `securelyStoredPassword`.  
  
## Vea también  
 [Almacenar datos en caché](../vsto/caching-data.md)   
 [Cómo: Almacenar datos en la memoria caché para el uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Cómo: Almacenar en memoria caché un origen de datos de un documento de Office mediante programación](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  