---
title: Propiedades de documentos XML, Ventana Propiedades
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99102248a9456de3a2b3aeba28e54de4299fae40
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604153"
---
# <a name="xml-document-properties-properties-window"></a>Propiedades de documento XML, ventana Propiedades

La ventana **propiedades** proporciona información básica sobre el documento que está activo en el editor XML. Las propiedades disponibles pueden variar según el tipo de documento XML que esté actualmente activo.

> [!NOTE]
> Todas las propiedades del documento XML se guardan en la solución. Por tanto, no es necesario que vuelva a escribir estos valores la próxima vez que abra la solución.

**Codificación**

La codificación de caracteres del archivo. Si cambia esta propiedad también cambia el atributo de codificación de la declaración XML, y viceversa. La nueva codificación se usa para codificar el archivo cuando se guarda el archivo.

**Entrada**

El documento de entrada asociado con la hoja de estilos XSLT. Los comandos **Start XSLT** lo usan, por ejemplo, **XML**  > **iniciar XSLT sin depurar**. Se puede seleccionar un documento mediante el botón Examinar ( **...** ).

Esta propiedad solo es visible cuando un archivo XSLT está abierto en el editor.

**Resultado**

El archivo que se genera al transformar un documento XML.

Si no se especifica un archivo, se genera un nombre de archivo predeterminado basado en el atributo `method` del elemento `xsl:output`, que determina la extensión de archivo. El archivo predeterminado está ubicado en el directorio temporal del usuario actual.

**Esquemas**

Los esquemas que se utilizan en la validación. El botón abre el cuadro de diálogo **esquemas XSD** , que se puede usar para seleccionar los esquemas que se van a utilizar.

También puede introducir la ruta a los esquemas. Si se especifican varios esquemas, cada una de las rutas debe ir entre comillas dobles.

**Hoja**

Archivo XSLT que se usa para transformar el documento cuando se usan los comandos **iniciar depuración XSLT** e **iniciar XSLT sin depurar** . Si este campo está en blanco, el editor usa el valor proporcionado en el `xml-stylesheet` instrucción de procesamiento del documento o le pide un nombre de archivo.

Al editar un archivo XSLT, esta propiedad se puede utilizar para especificar que se debe utilizar una hoja de estilos diferente cuando se selecciona el comando **iniciar depuración XSLT** o **iniciar XSLT sin depurar** . Por ejemplo, puede que desee hacer esto al editar una hoja de estilos que se incluye en una hoja de estilos primaria.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)