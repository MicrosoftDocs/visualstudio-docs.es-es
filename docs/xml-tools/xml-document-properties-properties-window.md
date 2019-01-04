---
title: Propiedades de documentos XML, Ventana Propiedades
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a89e6f12cb3e061abc4ebbe30cfe8d3a92138df6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913315"
---
# <a name="xml-document-properties-properties-window"></a>Propiedades del documento XML, ventana Propiedades

El **propiedades** ventana proporciona información básica sobre el documento que está activo en el Editor XML. Las propiedades disponibles pueden variar según el tipo de documento XML que esté actualmente activo.

> [!NOTE]
> Todas las propiedades del documento XML se guardan en la solución. Por tanto, no es necesario que vuelva a escribir estos valores la próxima vez que abra la solución.

 **Codificación**

 La codificación de caracteres del archivo. Si cambia esta propiedad también cambia el atributo de codificación de la declaración XML, y viceversa. La nueva codificación se utilizará para codificar el archivo cuando lo guarde.

 **Entrada**

 El documento de entrada asociado con la hoja de estilos XSLT. Está usando el **ShowXSLT salida** comando. Se puede seleccionar un documento mediante el examen (**...** ) botón.

 Esta propiedad solo está visible cuando hay un archivo XSLT activo en ese momento en la ventana del editor.

 **Salida**

 El archivo que se genera al transformar un documento XML.

 Si no se especifica un archivo, se genera un nombre de archivo predeterminado basado en el atributo `method` del elemento `xsl:output` que determina la extensión de archivo. El archivo predeterminado está ubicado en el directorio temporal del usuario actual.

 **Esquemas**

 Los esquemas que se utilizan en la validación. El botón abre el **esquemas XSD** cuadro de diálogo que puede usarse para seleccionar los esquemas que se va a usar.

 También puede introducir la ruta a los esquemas. Si se especifican varios esquemas, cada una de las rutas debe ir entre comillas dobles.

 **Hoja de estilos**

 El archivo XSLT que se utiliza para transformar el documento cuando el **Mostrar resultado XSLT** se usa el comando. Si este campo está en blanco cuando el **Mostrar resultado XSLT** es utilizar el comando, el editor utiliza el valor proporcionado en el `xml-stylesheet` procesamiento de instrucciones de documento, o bien le pedirá el nombre de archivo.

 Al editar un archivo XSLT, esta propiedad puede utilizarse para especificar que debe ser una hoja de estilos diferentes cuando usa el **Mostrar resultado XSLT** o **depurar XSLT** comando está seleccionado. Por ejemplo, podría hacer esto cuando edita una hoja de estilos que se incluye en una hoja de estilos principal.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
- [Componentes del Editor XML](../xml-tools/xml-editor-components.md)