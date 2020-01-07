---
title: Evaluar una expresión XPath durante la depuración
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e0b6c84fa9447dc38aa7976fa59bb5aa67d5c3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592729"
---
# <a name="evaluate-xpath-expressions"></a>Evaluar expresiones XPath

Puede evaluar las expresiones XPath mediante la ventana **Inspección rápida** durante la depuración. La expresión XPath debe ser válida de acuerdo con la recomendación XPath 1.0 de W3C. El contexto XSLT actual (es decir, el nodo `self::node()` en la ventana **variables locales** ) proporciona el contexto de evaluación para la expresión XPath.

Al evaluar una expresión XPath:

- Se admiten funciones XPath integradas.

- No se admiten funciones XSLT integradas ni funciones definidas por el usuario.

> [!NOTE]
> La depuración XSLT solo está disponible en la edición Enterprise de Visual Studio.

## <a name="evaluate-an-xpath-expression"></a>Evaluación de una expresión XPath

En el procedimiento siguiente se usan los archivos *below-Average. xsl* y *books. XML* de la página [Tutorial: depurar una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) .

1. Inserte un punto de interrupción en la etiqueta de apertura `xsl:if`.

2. Para iniciar la depuración, elija **XML** > **iniciar depuración de XSLT** en la barra de menús (o presione **Alt**+**F5**).

   Se inicia el depurador y se interrumpe en la etiqueta `xsl:if`.

3. Haga clic con el botón derecho y seleccione **Inspección rápida**.

   Se abre la ventana **Inspección rápida** .

4. Escriba `./price/text()` en el campo **expresión** del cuadro de diálogo **Inspección rápida** y, a continuación, elija volver a **evaluar**.

   El precio del nodo de libro actual aparece en el cuadro **valor** .

   ![Evaluar una expresión XPath en la ventana Inspección rápida](media/quickwatch-price.png)

5. Cambie la expresión XPath a `./price/text() < $bookAverage` y haga clic en volver a **evaluar**.

   El cuadro **valor** muestra que la expresión XPath se evalúa como `true`.

## <a name="see-also"></a>Vea también

- [Depuración de XSLT](../xml-tools/debugging-xslt.md)
