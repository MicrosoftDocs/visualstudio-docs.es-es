---
title: Edición de hojas de estilos XSLT | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a228c83972c31875b9c8923922d36c9bc638380f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="editing-xslt-style-sheets"></a>Editar hojas de estilos XSLT
El Editor XML se puede utilizar también para editar hojas de estilos XSLT. Puede aprovechar las características predeterminadas del editor como IntelliSense, esquematización, fragmentos XML, etc. Además, se incluyen también nuevas características que facilitan la programación en XSLT.  
  
## <a name="xslt-features"></a>Características XSLT  
 En la siguiente tabla se describen características específicas del trabajo con hojas de estilos XSLT.  
  
 **Colorear la sintaxis**  
 Las palabras clave XSLT, como `template`, `match`, y así sucesivamente, se muestran en el color de palabra clave XSLT especificado por el **fuentes y colores** configuración.  
  
 **Subrayados ondulados**  
 El Editor XML utiliza el archivo xslt.xsd instalado para validar las hojas de estilos XSLT. Los errores de validación se muestran con un subrayado ondulado de color azul. El Editor XML también compila la hoja de estilos en segundo plano e informa de los errores o advertencias del compilador mediante el subrayado ondulado adecuado.  
  
 **Compatibilidad con bloques de scripts**  
 El depurador de XSLT admite el código en bloques de scripts, de modo que puede definir puntos de interrupción y examinar el código del bloque de script.  
  
 **Ver el resultado XSLT**  
 Puede ejecutar una transformación XSL y ver el resultado desde el Editor XML. Para obtener más información, consulte [Cómo: ejecutar una transformación XSLT desde el Editor XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).  
  
 **Depurar XSLT**  
 Puede iniciar el depurador de XSLT desde un archivo XSLT del Editor XML. El depurador admite la definición de puntos de interrupción en el archivo XSLT, la visualización del estado de ejecución de XSLT, etc. Al mantener el mouse sobre una variable XSLT se muestra un cuadro de información sobre herramientas con el valor de la variable. El depurador se puede utilizar para depurar una hoja de estilos o para depurar una transformación XSL compilada invocada desde otra aplicación. Para obtener más información, consulte [depuración XSLT](../xml-tools/debugging-xslt.md).  
  
## <a name="see-also"></a>Vea también  
 [Editor XML](../xml-tools/xml-editor.md)