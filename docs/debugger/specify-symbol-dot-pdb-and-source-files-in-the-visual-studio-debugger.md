---
title: Definición de archivos de código fuente y símbolos (.pdb) en el depurador
description: Más información sobre cómo configurar y administrar archivos de código fuente y símbolos en Visual Studio
ms.custom: ''
ms.date: 10/31/2019
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 496994c0f9d546efe8804481230081090309d47e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903571"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Definición de archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio (C#, C++, Visual Basic, F#)

Los archivos de base de datos de programa ( *.pdb*), también denominados archivos de símbolos, asignan los identificadores y las instrucciones en el código fuente del proyecto a los identificadores y las instrucciones correspondientes en las aplicaciones compiladas. Estos archivos de asignación vinculan el depurador al código fuente, lo que permite la depuración.

Cuando se compila un proyecto desde el IDE de Visual Studio con la configuración de compilación de depuración estándar, el compilador crea los archivos de símbolos adecuados. En este artículo se describe cómo administrar archivos de símbolos en el IDE; por ejemplo, cómo [especificar la ubicación de los símbolos en las opciones del depurador](#BKMK_Specify_symbol_locations_and_loading_behavior), cómo [comprobar el estado de carga de los símbolos](#work-with-symbols-in-the-modules-window) durante la depuración y cómo [establecer opciones de símbolo en el código](#compiler-symbol-options).

Para obtener una explicación detallada de los archivos de símbolos, consulte lo siguiente:

- [Descripción de los archivos de símbolos y la configuración de símbolos de Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [¿Por qué Visual Studio requiere que los archivos de símbolos del depurador coincidan exactamente con los archivos binarios con los que se compilaron?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with)

## <a name="how-symbol-files-work"></a>Cómo funcionan los archivos de símbolos

El archivo *.pdb* contiene información sobre el estado de la depuración y del proyecto que permite la vinculación incremental de una configuración de depuración de la aplicación. El depurador de Visual Studio usa archivos *.pdb* para determinar dos partes clave de la información durante la depuración:

* Nombre y número de línea del archivo de código fuente que se va a mostrar en el IDE de Visual Studio.
* En qué parte de la aplicación detenerse durante un punto de ruptura.

Los archivos de símbolos también muestran la ubicación de los archivos de origen y, opcionalmente, el servidor del que se recuperan.

El depurador solo carga archivos *.pdb* que coinciden exactamente con los archivos *.pdb* creados al compilar una aplicación (es decir, los archivos *.pdb* originales o copias). Esta [duplicación exacta](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with) es necesaria porque el diseño de las aplicaciones puede cambiar aunque el propio código no haya cambiado.

> [!TIP]
> Para depurar código externo al código fuente del proyecto, por ejemplo código de Windows o de terceros que el proyecto llame, tiene que especificar la ubicación de los archivos *.pdb* del código externo (y, opcionalmente, de los archivos de código fuente), que deben coincidir exactamente con la versión de compilación de los archivos ejecutables.

## <a name="symbol-file-locations-and-loading-behavior"></a>Ubicaciones de archivos de símbolos y comportamiento de carga

Cuando se depura un proyecto en el IDE de Visual Studio, el depurador carga automáticamente los archivos de símbolos que se encuentran en la carpeta del proyecto.

> [!NOTE]
> Al depurar código administrado en un dispositivo remoto, todos los archivos de símbolos deben encontrarse en la máquina local o en una ubicación [especificada en las opciones del depurador](#BKMK_Specify_symbol_locations_and_loading_behavior).

El depurador busca también archivos de símbolos en las siguientes ubicaciones:

1. La ubicación que se especifica en el archivo DLL o el archivo ejecutable ( *.exe*).

   De forma predeterminada, si ha compilado un archivo DLL o *.exe* en su equipo, el vinculador coloca la ruta de acceso completa y el nombre del archivo *.pdb* asociado dentro del archivo DLL o *.exe*. El depurador comprueba si el archivo de símbolos existe en esa ubicación.

2. La misma carpeta que el archivo DLL o *.exe*.

3. Las ubicaciones especificadas en las opciones del depurador para los archivos de símbolos. Para agregar y habilitar ubicaciones de símbolos, consulte [Configuración de ubicaciones de símbolos y opciones de carga](#BKMK_Specify_symbol_locations_and_loading_behavior).

   - Cualquier carpeta de caché de símbolos local.

   - Ubicaciones y servidores de red, Internet o de símbolos locales especificados, como los servidores de símbolos de Microsoft, si se seleccionan. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede descargar archivos de símbolos de depuración de servidores de símbolos que implementan el protocolo `symsrv`. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) y las [Herramientas de depuración para Windows](/windows-hardware/drivers/debugger/index) son dos herramientas que pueden usar servidores de símbolos.

     Los servidores de símbolos que podría utilizar incluyen:

     **Servidores de símbolos públicos de Microsoft**: Para depurar un bloqueo que se produzca durante una llamada a un archivo DLL del sistema o a una biblioteca de terceros, generalmente necesitará archivos *.pdb* del sistema. Los archivos *.pdb* del sistema contienen símbolos para archivos DDL de Windows, archivos *.exe* y controladores de dispositivos. Puede obtener símbolos para los sistemas operativos Windows, MDAC, IIS, ISA y .NET desde los servidores de símbolos públicos de Microsoft.

     **Servidores de símbolos de una red interna o del equipo local**: Su equipo o compañía puede crear servidores de símbolos para sus propios productos y como memoria caché de símbolos de orígenes externos. Podría tener un servidor de símbolos en su propio equipo.

     **Servidores de símbolos de terceros**: Los proveedores de aplicaciones Windows y bibliotecas de terceros pueden proporcionar acceso al servidor de símbolos en Internet.

     > [!WARNING]
     > Si utiliza un servidor de símbolos distinto de los servidores de símbolos públicos de Microsoft, asegúrese de que el servidor de símbolos y la ruta de acceso son de confianza. Dado que los archivos de símbolos pueden contener código ejecutable arbitrario, puede que se vea expuesto a amenazas de seguridad.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Configuración de ubicaciones de símbolos y opciones de carga

En la página **Herramientas** > **Opciones** > **Depuración** > **Símbolos**, puede:

- Especificar y seleccionar rutas de búsqueda y servidores de símbolos para componentes de Microsoft, de Windows o de terceros.
- Especificar los módulos para los que quiere que el depurador cargue símbolos automáticamente.
- Cambiar esta configuración mientras depura activamente. Consulte [Administración de símbolos durante la depuración](#manage-symbols-while-debugging).

**Para especificar las ubicaciones de símbolos y el comportamiento de carga:**

1. En Visual Studio, abra **Herramientas** > **Opciones** > **Depuración** > **Símbolos** (o **Depurar** > **Opciones** > **Símbolos**).

2. En **Ubicaciones del archivo de símbolos (.pdb)** .
   - Para usar **Servidores de símbolos de Microsoft** o **Servidor de símbolos de NuGet.org**, active la casilla.

   - Para agregar una nueva ubicación del servidor de símbolos:
     1. Seleccione el símbolo **+** en la barra de herramientas.
     1. Escriba la dirección URL (http), el recurso compartido de red o la ruta de acceso local del servidor de símbolos o la ubicación del símbolo en el campo de texto. La finalización de instrucciones le será de ayuda para especificar el formato correcto.

     Página ![Herramientas > Opciones > Depuración > Símbolos](media/dbg-options-symbols.gif "Página Herramientas &#45; Opciones &#45; Depuración &#45; Símbolos")

     >[!NOTE]
     >Solo se busca en la carpeta especificada. Ha de agregar entradas para las subcarpetas en las que quiera buscar.

   - Para agregar una nueva ubicación del servidor de símbolos de VSTS,
     1. Seleccione el icono de nuevo servidor ![Herramientas\Opciones \Depuración\Símbolos](media/dbg_tools_options_foldersicon.png "Icono de nuevo servidor Herramientas &#45; Opciones &#45; Depuración &#45; Símbolos") en la barra de herramientas.
     1. En el cuadro de diálogo **Conectar al servidor de símbolos de VSTS**, elija uno de los servidores de símbolos disponibles y elija **Conectar**.

   - Para cambiar el orden de carga de las ubicaciones de símbolos, use **Ctrl**+**Arriba** y **Ctrl**+**Abajo** o los iconos de flecha **arriba** y **abajo**.
   - Para editar una dirección URL o una ruta de acceso, haga doble clic en la entrada o selecciónela y presione **F2**.
   - Para quitar una entrada, selecciónela y elija el icono de **-** .

3. (Opcional) Para mejorar el rendimiento de la carga de símbolos, en **Almacenar símbolos en caché a este directorio**, escriba la ruta de acceso de la carpeta local en la que los servidores de símbolos pueden copiar símbolos.

   > [!NOTE]
   > No coloque la memoria caché de símbolos local en una carpeta protegida, como C:\Windows, o una subcarpeta. Utilice una carpeta de lectura y escritura en su lugar.

   > [!NOTE]
   > En proyectos de C++, si tiene establecida la variable de entorno `_NT_SYMBOL_PATH`, invalidará el valor establecido en **Almacenar símbolos en caché a este directorio**.

4. Especifique los módulos que quiere que el depurador cargue desde las **ubicaciones del archivo de símbolos (.pdb)** al iniciarse.

   - Seleccione **Load all modules, unless excluded** (Cargar todos los módulos, salvo los excluidos) (valor predeterminado) para cargar todos los símbolos de todos los módulos de la ubicación del archivo de símbolos, excepto los módulos que se excluyen específicamente. Para excluir determinados módulos, seleccione **Especificar módulos excluidos**, elija el icono de **+** , escriba los nombres de los módulos que quiere excluir y seleccione **Aceptar**.

   - Para cargar solo los módulos que especifique en las ubicaciones del archivo de símbolos, seleccione **Cargar solo los módulos especificados**. Seleccione **Especificar módulos incluidos**, elija el icono de **+** , escriba los nombres de los módulos que se van a incluir y seleccione **Aceptar**. No se cargarán los archivos de símbolos de otros módulos.

5. Seleccione **Aceptar**.

## <a name="other-symbol-options-for-debugging"></a>Otras opciones de símbolos para la depuración

Puede seleccionar opciones de símbolos adicionales en **Herramientas** > **Opciones** > **Depuración** > **General** (o **Depurar** > **Opciones** > **General**):

- **Cargar exportaciones de dll (solo nativas)**

  Carga las tablas de exportación de archivos DLL para C/C++. Para más información, consulte [Tablas de exportación de archivos DLL](#use-dumpbin-exports). La lectura de la información de exportación de archivos DLL implica cierta sobrecarga, por lo que la carga de tablas de exportación está desactivada de forma predeterminada. También puede usar `dumpbin /exports` en una línea de comandos de compilación de C/ C++.

- **Habilitar la depuración de nivel de dirección** y **Mostrar desensamblado si el código fuente no está disponible**

  Muestra siempre el desensamblado cuando no se encuentran los archivos de código fuente o de símbolos.

  ![Opciones\Depuración\Opciones generales de desensamblado](../debugger/media/dbg_options_general_disassembly_checkbox.png "Opciones &#47; Depuración &#47; Opciones generales de desensamblado")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Habilitar compatibilidad de servidor de origen**

  Usa el servidor de origen para ayudar a depurar una aplicación cuando no hay código fuente en la máquina local o el archivo *.pdb* no coincide con el código fuente. El servidor de origen recoge solicitudes de archivos y devuelve los archivos reales del control de código fuente. El servidor de origen se ejecuta mediante un archivo DLL denominado *srcsrv.dll* para leer el archivo *.pdb* de la aplicación. El archivo *.pdb* contiene punteros al repositorio de código fuente, y comandos que se utilizan para recuperar el código fuente del repositorio.

  Puede limitar los comandos que *srcsrv.dll* puede ejecutar desde el archivo *.pdb* de la aplicación creando una lista de comandos permitidos en un archivo denominado *srcsrv.ini*. Coloque el archivo *srcsrv.ini* en la misma carpeta que *srcsrv.dll* y *devenv.exe*.

  >[!IMPORTANT]
  >En el archivo *.pdb* de la aplicación se pueden insertar comandos arbitrarios, por lo que debe asegurarse de colocar únicamente los que quiera ejecutar en el archivo *srcsrv.ini*. Todo intento de ejecutar un comando no incluido en el archivo *srcsvr.ini* provocará la aparición de un cuadro de diálogo de confirmación. Para obtener más información, vea [Advertencia de seguridad: El depurador debe ejecutar un comando que no es de confianza](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >No se realiza ninguna validación de los parámetros de comando, por lo que debe tener cuidado con los comandos de confianza. Por ejemplo, si incluyó *cmd.exe* en *srcsrv.ini*, un usuario malintencionado podría especificar parámetros de *cmd.exe* que lo harían peligroso.

  Seleccione este elemento y los elementos secundarios que quiera. **Permitir servidor de origen para ensamblados de confianza parcial (solo administrado)** y **Ejecutar siempre los comandos del servidor de origen que no sean de confianza sin preguntar** pueden aumentar los riesgos de seguridad.

  ![Habilitar opciones de servidor de origen](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>Opciones de símbolos del compilador

Cuando compila un proyecto mediante el IDE de Visual Studio con la configuración de compilación de **depuración** estándar, los compiladores administrados y de C++ crean archivos de símbolos adecuados para el código. También puede establecer opciones del compilador en el código.

### <a name="net-options"></a>Opciones de .NET

Compile con **/debug** para crear un archivo *.pdb*. Puede compilar las aplicaciones con **/debug:full** o **/debug:pdbonly**. La compilación mediante **/debug:full** genera código depurable. La compilación mediante **/debug:pdbonly** genera archivos *.pdb*, pero no genera el atributo `DebuggableAttribute` que indica al compilador JIT que existe información de depuración disponible. Use **/debug:pdbonly** si quiere generar archivos *.pdb* para una compilación de versión que no quiere que sea depurable. Para obtener más información, vea [/debug (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) (/degug [Opciones del compilador de C#]) o [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug) (/debug [Visual Basic]).

### <a name="cc-options"></a>Opciones de C/C++

- Archivos *VC\<x>.pdb* y *\<project>.pdb*

  Cuando se compila con [/ZI o /Zi](/cpp/build/reference/z7-zi-zi-debug-information-format), se crea un archivo *.pdb* para C/C++ . En [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], la opción [/Fd](/cpp/build/reference/fd-program-database-file-name) asigna nombre al archivo *.pdb* creado por el compilador. Al crear un proyecto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con el IDE, se establece la opción **/Fd** para crear un archivo *.pdb* denominado *\<project>.pdb*.

  Si compila una aplicación de C/C++ mediante un archivo Make y especifica **/ZI** o **/Zi** sin usar **/Fd**, el compilador creará dos archivos *.pdb*:

  - *VC\<x>.pdb*, donde *\<x>* representa la versión del compilador de Microsoft C++, por ejemplo *VC11.pdb*

    En el archivo *VC\<x>.pdb* se almacena toda la información de depuración de los archivos de objeto individuales y reside en el mismo directorio que el archivo Make del proyecto. Cada vez que crea un archivo de objeto, el compilador de C/C++ combina la información de depuración en *VC\<x>.pdb*. Por tanto, aunque cada archivo de código fuente incluya archivos de encabezado comunes como *\<windows.h>* , las definiciones de tipo de esos encabezados solo se almacenan una vez, en lugar de aparecer en todos los archivos de objeto. La información insertada incluye información de tipo, pero no información de símbolo como definiciones de función.

  - *\<project>.pdb*

    En el archivo *\<project>.pdb* se almacena toda la información de depuración del archivo *.exe* del proyecto y reside en el subdirectorio *\debug*. El archivo *\<project>.pdb* contiene toda la información de depuración, incluidos los prototipos de función, no solo la información de tipos que se encuentra en *VC\<x>.pdb*.

  Los archivos *VC\<x>.pdb* y *\<project>.pdb* permiten actualizaciones incrementales. El vinculador también inserta la ruta de acceso a los archivos *.pdb* en el archivo *.exe* o *.dll* que crea.

- <a name="use-dumpbin-exports"></a>Tablas de exportación de archivos DLL

  Use `dumpbin /exports` para ver los símbolos que están disponibles en la tabla de exportación de un archivo DLL. La información de símbolos de las tablas de exportación de archivos DLL puede resultar útil si se trabaja con mensajes de Windows, procedimientos de Windows (WindowProc), objetos COM, cálculo de referencias o cualquier archivo DLL para el que no disponga de símbolos. Los símbolos están disponibles para cualquier archivo DLL de sistema de 32 bits. Las llamadas se muestran en una lista según el orden de llamada, y la función actual (la que está anidada a mayor profundidad) aparece en la parte superior.

  Si lee la salida de `dumpbin /exports`, podrá ver los nombres de función exactos, incluidos los caracteres no alfanuméricos. Ver los nombres de función exactos resulta útil para establecer un punto de interrupción en una función, ya que los nombres de función se pueden truncar en otros lugares del depurador. Para obtener más información, vea [dumpbin /exports](/cpp/build/reference/dash-exports).

### <a name="web-applications"></a>Aplicaciones web

Establezca el archivo *web.config* de la aplicación ASP.NET en modo de depuración. El modo de depuración hace que ASP.NET genere símbolos para los archivos generados dinámicamente y permite al depurador asociarse a la aplicación ASP.NET. Visual Studio lo establece automáticamente al empezar a depurar si el proyecto se creó a partir de la plantilla de proyectos web.

## <a name="manage-symbols-while-debugging"></a>Administración de símbolos durante la depuración

Puede usar las ventanas **Módulos**, **Pila de llamadas**, **Variables locales**, **Automático** o **Inspección** cargar símbolos o cambiar opciones de símbolo durante la depuración. Para más información, vea [Familiarizarse con el modo en que el depurador se asocia a la aplicación](../debugger/debugger-tips-and-tricks.md#modules_window).

### <a name="work-with-symbols-in-the-modules-window"></a>Uso de símbolos en la ventana Módulos

Durante la depuración, la ventana **Módulos** muestra los módulos de código que el depurador trata como código de usuario, o Mi código, con su estado de carga de símbolos. En la ventana **Módulos** también puede supervisar el estado de carga de símbolos, cargar símbolos y cambiar opciones de símbolo.

**Para supervisar o cambiar ubicaciones de símbolos u opciones de símbolo durante la depuración:**

1. Para abrir la ventana **Módulos** mientras realiza la depuración, seleccione **Depurar** > **Ventanas** > **Módulos** (o bien, presione **CTRL** + **Alt** + **U**).
1. En la ventana **Módulos**, haga clic con el botón derecho en los encabezados **Estado del símbolo** o **Archivo de símbolo** o en cualquier módulo.
1. En el menú contextual, seleccione una de las siguientes opciones:

|Opción|Descripción|
|------------|-----------------|
|**Cargar símbolos**|Aparece en los módulos con símbolos omitidos, no encontrados o no cargados. Intenta cargar símbolos de las ubicaciones especificadas en la página **Opciones** > **Depuración** > **Símbolos**. Si el archivo de símbolos no se encuentra o no está cargado, se inicia el **Explorador de archivos** para que se pueda especificar una nueva ubicación en la que buscar.|
|**Información de carga de símbolos**|Muestra la ubicación de un archivo de símbolos cargado o las ubicaciones buscadas en caso de que el depurador no encuentre el archivo.|
|**Configuración de símbolos**|Abre la página **Opciones** > **Depuración** > **Símbolos**, donde puede editar y agregar ubicaciones de símbolos.|
|**Cargar siempre automáticamente**|Agrega el archivo de símbolos seleccionado a la lista de archivos que el depurador carga automáticamente.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Uso de las páginas No se cargaron símbolos/No se cargaron orígenes

Hay varias maneras de que el depurador interrumpa el código que no tiene archivos de símbolos o de código fuente disponibles:

- Depurar código paso a paso por instrucciones.
- Interrumpir el código desde un punto de interrupción o una excepción.
- Cambiar a otro subproceso.
- Cambiar el marco de pila haciendo doble clic en un marco de la ventana **Pila de llamadas**.

Cuando esto sucede, el depurador muestra la página **No se cargaron símbolos** o **No se cargaron orígenes** para ayudar a encontrar y cargar los símbolos o los orígenes necesarios.

 ![Página No se cargaron símbolos](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**Para usar la página de documento No se cargaron símbolos para ayudar a encontrar y cargar los símbolos que faltan:**

- Para cambiar la ruta de búsqueda, seleccione una ruta de acceso no seleccionada o seleccione **Nueva ruta de acceso** o **Nueva ruta de acceso de VSTS** y escriba o seleccione una nueva ruta de acceso. Seleccione **Cargar** para buscar de nuevo las rutas de acceso y cargar el archivo de símbolos si se encuentra.
- Para invalidar cualquier opción de símbolo y reintentar las rutas de acceso de búsqueda, seleccione **Examinar y buscar \<executable-name>** . Se carga el archivo de símbolos, si se encuentra, o se abre el **Explorador de archivos** para que pueda seleccionar manualmente el archivo de símbolos.
- Para abrir la página **Opciones** > **Depuración** > **Símbolos**, seleccione **Cambiar configuración de símbolos**.
- Para mostrar el desensamblado una vez en una nueva ventana, seleccione **ver desensamblado** o elija **Cuadro de diálogo Opciones** para establecer la opción de mostrar siempre el desensamblado cuando no se encuentren archivos de código fuente o de símbolos.
- Para mostrar las ubicaciones en las que se buscó y el resultado, expanda **Información de carga de símbolos**.

Si, después de ejecutar una de las opciones, el depurador encuentra el archivo *.pdb* y puede recuperar el archivo de código fuente mediante la información del archivo *.pdb*, muestra el código fuente. En caso contrario, se muestra una página **No se cargaron orígenes** que describe el problema, con vínculos a acciones que podrían resolver el problema.

**Para agregar rutas de acceso de búsqueda de archivos de código fuente a una solución:**

Puede especificar las ubicaciones en las que el depurador busca archivos de código fuente y excluir archivos específicos de la búsqueda.

1. Seleccione la solución en el **Explorador de soluciones** y luego elija el icono **Propiedades**, presione **Alt**+**Entrar** o haga clic con el botón derecho y seleccione **Propiedades**.

1. Seleccione **Depurar archivos de código fuente**.

1. En **Directorios que contienen código fuente**, escriba o seleccione las ubicaciones del código fuente que va a buscar. Use el icono **Nueva línea** para agregar más ubicaciones, los iconos de flecha **arriba** and **abajo** para reordenarlas, o el icono **X** para eliminarlas.

   >[!NOTE]
   >El depurador solo busca en el directorio especificado. Debe agregar entradas para cualquier subdirectorio que desee buscar.

1. En **No busque los siguientes archivos de código fuente**, escriba los nombres de los archivos de código fuente que se van a excluir de la búsqueda.

1. Haga clic en **Aceptar** o en **Aplicar**.

## <a name="see-also"></a>Vea también
- [Descripción de los archivos de símbolos y la configuración de símbolos de Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Cambios en la carga remota de símbolos .NET en Visual Studio 2012 y 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)