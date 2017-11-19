---
title: "El enlace en tiempo de ejecución en las soluciones de Office | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
ms.assetid: 80b0d23e-df68-4ea9-a02b-238aee8ca9c0
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 932a7ccc3f52d80e4f75999f401c61b2663095f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="late-binding-in-office-solutions"></a>Enlace en tiempo de ejecución en las soluciones de Office
  Algunos tipos en los modelos de objetos de aplicaciones de Office proporcionan funcionalidad que está disponible a través de características de enlace de tiempo de ejecución. Por ejemplo, algunos métodos y propiedades pueden devolver distintos tipos de objetos según el contexto de la aplicación de Office y algunos tipos pueden exponer métodos o propiedades en diferentes contextos diferentes.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Proyectos de Visual Basic donde **Option Strict** está desactivado y proyectos de Visual C# que tienen como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o el [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] puede trabajar directamente con los tipos que emplean estas características de enlace.  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Conversión implícita y explícita de los valores devueltos del objeto  
 Muchos métodos y propiedades en devuelven ensamblados de interoperabilidad primarios (PIA) de Microsoft Office <xref:System.Object> valores, porque pueden devolver distintos tipos de objetos. Por ejemplo, el <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> propiedad devuelve un <xref:System.Object> porque su valor devuelto puede ser un <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Excel.Chart> objeto, dependiendo de qué es la hoja activa.  
  
 Cuando un método o una propiedad devuelve un <xref:System.Object>, debe convertir explícitamente (en Visual Basic) el objeto al tipo correcto en proyectos de Visual Basic donde **Option Strict** se encuentra en. No es necesario convertir explícitamente <xref:System.Object> devuelven valores en proyectos de Visual Basic donde **Option Strict** está desactivada.  
  
 En la mayoría de los casos, la documentación de referencia enumera los posibles tipos de valor devuelto de un miembro que devuelve un <xref:System.Object>. Convertir o convertir el objeto habilita IntelliSense para el objeto en el Editor de código.  
  
 Para obtener información acerca de la conversión en Visual Basic, consulte [implícitas y las conversiones explícitas &#40; Visual Basic &#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) y [CType (función) &#40; Visual Basic &#41; ](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### <a name="examples"></a>Ejemplos  
 En el ejemplo de código siguiente se muestra cómo convertir un objeto a un tipo específico en un proyecto de Visual Basic donde **Option Strict** se encuentra en. En este tipo de proyecto, se debe convertir explícitamente el <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> propiedad a un <xref:Microsoft.Office.Interop.Excel.Range>. Este ejemplo necesita un proyecto de Excel de nivel de documento con una clase de hoja de cálculo denominada `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 En el ejemplo de código siguiente se muestra cómo convertir implícitamente un objeto a un tipo específico en un proyecto de Visual Basic donde **Option Strict** está apagado o en un proyecto de Visual C# que tenga como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. En estos tipos de proyectos, el <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> propiedad se convierte implícitamente en un <xref:Microsoft.Office.Interop.Excel.Range>. Este ejemplo necesita un proyecto de Excel de nivel de documento con una clase de hoja de cálculo denominada `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="accessing-members-that-are-available-only-through-late-binding"></a>Obtener acceso a miembros que están disponibles solo a través de enlace más tarde  
 Algunas propiedades y métodos de los PIA de Office están disponibles solo a través de enlaces de tiempo de ejecución. En Visual Basic, proyectos where **Option Strict** está apagado o en proyectos de Visual C# que tienen como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], puede usar las características de enlace en tiempo de ejecución en estos idiomas para tener acceso a los miembros enlazados en tiempo de ejecución. En Visual Basic, proyectos where **Option Strict** está activado, debe usar la reflexión para tener acceso a estos miembros.  
  
### <a name="examples"></a>Ejemplos  
 En el ejemplo de código siguiente se muestra cómo obtener acceso a los miembros de tiempo de ejecución en un proyecto de Visual Basic donde **Option Strict** está apagado o en un proyecto de Visual C# que tenga como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Este ejemplo accede a las enlazadas **nombre** propiedad de la **abrir archivo** cuadro de diálogo de Word. Para usar este ejemplo, ejecútelo desde la `ThisDocument` o `ThisAddIn` clase en un proyecto de Word.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 En el ejemplo de código siguiente se muestra cómo usar la reflexión para realizar la misma tarea en un proyecto de Visual Basic donde **Option Strict** se encuentra en.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Vea también  
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Uso de tipo dinámico &#40; C &#35; Guía de programación de &#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)  (Option Strict (Instrucción))  
 [Reflexión (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflexión (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [Diseño y creación de soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  