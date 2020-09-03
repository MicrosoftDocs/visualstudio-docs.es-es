---
title: 'Cómo: utilizar puntos de interrupción con XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0519c3ab19e7d36aa26ea2f462c8a4571b9f8b32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656307"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Cómo: Utilizar puntos de interrupción con XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede establecer los puntos de interrupción en una hoja de estilos XSLT o en el documento de origen XML. Si establece un punto de interrupción en una etiqueta, cuando comienza la ejecución el punto de interrupción se traslada a la siguiente instrucción que tiene información de línea de código fuente.

 Para obtener más información, vea [conceptos básicos de depuración: puntos de interrupción](https://msdn.microsoft.com/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Establecer un punto de interrupción en una hoja de estilos
 Se pueden establecer los puntos de interrupción en las etiquetas de apertura y de cierre, y en los nodos de texto de una hoja de estilos XSLT. También pueden establecerse en el código de un bloque de scripts.

#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Para establecer un punto de interrupción en una hoja de estilos

1. Abra una hoja de estilos en el Editor XML.

2. Coloque el cursor en la ubicación del punto de interrupción, haga clic con el botón secundario, seleccione punto de **interrupción**y haga clic en **Insertar punto de interrupción**.

3. Haga clic en el botón Examinar (**...**) del campo de **entrada** de la ventana Propiedades del documento.

4. Busque el documento de origen XML y haga clic en **abrir**.

     De esta forma se establece el archivo del documento de origen que se utilizará para la transformación XSLT.

5. Haga clic en el botón **depurar XSL** en la barra de herramientas del editor XML.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Establecer un punto de interrupción en un documento de origen XML
 Pueden establecerse puntos de interrupción en los elementos, atributos, nodos de espacio de nombres, comentarios, instrucciones de procesamiento y nodos de texto de un documento de origen XML. No puede establecerse un punto de interrupción en el nodo de documentos ni en un nodo de espacio de nombres heredado del elemento primario.

#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Para establecer un punto de interrupción en un documento de origen XML

1. Abra el documento XML en el Editor XML.

2. Coloque el cursor en la ubicación del punto de interrupción, haga clic con el botón secundario, seleccione punto de **interrupción**y haga clic en **Insertar punto de interrupción**.

3. Haga clic en el botón Examinar (**...**) del campo **hoja de estilos** de la ventana Propiedades del documento.

4. Busque el documento de origen XML y haga clic en **abrir**.

     De esta forma se establece el archivo del documento de origen que se utilizará para la transformación XSLT.

5. Haga clic en el botón **depurar XSL** en la barra de herramientas del editor XML.

## <a name="see-also"></a>Consulte también
 [Tutorial: depurar una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
