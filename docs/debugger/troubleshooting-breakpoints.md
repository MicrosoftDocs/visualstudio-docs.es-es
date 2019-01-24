---
title: Solución de problemas de puntos de interrupción en el depurador | Microsoft Docs
ms.custom: seodec18
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a2afbff14be944e17a26df09d041d9267ac5cb87
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989914"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Solución de problemas de puntos de interrupción en el depurador de Visual Studio

## <a name="breakpoint-warnings"></a>Advertencias de punto de interrupción

Al depurar, un punto de interrupción tiene dos posibles estados visuales: un círculo rojo sólido y un hueco (blanco rellenada) círculo. Si el depurador puede establecer correctamente un punto de interrupción en el proceso de destino, permanecerá un círculo rojo sólido. Si el punto de interrupción es un círculo vacío, se deshabilita el punto de interrupción o se produjo una advertencia al intentar establecer el punto de interrupción. Para determinar la diferencia, mantenga el mouse sobre el punto de interrupción y ver si hay una advertencia.

Las dos secciones siguientes describen advertencias prominentes y cómo corregirlos. 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"No se ha cargado ningún símbolo para este documento" 

Vaya a la **módulos** ventana (**depurar** > **Windows** > **módulos**) y compruebe si el módulo es puede cargar.  
* Si se carga el módulo, compruebe el **estado del símbolo** columna para ver si se han cargado los símbolos. 
  * Si no se cargan los símbolos, compruebe el estado de símbolos para diagnosticar el problema. En el menú contextual en un módulo en el **módulos** ventana, haga clic en **información de carga de símbolos...**  para ver que se analizó el depurador para intentar cargar los símbolos. Para obtener más información sobre la carga de símbolos, vea [especificar símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  * Si los símbolos se cargan, el archivo PDB no contiene información acerca de los archivos de origen. Estas son algunas causas posibles: 
    * Si los archivos de origen se agregaron recientemente, confirme que se está cargando una versión actualizada del módulo.  
    * Es posible crear los archivos PDB eliminados mediante el **/PDBSTRIPPED** opción del vinculador. Los archivos PDB eliminados no contienen información de archivo de origen. Confirme que está trabajando con un completo PDB y no un archivo PDB eliminado.  
    * El archivo PDB parcial está dañado. Elimine el archivo y realizar una compilación limpia del módulo para intentar resolver el problema. 

* Si no se carga el módulo, compruebe lo siguiente para averiguar la causa: 
  * Confirme que está depurando el proceso correcto. 
  * Compruebe que está depurando el tipo correcto de código. Puede averiguar qué tipo de código, el depurador está configurado para depurar en el **procesos** ventana (**depurar** > **Windows**  >  **Procesos**). Por ejemplo, si está intentando depurar código de C#, confirme que el depurador está configurado para el tipo de .NET Framework adecuado (por ejemplo, administrado (v4\*) frente a administrado (v2\*/v3\*) frente a administrado (CoreCLR)). 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… el código fuente actual es diferente de la versión integrada en …" 

Si ha cambiado un archivo de origen y el origen ya no coincide con el código que se está depurando, el depurador no establecerá los puntos de interrupción en el código de forma predeterminada. Normalmente, este problema se produce cuando se modifica un archivo de origen, pero no se vuelven a generar el código fuente. Para corregir este problema, recompile el proyecto. Si el sistema de compilación se considera que el proyecto ya está actualizado, aunque no es así, puede forzar el sistema del proyecto para volver a generar por volver a guardar el archivo de origen o mediante la limpieza del proyecto salida antes de la compilación de la compilación. 

En casos poco frecuentes, es posible que desea depurar sin necesidad de código fuente coincidente. Depuración sin el correspondiente código fuente puede dar lugar a un confuso, la experiencia en depuración por lo que asegúrese de que trata cómo desea continuar.  

Para deshabilitar estas comprobaciones de seguridad, realice una de las siguientes acciones: 
* Para modificar un punto de interrupción, mantenga el mouse sobre el icono de punto de interrupción en el editor y haga clic en el icono de configuración (engranaje). Se agrega una ventana de peek en el editor. En la parte superior de la ventana de peek, hay un hipervínculo que indica la ubicación del punto de interrupción. Haga clic en el hipervínculo para permitir la modificación de la ubicación del punto de interrupción y comprobar **permitir que el código fuente sea diferente del original**.
* Para modificar esta configuración para todos los puntos de interrupción, vaya a **depurar** > **opciones y configuración**. En la página **Depuración/General** , desactive la opción **Es necesario que los archivos de código fuente coincidan con la versión original** . No olvide volver a habilitar esta opción cuando haya terminado la depuración. 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>El punto de interrupción se estableció correctamente (ninguna advertencia), pero no de aciertos 

Esta sección proporciona información para solucionar problemas cuando el depurador no muestra cualquier advertencia: el punto de interrupción es un círculo rojo sólido durante la depuración activamente, aunque no se vea afectado el punto de interrupción. 

Estos son algunos aspectos que debe comprobar: 
1. Si el código se ejecuta en más de un proceso o más de un equipo, asegúrese de que está depurando el proceso correcto o el equipo.  
2. Confirme que se está ejecutando el código. Para probar que se está ejecutando el código, agregue una llamada a `System.Diagnostics.Debugger.Break` (C# /VB) o `__debugbreak` (C++) a la línea de código donde está intentando establecer el punto de interrupción y, a continuación, recompile el proyecto. 
3. Si depura código optimizado, asegúrese de que la función donde se establece el punto de interrupción no se está insertada en otra función. El `Debugger.Break` prueba que se describe en la comprobación anterior puede trabajar para probar este problema también. 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Eliminé un punto de interrupción, pero continúa alcanzándose al iniciar de nuevo la depuración 

Si elimina un punto de interrupción durante la depuración, puede alcanzar el punto de interrupción en la próxima vez que se inicie la depuración. Para dejar de encontrar este punto de interrupción, asegúrese de que todas las instancias del punto de interrupción se quitan de la ventana **Puntos de interrupción** .  
