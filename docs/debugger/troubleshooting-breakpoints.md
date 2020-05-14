---
title: Solución de problemas de puntos de interrupción en el depurador de Visual Studio | Microsoft Docs
ms.custom: seodec18
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c11741cb9bb9a0b0c64b9452b54daa6ac226b92
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535933"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Solución de problemas de puntos de interrupción en el depurador de Visual Studio

## <a name="breakpoint-warnings"></a>Advertencias de puntos de interrupción

Al depurar, un punto de interrupción tiene dos posibles estados visuales: un círculo rojo sólido y un círculo hueco (con relleno en blanco). Si el depurador puede establecer correctamente un punto de interrupción en el proceso de destino, se mantendrá un círculo rojo sólido. Si el punto de interrupción es un círculo hueco, se deshabilita el punto de interrupción o se produce una advertencia al intentar establecer el punto de interrupción. Para determinar la diferencia, mantenga el puntero sobre el punto de interrupción y compruebe si hay una advertencia.

En las dos secciones siguientes se describen las advertencias destacadas y cómo corregirlas.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"No se ha cargado ningún símbolo para este documento"

Vaya a la ventana **Módulos** (**Depurar** > **Windows** > **Módulos**) y compruebe si el módulo está cargado.
* Si el módulo está cargado, compruebe la columna **Estado de símbolos** para ver si se han cargado los símbolos.
  * Si no se cargan los símbolos, compruebe el estado del símbolo para diagnosticar el problema. En el menú contextual de un módulo de la ventana **Módulos**, haga clic en **Información de carga de símbolos...** para ver dónde el depurador ha intentado probar y cargar símbolos. Para más información sobre la carga de símbolos, vea [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  * Si se cargan los símbolos, el archivo PDB no contiene información sobre los archivos de código fuente. Estas causas principales pueden ser varias:
    * Si los archivos de código fuente se agregaron recientemente, confirme que se está cargando una versión actualizada del módulo.
    * Es posible crear archivos PDB quitados mediante la opción del enlazador **/PDBSTRIPPED**. Los archivos PDB quitados no contienen información del archivo de código fuente. Confirme que está trabajando con un archivo PDB completo y no con un archivo PDB quitado.
    * El archivo PDB está dañado parcialmente. Elimine el archivo y realice una compilación limpia del módulo para intentar resolver el problema.

* Si el módulo no está cargado, compruebe lo siguiente para encontrar la causa:
  * Confirme que está depurando el proceso correcto.
  * Compruebe que está depurando el tipo de código correcto. Puede averiguar el tipo de código en el que está configurado el depurador para depurar en la ventana **Procesos** (**Depurar** > **Windows** > **Procesos**). Por ejemplo, si intenta depurar código de C#, confirme que el depurador está configurado para el tipo y la versión adecuados de .NET; por ejemplo, Administrado (v4\*) frente a Administrado (v2\*/v3\*) en lugar de Administrado (CoreCLR).

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… el código fuente actual es distinto al de la versión compilada en..."

Si un archivo de código fuente ha cambiado y el origen ya no coincide con el código que se está depurando, el depurador no establecerá puntos de interrupción en el código de forma predeterminada. Normalmente, este problema se produce cuando se cambia un archivo de código fuente, sin que se haya recompilado el código fuente. Para corregir este problema, recompile el proyecto. Si el sistema de compilación considera que el proyecto ya está actualizado aunque no lo esté, puede forzar la recompilación del sistema del proyecto al volver a guardar el archivo de código fuente o al limpiar el resultado de la compilación del proyecto antes de la compilación.

En raras ocasiones, es posible que desee depurar sin necesidad de tener código fuente coincidente. La depuración sin código fuente coincidente puede conducir a una experiencia de depuración confusa, por lo que debe asegurarse de que esta es la forma en que desea continuar.

Para deshabilitar estas comprobaciones de seguridad, realice una de las acciones siguientes:
* Para modificar un solo punto de interrupción, mantenga el puntero sobre el icono de punto de interrupción en el editor y haga clic en el icono de configuración (engranaje). Se agrega una ventana de inspección al editor. En la parte superior de la ventana de inspección, hay un hipervínculo que indica la ubicación del punto de interrupción. Haga clic en el hipervínculo para permitir la modificación de la ubicación del punto de interrupción y active **Permitir que el código fuente sea distinto del de la versión original**.
* Para modificar esta configuración para todos los puntos de interrupción, vaya a **Depurar** > **Opciones y configuración**. En la página **Depuración/General** , desactive la opción **Es necesario que los archivos de código fuente coincidan con la versión original** . Asegúrese de volver a habilitar esta opción cuando termine la depuración.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>El punto de interrupción se estableció correctamente (sin advertencia), pero no se alcanzó.

En esta sección se proporciona información para solucionar problemas cuando el depurador no muestra ninguna advertencia: el punto de interrupción es un círculo rojo sólido mientras se depura activamente, pero no se alcanza el punto de interrupción.

A continuación se indican algunas cosas que puede comprobar:
1. Si el código se ejecuta en más de un proceso o en más de un equipo, asegúrese de que depura el proceso o equipo correcto.
2. Confirme que el código se está ejecutando. Para probar que el código se está ejecutando, agregue una llamada a `System.Diagnostics.Debugger.Break` (C#/VB) o `__debugbreak` (C++) a la línea de código en la que está intentando establecer el punto de interrupción y, después, recompile el proyecto.
3. Si está depurando código optimizado, asegúrese de que la función en la que se establece el punto de interrupción no se inserta en otra función. La prueba de `Debugger.Break` descrita en la comprobación anterior también puede funcionar para probar este problema.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Eliminé un punto de interrupción, pero continúa alcanzándose al iniciar de nuevo la depuración

Si eliminó un punto de interrupción durante la depuración, puede alcanzarse de nuevo la próxima vez que se inicia la depuración. Para dejar de encontrar este punto de interrupción, asegúrese de que todas las instancias del punto de interrupción se quitan de la ventana **Puntos de interrupción** .
