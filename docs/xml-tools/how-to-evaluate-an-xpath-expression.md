---
title: Evaluar una expresión XPath durante la depuración
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1585b54d084e3471583f9388d63f5c17e65fc3a7
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526327"
---
# <a name="evaluate-xpath-expressions"></a>Evaluar las expresiones XPath

Puede evaluar expresiones XPath utilizando el **Inspección rápida** ventana durante la depuración. La expresión XPath debe ser válida de acuerdo con la recomendación XPath 1.0 de W3C. El contexto XSLT actual (es decir, el `self::node()` nodo en el **variables locales** ventana) proporciona el contexto de evaluación para la expresión XPath.

Al evaluar una expresión XPath:

- Se admiten funciones XPath integradas.

- No se admiten funciones XSLT integradas y funciones definidas por el usuario.

> [!NOTE]
> Depuración de XSLT solo está disponible en la edición Enterprise de Visual Studio.

## <a name="evaluate-an-xpath-expression"></a>Evaluar una expresión XPath

El siguiente procedimiento usa la *debajo average.xsl* y *books.xml* archivos desde el [Tutorial: Depurar una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) página.

1. Inserte un punto de interrupción en la etiqueta de apertura `xsl:if`.

2. Para iniciar la depuración, elija **XML** > **iniciar la depuración de XSLT** en la barra de menús (o presione **Alt**+**F5** ).

   Se inicia el depurador y se interrumpe en la etiqueta `xsl:if`.

3. Haga clic en y seleccione **Inspección rápida**.

   El **Inspección rápida** abre la ventana.

4. Escriba `./price/text()` en el **expresión** campo de la **Inspección rápida** diálogo cuadro y, a continuación, elija **volver a evaluar**.

   El precio del nodo de libro actual aparece en el **valor** cuadro.

   ![Evaluar una expresión XPath en la ventana Inspección rápida](media/quickwatch-price.png)

5. Cambie la expresión XPath para `./price/text() < $bookAverage` y haga clic en **volver a evaluar**.

   El **valor** cuadro muestra que la expresión XPath se evalúa como `true`.

## <a name="see-also"></a>Vea también

- [Depuración de XSLT](../xml-tools/debugging-xslt.md)