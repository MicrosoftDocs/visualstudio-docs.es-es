---
title: Procedimiento Utilizar puntos de interrupción con XSLT
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a569e3bc9d467b1cfce16d3836fdd1bb2a86e1c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013696"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Procedimiento Utilizar puntos de interrupción con XSLT

Puede establecer los puntos de interrupción en una hoja de estilos XSLT o en el documento de origen XML. Si establece un punto de interrupción en una etiqueta, cuando comienza la ejecución el punto de interrupción se traslada a la siguiente instrucción que tiene información de línea de código fuente.

Para obtener más información, consulte [Fundamentos de la depuración: Los puntos de interrupción](../debugger/using-breakpoints.md).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Establecer un punto de interrupción en una hoja de estilos

Se pueden establecer los puntos de interrupción en las etiquetas de apertura y de cierre, y en los nodos de texto de una hoja de estilos XSLT. También pueden establecerse en el código de un bloque de scripts.

### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Para establecer un punto de interrupción en una hoja de estilos

1.  Abra una hoja de estilos en el Editor XML.

2.  Coloque el cursor en la ubicación del punto de interrupción, haga clic en, seleccione **punto de interrupción**y haga clic en **Insertar punto de interrupción**.

3.  Haga clic en el botón Examinar (**...** ) en el **entrada** campo de la ventana de propiedades de documento.

4.  Busque el documento origen XML y haga clic en **abierto**.

     De esta forma se establece el archivo del documento de origen que se utilizará para la transformación XSLT.

5.  Haga clic en el **Depurar XSL** en la barra de herramientas del Editor XML.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Establezca un punto de interrupción en un documento de origen XML

Pueden establecerse puntos de interrupción en los elementos, atributos, nodos de espacio de nombres, comentarios, instrucciones de procesamiento y nodos de texto de un documento de origen XML. No puede establecerse un punto de interrupción en el nodo de documentos ni en un nodo de espacio de nombres heredado del elemento primario.

### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Para establecer un punto de interrupción en un documento de origen XML

1.  Abra el documento XML en el Editor XML.

2.  Coloque el cursor en la ubicación del punto de interrupción, haga clic en, seleccione **punto de interrupción**y haga clic en **Insertar punto de interrupción**.

3.  Haga clic en el botón Examinar (**...** ) en el **Stylesheet** campo de la ventana de propiedades de documento.

4.  Busque el documento origen XML y haga clic en **abierto**.

     De esta forma se establece el archivo del documento de origen que se utilizará para la transformación XSLT.

5.  Haga clic en el **Depurar XSL** en la barra de herramientas del Editor XML.

## <a name="see-also"></a>Vea también

- [Tutorial: Depurar una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)