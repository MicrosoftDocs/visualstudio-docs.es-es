---
title: Enlace en tiempo de tarde en soluciones de Office
description: Obtenga información sobre cómo algunos tipos de modelos de objetos Microsoft Office proporcionan funcionalidad que está disponible a través de características de enlace en tiempo de ejecución.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e618dcd0cc699b4626f825890cf0fc8bd7ddd853
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823891"
---
# <a name="late-binding-in-office-solutions"></a>Enlace en tiempo de tarde en soluciones de Office
  Algunos tipos de los modelos de objetos de las aplicaciones de Office proporcionan funcionalidad que está disponible a través de características de enlace en tiempo de ejecución. Por ejemplo, algunos métodos y propiedades pueden devolver distintos tipos de objetos en función del contexto de la aplicación de Office, y algunos tipos pueden exponer diferentes métodos o propiedades en contextos diferentes.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual Basic proyectos en los que **Option Strict** está desactivado y los proyectos de Visual C# que tienen como destino o pueden funcionar directamente con tipos que emplean estas características de enlace en tiempo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] de [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] tarde.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Conversión implícita y explícita de valores devueltos de objetos
 Muchos métodos y propiedades de Microsoft Office ensamblados de interoperabilidad primarios (PIA) devuelven valores, ya que pueden devolver varios <xref:System.Object> tipos diferentes de objetos. Por ejemplo, la propiedad devuelve porque su valor devuelto puede ser un objeto <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> <xref:System.Object> o , <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Chart> dependiendo de cuál sea la hoja activa.

 Cuando un método o propiedad devuelve , debe convertir explícitamente (en Visual Basic) el objeto al tipo correcto en los proyectos de Visual Basic en los que <xref:System.Object> **Option Strict** está en . No es necesario convertir explícitamente valores devueltos en <xref:System.Object> Visual Basic donde Option **Strict** está desactivado.

 En la mayoría de los casos, la documentación de referencia enumera los posibles tipos del valor devuelto para un miembro que devuelve <xref:System.Object> . Convertir o convertir el objeto habilita IntelliSense para el objeto en el Editor de código.

 Para obtener información sobre la conversión en Visual Basic, vea [Implicit and explicit conversions &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) and [CType function &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).

### <a name="examples"></a>Ejemplos
 En el ejemplo de código siguiente se muestra cómo convertir un objeto a un tipo específico en un proyecto de Visual Basic donde **Option Strict** está en . En este tipo de proyecto, debe convertir explícitamente la <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> propiedad en <xref:Microsoft.Office.Interop.Excel.Range> . Este ejemplo requiere un proyecto de Excel de nivel de documento con una clase de hoja de cálculo denominada `Sheet1` .

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet9":::

 En el ejemplo de código siguiente se muestra cómo convertir implícitamente un objeto a un tipo específico en un proyecto de Visual Basic donde **Option Strict** está desactivado o en un proyecto de Visual C# que tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . En estos tipos de proyectos, la propiedad se convierte <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> implícitamente en <xref:Microsoft.Office.Interop.Excel.Range> . Este ejemplo requiere un proyecto de Excel de nivel de documento con una clase de hoja de cálculo denominada `Sheet1` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet10":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="access-members-that-are-available-only-through-late-binding"></a>Acceso a miembros que solo están disponibles a través del enlace en tiempo de tarde
 Algunas propiedades y métodos de los PIA de Office solo están disponibles a través del enlace en tiempo de tarde. En Visual Basic proyectos en los que **Option Strict** está desactivado o en proyectos de Visual C# que tienen como destino o , puede usar las características de enlace en tiempo de tarde en estos lenguajes para acceder a los miembros enlazados en tiempo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] de [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] lectura. En Visual Basic proyectos en los **que Option Strict** está en , debe usar la reflexión para acceder a estos miembros.

### <a name="examples"></a>Ejemplos
 En el ejemplo de código siguiente se muestra cómo acceder a los miembros enlazados en tiempo de ejecución en un proyecto de Visual Basic donde **Option Strict** está desactivado o en un proyecto de Visual C# que tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . En este ejemplo se accede a la propiedad **Name** enlazada en tiempo de tiempo del **cuadro de diálogo** Abrir archivo en Word. Para usar este ejemplo, ejecute desde la clase `ThisDocument` o en un proyecto de `ThisAddIn` Word.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 En el ejemplo de código siguiente se muestra cómo usar la reflexión para realizar la misma tarea en un proyecto de Visual Basic donde **Option Strict** está en .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>Consulte también
- [Escritura de código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Uso de la guía de programación de &#40;de&#35; C&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Instrucción Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflexión (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Reflexión [Visual Basic])
- [Diseño y creación de soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
