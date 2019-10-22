---
title: 'Cómo: ejecutar una transformación XSLT desde el editor XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b305d88779603b374e5f95842d7a5271a657268
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666534"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Cómo: Ejecutar una transformación XSLT desde el Editor XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Editor XML permite asociar una hoja de estilos XSLT con un documento XML, realizar la transformación y ver el resultado. El resultado de la transformación XSLT se muestra en una nueva ventana de documento.

 La propiedad de **salida** especifica el nombre de archivo de la salida. Si la propiedad de **salida** está en blanco, se genera un nombre de archivo en el directorio temporal. La extensión de archivo se basa en el elemento `xsl:output` de la hoja de estilos y puede ser .xml, .txt o .htm.

 Si la propiedad de **salida** especifica un nombre de archivo con una extensión. htm o. html, se muestra una vista previa de la salida XSLT mediante [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer. Todas las demás extensiones de archivo se abren con el editor predeterminado que elija [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio. Por ejemplo, si la extensión de archivo es .xml, Visual Studio utiliza el Editor XML.

### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Para ejecutar una transformación XSLT desde un documento XML

1. Abra un documento XML en el Editor XML.

2. Asocie una hoja de estilos XSLT con el documento XML.

    - Agregue una instrucción de procesamiento `xml-stylesheet` al documento XML. Por ejemplo, agregue la siguiente línea `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` al prólogo del documento.

         o bien

    - Agregue la hoja de estilos XSLT mediante la ventana **propiedades** . En la **ventana Propiedades**del documento, haga clic en el botón **examinar** del campo **hoja de estilos** , seleccione la hoja de estilos XSLT y haga clic en **abrir**.

3. Haga clic en el botón **ShowXSL Output** en la barra de herramientas del **Editor XML** .

    > [!NOTE]
    > Si no hay ninguna hoja de estilos asociada con el documento XML, un cuadro de diálogo le pide que proporcione la hoja de estilos que desea utilizar.
    >
    >  El resultado de la transformación XSLT se muestra en una nueva ventana de documento.

### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Para ejecutar una transformación XSLT desde una hoja de estilos XSLT

1. Abra una hoja de estilos XSLT en el Editor XML.

2. Especifique un documento XML en el campo **entrada** de la ventana **propiedades** del documento.

    > [!NOTE]
    > El documento XML es el documento de entrada que se utiliza en la transformación. Si no se especifica un documento cuando se inicia la transformación XSLT, aparece el cuadro de diálogo **Abrir archivo** y puede especificar un documento en ese momento.

3. Haga clic en el botón **ShowXSLT Output** en la barra de herramientas del **Editor XML** .

     El resultado de la transformación XSLT se muestra en una nueva ventana de documento.

### <a name="to-provide-a-different-output-file-name"></a>Para proporcionar un nombre de archivo de salida diferente

1. Especifique un nombre de archivo en el campo de **salida** de la ventana **propiedades** del documento.

2. Haga clic en el botón **ShowXSLT Output** en la barra de herramientas del **Editor XML** .

     El resultado de la transformación XSLT se muestra en una nueva ventana de documento y el editor usado en la ventana de salida depende de la extensión de archivo de la propiedad de documento de **salida** .

## <a name="see-also"></a>Vea también
 [Editor XML](../xml-tools/xml-editor.md)
