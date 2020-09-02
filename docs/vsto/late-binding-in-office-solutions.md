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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62583951"
---
# <a name="late-binding-in-office-solutions"></a>Enlace en tiempo de ejecución en las soluciones de Office
  Algunos tipos de los modelos de objetos de las aplicaciones de Office proporcionan funcionalidad que está disponible a través de las características de enlace en tiempo de ejecución. Por ejemplo, algunos métodos y propiedades pueden devolver distintos tipos de objetos en función del contexto de la aplicación de Office, y algunos tipos pueden exponer métodos o propiedades diferentes en contextos diferentes.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual Basic proyectos en los que **Option Strict** es OFF y los proyectos de Visual C# que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] pueden funcionar directamente con tipos que emplean estas características de enlace en tiempo de ejecución.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Conversión implícita y explícita de valores devueltos de objeto
 Muchos métodos y propiedades en el Microsoft Office ensamblados de interoperabilidad primarios (PIA) devuelven <xref:System.Object> valores, ya que pueden devolver varios tipos diferentes de objetos. Por ejemplo, la <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> propiedad devuelve un <xref:System.Object> porque su valor devuelto puede ser <xref:Microsoft.Office.Interop.Excel.Worksheet> un <xref:Microsoft.Office.Interop.Excel.Chart> objeto o, dependiendo de cuál sea la hoja activa.

 Cuando un método o una propiedad devuelven un <xref:System.Object> , debe convertir explícitamente (en Visual Basic) el objeto al tipo correcto en los proyectos de Visual Basic donde **Option Strict** está activada. No es necesario convertir explícitamente <xref:System.Object> los valores devueltos en Visual Basic Proyectos donde **Option Strict** es OFF.

 En la mayoría de los casos, la documentación de referencia muestra los posibles tipos de valor devuelto de un miembro que devuelve <xref:System.Object> . La conversión o conversión del objeto habilita IntelliSense para el objeto en el editor de código.

 Para obtener información sobre la conversión en Visual Basic, vea [conversiones implícitas y explícitas &#40;Visual Basic función&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) y [CType &#40;](/dotnet/visual-basic/language-reference/functions/ctype-function)Visual Basic&#41;.

### <a name="examples"></a>Ejemplos
 En el ejemplo de código siguiente se muestra cómo convertir un objeto a un tipo específico en un proyecto de Visual Basic donde **Option Strict** es on. En este tipo de proyecto, debe convertir explícitamente la <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> propiedad en <xref:Microsoft.Office.Interop.Excel.Range> . Este ejemplo requiere un proyecto de Excel de nivel de documento con una clase de hoja de cálculo denominada `Sheet1` .

 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]

 En el ejemplo de código siguiente se muestra cómo convertir implícitamente un objeto en un tipo específico en un proyecto de Visual Basic donde **Option Strict** es OFF o en un proyecto de Visual C# que tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . En estos tipos de proyectos, la <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> propiedad se convierte implícitamente a <xref:Microsoft.Office.Interop.Excel.Range> . Este ejemplo requiere un proyecto de Excel de nivel de documento con una clase de hoja de cálculo denominada `Sheet1` .

 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]

## <a name="access-members-that-are-available-only-through-late-binding"></a>Obtener acceso a los miembros que solo están disponibles a través del enlace en tiempo de ejecución
 Algunas propiedades y métodos de los PIA de Office solo están disponibles a través del enlace en tiempo de ejecución. En Visual Basic proyectos en los que **Option Strict** es OFF o en proyectos de Visual C# que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , puede usar las características de enlace en tiempo de ejecución de estos lenguajes para tener acceso a los miembros enlazados en tiempo de ejecución. En Visual Basic proyectos en los que **Option Strict** está activada, debe usar la reflexión para tener acceso a estos miembros.

### <a name="examples"></a>Ejemplos
 En el ejemplo de código siguiente se muestra cómo obtener acceso a los miembros enlazados en tiempo de ejecución en un proyecto de Visual Basic donde **Option Strict** es OFF o en un proyecto de Visual C# que tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . En este ejemplo se obtiene acceso a la propiedad de **nombre** enlazado en tiempo de ejecución del cuadro de diálogo **Abrir archivo** de Word. Para usar este ejemplo, ejecútelo desde la `ThisDocument` clase o `ThisAddIn` en un proyecto de Word.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 En el ejemplo de código siguiente se muestra cómo usar la reflexión para realizar la misma tarea en un proyecto Visual Basic donde **Option Strict** está activada.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Consulte también
- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Use la guía de programación de tipo Dynamic &#40;C&#35;&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Option Strict (instrucción)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflexión (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Reflexión [Visual Basic])
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
