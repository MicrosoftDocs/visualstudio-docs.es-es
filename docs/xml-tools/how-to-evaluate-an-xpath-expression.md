---
title: 'Cómo: Evaluar una expresión XPath'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02492f2e1760df3ce5cd6751808303bae75577e2
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Cómo: Evaluar una expresión XPath

Puede evaluar expresiones XPath con el **Inspección rápida** cuadro de diálogo. La expresión XPath debe ser válida de acuerdo con la recomendación XPath 1.0 de W3C. El contexto XSLT actual, es decir, el `self::node()` nodo en el **locales** ventana: proporciona el contexto de evaluación para la expresión XPath.

 En la siguiente lista se describen las funciones que se admiten al evaluar una expresión XPath:

-   Se admiten funciones XPath integradas.

-   No se admiten funciones XSLT integradas.

-   No se admiten funciones definidas por el usuario.

> [!NOTE]
> El siguiente procedimiento usa el *belowAvg.xsl* y *books.xml* archivos desde el [Tutorial: depurar una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) tema.

## <a name="to-evaluate-an-xpath-expression"></a>Para evaluar una expresión XPath

1.  Inserte un punto de interrupción en la etiqueta de apertura `xsl:if`.

2.  Haga clic en el **Depurar XSL** botón en la barra de herramientas del Editor XML.

     Se inicia el depurador y se interrumpe en la etiqueta `xsl:if`.

3.  Haga clic en y seleccione **Inspección rápida**.

     El **Inspección rápida** se muestra el cuadro de diálogo.

4.  Escriba `./price/text()` en el **expresión** campo de la **Inspección rápida** cuadro de diálogo y haga clic en **actualizar**.

     El precio del nodo de libro actual aparece en la **valor** cuadro.

5.  Cambie la expresión XPath para `./price/text() < $bookAverage` y haga clic en **actualizar**.

     El **valor** cuadro muestra que la expresión XPath se evalúa como `true`.

## <a name="see-also"></a>Vea también

- [Depuración de XSLT](../xml-tools/debugging-xslt.md)