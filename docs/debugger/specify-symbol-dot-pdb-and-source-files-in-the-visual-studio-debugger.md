---
title: Establece los archivos de código fuente y símbolos (.pdb) en el depurador
ms.custom: seodec18
ms.date: 10/08/2018
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f2343d71d2ed0745f9c5a2a799c3018a2e64945
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746248"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Especificar archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio (C#, C++, Visual Basic, F#)

Base de datos de programa ( *.pdb*) archivos, denominados también archivos de símbolos, asignan identificadores y las instrucciones de código fuente de su proyecto a sus identificadores correspondientes y las instrucciones de compilan aplicaciones.

Al compilar un proyecto desde el IDE de Visual Studio con el estándar de configuración de compilación de depuración, el compilador crea los archivos de símbolos adecuados. También puede [establecer opciones de símbolo en el código](#compiler-symbol-options).

El *.pdb* archivo contiene información de estado de depuración y del proyecto que permite la vinculación incremental de una configuración de depuración de la aplicación. El depurador de Visual Studio utiliza *.pdb* archivos para determinar dos elementos clave de información durante la depuración:

* El origen archivo nombre y número de línea que se muestra en el IDE de Visual Studio.
* Punto de la aplicación para detener un punto de interrupción.

Los archivos de símbolos también muestran la ubicación de los archivos de origen y, opcionalmente, recuperarlos desde el servidor.

El depurador solo carga *.pdb* archivos que coincidan exactamente con el *.pdb* archivos creados cuando se compila una aplicación (es decir, el original *.pdb* copias o archivos). Esta duplicación exacta es necesaria porque puede cambiar el diseño de aplicaciones incluso si no ha cambiado el propio código. Para obtener más información, vea [Why does Visual Studio require debugger symbol files to *exactly* match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/) ¿Por qué Visual Studio requiere que los archivos de símbolo del depurador coincidan exactamente con los archivos binarios con los que se crearon?

> [!TIP]
> Para depurar el código fuera de su código fuente del proyecto, como las llamadas de proyecto de código de código de Windows o de terceros, debe especificar la ubicación del código externo *.pdb* archivos (y opcionalmente, los archivos de origen), que debe coincidir exactamente con las compilaciones en la aplicación.

## <a name="symbol-file-locations-and-loading-behavior"></a>Ubicaciones del archivo de símbolos y el comportamiento de carga

> [!NOTE]
> Al depurar código administrado en un dispositivo remoto, todos los archivos de símbolos deben encontrarse en el equipo local o en una ubicación [especificado en las opciones del depurador](#BKMK_Specify_symbol_locations_and_loading_behavior).

Cuando se depura un proyecto en el IDE de Visual Studio, el depurador carga automáticamente los archivos de símbolos que se encuentran en la carpeta del proyecto.

El depurador también busca los archivos de símbolos en las siguientes ubicaciones:

1. La ubicación especificada dentro del archivo DLL o el archivo ejecutable ( *.exe*) archivo.

   De forma predeterminada, si se ha creado un archivo DLL o un *.exe* archivo en el equipo, el vinculador coloca la ruta de acceso completa y el nombre del asociado *.pdb* archivo en el archivo DLL o *.exe* archivo. El depurador comprueba si existe el archivo de símbolos en esa ubicación.

2. La misma carpeta que el archivo DLL o *.exe* archivo.

3. Las ubicaciones especificadas en las opciones del depurador para los archivos de símbolos. Para agregar y habilitar ubicaciones de símbolos, vea [configurar ubicaciones de símbolos y las opciones de carga](#BKMK_Specify_symbol_locations_and_loading_behavior).

   - Cualquier carpeta de caché de símbolos local.

   - Especifica la red, internet, o servidores de símbolos local y ubicaciones, como los servidores de símbolos de Microsoft si ha seleccionado. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Puede descargar los archivos de símbolos de depuración de servidores de símbolos que implementan el `symsrv` protocolo. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) y [herramientas de depuración para Windows](/windows-hardware/drivers/debugger/index) son dos herramientas que pueden usar servidores de símbolos.

     Servidores de símbolos que podría utilizar incluyen:

     **Servidores de símbolos públicos de Microsoft**: Para depurar un bloqueo que se produce durante una llamada a un archivo DLL del sistema o a una biblioteca de terceros, a menudo necesita sistema *.pdb* archivos. Sistema *.pdb* archivos contienen símbolos para archivos DLL de Windows, *.exe* archivos y controladores de dispositivos. Puede obtener los símbolos para los sistemas operativos Windows, MDAC, IIS, ISA y .NET Framework de los servidores de símbolos públicos de Microsoft.

     **Servidores de símbolos de una red interna o del equipo local**: Su equipo o compañía puede crear servidores de símbolos para sus propios productos y como memoria caché de símbolos de orígenes externos. Podría tener un servidor de símbolos en su propio equipo.

     **Servidores de símbolos de terceros**: Los proveedores de aplicaciones Windows y bibliotecas de terceros pueden proporcionar acceso al servidor de símbolos en Internet.

     > [!WARNING]
     > Si usa un servidor de símbolos que no sean los servidores de símbolos públicos de Microsoft, asegúrese de que el servidor de símbolos y su ruta de acceso son de confianza. Dado que los archivos de símbolos pueden contener código ejecutable arbitrario, pueden exponerse a amenazas de seguridad.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Configurar ubicaciones de símbolos y las opciones de carga

En el **herramientas** > **opciones** > **depuración** > **símbolos** página, puede:

- Especificar y seleccione las rutas de búsqueda y servidores de símbolos de Microsoft, Windows o componentes de terceros.
- Especifique los módulos que desea o no desea que el depurador cargue símbolos automáticamente.
- Cambiar esta configuración mientras está depurando activamente. Consulte [administrar símbolos durante la depuración](#manage-symbols-while-debugging).

**Para especificar ubicaciones de símbolos y las opciones de carga:**

1. En Visual Studio, abra **herramientas** > **opciones** > **depuración** > **símbolos** (o **Depurar** > **opciones** > **símbolos**).

   ![Herramientas &#45; opciones &#45; depuración &#45; página símbolos](media/dbg-options-symbols.png "herramientas &#45; opciones &#45; depuración &#45; página símbolos")

2. En **ubicaciones de archivo (.pdb) de símbolos**,
   - Para usar el **servidores de símbolos de Microsoft**, active la casilla de verificación.

   - Para agregar una nueva ubicación de servidor de símbolos
     1. Seleccione el **+** símbolo en la barra de herramientas.
     1. Escriba la ruta de acceso de dirección URL o una carpeta del servidor de símbolos o ubicación de símbolos en el campo de texto. La finalización de instrucciones le será de ayuda para especificar el formato correcto.

     >[!NOTE]
     >Se busca solo en la carpeta especificada. Debe agregar entradas para todas las subcarpetas que desea buscar.

   - Para agregar una nueva ubicación de servidor de símbolos de VSTS,
     1. Seleccione el ![herramientas&#47; opciones&#47; depuración&#47;icono del nuevo servidor de símbolos](media/dbg_tools_options_foldersicon.png "herramientas &#45; opciones &#45; depuración &#45; icono del nuevo servidor de símbolos") icono en la barra de herramientas.
     1. En el **conectar al servidor de símbolos de VSTS** cuadro de diálogo, elija uno de los servidores de símbolos disponibles y seleccione **Connect**.

   - Para cambiar el orden de carga para las ubicaciones de símbolos, use **Ctrl**+**seguridad** y **Ctrl**+**abajo**, o el **seguridad** y **abajo** iconos de flecha.
   - Para editar una dirección URL o ruta de acceso, haga doble clic en la entrada, o selecciónelo y presione **F2**.
   - Para quitar una entrada, selecciónelo y, a continuación, seleccione el **-** icono.

3. (Opcional) Para mejorar el rendimiento de la carga de símbolos, en **almacenar en caché los símbolos de este directorio**, una ruta de acceso de carpeta local que pueden copiar los servidores de símbolos de los símbolos para el tipo.

   > [!NOTE]
   > No coloque la memoria caché de símbolos local en una carpeta protegida, como C:\Windows o una subcarpeta. Utilice una carpeta de lectura y escritura en su lugar.

   > [!NOTE]
   > Los proyectos de C++, si tiene la `_NT_SYMBOL_PATH` conjunto de variables de entorno, reemplazará el valor establecido en **almacenar en caché los símbolos de este directorio**.

4. Especifique los módulos que desea que el depurador cargue desde el **ubicaciones de archivo (.pdb) de símbolos** cuando se inicia.

   - Seleccione **cargar todos los módulos, excepto los excluidos** (predeterminado) para cargar todos los símbolos para todos los módulos en la ubicación del archivo de símbolos, excepto los módulos que las excluya expresamente. Para excluir ciertos módulos, seleccione **especificar módulos excluidos**, seleccione el **+** icono, escriba los nombres de los módulos para excluir y seleccione **Aceptar**.

   - Para cargar solo los módulos especificados a partir de las ubicaciones de archivos de símbolos, seleccione **carga solo los módulos especificados**. Seleccione **especificar módulos incluidos**, seleccione el **+** icono, escriba los nombres de los módulos para incluir y, a continuación, seleccione **Aceptar**. No se cargan los archivos de símbolos de otros módulos.

5. Seleccione **Aceptar**.

## <a name="other-symbol-options-for-debugging"></a>Otras opciones de símbolos de depuración

Puede seleccionar opciones de símbolos adicionales en **herramientas** > **opciones** > **depuración** > **General** (o **depurar** > **opciones** > **General**):

- **Cargar exportaciones de dll (solo nativas)**

  Las tablas de exportación de DLL de carga para C/C ++. Para obtener más información, consulte [DLL exporta tablas](#use-dumpbin-exports). Exportar información de lectura DLL implica cierta sobrecarga, por lo que al cargar las tablas de exportación se ha desactivado de forma predeterminada. También puede usar `dumpbin /exports` en una línea de comandos de compilación de C/C ++.

- **Habilitar la depuración de nivel de dirección** y **Mostrar desensamblado si el código fuente no está disponible**

  Muestra siempre el desensamblado cuando no se encuentran los archivos de origen o de símbolos.

  ![Opciones de &#47; depuración &#47; opciones generales de desensamblado](../debugger/media/dbg_options_general_disassembly_checkbox.png "opciones &#47; depuración &#47; opciones generales de desensamblado")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Habilitar compatibilidad de servidor de origen**

  Servidor de origen se utiliza para ayudar a depurar una aplicación cuando no hay ningún código de origen en el equipo local, o el *.pdb* archivo no coincide con el código fuente. Servidor de origen recoge solicitudes de archivos y devuelve los archivos de control de código fuente. Servidor de origen se ejecuta mediante un archivo DLL denominado *srcsrv.dll* para leer la aplicación *.pdb* archivo. El *.pdb* archivo contiene punteros al repositorio de código fuente, así como los comandos usados para recuperar el código fuente desde el repositorio.

  Puede limitar los comandos que *srcsrv.dll* puede ejecutar desde la aplicación *.pdb* archivo con una lista de los comandos permitidos en un archivo denominado *srcsrv.ini*. Colocar el *srcsrv.ini* archivo en la misma carpeta que *srcsrv.dll* y *devenv.exe*.

  >[!IMPORTANT]
  >Se pueden incrustar comandos arbitrarios en una aplicación *.pdb* de archivos, así que asegúrese de colocar únicamente los comandos que desea ejecutar en un *srcsrv.ini* archivo. Todo intento de ejecutar un comando no incluido en el archivo *srcsvr.ini* provocará la aparición de un cuadro de diálogo de confirmación. Para obtener más información, consulte [advertencia de seguridad: El depurador debe ejecutar un comando que no es de confianza](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >No se realiza ninguna validación de los parámetros de comando, por lo que debe tener cuidado con los comandos de confianza. Por ejemplo, si se ha incluido *cmd.exe* en su *srcsrv.ini*, un usuario malintencionado podría especificar parámetros de *cmd.exe* que sería peligroso.

  Seleccione este elemento y los elementos secundarios que desee. **Permitir servidor de origen para ensamblados de confianza parcial (solo administrado)** y **ejecutar comandos de servidor de origen de confianza sin preguntar siempre** puede aumentar los riesgos de seguridad.

  ![Habilitar las opciones de servidor de origen](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>Opciones del compilador de símbolos

Cuando compila un proyecto desde el IDE de Visual Studio con el estándar **depurar** configuración de compilación, C++ y los compiladores administrados crean archivos de símbolos adecuados para el código. También puede establecer las opciones del compilador en código.

### <a name="cc-options"></a>Opciones de C/C++

- *VC\<x > .pdb* y  *\<proyecto > .pdb* archivos

  Un *.pdb* archivo de C o C++ se crea cuando se compila con [/Zi o/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format). En [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], [/Fd](/cpp/build/reference/fd-program-database-file-name) opción nombres la *.pdb* el compilador crea el archivo. Cuando se crea un proyecto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mediante el IDE, el **/Fd** se establece la opción para crear un *.pdb* archivo denominado  *\<proyecto > .pdb*.

  Si compila la aplicación de C/C ++ mediante un archivo MAKE y especifica **/Zi** o **/Zi** sin usar **/Fd**, el compilador crea dos *.pdb*archivos:

  - *VC\<x>.pdb*, donde *\<x>* representa la versión de Visual C++, por ejemplo *VC11.pdb*

    El *VC\<x > .pdb* archivo almacena toda información de depuración para los archivos de objeto individuales y reside en el mismo directorio que el archivo MAKE del proyecto. Cada vez que crea un archivo de objeto, el compilador de C/C ++ combina la información de depuración en *VC\<x > .pdb*. Por tanto, incluso si cada archivo de código fuente incluye archivos de encabezado comunes como  *\<windows.h >* , se almacenan las definiciones de tipo de esos encabezados solo una vez, en lugar de en todos los archivos objeto. La información insertada incluye información de tipo, pero no información de símbolo como definiciones de función.

  - *\<project>.pdb*

    El  *\<proyecto > .pdb* archivo almacena toda la información de depuración para el proyecto *.exe* de archivos y reside en el *\debug* subdirectorio. El archivo *\<proyecto.pdb* contiene toda la información de depuración, incluidos los prototipos de función, y no solo la información de tipo que se encuentra en *VC\<x>.pdb*.

  Tanto el *VC\<x > .pdb* y  *\<proyecto > .pdb* archivos permiten actualizaciones incrementales. El vinculador también incrusta la ruta de acceso a la *.pdb* archivos en el *.exe* o *.dll* archivo que crea.

- <a name="use-dumpbin-exports"></a>Tablas de exportación DLL

  Use `dumpbin /exports` para ver los símbolos disponibles en la tabla de exportación de un archivo DLL. Información simbólica de las tablas de exportación DLL puede ser útil para trabajar con mensajes de Windows, procedimientos de Windows (WindowProc), COM objetos, el cálculo de referencias o cualquier archivo DLL no tiene los símbolos para. Los símbolos están disponibles para cualquier archivo DLL de sistema de 32 bits. Las llamadas se muestran en una lista según el orden de llamada, y la función actual (la que está anidada a mayor profundidad) aparece en la parte superior.

  Leyendo el `dumpbin /exports` de salida, puede ver los nombres de función exacto, incluidos los caracteres no alfanuméricos. Ver los nombres de función exacta es útil para establecer un punto de interrupción en una función, como los nombres de función se pueden truncar en otro lugar en el depurador. Para obtener más información, vea [dumpbin /exports](/cpp/build/reference/dash-exports).

### <a name="net-framework-options"></a>Opciones de .NET Framework

Compilar con **/debug** para crear un *.pdb* archivo. Puede compilar las aplicaciones con **/debug:full** o **/debug:pdbonly**. La compilación mediante **/debug:full** genera código depurable. La compilación mediante **/debug:pdbonly** genera archivos *.pdb*, pero no genera el atributo `DebuggableAttribute` que indica al compilador JIT que existe información de depuración disponible. Use **/debug:pdbonly** si quiere generar archivos *.pdb* para una compilación de versión que no quiere que sea depurable. Para obtener más información, vea [/debug (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) (/degug [Opciones del compilador de C#]) o [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug) (/debug [Visual Basic]).

### <a name="web-applications"></a>Aplicaciones web

Establecer el *web.config* archivo de la aplicación ASP.NET en modo de depuración. El modo de depuración hace que ASP.NET genere símbolos para los archivos generados dinámicamente y permite al depurador asociarse a la aplicación ASP.NET. Visual Studio lo establece automáticamente cuando empiece a depurar, si ha creado el proyecto de la plantilla de proyectos web.

## <a name="manage-symbols-while-debugging"></a>Administrar símbolos durante la depuración

Puede usar el **módulos**, **pila de llamadas**, **variables locales**, **automático**, o cualquier **inspección** ventana para cargar los símbolos o cambiar las opciones de símbolos durante la depuración. Para obtener más información, consulte [familiarizarse más con cómo el depurador se asocia a la aplicación](../debugger/debugger-tips-and-tricks.md#modules_window).

### <a name="use-the-modules-window"></a>Uso de la ventana Módulos

Durante la depuración, la **módulos** ventana muestra los módulos de código, el depurador está tratando como código de usuario, o mi código y su estado de carga de símbolos. También puede supervisar el estado de la carga de símbolos, cargar los símbolos y cambiar las opciones del símbolo en el **módulos** ventana.

**Para supervisar o cambiar las opciones o ubicaciones de símbolos durante la depuración:**

1. Para abrir el **módulos** ventana, durante la depuración, seleccione **depurar** > **Windows** > **módulos**.
1. En el **módulos** ventana, haga clic en el **estado del símbolo** o **el archivo de símbolos** encabezados o cualquier módulo.
1. En el menú contextual, seleccione una de las siguientes opciones:

|Opción|Descripción|
|------------|-----------------|
|**Cargar símbolos**|Aparece para los módulos con símbolos omitidos, no se encuentra o no está cargados. Intenta cargar símbolos desde las ubicaciones especificadas en el **opciones** > **depuración** > **símbolos** página. Si el archivo de símbolos no se encuentra o no está cargado, inicia **Explorador de archivos** por lo que puede especificar una ubicación nueva para buscar.|
|**Información de carga de símbolos**|Muestra la ubicación de un archivo de símbolos cargado, o las ubicaciones buscadas en caso de que el depurador no encuentra el archivo.|
|**Configuración de símbolos**|Se abre el **opciones** > **depuración** > **símbolos** página, donde puede editar y agregar ubicaciones de símbolos.|
|**Cargar siempre automáticamente**|Agrega el archivo de símbolos seleccionados a la lista de archivos que se cargan automáticamente el depurador.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Use las páginas No Loaded/No origen se cargaron símbolos

Hay varias maneras para que el depurador interrumpir el código que no tiene archivos de origen o de símbolos disponibles:

- Ir al código.
- Interrumpir el código desde un punto de interrupción o una excepción.
- Cambiar a un subproceso diferente.
- Cambiar el marco de pila haciendo doble clic en un marco en el **pila de llamadas** ventana.

Cuando esto sucede, el depurador muestra el **No se cargaron símbolos** o **No se cargaron orígenes** páginas que le ayudarán a encontrar y cargar el origen o los símbolos necesarios.

 ![No hay ninguna página se cargaron símbolos](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**Para usar la página del documento No se cargaron símbolos para ayudar a encontrar y cargar los símbolos que faltan:**

- Para cambiar la ruta de acceso de búsqueda, seleccione una ruta de acceso no seleccionada o seleccione **nueva ruta de acceso** o **nueva ruta de acceso de VSTS** y escriba o seleccione una nueva ruta de acceso. Seleccione **cargar** para buscar las rutas de acceso nuevo y cargar el archivo de símbolos si se encuentra.
- Para invalidar cualquier opción de símbolo y reintentar las rutas de búsqueda, seleccione **examinar y buscar \<ejecutable-name >** . Se carga el archivo de símbolos si se encuentra, o **Explorador de archivos** se abre para que pueda seleccionar manualmente el archivo de símbolos.
- Para abrir el **opciones** > **depuración** > **símbolos** página, seleccione **cambiar configuración de símbolos**.
- Para mostrar el desensamblado en una nueva ventana una vez, seleccione **ver desensamblado**, o bien seleccione **cuadro de diálogo Opciones** para establecer la opción para mostrar siempre el desensamblado cuando no se encuentran los archivos de origen o de símbolos.
- Para mostrar las ubicaciones que busca y el resultado, expanda **información de carga de símbolos**.

Si el depurador busca la *.pdb* archivo después de ejecutar una de las opciones y puede recuperar el archivo de origen con la información de la *.pdb* archivo, muestra el origen. En caso contrario, muestra un **No se cargaron orígenes** página que describe el problema, con vínculos a las acciones que podrían resolver el problema.

**Para agregar rutas de búsqueda del archivo de origen a una solución:**

Puede especificar las ubicaciones que el depurador busca archivos de código fuente y excluir determinados archivos de la búsqueda.

1. Seleccione la solución en **el Explorador de soluciones**y, a continuación, seleccione el **propiedades** icono, presione **Alt**+**ENTRAR**, o Haga clic en y seleccione **propiedades**.

1. Seleccione **depurar archivos de código fuente**.

1. En **directorios que contienen código fuente**, escriba o seleccione las ubicaciones de código fuente para buscar. Use el **nueva línea** icono para agregar más ubicaciones, el **seguridad** y **abajo** iconos de flecha para reordenarlas, o el **X** icono para eliminarlos.

   >[!NOTE]
   >El depurador busca sólo el directorio especificado. Debe agregar entradas para cualquier subdirectorio que desee buscar.

1. En **no buscar estos archivos de código fuente**, escriba los nombres de archivos de origen para excluir de la búsqueda.

1. Seleccione **Aceptar** o **aplicar**.

## <a name="see-also"></a>Vea también
- [Comprender los archivos de símbolos y la configuración de símbolos de Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Cambios en la carga remota de símbolos .NET en Visual Studio 2012 y 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
