---
title: Filtrar Evaluar una expresión XPath | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 77c9acae710baeb885bcf901257367251d86c3a2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999647"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Filtrar Evaluar una expresión XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede evaluar expresiones XPath con el **Inspección rápida** cuadro de diálogo. La expresión XPath debe ser válida de acuerdo con la recomendación XPath 1.0 de W3C. El contexto XSLT actual, es decir, el `self::node()` nodo en el **variables locales** ventana, proporciona el contexto de evaluación para la expresión XPath.  
  
 En la siguiente lista se describen las funciones que se admiten al evaluar una expresión XPath:  
  
-   Se admiten funciones XPath integradas.  
  
-   No se admiten funciones XSLT integradas.  
  
-   No se admiten funciones definidas por el usuario.  
  
> [!NOTE]
>  El siguiente procedimiento utiliza los archivos belowAvg.xsl y books.xml desde el [Tutorial: Depurar una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) tema.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Para evaluar una expresión XPath  
  
1.  Inserte un punto de interrupción en la etiqueta de apertura `xsl:if`.  
  
2.  Haga clic en el **Depurar XSL** en la barra de herramientas del Editor XML.  
  
     Se inicia el depurador y se interrumpe en la etiqueta `xsl:if`.  
  
3.  Haga clic en y seleccione **Inspección rápida**.  
  
     El **Inspección rápida** se muestra el cuadro de diálogo.  
  
4.  Escriba `./price/text()` en el **expresión** campo de la **Inspección rápida** cuadro de diálogo y haga clic en **volver a evaluar**.  
  
     El precio del nodo de libro actual aparece en el **valor** cuadro.  
  
5.  Cambie la expresión XPath para `./price/text() < $bookAverage` y haga clic en **volver a evaluar**.  
  
     El **valor** cuadro muestra que la expresión XPath se evalúa como `true`.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de XSLT](../xml-tools/debugging-xslt.md)
