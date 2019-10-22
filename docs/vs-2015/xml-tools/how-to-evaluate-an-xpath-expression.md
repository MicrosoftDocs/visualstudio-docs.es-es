---
title: 'Cómo: evaluar una expresión XPath | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ecec9004506a9bd05d3d773e44bb264af363f96f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670864"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Cómo: Evaluar una expresión XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede evaluar las expresiones XPath con el cuadro de diálogo **Inspección rápida** . La expresión XPath debe ser válida de acuerdo con la recomendación XPath 1.0 de W3C. El contexto XSLT actual (es decir, el nodo `self::node()` en la ventana **variables locales** ) proporciona el contexto de evaluación para la expresión XPath.

 En la siguiente lista se describen las funciones que se admiten al evaluar una expresión XPath:

- Se admiten funciones XPath integradas.

- No se admiten funciones XSLT integradas.

- No se admiten funciones definidas por el usuario.

> [!NOTE]
> En el procedimiento siguiente se usan los archivos belowAvg. xsl y Books. xml del tema [Tutorial: depurar una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) .

### <a name="to-evaluate-an-xpath-expression"></a>Para evaluar una expresión XPath

1. Inserte un punto de interrupción en la etiqueta de apertura `xsl:if`.

2. Haga clic en el botón **depurar XSL** en la barra de herramientas del editor XML.

     Se inicia el depurador y se interrumpe en la etiqueta `xsl:if`.

3. Haga clic con el botón derecho y seleccione **Inspección rápida**.

     Se muestra el cuadro de diálogo **Inspección rápida** .

4. Escriba `./price/text()` en el campo **expresión** del cuadro de diálogo **Inspección rápida** y haga clic en volver a **evaluar**.

     El precio del nodo de libro actual aparece en el cuadro **valor** .

5. Cambie la expresión XPath a `./price/text() < $bookAverage` y haga clic en volver a **evaluar**.

     El cuadro **valor** muestra que la expresión XPath se evalúa como `true`.

## <a name="see-also"></a>Vea también
 [Depuración de XSLT](../xml-tools/debugging-xslt.md)
