---
title: "Par&#225;metros opcionales en las soluciones de Office | Microsoft Docs"
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
  - "desarrollo de aplicaciones [desarrollo de Office en Visual Studio], parámetros opcionales"
  - "campo que falta [desarrollo de Office en Visual Studio]"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], parámetros opcionales"
  - "parámetros opcionales [desarrollo de Office en Visual Studio]"
  - "parámetros [desarrollo de Office en Visual Studio], opcionales"
  - "Visual Basic [desarrollo de Office en Visual Studio], parámetros opcionales"
  - "Visual C# [desarrollo de Office en Visual Studio], parámetros opcionales"
ms.assetid: 109eaef6-08bb-4b59-a29e-921f856027cc
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Par&#225;metros opcionales en las soluciones de Office
  Muchos de los métodos de los modelos de objetos de las aplicaciones de Microsoft Office aceptan parámetros opcionales.  Si utiliza Visual Basic para desarrollar una solución de Office en Visual Studio, no es necesario pasar un valor para los parámetros opcionales, ya que se usan automáticamente los valores predeterminados para cada parámetro que falte.  En la mayoría de los casos, también puede omitir los parámetros opcionales en los proyectos de Visual C\#. Sin embargo, no puede omitir los parámetros **ref** opcionales de la clase `ThisDocument` en proyectos de Word de nivel de documento.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Para obtener más información sobre el trabajo con parámetros opcionales en los proyectos de Visual C\# y Visual Basic, vea [Argumentos opcionales y con nombre &#40;Guía de programación de C&#35;&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) y [Parámetros opcionales &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).  
  
> [!NOTE]  
>  En versiones anteriores de Visual Studio, tiene que pasar un valor para cada parámetro opcional en los proyectos de Visual C\#.  Por comodidad, estos proyectos incluyen una variable global denominada `missing` que puede pasar a un parámetro opcional cuando desee utilizar el valor predeterminado del parámetro.  Los proyectos de Visual C\# para Office en Visual Studio todavía incluyen la variable `missing`, pero normalmente no es necesario usarla cuando se desarrollan soluciones de Office en [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], excepto cuando se llama a métodos con parámetros **ref** opcionales en la clase `ThisDocument` en proyectos de nivel de documento para Word.  
  
## Ejemplo de Excel  
 El método <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> tiene muchos parámetros opcionales.  Puede especificar valores para algunos parámetros y aceptar el valor predeterminado de otros, como se muestra en el siguiente ejemplo de código.  Este ejemplo requiere un proyecto de nivel de documento con una clase de hoja de cálculo denominada `Sheet1`.  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/VB/Sheet1.vb#1)]  
  
## Ejemplo de Word  
 El método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> tiene muchos parámetros opcionales.  Puede especificar valores para algunos parámetros y aceptar el valor predeterminado de otros, como se muestra en el siguiente ejemplo de código.  
  
 [!code-csharp[Trin_VstrefGeneralWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstrefGeneralWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/VB/ThisDocument.vb#1)]  
  
## Usar parámetros opcionales de métodos en la clase ThisDocument en proyectos de nivel de documento de Visual C\# para Word  
 El modelo de objetos de Word contiene muchos métodos con parámetros **ref** opcionales que aceptan valores <xref:System.Object>.  Sin embargo, no puede omitir los parámetros **ref** opcionales de métodos de la clase `ThisDocument` generada en proyectos de nivel de documento de Visual C\# para Word.  Visual C\# permite omitir parámetros **ref** opcionales solo para los métodos de las interfaces, no las clases.  Por ejemplo, en el siguiente ejemplo de código no se compila, porque no se pueden omitir los parámetros **ref** opcionales del método <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> de la clase `ThisDocument`.  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#3)]  
  
 Cuando llame a métodos de la clase `ThisDocument`, siga estas directrices:  
  
-   Para aceptar el valor predeterminado de un parámetro **ref** opcional, pase la variable `missing` al parámetro.  La variable `missing` se define automáticamente en los proyectos de Office de Visual C\# y se asigna al valor <xref:System.Type.Missing> en el código de proyecto generado.  
  
-   Para especificar su propio valor para un parámetro **ref** opcional, declare un objeto asignado al valor que desee especificar y, a continuación, pase el objeto al parámetro.  
  
 En el ejemplo de código siguiente se muestra cómo llamar al método <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> especificando un valor para el parámetro *ignoreUppercase* y aceptando el valor predeterminado para los otros parámetros.  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#4)]  
  
 Si desea escribir código que omita los parámetros **ref** opcionales de un método de la clase `ThisDocument`, también puede llamar al mismo método en el objeto <xref:Microsoft.Office.Interop.Word.Document> devuelto por la propiedad <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> y omitir los parámetros de ese método.  Puede hacerlo porque <xref:Microsoft.Office.Interop.Word.Document> es una interfaz y no una clase.  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#5)]  
  
 Para obtener más información acerca de los parámetros de tipo de valor y de referencia, vea [Pasar argumentos por valor y por referencia &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) \(para Visual Basic\) y [Pasar parámetros &#40;Guía de programación de C&#35;&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Vea también  
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)  
  
  