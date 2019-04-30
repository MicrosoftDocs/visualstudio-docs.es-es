---
title: Propiedades de documentos XML, Ventana Propiedades
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 679ac529708a49d18025672ce8f880c4f7710471
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808137"
---
# <a name="xml-document-properties-properties-window"></a>Propiedades del documento XML, ventana Propiedades

El **propiedades** ventana proporciona información básica sobre el documento que está activo en el editor XML. Las propiedades disponibles pueden variar según el tipo de documento XML que esté actualmente activo.

> [!NOTE]
> Todas las propiedades del documento XML se guardan en la solución. Por tanto, no es necesario que vuelva a escribir estos valores la próxima vez que abra la solución.

**Codificación**

La codificación de caracteres del archivo. Si cambia esta propiedad también cambia el atributo de codificación de la declaración XML, y viceversa. La nueva codificación se usa para codificar el archivo cuando guarde el archivo.

**Entrada**

El documento de entrada asociado con la hoja de estilos XSLT. Está usando el **iniciar XSLT** comandos, por ejemplo, **XML** > **iniciar sin depuración XSLT**. Se puede seleccionar un documento mediante el examen (**...** ) botón.

Esta propiedad es visible solo cuando se abre en el editor de un archivo XSLT.

**Salida**

El archivo que se genera al transformar un documento XML.

Si no se especifica un archivo, un nombre de archivo predeterminado se genera según el `method` atributo el `xsl:output` elemento, que determina la extensión de archivo. El archivo predeterminado está ubicado en el directorio temporal del usuario actual.

**Esquemas**

Los esquemas que se utilizan en la validación. El botón abre el **esquemas XSD** cuadro de diálogo que puede usarse para seleccionar los esquemas que se va a usar.

También puede introducir la ruta a los esquemas. Si se especifican varios esquemas, cada una de las rutas debe ir entre comillas dobles.

**Stylesheet**

El archivo XSLT que se utiliza para transformar el documento cuando el **iniciar la depuración de XSLT** y **iniciar sin depuración XSLT** comandos se usan. Si este campo está en blanco, el editor utiliza el valor proporcionado en el `xml-stylesheet` procesamiento de instrucciones del documento o le pedirá un nombre de archivo.

Al editar un archivo XSLT, esta propiedad puede utilizarse para especificar que debe ser una hoja de estilos diferentes cuando usa el **iniciar la depuración de XSLT** o **iniciar sin depuración XSLT** se selecciona el comando. Por ejemplo, es posible que desee hacer esto cuando edita una hoja de estilos que se incluye en una hoja de estilos principal.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)