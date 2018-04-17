---
title: Solucionar problemas de puntos de interrupción en el depurador de Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 01/23/2018
ms.technology:
- vs-ide-debug
ms.topic: conceptual
author: carpediemma
ms.author: emrou
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93d8d2dacdc15e4ff92a31486f94b328b957ea55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Solucionar problemas de puntos de interrupción en el depurador de Visual Studio

## <a name="breakpoint-warnings"></a>Advertencias de punto de interrupción

Al depurar, un punto de interrupción tiene dos estados visuales posibles: un círculo rojo sólido y un hueco (blanco rellenado) círculo. Si el depurador puede establecer correctamente un punto de interrupción en el proceso de destino, permanecerá un círculo rojo sólido. Si el punto de interrupción es un círculo vacío, se deshabilita el punto de interrupción o se produjo una advertencia al intentar establecer el punto de interrupción. Para determinar la diferencia, mantenga el mouse sobre el punto de interrupción y ver si existe una advertencia.

Las dos secciones siguientes describen las advertencias prominentes y cómo corregirlos. 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"No se han cargado ningún símbolo para este documento" 

Vaya a la **módulos** ventana (**depurar** > **Windows** > **módulos**) y compruebe si el módulo es cargar.  
* Si se carga el módulo, compruebe el **estado del símbolo** columna para ver si se han cargado los símbolos. 
  * Si no se cargaron símbolos, compruebe el estado del símbolo para diagnosticar el problema. En el menú contextual en un módulo en el **módulos** ventana, haga clic en **información de carga de símbolos...**  para ver dónde busca el depurador para probar y cargar los símbolos. Para obtener más información sobre la carga de símbolos, vea [especificar símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  * Si se cargan los símbolos, esto significa que el archivo PDB no contiene información acerca de los archivos de origen. Estas son algunas causas posibles: 
    * Si los archivos de origen se agregaron recientemente, confirme que se está cargando una versión actualizada del módulo.  
    * Es posible crear archivos PDB eliminados mediante la **/PDBSTRIPPED** opción del vinculador. Archivos PDB eliminados no contienen información de archivo de origen. Confirme que está trabajando con un completo PDB y no es un archivo PDB eliminado.  
    * El archivo PDB parcialmente está dañado. Intente eliminar el archivo y realizar una compilación limpia del módulo para ver si resuelve el problema. 

* Si no se carga el módulo, compruebe lo siguiente para encontrar la causa: 
  * Confirme que está depurando el proceso adecuado. 
  * Compruebe que está depurando el tipo correcto de código. Puede averiguar qué tipo de código que el depurador está configurado para depurar en el **procesos** ventana (**depurar** > **Windows**  >  **Procesos**). Por ejemplo, si está intentando depurar código de C#, confirme que el depurador está configurado para el tipo de .NET Framework adecuado (por ejemplo, administrado (v4\*) frente a administrado (v2\*/v3\*) frente a administrado (CoreCLR)). 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… el código fuente actual es diferente de la versión integrada en..." 

Si un archivo de origen ha cambiado y el origen ya no coincide con el código que se está depurando, el depurador no establecerá los puntos de interrupción en el código de forma predeterminada. Normalmente, este problema se produce cuando se modifica un archivo de origen, pero no se vuelven a generar el código fuente. Para corregir este problema, vuelva a generar el proyecto. Si el sistema de compilación se considera que el proyecto ya está actualizado, aunque no es así, puede forzar el sistema del proyecto a generar mediante volver a guardar el archivo de origen o por el proyecto de limpieza de los resultados antes de generar compilación. 

En algunos casos, puede que desee depurar sin necesidad de código fuente correspondiente. Esto puede dar lugar a una experiencia de depuración muy confusa, por lo tanto, asegúrese de que se trata cómo desea continuar.  

Para deshabilitar estas comprobaciones de seguridad, realice una de las siguientes acciones: 
* Para modificar un punto de interrupción, mantenga el mouse sobre el icono de punto de interrupción en el editor y haga clic en el icono de configuración (engranaje). Una ventana de información se agrega al editor. En la parte superior de la ventana de información hay un hipervínculo que indica la ubicación del punto de interrupción. Haga clic en el hipervínculo para permitir la modificación de la ubicación de punto de interrupción y comprobar **permitir que el código fuente sea distinto de la versión original**.
* Para modificar esta configuración para todos los puntos de interrupción, vaya a **depurar** > **opciones y configuración**. En la página **Depuración/General** , desactive la opción **Es necesario que los archivos de código fuente coincidan con la versión original** . Asegúrese de volver a habilitar esta opción cuando haya terminado la depuración. 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>El punto de interrupción se estableció correctamente (ninguna advertencia), pero no de llamadas 

Esta sección proporciona información para solucionar problemas cuando el depurador no muestra las advertencias: el punto de interrupción es un círculo rojo sólido durante la depuración activamente, pero aún no se alcanza el punto de interrupción. 

Estas son algunas cosas para comprobar: 
1. Si el código se ejecuta en más de un proceso o en más de un equipo, asegúrese de que está depurando el proceso adecuado o equipo.  
2. Confirme que se ejecuta el código. Una forma sencilla de probar esto consiste en Agregar una llamada a `System.Diagnostics.Debugger.Break` (C# / VB) o `__debugbreak` (C++) a la línea de código donde está intentando establecer el punto de interrupción y, a continuación, recompile el proyecto. 
3. Si está depurando código optimizado, asegúrese de que la función donde se establece el punto de interrupción no está insertada en otra función. El `Debugger.Break` prueba descrita en la comprobación anterior puede funcionar para probar esto también. 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Eliminé un punto de interrupción, pero continúa alcanzándose al iniciar de nuevo la depuración 

Si elimina un punto de interrupción durante la depuración, puede alcanzado el punto de interrupción en la próxima vez que se inicie la depuración. Para dejar de encontrar este punto de interrupción, asegúrese de que todas las instancias del punto de interrupción se quitan de la ventana **Puntos de interrupción** .  
