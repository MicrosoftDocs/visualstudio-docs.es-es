---
title: Ejecutar una transformación XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e84b1c6303da4c0db39da1b3585a7d4548560feb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001939"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Procedimiento Ejecución de una transformación XSLT desde el editor XML

El editor XML permite asociar una hoja de estilos XSLT a un documento XML, realizar la transformación y ver la salida. El resultado de la transformación XSLT se muestra en una nueva ventana de documento.

El **salida** propiedad especifica el nombre de archivo para la salida. Si el **salida** propiedad está en blanco, se genera un nombre de archivo en el directorio temporal. La extensión de archivo se basa en el `xsl:output` elemento en su estilo de hoja y puede ser. *XML*,. *txt* o. *htm*.

Si el **salida** propiedad especifica un nombre de archivo con un. *htm* o. *HTML* extensión, el resultado XSLT es una vista previa con un explorador web. Todas las demás extensiones de archivo se abren mediante el editor predeterminado elegido por Visual Studio. Por ejemplo, si es la extensión de archivo. *xml*, Visual Studio utiliza el editor XML.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Ejecutar una transformación XSLT desde un archivo XML

1. Abra un documento XML en el editor XML.

2. Asocie una hoja de estilos XSLT con el documento XML.

    - Agregue una instrucción de procesamiento `xml-stylesheet` al documento XML. Por ejemplo, agregue la siguiente línea en el prólogo del documento: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       -o bien-

    - Agregar hoja de estilos XSLT mediante la **propiedades** ventana. Con el archivo XML abierto en el editor, haga clic en cualquier lugar en el editor y elija **propiedades**. En el **propiedades** ventana, haga clic en el **Stylesheet** campo y elija el botón Examinar (...). Seleccione la hoja de estilos XSLT y, a continuación, elija **abierto**.

3. En la barra de menús, elija **XML** > **iniciar sin depuración XSLT**. O bien, presione **Ctrl**+**Alt**+**F5**.

   La salida de la transformación XSLT se muestra en una nueva ventana de documento.

   > [!NOTE]
   > Si no hay ninguna hoja de estilos asociada con el documento XML, un cuadro de diálogo le pide que proporcione la hoja de estilos que desea utilizar.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Ejecutar una transformación XSLT desde una hoja de estilos XSLT

1. Abra una hoja de estilos XSLT en el editor XML.

2. Especifique un documento XML en el **entrada** campo del documento **propiedades** ventana.

   > [!NOTE]
   > El documento XML es el documento de entrada que se utiliza en la transformación. Si no se especifica un documento cuando se inicia la transformación XSLT, el **abrir archivo** aparece el cuadro de diálogo y se puede especificar un documento en ese momento.

3. En la barra de menús, elija **XML** > **iniciar sin depuración XSLT**. O bien, presione **Ctrl**+**Alt**+**F5**.

   La salida de la transformación XSLT se muestra en una nueva ventana de documento.

## <a name="specify-an-output-file-name"></a>Especifique un nombre de archivo de salida

Puede especificar un nombre de archivo de salida para archivos XML y XSL. Abra el **propiedades** ventana y especifique un nombre de archivo en el **salida** campo.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)