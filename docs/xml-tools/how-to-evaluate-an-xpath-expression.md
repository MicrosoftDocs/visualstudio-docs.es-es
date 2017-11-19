---
title: "Cómo: evaluar una expresión XPath | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d549afb96465590a21e516f649d860f23f4056f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Cómo: Evaluar una expresión XPath
Puede evaluar expresiones XPath con el **Inspección rápida** cuadro de diálogo. La expresión XPath debe ser válida de acuerdo con la recomendación XPath 1.0 de W3C. El contexto XSLT actual, es decir, el `self::node()` nodo en el **locales** ventana: proporciona el contexto de evaluación para la expresión XPath.  
  
 En la siguiente lista se describen las funciones que se admiten al evaluar una expresión XPath:  
  
-   Se admiten funciones XPath integradas.  
  
-   No se admiten funciones XSLT integradas.  
  
-   No se admiten funciones definidas por el usuario.  
  
> [!NOTE]
>  El siguiente procedimiento usa los archivos belowAvg.xsl y books.xml desde el [Tutorial: depurar una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) tema.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Para evaluar una expresión XPath  
  
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
 [Depuración de XSLT](../xml-tools/debugging-xslt.md)