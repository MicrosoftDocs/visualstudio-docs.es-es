---
title: "Extensi&#243;n de Excel de muestra: clases de elementos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Extensi&#243;n de Excel de muestra: clases de elementos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La extensión usa clases que se derivan de <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> y representan los controles Worksheet y Cell en [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
 El elemento base para esta extensión es `ExcelElement`.  Las clases `ExcelWorksheetElement` y `ExcelCellElement` heredan de ese elemento.  
  
## Element y ElementInformation \(clases\)  
 `Element`  es la clase base para todos los elementos de la interfaz de usuario para la extensión Excel y hereda de la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>.  `ElementInformation` es la clase base para las clases de información de elemento del ejemplo y no tiene ningún miembro.  
  
#### Propiedades y métodos simples  
 Estos miembros devuelven valores simples, como el valor de la propiedad `Name` o el valor de la propiedad `ClassName` y el código es claro y fácil de leer.  Algunos valores se devuelven usando la clase `Utility`, que se describe más adelante.  Otros devuelven `null` porque no son pertinentes en esta extensión de ejemplo.  Hay dos miembros más interesantes que otros: la propiedad <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> y el método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A>.  
  
#### QueryId \(propiedad\)  
 Esta propiedad devuelve una condición formada por pares de nombre y valor de propiedad que identifican de manera única el control durante la reproducción.  Para cada clase de control derivada, el desarrollador debe invalidar esta propiedad para devolver un objeto <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> que el marco pueda usar para encontrar el control en la interfaz de usuario.  
  
#### CacheProperties \(método\)  
 El marco de prueba llama a este método durante el proceso de grabación para indicar al elemento que debe guardar una instantánea de las propiedades importantes.  Esto hace que se conserven las propiedades aunque el control real de la interfaz de usuario no esté ya en la pantalla.  
  
## WorksheetElement y WorksheetInformation \(clases\)  
 La clase `WorksheetElement` representa una hoja de cálculo de Excel en el marco de prueba y hereda de la clase base `Element`.  Se invalidan tres propiedades para proporcionar información específica sobre el objeto Worksheet de Excel: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> y <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> también se aplica a esta clase para hacerla visible para COM.  
  
 La clase `WorksheetInformation` representa información sobre una hoja de cálculo de Excel.  Solo tiene un miembro, la propiedad `SheetName`, que es suficiente para este ejemplo.  
  
## CellElement y CellInformation \(clases\)  
 La clase `CellElement` representa una celda de Excel y hereda de la clase base `Element`.  El único miembro invalidado es la propiedad <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>, que devuelve una interfaz <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> que usa las propiedades `RowIndex` y `ColumnIndex` para identificar la celda.  
  
## Utilities y ExcelUtilities \(clases\)  
 La clase `ExcelUtilities` interna proporciona algunos valores constantes, como el nombre de la tecnología, y un método que determina si el identificador de ventana proporcionado representa una hoja de cálculo de Excel.  
  
 La clase `Utilities` tiene métodos auxiliares que devuelven diversa información sobre la interfaz de usuario.  Algunos métodos usan llamadas directas en las DLL del sistema externas, como **USER32.DLL** y **OLEACC.DLL**, para obtener los identificadores de ventana de la interfaz de usuario**.**  
  
## Vea también  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)