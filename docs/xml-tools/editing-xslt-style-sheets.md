---
title: Editar hojas de estilos XSLT
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dab4013bf3921a2af4f69d464c10d1e70f9407b3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996995"
---
# <a name="edit-xslt-style-sheets"></a>Editar hojas de estilos XSLT

También se puede usar el editor XML para editar hojas de estilos XSLT. Puede aprovechar las características predeterminadas del editor como IntelliSense, esquematización, fragmentos XML, etc. Además, se incluyen también nuevas características que facilitan la programación en XSLT.

## <a name="xslt-features"></a>Características XSLT

En la siguiente tabla se describen características específicas del trabajo con hojas de estilos XSLT.

**Color de sintaxis**

Las palabras clave XSLT, como `template` y `match`, se muestran en el color de palabra clave XSLT especificado por el **fuentes y colores** configuración.

**Subrayado ondulado**

El editor XML utiliza el instalado *xslt.xsd* archivo para validar las hojas de estilos XSLT. Los errores de validación se muestran con un subrayado ondulado de color azul. El editor XML también compila la hoja de estilos en segundo plano y del compilador informa de los errores o advertencias con un subrayado ondulado adecuado.

**Compatibilidad con bloques de scripts**

El depurador de XSLT admite el código en bloques de scripts, de modo que puede definir puntos de interrupción y examinar el código del bloque de script.

**Ver el resultado XSLT**

Puede ejecutar una transformación XSL y ver la salida desde el editor XML. Para obtener más información, vea [Cómo: Ejecutar una transformación XSLT desde el editor XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**Depurar XSLT**

Puede iniciar al depurador de XSLT desde un archivo XSLT en el editor XML. El depurador admite la definición de puntos de interrupción en el archivo XSLT, la visualización del estado de ejecución de XSLT, etc. Al mantener el mouse sobre una variable XSLT se muestra un cuadro de información sobre herramientas con el valor de la variable. El depurador se puede utilizar para depurar una hoja de estilos o para depurar una transformación XSL compilada invocada desde otra aplicación. Para obtener más información, consulte [depuración XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)