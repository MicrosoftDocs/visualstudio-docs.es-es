---
title: Propiedades de documento XML, ventana Propiedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f620cc2bd189dccf067c6276f760d21cde5cf05e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669519"
---
# <a name="xml-document-properties-properties-window"></a>Propiedades de documentos XML, Ventana Propiedades
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La ventana **propiedades** proporciona información básica sobre el documento que está activo en el editor XML. Las propiedades disponibles pueden variar según el tipo de documento XML que esté actualmente activo.

> [!NOTE]
> Todas las propiedades del documento XML se guardan en la solución. Por tanto, no es necesario que vuelva a escribir estos valores la próxima vez que abra la solución.

 **Codificación** Codificación de caracteres del archivo. Si cambia esta propiedad también cambia el atributo de codificación de la declaración XML, y viceversa. La nueva codificación se utilizará para codificar el archivo cuando lo guarde.

 **Entrada** de Documento de entrada asociado a la hoja de estilos XSLT. Lo usa el comando de **salida ShowXSLT** . Los documentos se pueden seleccionar con el botón Examinar ( **…** ).

 Esta propiedad solo está visible cuando hay un archivo XSLT activo en ese momento en la ventana del editor.

 **Salida** de El archivo que se genera al transformar un documento XML.

 Si no se especifica un archivo, se genera un nombre de archivo predeterminado basado en el atributo `method` del elemento `xsl:output` que determina la extensión de archivo. El archivo predeterminado está ubicado en el directorio temporal del usuario actual.

 **Esquemas** Esquemas que se van a usar para la validación. El botón abre el cuadro de diálogo **Esquemas XSD**, que se puede emplear para seleccionar los esquemas que se van a utilizar.

 También puede introducir la ruta a los esquemas. Si se especifican varios esquemas, cada una de las rutas debe ir entre comillas dobles.

 **Hoja de estilos** Archivo XSLT que se usa para transformar el documento cuando se usa el comando **Mostrar salida XSLT** . Si este campo está en blanco cuando se usa el comando **Mostrar salida XSLT** , el editor usa el valor proporcionado en la `xml-stylesheet` instrucción de procesamiento del documento o le pide el nombre de archivo.

 Al editar un archivo XSLT, esta propiedad se puede utilizar para especificar que se debe utilizar una hoja de estilos diferente cuando se selecciona el comando **Mostrar salida XSLT** o **depurar XSLT** . Por ejemplo, podría hacer esto cuando edita una hoja de estilos que se incluye en una hoja de estilos principal.

## <a name="see-also"></a>Consulte también
 [Componentes del editor XML](../xml-tools/xml-editor-components.md) del [Editor XML](../xml-tools/xml-editor.md)
