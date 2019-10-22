---
title: Configurar un proyecto de C++ para IntelliSense
ms.date: 10/08/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 5c95990eb875c52a66cd0efa5579c9d39eab5469
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154906"
---
# <a name="configure-a-c-project-for-intellisense"></a>Configurar un proyecto de C++ para IntelliSense

En algunos casos, es posible que tenga que configurar manualmente el proyecto de C++ para que IntelliSense funcione correctamente. En los proyectos de MSBuild (basado en archivos .vcxproj), puede ajustar la configuración en las propiedades de los proyectos. En los proyectos que no son de MSBuild, puede ajustar la configuración en el archivo CppProperties.json del directorio raíz del proyecto. En algunos casos, puede que sea necesario crear un archivo de indicaciones para ayudar a que IntelliSense entienda las definiciones de macros. El IDE de Visual Studio ayuda a identificar y corregir problemas de IntelliSense.

## <a name="single-file-intellisense"></a>Intellisense de archivo único

Al abrir un archivo no incluido en un proyecto, Visual Studio proporciona cierta compatibilidad con IntelliSense pero no se muestra ningún subrayado ondulado de error. Si en la **barra de navegación** dice *Archivos varios*, eso probablemente explique por qué no ve ningún subrayado ondulado de error debajo del código incorrecto o por qué no hay definida ninguna macro de preprocesador.

## <a name="check-the-error-list"></a>Comprobar la lista de errores

Si un archivo no se abre en modo de archivo único e IntelliSense no funciona correctamente, el primer lugar que se debe revisar es la ventana Lista de errores. Para ver todos los errores de IntelliSense del archivo de origen actual junto con los archivos de encabezado incluidos, elija **Compilación + IntelliSense** en el menú desplegable:

![IntelliSense para VC++ en Lista de errores](media/vcpp-intellisense-error-list.png)

IntelliSense genera un máximo de 1000 errores. Si hay más de 1000 errores en los archivos de encabezado incluidos por un archivo de origen, solo se muestra un subrayado ondulado de error al inicio del archivo de origen.

## <a name="ensure-include-paths-are-correct"></a>Asegurarse de que las rutas de acceso #include sean correctas

### <a name="msbuild-projects"></a>Proyectos de MSBuild

Si ejecuta las compilaciones fuera del IDE de Visual Studio y se realizan correctamente, pero IntelliSense no es correcto, es posible que la línea de comandos no esté sincronizada con los ajustes de proyecto de una o más configuraciones. Haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y asegúrese de que todas las rutas de acceso **#include** sean correctas para la plataforma y configuración actuales. Si las rutas de acceso son idénticas en todas las configuraciones y plataformas, puede seleccionar **Todas las configuraciones** y **Todas las plataformas** y luego comprobar que las rutas de acceso sean correctas.

![Directorios de archivos de inclusión de VC++](media/vcpp-intellisense-include-paths.png)

Para ver los valores actuales de las macros de compilación como **VC_IncludePath**, seleccione la línea Directorios de archivos de inclusión y haga clic en el menú desplegable de la derecha. Luego elija **\<Editar>** y haga clic en el botón **Macros**.

### <a name="makefile-projects"></a>proyectos de archivos Make

Para proyectos de archivos Make basados en la plantilla de proyecto NMake, elija **NMake** en el panel de la izquierda y, luego, **Ruta de acceso de búsqueda de inclusión** en la categoría **IntelliSense**:

![Rutas de acceso de inclusión de proyectos de archivos Make](media/vcpp-intellisense-makefile-include-paths.png)

### <a name="open-folder-projects"></a>Proyectos Abrir carpeta

En el caso de los proyectos CMake, asegúrese de que las rutas de acceso #include están correctamente especificadas para todas las configuraciones en CMakeLists.txt. Es posible que otros tipos de proyecto requieran un archivo CppProperties.json. Para más información, consulte [Configurar IntelliSense con CppProperties.json](/cpp/build/open-folder-projects-cpp#configure-code-navigation-with-cpppropertiesjson). Asegúrese de que las rutas de acceso sean correctas para cada configuración definida en el archivo.

Si hay un error de sintaxis en el archivo CppProperties.json, IntelliSense será incorrecto en los archivos afectados. Visual Studio mostrará el error en la ventana de salida.

## <a name="tag-parser-issues"></a>Problemas con el analizador de etiquetas

El analizador de etiquetas es un analizador "aproximado" de C++ que se usa para exploración y navegación. Es muy rápido, pero no intenta comprender completamente cada construcción de código.

Por ejemplo, no evalúa las macros de preprocesador y, por tanto, es posible que analice incorrectamente el código que las usa de manera intensiva. Cuando el analizador de etiquetas encuentra una construcción de código desconocida, puede que imita toda esa región de código.

Este problema se manifiesta de dos maneras habituales en Visual Studio:

1. Si en la barra de navegación se muestra una macro más interna, se omitió la definición de función actual:

   ![El analizador de etiquetas omite la definición de función](media/vcpp-intellisense-tag-parser-macro.png)

1. El IDE ofrece crear la definición de una función ya definida:

   ![El analizador de etiquetas ofrece definir una función ya existente](media/vcpp-intellisense-tag-parser-function.png)

Para corregir estos problemas, agregue un archivo llamado **cpp.hint** en la raíz del directorio de la solución. Para más información, consulte [Archivos de indicaciones](/cpp/build/reference/hint-files).

Los errores del analizador de etiquetas aparecen en la ventana **Lista de errores**.

## <a name="validate-project-settings-with-diagnostic-logging"></a>Validar la configuración del proyecto con el registro de diagnóstico

Para comprobar si el compilador de IntelliSense usa las opciones del compilador correctas, incluidas las rutas de acceso de inclusión y las macros de preprocesador, active Registro de diagnóstico de las líneas de comandos de IntelliSense en **Herramientas > Opciones > Editor de texto > C/C++ > Avanzadas > Registro de diagnóstico**. Establezca **Enable Logging** (Habilitar registro) en True, **Logging Level** (Nivel de registro) en 5 (el más detallado) y **Logging Filter** (Filtro de registro) en 8 (registro de IntelliSense).

La ventana de salida ahora mostrará las líneas de comandos que se pasan al compilador de IntelliSense. Esta es una salida de ejemplo:

```output
[IntelliSense] Configuration Name: Debug|Win32
[IntelliSense] Toolset IntelliSense Identifier:
[IntelliSense] command line options:
/c
/I.
/IC:\Repo\Includes
/DWIN32
/DDEBUG
/D_DEBUG
/Zc:wchar_t-
/Zc:forScope
/Yustdafx.h
```

Esta información puede ayudarlo a entender por qué IntelliSense proporciona información inexacta. Por ejemplo, si el directorio de archivos de inclusión del proyecto contiene **$(MyVariable)\Include** y el registro de diagnóstico muestra **/I\Include** como una ruta de acceso de inclusión, significa que no se evaluó **$(MyVariable)** y que se quitó de la ruta de acceso de inclusión final.

## <a name="about-the-intellisense-build"></a>Información sobre la compilación de IntelliSense

Visual Studio usa un compilador de C++ dedicado para crear y mantener la base de datos que activa todas las características de IntelliSense. Para mantener la base de datos de IntelliSense sincronizada con el código, Visual Studio inicia automáticamente compilaciones solo de IntelliSense como tareas en segundo plano como respuesta a ciertos cambios hechos en la configuración del proyecto o los archivos de origen.

Sin embargo, es posible que en algunos casos, Visual Studio no actualice la base de datos de IntelliSense de manera oportuna. Por ejemplo, cuando se ejecuta un comando **git pull** o **git checkout**, puede que Visual Studio tarde hasta una hora en detectar los cambios en los archivos. Para forzar que se vuelvan a examinar todos los archivos de una solución, haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y elija **Volver a examinar la solución**.

## <a name="troubleshooting-intellisense-build-failures"></a>Solución de problemas y errores de compilación de IntelliSense

Una compilación de IntelliSense no genera archivos binarios, pero de todos modos pueden producir un error. Una causa posible de error son los archivos personalizados .props o .targets. En Visual Studio 2017 versión 15.6 y posteriores, los errores de compilación solo de IntelliSense se registran en la ventana de salida. Para verlos, establezca **Mostrar resultados desde** en **Solución**:

![Ventana de salida para errores de la solución](media/vcpp-intellisense-output-window.png)

Es posible que el mensaje de error le indique habilitar el seguimiento en tiempo de diseño:

```output
error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
configuration 'Debug|x64'. IntelliSense might be unavailable.
Set environment variable TRACEDESIGNTIME=true and restart
Visual Studio to investigate.
```

Si establece la variable de entorno TRACEDESIGNTIME en true y reinicia Visual Studio, verá un archivo de registro en el directorio %TEMP%, que podría ayudar a diagnosticar el error de la compilación.

Para más información sobre la variable de entorno TRACEDESIGNTIME, consulte [Roslyn](https://github.com/dotnet/roslyn/wiki/Diagnosing-Project-System-Build-Errors) y [Common Project System](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md) (Sistema de proyectos comunes). La información que aparece en estos artículos se aplica a los proyectos de C++.

## <a name="see-also"></a>Otras referencias

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
