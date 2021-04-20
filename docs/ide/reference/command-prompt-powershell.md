---
title: Shells de línea de comandos y símbolo del sistema para desarrolladores
description: Inicio desde el menú Herramientas > Línea de comandos. Símbolo del sistema para desarrolladores de Visual Studio, PowerShell para desarrolladores y un terminal le permiten usar las herramientas de .NET y C++ con más facilidad.
ms.date: 04/11/2021
ms.custom: contperf-fy21q4
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: 57cbc93f4b6e8cf64dd5149462788e0cde833350
ms.sourcegitcommit: 52b093e000334f53d87c6165d1418347e4f45dec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2021
ms.locfileid: "107221736"
---
# <a name="visual-studio-developer-command-prompt-and-developer-powershell"></a>Símbolo del sistema para desarrolladores de Visual Studio y PowerShell para desarrolladores

Visual Studio 2019 incluye dos shells de línea de comandos para desarrolladores:

- **Símbolo del sistema para desarrolladores de Visual Studio**: se trata de un símbolo del sistema estándar con ciertas variables de entorno establecidas para facilitar el uso de las herramientas de desarrollo de línea de comandos. Está disponible desde Visual Studio 2015.

- **PowerShell de Visual Studio para desarrolladores**: es más eficaz que un símbolo del sistema. Por ejemplo, puede pasar la salida de un comando (denominado *cmdlet* ) a otro cmdlet. Este shell tiene las mismas variables de entorno establecidas que el Símbolo del sistema para desarrolladores. Está disponible desde Visual Studio 2019.


:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="Símbolo del sistema para desarrolladores para Visual Studio que muestra la herramienta clrver":::

A partir de la versión 16.5 de Visual Studio 2019, Visual Studio incluye un **terminal** integrado que puede hospedar cualquiera de estas shells (Símbolo del sistema para desarrolladores y PowerShell para desarrolladores). También puede abrir varias pestañas de cada shell. El terminal de Visual Studio se basa en [Terminal Windows](/windows/terminal/). Para abrir el terminal en Visual Studio, elija **Ver** > **Terminal**.

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="Terminal de Visual Studio que muestra varias pestañas":::

Al abrir uno de los shells de desarrollador desde Visual Studio, como una aplicación independiente o en la ventana de terminal, se abre en el directorio de la solución actual (si tiene una solución cargada). Este comportamiento facilita la ejecución de comandos en la solución o en sus proyectos.

Ambos shells tienen conjuntos de variables de entorno específicas que le permiten usar las herramientas de desarrollo de línea de comandos más fácilmente. Después de abrir uno de estos shells, puede escribir los comandos para diferentes utilidades sin tener que saber dónde se encuentran. 

|Comandos más usados|Descripción|
|--|--|
|[`MSBuild`](../../msbuild/msbuild-command-line-reference.md)|Creación de un proyecto o una solución|
|[`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool)| [Herramientas de .NET Framework](/dotnet/framework/tools/index) para CLR.|
|[`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler)|Una [herramienta de .NET Framework](/dotnet/framework/tools/index) para desensamblador.|
|[`dotnet`](/dotnet/core/tools/dotnet)|Un [comando de la CLI de .NET](/dotnet/core/tools/index)|
|[`dotnet run`](/dotnet/core/tools/dotnet-run)|Un [comando de la CLI de .NET](/dotnet/core/tools/index)|
|[`CL`](/cpp/build/reference/compiler-command-line-syntax)|Herramienta de compilación de C/C++|
|[`NMAKE`](/cpp/build/reference/running-nmake)|Herramienta de compilación de C/C++|
|[`LIB`](/cpp/build/reference/lib-reference)| Herramienta de compilación de C/C++|
|[`DUMPBIN`](/cpp/build/reference/dumpbin-reference)| Herramienta de compilación de C/C++|


## <a name="start-in-visual-studio"></a>Inicio en Visual Studio

Siga estos pasos para abrir Símbolo del sistema para desarrolladores o PowerShell para desarrolladores desde Visual Studio:

1. Abra Visual Studio.

1. En la barra de menús, elija **Herramientas** > **Línea de comandos** > **Símbolo del sistema para desarrolladores** o **PowerShell para desarrolladores**.

   ![Elemento de menú del símbolo del sistema en Visual Studio](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="start-from-windows-menu"></a>Inicio desde el menú de Windows

Otra manera de iniciar los shells es desde el menú Inicio. Es posible que tenga varios símbolos del sistema, en función de la versión de Visual Studio y de los SDK y las cargas de trabajo adicionales que haya instalado. 

### <a name="windows-10"></a>Windows 10

1. Seleccione **Inicio** ![Tecla del logotipo de Windows del teclado.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) y desplácese hasta la letra **V**.

1. Expanda la carpeta **Visual Studio 2019**.

1. Elija **Símbolo del sistema para desarrolladores para VS 2019** o **PowerShell para desarrolladores para VS 2019**.

   Como alternativa, puede empezar a escribir el nombre del shell en el cuadro de búsqueda de la barra de tareas y elegir el resultado que desee a medida que la lista de resultados empiece a mostrar las coincidencias de búsqueda.

   ![GIF animado que muestra el comportamiento de búsqueda en Windows 10](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Vaya a la pantalla **Inicio** al presionar la tecla de logotipo de Windows ![Tecla de logotipo de Windows en el teclado.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) en el teclado, por ejemplo.

1. En la pantalla **Inicio**, presione **Ctrl**+**Tabulador** para abrir la lista **Aplicaciones** y presione **V**. Esto muestra una lista que incluye todos los símbolos del sistema de Visual Studio instalados.

1. Elija **Símbolo del sistema para desarrolladores para VS 2019** o **PowerShell para desarrolladores para VS 2019**.

### <a name="windows-7"></a>Windows 7

1. Elija **Inicio** y, a continuación, expanda **Todos los programas**.

1. Elija **Visual Studio 2019** > **Visual Studio Tools** > **Símbolo del sistema para desarrolladores para VS 2019** o bien **PowerShell para desarrolladores para VS 2019**.

   ![Menú Inicio de Windows 7 con el símbolo del sistema resaltado](./media/developer-command-prompt-for-vs/windows-7-menu.png)

Si tiene instalados otros SDK, como el [SDK de Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) o [versiones anteriores](https://developer.microsoft.com/windows/downloads/sdk-archive), es posible que vea símbolos del sistema adicionales. Consulte la documentación de cada herramienta para conocer la versión del símbolo del sistema que debe utilizar.

## <a name="start-from-file-browser"></a>Inicio desde el explorador de archivos 

Normalmente, los accesos directos de los shells que haya instalado se colocan en la carpeta **Menú Inicio** en Visual Studio; por ejemplo, en *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*. Pero si la búsqueda del símbolo del sistema no produce los resultados esperados, puede intentar buscar manualmente los archivos en el equipo.

### <a name="developer-command-prompt"></a>Símbolo del sistema para desarrolladores

Busque el nombre del archivo de símbolo del sistema; por ejemplo, *VsDevCmd.bat* o vaya a la carpeta Tools de Visual Studio; por ejemplo, *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (la ruta de acceso cambia según la versión de Visual Studio, la edición y la ubicación de instalación).

Cuando haya encontrado el archivo del símbolo del sistema, ábralo escribiendo el siguiente comando en una ventana del símbolo del sistema normal:

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

O bien, escriba el siguiente comando en el cuadro de diálogo **Ejecutar** de Windows:

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> Tendrá que editar la ruta de acceso para que coincida con la instalación de Visual Studio.

### <a name="developer-powershell"></a>PowerShell para desarrolladores

Busque un archivo de script de PowerShell denominado *Launch-VsDevShell.ps1* o vaya a la carpeta Tools de Visual Studio, como *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools*. (La ruta cambia según la ubicación de instalación, la edición y la versión de Visual Studio). Cuando haya localizado el archivo PowerShell, ejecútelo introduciendo el siguiente comando en un símbolo del sistema de Windows PowerShell o PowerShell 6:

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

De forma predeterminada, la instancia de PowerShell para desarrolladores que se inicia está configurada para la instalación de Visual Studio cuya ruta de acceso de instalación se encuentra en el archivo de *Launch-VsDevShell.ps1*.

> [!TIP]
> Se debe establecer la [directiva de ejecución](/powershell/module/microsoft.powershell.core/about/about_execution_policies) para que se ejecute cmdlet.

## <a name="see-also"></a>Consulte también

- [PowerShell para desarrolladores](https://devblogs.microsoft.com/visualstudio/the-powershell-you-know-and-love-now-with-a-side-of-visual-studio/)
- [Dé la bienvenida al nuevo terminal de Visual Studio](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/)
- [Terminal Windows](/windows/terminal/)
- [Herramientas de .NET Framework](/dotnet/framework/tools/index)
- [Administrar herramientas externas](../managing-external-tools.md)
- [Uso del conjunto de herramientas de Microsoft C++ desde la línea de comandos](/cpp/build/building-on-the-command-line)
