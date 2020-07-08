---
title: Ejecución de una transformación XSLT
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e74beb2903cd133dfdd322ce4c297692eae3411
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817195"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Procedimiento Ejecución de una transformación XSLT desde el editor XML

El editor XML permite asociar una hoja de estilos XSLT con un documento XML, realizar la transformación y ver el resultado. El resultado de la transformación XSLT se muestra en una nueva ventana de documento.

La propiedad **Salida** especifica el nombre de archivo de la salida. Si la propiedad **Salida** está en blanco, se genera un nombre de archivo en el directorio temporal. La extensión de archivo se basa en el elemento `xsl:output` de la hoja de estilos y puede ser .*xml*, .*txt* o .*htm*.

Si la propiedad **Salida** especifica un nombre de archivo con una extensión .*html* o .*html*, se puede obtener una vista previa de la salida XSLT mediante un explorador web. Todas las demás extensiones de archivo se abren con el editor predeterminado que Visual Studio elija. Por ejemplo, si la extensión de archivo es .*xml*, Visual Studio utiliza el editor XML.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Ejecución de una transformación XSLT desde un archivo XML

1. Abra un documento XML en el editor XML.

2. Asocie una hoja de estilos XSLT con el documento XML.

    - Agregue una instrucción de procesamiento `xml-stylesheet` al documento XML. Por ejemplo, agregue la siguiente línea al prólogo del documento: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       o bien

    - Agregue la hoja de estilos XSLT mediante la ventana **Propiedades**. Con el archivo XML abierto en el editor, haga clic con el botón derecho en cualquier parte del editor y elija **Propiedades**. En la ventana **Propiedades**, haga clic en el campo **Stylesheet** y después elija el botón Examinar (...). Seleccione la hoja de estilos XSLT y, a continuación, elija **Abrir**.

3. En la barra de menús, seleccione **XML** > **Iniciar XSLT sin depurar**. También puede presionar **Ctrl**+**Alt**+**F5**.

   La salida de la transformación XSLT se muestra en una nueva ventana de documento.

   > [!NOTE]
   > Si no hay ninguna hoja de estilos asociada con el documento XML, un cuadro de diálogo le pide que proporcione la hoja de estilos que desea utilizar.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Ejecución de una transformación XSLT desde una hoja de estilos XSLT

1. Abra una hoja de estilos XSLT en el editor XML.

2. Especifique un documento XML en el campo **Entrada** de la ventana **Propiedades** del documento.

   > [!NOTE]
   > El documento XML es el documento de entrada que se utiliza en la transformación. Si no se especifica un documento cuando se inicia la transformación XSLT, aparece el cuadro de diálogo **Abrir archivo**, donde podrá especificar un documento en ese momento.

3. En la barra de menús, seleccione **XML** > **Iniciar XSLT sin depurar**. También puede presionar **Ctrl**+**Alt**+**F5**.

   La salida de la transformación XSLT se muestra en una nueva ventana de documento.

## <a name="specify-an-output-file-name"></a>Especificación de un nombre de archivo de salida

Puede especificar un nombre de archivo de salida para los archivos XML y XSL. Abra la ventana **Propiedades** y especifique un nombre de archivo en el campo **Salida**.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
