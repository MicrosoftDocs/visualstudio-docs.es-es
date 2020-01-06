---
title: Ejecutar una transformación XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3bd26eaadf921d13fc425a91031a39df5a80ea2a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592703"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Cómo: ejecutar una transformación XSLT desde el editor XML

El editor XML permite asociar una hoja de estilos XSLT con un documento XML, realizar la transformación y ver la salida. El resultado de la transformación XSLT se muestra en una nueva ventana de documento.

La propiedad de **salida** especifica el nombre de archivo de la salida. Si la propiedad de **salida** está en blanco, se genera un nombre de archivo en el directorio temporal. La extensión de archivo se basa en el elemento `xsl:output` de la hoja de estilos y puede ser. *XML*,. *txt* o. *htm*.

Si la propiedad de **salida** especifica un nombre de archivo con un. *htm* o. extensión *HTML* , se muestra una vista previa de la salida XSLT mediante un explorador Web. Todas las demás extensiones de archivo se abren con el editor predeterminado elegido por Visual Studio. Por ejemplo, si la extensión de archivo es. *XML*, Visual Studio usa el editor XML.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Ejecutar una transformación XSLT desde un archivo XML

1. Abra un documento XML en el editor XML.

2. Asocie una hoja de estilos XSLT con el documento XML.

    - Agregue una instrucción de procesamiento `xml-stylesheet` al documento XML. Por ejemplo, agregue la siguiente línea al prólogo del documento: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       O bien,

    - Agregue la hoja de estilos XSLT mediante la ventana **propiedades** . Con el archivo XML abierto en el editor, haga clic con el botón secundario en cualquier parte del editor y elija **propiedades**. En la ventana **propiedades** , haga clic en el campo **hoja de estilos** y elija el botón Examinar (...). Seleccione la hoja de estilos XSLT y, a continuación, elija **abrir**.

3. En la barra de menús, elija **XML** > **iniciar XSLT sin depurar**. O bien, presione **Ctrl**+**Alt**+**F5**.

   La salida de la transformación XSLT se muestra en una nueva ventana de documento.

   > [!NOTE]
   > Si no hay ninguna hoja de estilos asociada con el documento XML, un cuadro de diálogo le pide que proporcione la hoja de estilos que desea utilizar.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Ejecutar una transformación XSLT desde una hoja de estilos XSLT

1. Abra una hoja de estilos XSLT en el editor XML.

2. Especifique un documento XML en el campo **entrada** de la ventana **propiedades** del documento.

   > [!NOTE]
   > El documento XML es el documento de entrada que se utiliza en la transformación. Si no se especifica un documento cuando se inicia la transformación XSLT, aparece el cuadro de diálogo **Abrir archivo** y puede especificar un documento en ese momento.

3. En la barra de menús, elija **XML** > **iniciar XSLT sin depurar**. O bien, presione **Ctrl**+**Alt**+**F5**.

   La salida de la transformación XSLT se muestra en una nueva ventana de documento.

## <a name="specify-an-output-file-name"></a>Especificar un nombre de archivo de salida

Puede especificar un nombre de archivo de salida para los archivos XML y XSL. Abra la ventana **propiedades** y especifique un nombre de archivo en el campo **salida** .

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
