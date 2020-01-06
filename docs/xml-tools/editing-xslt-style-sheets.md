---
title: Editar hojas de estilos XSLT
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81bab324c58c06cc1ca553bae2f81faf474c4ad0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592846"
---
# <a name="edit-xslt-style-sheets"></a>Editar hojas de estilos XSLT

El editor XML también se puede utilizar para editar hojas de estilos XSLT. Puede aprovechar las características predeterminadas del editor como IntelliSense, esquematización, fragmentos XML, etc. Además, se incluyen también nuevas características que facilitan la programación en XSLT.

## <a name="xslt-features"></a>Características XSLT

En la siguiente tabla se describen características específicas del trabajo con hojas de estilos XSLT.

**Color de la sintaxis**

Las palabras clave XSLT, como `template` y `match`, se muestran en el color de palabra clave XSLT especificado por la configuración de **fuentes y colores** .

**Subrayados ondulados**

El editor XML utiliza el archivo *XSLT. xsd* instalado para validar las hojas de estilos XSLT. Los errores de validación se muestran con un subrayado ondulado de color azul. El editor XML también compila la hoja de estilos en segundo plano e informa de los errores o advertencias del compilador con el subrayado ondulado adecuado.

**Compatibilidad con bloques de scripts**

El depurador de XSLT admite el código en bloques de scripts, de modo que puede definir puntos de interrupción y examinar el código del bloque de script.

**Ver salida XSLT**

Puede ejecutar una transformación XSL y ver el resultado desde el editor XML. Para obtener más información, vea [Cómo: ejecutar una transformación XSLT desde el editor XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**Depurar XSLT**

Puede iniciar el depurador de XSLT desde un archivo XSLT en el editor XML. El depurador admite la definición de puntos de interrupción en el archivo XSLT, la visualización del estado de ejecución de XSLT, etc. Al mantener el mouse sobre una variable XSLT se muestra un cuadro de información sobre herramientas con el valor de la variable. El depurador se puede utilizar para depurar una hoja de estilos o para depurar una transformación XSL compilada invocada desde otra aplicación. Para obtener más información, vea [depuración de XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
