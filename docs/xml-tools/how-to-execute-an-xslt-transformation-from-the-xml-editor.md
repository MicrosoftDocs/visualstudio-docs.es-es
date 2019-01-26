---
title: Procedimiento Ejecutar una transformación XSLT desde el Editor XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 742e78eca883dd2e9e9fc5ecfa8ec5381f003b61
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987575"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Procedimiento Ejecutar una transformación XSLT desde el Editor XML

El Editor XML permite asociar una hoja de estilos XSLT con un documento XML, realizar la transformación y ver el resultado. El resultado de la transformación XSLT se muestra en una nueva ventana de documento.

El **salida** propiedad especifica el nombre de archivo para la salida. Si el **salida** propiedad está en blanco, se genera un nombre de archivo en el directorio temporal. La extensión de archivo se basa en el `xsl:output` elemento en su estilo de hoja y puede ser. *XML*,. *txt* o. *htm*.

Si el **salida** propiedad especifica un nombre de archivo con un. *htm* o. *HTML* extensión, el resultado XSLT es una vista previa con [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Internet Explorer. Todas las demás extensiones de archivo se abren con el editor predeterminado que elija [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio. Por ejemplo, si es la extensión de archivo. *xml*, Visual Studio utiliza el Editor XML.

## <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Para ejecutar una transformación XSLT desde un documento XML

1.  Abra un documento XML en el Editor XML.

2.  Asocie una hoja de estilos XSLT con el documento XML.

    -   Agregue una instrucción de procesamiento `xml-stylesheet` al documento XML. Por ejemplo, agregue la siguiente línea `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` al prólogo del documento.

         O bien

    -   Agregar hoja de estilos XSLT mediante la **propiedades** ventana. En el documento **ventana propiedades**, haga clic en el **examinar** botón el **Stylesheet** campo, seleccione la hoja de estilos XSLT y haga clic en **abrir**.

3.  Haga clic en el **ShowXSL salida** situado en la **Editor XML** barra de herramientas.

    > [!NOTE]
    > Si no hay ninguna hoja de estilos asociada con el documento XML, un cuadro de diálogo le pide que proporcione la hoja de estilos que desea utilizar.
    >
    >  El resultado de la transformación XSLT se muestra en una nueva ventana de documento.

## <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Para ejecutar una transformación XSLT desde una hoja de estilos XSLT

1.  Abra una hoja de estilos XSLT en el Editor XML.

2.  Especifique un documento XML en el **entrada** campo del documento **propiedades** ventana.

    > [!NOTE]
    > El documento XML es el documento de entrada que se utiliza en la transformación. Si no se especifica un documento cuando se inicia la transformación XSLT, el **abrir archivo** aparece el cuadro de diálogo, y puede especificar un documento en ese momento.

3.  Haga clic en el **ShowXSLT salida** situado en la **Editor XML** barra de herramientas.

     El resultado de la transformación XSLT se muestra en una nueva ventana de documento.

## <a name="to-provide-a-different-output-file-name"></a>Para proporcionar un nombre de archivo de salida diferente

1.  Especifique un nombre de archivo en el **salida** campo del documento **propiedades** ventana.

2.  Haga clic en el **ShowXSLT salida** situado en la **Editor XML** barra de herramientas.

     La salida resultante de la transformación XSLT se muestra en una nueva ventana de documento y el editor que se usa en la ventana de salida depende de la extensión de archivo de su **salida** propiedad de documento.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)