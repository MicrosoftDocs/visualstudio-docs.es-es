---
title: "Enlace en tiempo de ejecuci&#243;n en las soluciones de Office"
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
  - "objetos [desarrollo de Office en Visual Studio], convertir"
  - "tipos [desarrollo de Office en Visual Studio], convertir"
  - "automatización [desarrollo de Office en Visual Studio], convertir objetos"
  - "convertir, objetos a tipos específicos"
ms.assetid: 80b0d23e-df68-4ea9-a02b-238aee8ca9c0
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Enlace en tiempo de ejecuci&#243;n en las soluciones de Office
  Algunos tipos de los modelos de objetos de aplicaciones de Office proporcionan funcionalidad que está disponible a través de las características de enlace en tiempo de ejecución.  Por ejemplo, algunos métodos y propiedades pueden devolver distintos tipos de objetos en función del contexto de la aplicación de Office y algunos tipos pueden exponer métodos o propiedades diferentes en contextos diferentes.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Los proyectos de Visual Basic donde **Option Strict** desactivado y Visual c\# destinados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] puede trabajar directamente con los tipos que emplean estas características de tarde\- enlace.  
  
## Conversión implícita y explícita de los valores devueltos de los objetos  
 Muchos métodos y propiedades de los ensamblados de interoperabilidad primarios \(PIA\) de Microsoft Office devuelven valores <xref:System.Object>, porque tienen la capacidad de devolver varios tipos de objetos diferentes.  Por ejemplo, la propiedad <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> devuelve <xref:System.Object> porque su valor devuelto puede ser el objeto <xref:Microsoft.Office.Interop.Excel.Chart> o <xref:Microsoft.Office.Interop.Excel.Worksheet>, dependiendo de qué sea la hoja activa.  
  
 Cuando un método o una propiedad devuelve <xref:System.Object>, debe convertir explícitamente en Visual Basic\) el objeto a los proyectos correctos de Visual Basic de tipo en donde **Option Strict** on.  No tiene que convertir explícitamente los valores devueltos de <xref:System.Object> en proyectos de Visual Basic donde **Option Strict** desactivado.  
  
 En la mayoría de los casos, la documentación de referencia muestra los posibles tipos de valor devuelto para un miembro que devuelve <xref:System.Object>.  La conversión del objeto proporciona la habilitación de IntelliSense para el objeto en el Editor de código.  
  
 Para obtener información sobre las conversiones en Visual Basic, vea [Conversiones implícita y explícita &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) y [CType &#40;Función&#41; &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### Ejemplos  
 El ejemplo de código siguiente muestra cómo convertir un objeto a un tipo específico en un proyecto de Visual Basic donde **Option Strict** on.  En este tipo de proyecto, debe convertir explícitamente la propiedad de <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> a <xref:Microsoft.Office.Interop.Excel.Range>.  En este ejemplo se requiere un proyecto de Excel de nivel de documento con una clase de hoja de cálculo denominada `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#9)]  
  
 En el siguiente ejemplo de código se muestra cómo convertir implícitamente un objeto a un tipo específico en un proyecto de Visual Basic donde **Option Strict** está desactivada o en un proyecto de Visual C\# destinado a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  En estos tipos de proyectos, la propiedad <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> se convierte implícitamente a <xref:Microsoft.Office.Interop.Excel.Range>.  En este ejemplo se requiere un proyecto de Excel de nivel de documento con una clase de hoja de cálculo denominada `Sheet1`.  
  
 [!code-csharp[Trin_VstcoreProgramming#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#10)]
 [!code-vb[Trin_VstcoreProgramming#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#10)]  
  
## Obtener acceso a miembros que solo están disponibles a través del enlace en tiempo de ejecución  
 Algunas propiedades y métodos de los PIA de Office solo están disponibles a través del enlace en tiempo de ejecución.  En los proyectos de Visual Basic donde está o en proyectos de Visual c\# **Option Strict** destinados [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], puede utilizar las características de enlace en estos lenguajes para tener acceso a los miembros del tarde\- límite.  En proyectos de Visual Basic donde **Option Strict** on, deberá utilizar la reflexión para tener acceso a estos miembros.  
  
### Ejemplos  
 En el siguiente ejemplo de código se muestra cómo tener acceso a los miembros enlazados en tiempo de ejecución en un proyecto de Visual Basic donde **Option Strict** está desactivada o en un proyecto de Visual C\# destinado a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  En este ejemplo se tiene acceso a la propiedad enlazada en tiempo de ejecución **Name** del cuadro de diálogo **Abrir archivo** de Word.  Para usar este ejemplo, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` en un proyecto de Word.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 El ejemplo de código siguiente muestra cómo utilizar la reflexión para realizar la misma tarea en un proyecto de Visual Basic donde **Option Strict** on.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## Vea también  
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Uso de tipo dinámico &#40;Guía de programación de C&#35;&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict &#40;Instrucción&#41;](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflexión &#40;C&#35; y Visual Basic&#41;](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  