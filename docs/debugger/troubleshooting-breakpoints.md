---
title: Solucionar problemas de puntos de interrupción en el depurador | Microsoft Docs
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535933"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Solucionar problemas de puntos de interrupción en el depurador de Visual Studio

## <a name="breakpoint-warnings"></a>Advertencias de puntos de interrupción

Al depurar, un punto de interrupción tiene dos posibles estados visuales: un círculo rojo sólido y un círculo hueco (blanco relleno). Si el depurador puede establecer correctamente un punto de interrupción en el proceso de destino, se mantendrá un círculo rojo sólido. Si el punto de interrupción es un círculo hueco, se deshabilita el punto de interrupción o se produce una advertencia al intentar establecer el punto de interrupción. Para determinar la diferencia, mantenga el mouse sobre el punto de interrupción y compruebe si hay una advertencia.

En las dos secciones siguientes se describen las advertencias destacadas y cómo corregirlas.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"No se ha cargado ningún símbolo para este documento"

Vaya a la ventana **módulos** (**depurar**  > **módulos**de**Windows**  > ) y compruebe si el módulo está cargado.
* Si el módulo está cargado, Compruebe la columna **Estado** de los símbolos para ver si se han cargado los símbolos.
  * Si no se cargan los símbolos, compruebe el estado del símbolo para diagnosticar el problema. En el menú contextual de un módulo de la ventana **módulos** , haga clic en **información de carga de símbolos...** para ver dónde el depurador ha buscado y cargar símbolos. Para obtener más información sobre la carga de símbolos, vea [especificar archivos de código fuente y símbolos (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  * Si se cargan los símbolos, el archivo PDB no contiene información sobre los archivos de código fuente. Estas son algunas causas posibles:
    * Si los archivos de origen se agregaron recientemente, confirme que se está cargando una versión actualizada del módulo.
    * Es posible crear archivos PDB quitados mediante la opción del enlazador **/PDBSTRIPPED** . Los archivos PDB quitados no contienen información del archivo de código fuente. Confirme que está trabajando con un archivo PDB completo y no con un archivo PDB eliminado.
    * El archivo PDB está dañado parcialmente. Elimine el archivo y realice una compilación limpia del módulo para intentar resolver el problema.

* Si el módulo no está cargado, compruebe lo siguiente para encontrar la causa:
  * Confirme que está depurando el proceso correcto.
  * Compruebe que está depurando el tipo de código correcto. Puede averiguar el tipo de código en el que está configurado el depurador para depurar en la ventana **procesos** (**depurar**  > **procesos**de**Windows**  > ). Por ejemplo, si está intentando depurar C# código, confirme que el depurador está configurado para el tipo y la versión adecuados de .net (por ejemplo, administrado (V4 \*) frente a Managed (V2 \*/V3 \*) en lugar de administrado (CoreCLR)).

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… el código fuente actual es diferente de la versión integrada en...

Si un archivo de código fuente ha cambiado y el origen ya no coincide con el código que se está depurando, el depurador no establecerá puntos de interrupción en el código de forma predeterminada. Normalmente, este problema se produce cuando se cambia un archivo de código fuente, pero el código fuente no se ha vuelto a generar. Para corregir este problema, recompile el proyecto. Si el sistema de compilación considera que el proyecto ya está actualizado aunque no lo esté, puede forzar que el sistema del proyecto se vuelva a compilar; para ello, guarde el archivo de código fuente de nuevo o limpie el resultado de la compilación del proyecto antes de compilar.

En raras ocasiones, es posible que desee depurar sin necesidad de código fuente coincidente. La depuración sin código fuente coincidente puede conducir a una experiencia de depuración confusa, por lo que debe asegurarse de que es cómo desea continuar.

Para deshabilitar estas comprobaciones de seguridad, realice una de las acciones siguientes:
* Para modificar un solo punto de interrupción, mantenga el mouse sobre el icono de punto de interrupción en el editor y haga clic en el icono de configuración (engranaje). Se agrega una ventana de inspección al editor. En la parte superior de la ventana de PEEK hay un hipervínculo que indica la ubicación del punto de interrupción. Haga clic en el hipervínculo para permitir la modificación de la ubicación del punto de interrupción y Active **permitir que el código fuente sea diferente del original**.
* Para modificar esta configuración para todos los puntos de interrupción, vaya a **Depurar**  > **Opciones y configuración**. En la página **Depuración/General** , desactive la opción **Es necesario que los archivos de código fuente coincidan con la versión original** . Asegúrese de volver a habilitar esta opción cuando termine la depuración.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>El punto de interrupción se estableció correctamente (sin advertencia), pero no se alcanzó.

En esta sección se proporciona información para solucionar problemas cuando el depurador no muestra ninguna advertencia: el punto de interrupción es un círculo rojo sólido mientras se depura activamente, pero no se alcanza el punto de interrupción.

Estas son algunas de las cosas que debe comprobar:
1. Si el código se ejecuta en más de un proceso o en más de un equipo, asegúrese de que está depurando el proceso o equipo correcto.
2. Confirme que el código se está ejecutando. Para probar que el código se está ejecutando, agregue una llamada a `System.Diagnostics.Debugger.Break`C#(/VB) o `__debugbreak`C++() a la línea de código en la que está intentando establecer el punto de interrupción y, a continuación, recompile el proyecto.
3. Si está depurando código optimizado, asegúrese de que la función en la que se establece el punto de interrupción no se inserta en otra función. La prueba de `Debugger.Break` descrita en la comprobación anterior también puede funcionar para probar este problema.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Eliminé un punto de interrupción, pero continúa alcanzándose al iniciar de nuevo la depuración

Si eliminó un punto de interrupción durante la depuración, puede volver a alcanzar el punto de interrupción la próxima vez que inicie la depuración. Para dejar de encontrar este punto de interrupción, asegúrese de que todas las instancias del punto de interrupción se quitan de la ventana **Puntos de interrupción** .
