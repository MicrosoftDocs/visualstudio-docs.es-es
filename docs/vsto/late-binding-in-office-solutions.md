---
title: Enlace en tiempo de ejecución en las soluciones de Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62224006d04e0a1e7447053e868dd9946f00c97e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640693"
---
# <a name="late-binding-in-office-solutions"></a>Enlace en tiempo de ejecución en las soluciones de Office
  Algunos tipos en los modelos de objetos de aplicaciones de Office proporcionan funcionalidad que está disponible a través de las características de enlace. Por ejemplo, algunos métodos y propiedades pueden devolver distintos tipos de objetos según el contexto de la aplicación de Office, y algunos tipos pueden exponer métodos o propiedades en diferentes contextos diferentes.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Proyectos de Visual Basic donde **Option Strict** está desactivado y proyectos de Visual C# que tienen como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o el [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] puede trabajar directamente con los tipos que emplean estas características de enlace.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Los valores devueltos de conversión implícita y explícita del objeto
 Muchos métodos y propiedades en devuelven los ensamblados de interoperabilidad primarios (PIA) de Microsoft Office <xref:System.Object> valores, puesto que pueden devolver varios tipos diferentes de objetos. Por ejemplo, el <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> propiedad devuelve un <xref:System.Object> porque su valor devuelto puede ser un <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Excel.Chart> objeto, dependiendo de la hoja activa.

 Cuando un método o propiedad devuelve un <xref:System.Object>, debe convertir explícitamente (en Visual Basic) el objeto al tipo correcto en proyectos de Visual Basic donde **Option Strict** está activado. No es necesario convertir explícitamente <xref:System.Object> devolver valores de los proyectos de Visual Basic donde **Option Strict** está desactivada.

 En la mayoría de los casos, la documentación de referencia enumera los posibles tipos de valor devuelto para un miembro que devuelve un <xref:System.Object>. El objeto de la conversión habilita IntelliSense para el objeto en el Editor de código.

 Para obtener información acerca de la conversión en Visual Basic, vea [conversiones implícitas y explícitas &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) y [CType (función) &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).

### <a name="examples"></a>Ejemplos
 En el ejemplo de código siguiente se muestra cómo convertir un objeto a un tipo específico en un proyecto de Visual Basic donde **Option Strict** está activado. En este tipo de proyecto, debe convertir explícitamente el <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> propiedad a un <xref:Microsoft.Office.Interop.Excel.Range>. En este ejemplo requiere un proyecto de Excel de nivel de documento con una clase de hoja de cálculo denominada `Sheet1`.

 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]

 En el ejemplo de código siguiente se muestra cómo convertir implícitamente un objeto a un tipo específico en un proyecto de Visual Basic donde **Option Strict** está apagado o en un proyecto de Visual C# que tenga como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. En estos tipos de proyectos, la <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> propiedad se convierte implícitamente en un <xref:Microsoft.Office.Interop.Excel.Range>. En este ejemplo requiere un proyecto de Excel de nivel de documento con una clase de hoja de cálculo denominada `Sheet1`.

 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]

## <a name="access-members-that-are-available-only-through-late-binding"></a>Acceso a miembros que están disponibles solo a través de enlace en tiempo de ejecución
 Algunas propiedades y métodos en los PIA de Office están disponibles solo a través del enlace en tiempo de ejecución. En Visual Basic, los proyectos donde **Option Strict** está apagado o en proyectos de Visual C# que tienen como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], puede usar las características de enlace en tiempo de ejecución en los siguientes idiomas para tener acceso a miembros enlazados en tiempo de ejecución. En Visual Basic, los proyectos donde **Option Strict** está activado, debe usar la reflexión para tener acceso a estos miembros.

### <a name="examples"></a>Ejemplos
 El código siguiente muestra cómo obtener acceso a los miembros enlazados en tiempo de ejecución en un proyecto de Visual Basic donde **Option Strict** está apagado o en un proyecto de Visual C# que tenga como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Este ejemplo accede a las enlazadas **nombre** propiedad de la **abrir archivo** cuadro de diálogo de Word. Para usar este ejemplo, ejecútelo desde el `ThisDocument` o `ThisAddIn` clase en un proyecto de Word.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 En el ejemplo de código siguiente se muestra cómo usar la reflexión para realizar la misma tarea en un proyecto de Visual Basic donde **Option Strict** está activado.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Vea también
- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Uso de tipo dinámico &#40;C&#35; Guía de programación&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Option Strict (instrucción)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflexión (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflexión (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
