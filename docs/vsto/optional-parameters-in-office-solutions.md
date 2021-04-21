---
title: Parámetros opcionales en soluciones de Office
description: Obtenga información sobre cómo no tiene que pasar un valor para los parámetros opcionales porque los valores predeterminados se usan automáticamente para cada parámetro que falta.
ms.custom: SEO-VS-2020
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9c95842ac2c6d77a2312ac5c4c197ba22ed2020e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825425"
---
# <a name="optional-parameters-in-office-solutions"></a>Parámetros opcionales en soluciones de Office
  Muchos de los métodos de los modelos de objetos de las aplicaciones de Microsoft Office aceptan parámetros opcionales. Si utiliza Visual Basic para desarrollar una solución de Office en Visual Studio, no es necesario pasar un valor para los parámetros opcionales, ya que se usan automáticamente los valores predeterminados para cada parámetro que falte. En la mayoría de los casos, también puede omitir los parámetros opcionales en los proyectos de Visual C#. Sin embargo, no puede omitir los parámetros **ref** opcionales de la clase en proyectos de `ThisDocument` Word de nivel de documento.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Para obtener más información sobre cómo trabajar con parámetros opcionales en proyectos de Visual C# y Visual Basic, vea [Argumentos ](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) opcionales y con nombre &#40;Guía de programación de C&#35;&#41;y Parámetros [opcionales &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).

> [!NOTE]
> En versiones anteriores de Visual Studio, tiene que pasar un valor para cada parámetro opcional en los proyectos de Visual C#. Por comodidad, estos proyectos incluyen una variable global denominada `missing` que puede pasar a un parámetro opcional cuando desee utilizar el valor predeterminado del parámetro. Los proyectos de Visual C# para Office en Visual Studio todavía incluyen la variable , pero normalmente no es necesario usarla al desarrollar soluciones de Office en , excepto cuando se llama a métodos con parámetros ref opcionales en la clase en proyectos de nivel de documento para `missing` [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]  `ThisDocument` Word.

## <a name="example-in-excel"></a>Ejemplo de Excel
 El método <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> tiene muchos parámetros opcionales. Puede especificar valores para algunos parámetros y aceptar el valor predeterminado de otros, como se muestra en el siguiente ejemplo de código. Este ejemplo requiere un proyecto de nivel de documento con una clase de hoja de cálculo denominada `Sheet1`.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb" id="Snippet1":::

## <a name="example-in-word"></a>Ejemplo de Word
 El método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> tiene muchos parámetros opcionales. Puede especificar valores para algunos parámetros y aceptar el valor predeterminado de otros, como se muestra en el siguiente ejemplo de código.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet1":::

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Usar parámetros opcionales de métodos en la clase ThisDocument en proyectos de nivel de documento de Visual C# para Word
 El modelo de objetos de Word contiene muchos métodos con parámetros **ref** opcionales que aceptan <xref:System.Object> valores. Sin embargo, no puede omitir los parámetros **ref** opcionales de los métodos de la clase generada en proyectos de nivel de documento `ThisDocument` de Visual C# para Word. Visual C# permite omitir parámetros **ref** opcionales solo para métodos de interfaces, no clases. Por ejemplo, el ejemplo de código siguiente no se compila, porque no se pueden omitir los parámetros **ref** opcionales <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> del método de la clase `ThisDocument` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet3":::

 Cuando llame a métodos de la clase `ThisDocument`, siga estas directrices:

- Para aceptar el valor predeterminado de un parámetro **ref** opcional, pase la `missing` variable al parámetro . La variable `missing` se define automáticamente en los proyectos de Office de Visual C# y se asigna al valor <xref:System.Type.Missing> en el código de proyecto generado.

- Para especificar su propio valor para un parámetro **ref** opcional, declare un objeto asignado al valor que desea especificar y, a continuación, pase el objeto al parámetro .

  En el ejemplo de código siguiente se muestra cómo llamar al método especificando un valor para el parámetro <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> *ignoreUppercase* y aceptando el valor predeterminado para los demás parámetros.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet4":::

  Si desea escribir código que omita los parámetros **ref** opcionales de un método de la clase , también puede llamar al mismo método en el objeto devuelto por la propiedad y omitir los parámetros de ese `ThisDocument` <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> método. Puede hacerlo porque <xref:Microsoft.Office.Interop.Word.Document> es una interfaz y no una clase.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet5":::

  Para obtener más información sobre los parámetros de tipo de referencia y valor, vea Pasar [argumentos ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) por valor y por referencia &#40;Visual Basic&#41;(para Visual Basic) y Pasar parámetros [&#40;C&#35; guía ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)de programación&#41;.

## <a name="see-also"></a>Consulte también
- [Desarrollo de soluciones de Office](../vsto/developing-office-solutions.md)
- [Escritura de código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
