---
title: Procedimiento Especificar comandos anteriores y posteriores a la instrumentación | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0471d51ef00e176ab379a79a141ffd49c23aa28
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923706"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Procedimiento Especificar comandos anteriores y posteriores a la instrumentación

Puede especificar los comandos que se ejecutan antes o después de que los archivos binarios en una sesión de rendimiento se instrumenten. Cualquier comando que se puede emitir desde la línea de comandos puede especificarse como un evento anterior o posterior a la instrumentación. Por ejemplo, puede especificar comandos que automaticen la nueva firma de un ensamblado con una clave de nombre seguro en un archivo por lotes que se ejecuta después de que se instrumenten los binarios.

Puede especificar comandos para todos los binarios instrumentados en la ejecución de la generación de perfiles o para binarios individuales. Sin embargo, puede especificar que se ejecute solo un comando antes del proceso de instrumentación y solo un comando después del proceso de instrumentación. No se pueden especificar comandos para todos los binarios y para binarios individuales. Cuando especifica comandos para todos los binarios, los comandos se ejecutan antes o después de la instrumentación de cada binario en la sesión.

El directorio de trabajo en el que se ejecutan los comandos depende del sistema operativo en el que se ejecuta [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] y de la plataforma de destino de la aplicación de la que se generan perfiles.

Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="to-specify-pre-instrument-commands"></a>Para especificar comandos anteriores a la instrumentación

1. Realice uno de estos pasos:

    - Para especificar comandos anteriores a la instrumentación para todos los binarios de una sesión de rendimiento, seleccione el nodo de la sesión de rendimiento en **Explorador de rendimiento** y después haga clic con el botón derecho y seleccione **Propiedades**.

    - Para especificar comandos anteriores a la instrumentación para un binario concreto, haga clic con el botón derecho en el nombre del binario en la lista **Destinos** de la sesión de rendimiento y después seleccione **Propiedades**.

2. En las **Páginas de propiedades**, haga clic en **Instrumentación**.

3. Escriba el comando en el cuadro de texto **Línea de comandos** en **Eventos anteriores a la instrumentación**.

    > [!NOTE]
    > Puede hacer clic en el botón de puntos suspensivos **(...)** que se muestra junto al cuadro **Línea de comandos** para buscar y seleccionar el archivo .exe, .cmd o .bat apropiado.

4. Haga clic en **Aceptar**.

     Para deshabilitar la ejecución del comando sin quitarlo, seleccione la casilla **Excluir de la instrumentación**. Para modificar la configuración de vinculador o compilador, utilice las páginas de propiedades de proyecto.

## <a name="to-specify-post-instrument-commands"></a>Para especificar comandos posteriores a la instrumentación

1. Realice uno de estos pasos:

    - Para especificar comandos posteriores a la instrumentación para todos los binarios de una sesión de rendimiento, seleccione el nodo de la sesión de rendimiento en **Explorador de rendimiento** y después haga clic con el botón derecho y seleccione **Propiedades**.

    - Para especificar comandos posteriores a la instrumentación para un binario concreto, haga clic con el botón derecho en el nombre del binario en la lista **Destinos** de la sesión de rendimiento y después seleccione **Propiedades**.

2. En las **Páginas de propiedades**, haga clic en **Instrumentación**.

3. Escriba el comando en el cuadro de texto **Línea de comandos** en **Eventos posteriores a la instrumentación**.

    > [!NOTE]
    > Puede hacer clic en el botón de puntos suspensivos **(...)** que se muestra junto al cuadro **Línea de comandos** para buscar y seleccionar el archivo .exe, .cmd o .bat apropiado.

4. Haga clic en **Aceptar**.

     Para deshabilitar la ejecución del comando sin quitarlo, seleccione la casilla **Excluir de la instrumentación**. Para modificar la configuración de vinculador o compilador, utilice las páginas de propiedades de proyecto.

## <a name="see-also"></a>Vea también

[Configuración de sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
