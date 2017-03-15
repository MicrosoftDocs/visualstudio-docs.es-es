---
title: "C&#243;mo: Evaluar una expresi&#243;n XPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# C&#243;mo: Evaluar una expresi&#243;n XPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede evaluar expresiones XPath con el cuadro de diálogo **Inspección rápida**.La expresión XPath debe ser válida de acuerdo con la recomendación XPath 1.0 de W3C.El contexto de XSLT actual, es decir, el nodo `self::node()` de la ventana **Locales**, proporciona el contexto de evaluación para la expresión XPath.  
  
 En la siguiente lista se describen las funciones que se admiten al evaluar una expresión XPath:  
  
-   Se admiten funciones XPath integradas.  
  
-   No se admiten funciones XSLT integradas.  
  
-   No se admiten funciones definidas por el usuario.  
  
> [!NOTE]
>  En el siguiente procedimiento se utilizan los archivos belowAvg.xsl y books.xml del tema [Tutorial: Depurar una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md).  
  
### Para evaluar una expresión XPath  
  
1.  Inserte un punto de interrupción en la etiqueta de apertura `xsl:if`.  
  
2.  Haga clic en el botón **Depurar XSL** en la barra de herramientas del Editor XML.  
  
     Se inicia el depurador y se interrumpe en la etiqueta `xsl:if`.  
  
3.  Haga clic con el botón secundario y seleccione **Inspección rápida**.  
  
     Aparece el cuadro de diálogo **Inspección rápida**.  
  
4.  Escriba `./price/text()` en el campo **Expresión** del cuadro de diálogo **Inspección rápida** y haga clic en **Volver a evaluar**.  
  
     El precio del nodo de libro actual aparece en el cuadro **Valor**.  
  
5.  Cambie la expresión XPath a `./price/text() < $bookAverage` y haga clic en **Volver a evaluar**.  
  
     El cuadro **Valor** muestra que la expresión XPath se evalúa como `true`.  
  
## Vea también  
 [Depuración de XSLT](../xml-tools/debugging-xslt.md)