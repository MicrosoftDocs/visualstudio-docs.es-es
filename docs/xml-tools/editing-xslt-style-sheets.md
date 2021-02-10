---
title: Editar hojas de estilos XSLT
description: Obtenga información sobre las características del editor XML para editar hojas de estilos XSLT, incluidos el color de la sintaxis, los subrayados y el inicio del depurador de XSLT desde el editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: df9bff28e68b373bb932f33ff8fb34439f0b4e7c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969094"
---
# <a name="edit-xslt-style-sheets"></a>Editar hojas de estilos XSLT

El editor XML se puede utilizar también para editar hojas de estilos XSLT. Puede aprovechar las características predeterminadas del editor como IntelliSense, esquematización, fragmentos XML, etc. Además, se incluyen también nuevas características que facilitan la programación en XSLT.

## <a name="xslt-features"></a>Características XSLT

En la siguiente tabla se describen características específicas del trabajo con hojas de estilos XSLT.

**Seleccionar el color de la sintaxis**

Las palabras clave XSLT, como `template` y `match`, se muestran en el color de palabra clave XSLT especificado en la opción **Fuentes y colores**.

**Subrayado ondulado**

El editor XML utiliza el archivo *xslt.xsd* instalado para validar las hojas de estilos XSLT. Los errores de validación se muestran con un subrayado ondulado de color azul. El editor XML también compila la hoja de estilos en segundo plano e informa de los errores o advertencias del compilador mediante el subrayado ondulado adecuado.

**Compatibilidad con bloques de scripts**

El depurador de XSLT admite el código en bloques de scripts, de modo que puede definir puntos de interrupción y examinar el código del bloque de script.

**Ver la salida XSLT**

Puede ejecutar una transformación XSL y ver la salida desde el editor XML. Para obtener más información, vea [Cómo: Ejecución de una transformación XSLT desde el editor XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**Depurar XSLT**

Puede iniciar el depurador de XSLT desde un archivo XSLT del editor XML. El depurador admite la definición de puntos de interrupción en el archivo XSLT, la visualización del estado de ejecución de XSLT, etc. Al mantener el mouse sobre una variable XSLT se muestra un cuadro de información sobre herramientas con el valor de la variable. El depurador se puede utilizar para depurar una hoja de estilos o para depurar una transformación XSL compilada invocada desde otra aplicación. Para más información, consulte [Depuración de XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
