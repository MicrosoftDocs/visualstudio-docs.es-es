---
title: Propiedades de documentos XML, Ventana Propiedades
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b21f4435737597136e1ac4a4dd8651decaf4c65
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592430"
---
# <a name="xml-document-properties-properties-window"></a>Propiedades de documentos XML, ventana Propiedades

La ventana **Propiedades** ofrece información básica acerca del documento que está activo en el Editor XML. Las propiedades disponibles pueden variar según el tipo de documento XML que esté actualmente activo.

> [!NOTE]
> Todas las propiedades del documento XML se guardan en la solución. Por tanto, no es necesario que vuelva a escribir estos valores la próxima vez que abra la solución.

**Encoding**

La codificación de caracteres del archivo. Si cambia esta propiedad también cambia el atributo de codificación de la declaración XML, y viceversa. La codificación nueva se usa para codificar el archivo cuando lo guarde.

**Entrada**

El documento de entrada asociado con la hoja de estilos XSLT. Lo utilizan los comandos **Iniciar XSLT**, por ejemplo, **XML** > **Iniciar XSLT sin depurar**. Los documentos se pueden seleccionar con el botón Examinar ( **…** ).

Esta propiedad solo es visible cuando hay un archivo XSLT abierto en el editor.

**Salida**

El archivo que se genera al transformar un documento XML.

Si no se especifica un archivo, se genera un nombre de archivo predeterminado basado en el atributo `method` del elemento `xsl:output` que determina la extensión de archivo. El archivo predeterminado está ubicado en el directorio temporal del usuario actual.

**Esquemas**

Los esquemas que se utilizan en la validación. El botón abre el cuadro de diálogo **Esquemas XSD**, que se puede emplear para seleccionar los esquemas que se van a utilizar.

También puede introducir la ruta a los esquemas. Si se especifican varios esquemas, cada una de las rutas debe ir entre comillas dobles.

**Hoja de estilos**

El archivo XSLT que se usa para transformar el documento cuando se usan los comandos **Iniciar depuración de XSLT** e **Iniciar XSLT sin depurar**. Si este campo está en blanco, el editor usa el valor proporcionado en la instrucción de procesamiento `xml-stylesheet` del documento o le pide un nombre de archivo.

Al editar un archivo XSLT, esta propiedad se puede utilizar para especificar que se debe utilizar una hoja de estilos diferente cuando se selecciona el comando **Iniciar depuración de XSLT** o **Iniciar XSLT sin depurar**. Por ejemplo, podría hacer esto cuando edita una hoja de estilos que se incluye en una hoja de estilos principal.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
