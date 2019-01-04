---
title: Parámetros opcionales en las soluciones de Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 34f19c7fa27893b071251f61d01f2dd9c9809d3b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905103"
---
# <a name="optional-parameters-in-office-solutions"></a>Parámetros opcionales en las soluciones de Office
  Muchos de los métodos de los modelos de objetos de las aplicaciones de Microsoft Office aceptan parámetros opcionales. Si utiliza Visual Basic para desarrollar una solución de Office en Visual Studio, no es necesario pasar un valor para los parámetros opcionales, ya que se usan automáticamente los valores predeterminados para cada parámetro que falte. En la mayoría de los casos, también puede omitir los parámetros opcionales en los proyectos de Visual C#. Sin embargo, no se puede omitir opcional **ref** parámetros de la `ThisDocument` clase en proyectos de nivel de documento de Word.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Para obtener más información sobre cómo trabajar con los parámetros opcionales en los proyectos de Visual C# y Visual Basic, vea [argumentos opcionales y con nombre &#40;C&#35; Guía de programación&#41; ](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) y [ &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).  
  
> [!NOTE]  
>  En versiones anteriores de Visual Studio, tiene que pasar un valor para cada parámetro opcional en los proyectos de Visual C#. Por comodidad, estos proyectos incluyen una variable global denominada `missing` que puede pasar a un parámetro opcional cuando desee utilizar el valor predeterminado del parámetro. Proyectos de C# para Office en Visual Studio todavía incluyen la `missing` variable, pero normalmente no es necesario usar al desarrollar soluciones de Office en [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], excepto cuando se llama a métodos con opcional **ref** los parámetros en la `ThisDocument` clase en los proyectos de nivel de documento para Word.  
  
## <a name="example-in-excel"></a>Ejemplo de Excel  
 El método <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> tiene muchos parámetros opcionales. Puede especificar valores para algunos parámetros y aceptar el valor predeterminado de otros, como se muestra en el siguiente ejemplo de código. Este ejemplo requiere un proyecto de nivel de documento con una clase de hoja de cálculo denominada `Sheet1`.  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]  
  
## <a name="example-in-word"></a>Ejemplo de Word  
 El método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> tiene muchos parámetros opcionales. Puede especificar valores para algunos parámetros y aceptar el valor predeterminado de otros, como se muestra en el siguiente ejemplo de código.  
  
 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]  
  
## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Usar parámetros opcionales de métodos en la clase ThisDocument en proyectos de nivel de documento de Visual C# para Word  
 El modelo de objetos de Word contiene muchos métodos con opcional **ref** los parámetros que aceptan <xref:System.Object> valores. Sin embargo, no se puede omitir opcional **ref** parámetros de métodos de generado `ThisDocument` clase en Visual C# proyectos de nivel de documento para Word. Visual C# permite omitir opcional **ref** parámetros solo para los métodos de interfaces, no clases. Por ejemplo, el siguiente ejemplo de código no se compila, porque no se pueden omitir opcional **ref** parámetros de la <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> método de la `ThisDocument` clase.  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]  
  
 Cuando llame a métodos de la clase `ThisDocument`, siga estas directrices:  
  
- Para aceptar el valor predeterminado de un elemento opcional **ref** parámetro, pase el `missing` variable al parámetro. La variable `missing` se define automáticamente en los proyectos de Office de Visual C# y se asigna al valor <xref:System.Type.Missing> en el código de proyecto generado.  
  
- Para especificar su propio valor para un elemento opcional **ref** parámetro, declare un objeto que se asigna al valor que desee especificar y, a continuación, pase el objeto al parámetro.  
  
  En el ejemplo de código siguiente se muestra cómo llamar a la <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> método especificando un valor para el *ignoreUppercase* parámetro y aceptar el valor predeterminado para los demás parámetros.  
  
  [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]  
  
  Si desea escribir código que omita opcional **ref** parámetros de un método en el `ThisDocument` (clase), o bien puede llamar al mismo método en el <xref:Microsoft.Office.Interop.Word.Document> objeto devuelto por la <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> propiedad y se omite el parámetros de ese método. Puede hacerlo porque <xref:Microsoft.Office.Interop.Word.Document> es una interfaz y no una clase.  
  
  [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]  
  
  Para obtener más información acerca de los parámetros de tipo de valor y de referencia, consulte [pasar argumentos por valor y por referencia &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (para Visual Basic) y [pasar parámetros &#40;C&#35; Guía de programación&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)  
