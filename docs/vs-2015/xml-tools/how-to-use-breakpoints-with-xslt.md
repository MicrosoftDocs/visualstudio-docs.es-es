---
title: Procedimiento Utilizar puntos de interrupción con XSLT | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: df2fb0c6505bc5fa756443bd50fdb31ff151e7d7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65673677"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Procedimiento Utilizar puntos de interrupción con XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede establecer los puntos de interrupción en una hoja de estilos XSLT o en el documento de origen XML. Si establece un punto de interrupción en una etiqueta, cuando comienza la ejecución el punto de interrupción se traslada a la siguiente instrucción que tiene información de línea de código fuente.  
  
 Para obtener más información, consulte [Fundamentos de depuración: Los puntos de interrupción](https://msdn.microsoft.com/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).  
  
## <a name="set-a-breakpoint-in-a-style-sheet"></a>Establecer un punto de interrupción en una hoja de estilos  
 Se pueden establecer los puntos de interrupción en las etiquetas de apertura y de cierre, y en los nodos de texto de una hoja de estilos XSLT. También pueden establecerse en el código de un bloque de scripts.  
  
#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Para establecer un punto de interrupción en una hoja de estilos  
  
1. Abra una hoja de estilos en el Editor XML.  
  
2. Coloque el cursor en la ubicación del punto de interrupción, haga clic en, seleccione **punto de interrupción**y haga clic en **Insertar punto de interrupción**.  
  
3. Haga clic en el el botón Examinar (**...** ) en el **entrada** campo de la ventana de propiedades de documento.  
  
4. Busque el documento origen XML y haga clic en **abierto**.  
  
     De esta forma se establece el archivo del documento de origen que se utilizará para la transformación XSLT.  
  
5. Haga clic en el **Depurar XSL** en la barra de herramientas del Editor XML.  
  
## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Establecer un punto de interrupción en un documento de origen XML  
 Pueden establecerse puntos de interrupción en los elementos, atributos, nodos de espacio de nombres, comentarios, instrucciones de procesamiento y nodos de texto de un documento de origen XML. No puede establecerse un punto de interrupción en el nodo de documentos ni en un nodo de espacio de nombres heredado del elemento primario.  
  
#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Para establecer un punto de interrupción en un documento de origen XML  
  
1. Abra el documento XML en el Editor XML.  
  
2. Coloque el cursor en la ubicación del punto de interrupción, haga clic en, seleccione **punto de interrupción**y haga clic en **Insertar punto de interrupción**.  
  
3. Haga clic en el el botón Examinar (**...** ) en el **Stylesheet** campo de la ventana de propiedades de documento.  
  
4. Busque el documento origen XML y haga clic en **abierto**.  
  
     De esta forma se establece el archivo del documento de origen que se utilizará para la transformación XSLT.  
  
5. Haga clic en el **Depurar XSL** en la barra de herramientas del Editor XML.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Depuración de una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
