---
title: Uso de archivos de volcado de memoria en el depurador | Microsoft Docs
ms.custom: seodec18
ms.date: 11/05/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbfd8ac877fce4b1808a76e3bb2a66ac595693de
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970619"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Archivos de volcado de memoria en el depurador de Visual Studio.

<a name="BKMK_What_is_a_dump_file_"></a> Un *archivo de volcado de memoria* es una instantánea que muestra el proceso que se estaba ejecutando y los módulos que se cargaron para una aplicación en un momento dado. Un volcado con información de montón también incluye una instantánea de la memoria de la aplicación en ese momento.

Abrir un archivo de volcado de memoria con un montón en Visual Studio es como detenerse en un punto de interrupción en una sesión de depuración. Aunque no puede continuar la ejecución, puede examinar las pilas, los subprocesos y los valores de las variables de la aplicación en el momento del volcado de memoria.

Los volcados de memoria se usan principalmente para depurar problemas de máquinas a las que los desarrolladores no tienen acceso. Por ejemplo, puede usar un archivo de volcado de memoria desde la máquina de un cliente cuando no pueda reproducir el bloqueo o el programa que no responde en su propia máquina. Los evaluadores también crean volcados de memoria para guardar los datos del bloqueo o del programa que no responde que se van a usar para realizar más pruebas.

El depurador de Visual Studio puede guardar archivos de volcado de memoria de código administrado o nativo. Puede depurar archivos de volcados de memoria creados por Visual Studio o por otras aplicaciones que guardan archivos en el formato de *minivolcado*.

## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> Requisitos y limitaciones

- Para depurar archivos de volcado de memoria de máquinas de 64 bits, Visual Studio debe ejecutarse en una máquina de 64 bits.

- Visual Studio puede depurar archivos de volcado de memoria de aplicaciones nativas desde dispositivos ARM. También puede depurar volcados de memoria de aplicaciones administradas desde dispositivos ARM, pero solo en el depurador nativo.

- Para depurar archivos de volcado de memoria en [modo kernel](/windows-hardware/drivers/debugger/kernel-mode-dump-files) o usar la extensión de depuración [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) en Visual Studio, descargue las herramientas de depuración para Windows en el de [Kit para controladores de Windows (WDK)](/windows-hardware/drivers/download-the-wdk).

- Visual Studio no puede depurar archivos de volcado de memoria guardados en el formato antiguo, [volcado de memoria completo en modo usuario](/windows/desktop/wer/collecting-user-mode-dumps). Un volcado de memoria completo en modo usuario no es igual que un volcado de memoria con montón.

- La depuración de archivos de volcado de memoria de código optimizado puede resultar confusa. Por ejemplo, la inclusión en línea de funciones por parte del compilador puede dar lugar a pilas de llamadas inesperadas y otras optimizaciones podrían cambiar la duración de las variables.

## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> Archivos de volcado de memoria, con o sin montones

Los archivos de volcado de memoria pueden tener o no información de montón.

- Los **archivos de volcado de memoria con montón** contienen una instantánea de la memoria de la aplicación, que incluye los valores de variables en el momento del volcado de memoria. Visual Studio también guarda los archivos binarios de los módulos nativos cargados en el archivo de volcado de memoria, lo que puede facilitar mucho más la depuración. Visual Studio puede cargar símbolos de un archivo de volcado de memoria con un montón, incluso si no puede encontrar un binario de la aplicación.

- Los **archivos de volcado de memoria sin montones** son mucho más pequeños que los que tienen montones, pero el depurador debe cargar los archivos binarios de la aplicación para encontrar información de los símbolos. Los archivos binarios cargados deben coincidir exactamente con los que se ejecutan durante la creación del volcado de memoria. Los archivos de volcado de memoria sin montones guardan solo los valores de las variables de pila.

## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> Crear un archivo de volcado de memoria

Mientras depura un proceso en Visual Studio, puede guardar un archivo de volcado de memoria cuando el depurador se ha detenido en una excepción o en un punto de interrupción.

Con la [depuración Just-in-Time](../debugger/just-in-time-debugging-in-visual-studio.md) habilitada, puede asociar el depurador de Visual Studio a un proceso bloqueado fuera de Visual Studio y, luego, guardar un archivo de volcado de memoria desde el depurador. Consulte [Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Para guardar un archivo de volcado de memoria:**

1. Mientras se detiene en un error o un punto de interrupción durante la depuración, seleccione **Depurar** > **Guardar volcado como**.

1. En el cuadro de diálogo **Guardar volcado como**, en **Guardar como tipo**, seleccione **Minivolcado** o **Minivolcado con montón** (el valor predeterminado).

1. Busque una ruta de acceso y seleccione un nombre para el archivo de volcado de memoria y, luego, seleccione **Guardar**.

>[!NOTE]
>También puede crear archivos de volcado de memoria con cualquier programa que admita el formato de minivolcado de Windows. Por ejemplo, la utilidad de línea de comandos **Procdump** de [Windows Sysinternals](/sysinternals/) puede crear archivos de volcado de memoria correspondientes a bloqueos de procesos basados en desencadenadores o a petición. Consulte los [requisitos y limitaciones](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) para información sobre el uso de otras herramientas para crear archivos de volcado de memoria.

## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> Abrir un archivo de volcado de memoria

1. En Visual Studio, seleccione **Archivo** > **Abrir** > **Archivo**.

1. En el cuadro de diálogo **Abrir archivo**, busque y seleccione el archivo de volcado de memoria. Normalmente, tendrá la extensión *.dmp*. Seleccione **Aceptar**.

   La ventana **Resumen del archivo de minivolcado** muestra información de resumen y de los módulos del archivo de volcado de memoria y las acciones que se pueden realizar.

   ![Página de resumen de minivolcado](../debugger/media/dbg_dump_summarypage.png "Página de resumen de minivolcado")

1. En **Acciones**, haga lo siguiente:
   - Para establecer las ubicaciones de carga de los símbolos, seleccione **Establecer la ruta de acceso de símbolos**.
   - Para iniciar la depuración, seleccione **Depurar solo con código administrado**, **Depurar solo con código nativo**, **Depurar con código mixto** o **Debug with Managed Memory** (Depurar con memoria administrada).

## <a name="find-exe-pdb-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Búsqueda de archivos .exe, .pdb y de origen

Para usar todas las características de depuración completas en un archivo de volcado de memoria, Visual Studio necesita lo siguiente:

- El archivo *. exe* para el que se creó el volcado de memoria y otros archivos binarios (dll, etc.) que usó el proceso de volcado de memoria.
- Archivos de símbolos ( *.pdb*) del archivo *.exe* y otros archivos binarios.
- Los archivos *. exe* y *. pdb* que coincidan exactamente con la versión y la compilación de los archivos al crear el volcado.
- Los archivos de código fuente de los módulos correspondientes. Si no encuentra los archivos de código fuente, puede usar el desensamblado de los módulos.

Si el volcado de memoria tiene datos del montón, Visual Studio puede solventar el problema de que falten archivos binarios de algunos módulos, pero debe tener archivos binarios para suficientes módulos para poder generar pilas de llamadas válidas.

### <a name="search-paths-for-exe-files"></a>Búsqueda de rutas de acceso para archivos .exe

Visual Studio busca automáticamente en estas ubicaciones archivos *.exe* que no se incluyen en el archivo de volcado de memoria:

1. La carpeta que contiene el archivo de volcado de memoria.
2. La ruta de acceso del módulo que el archivo de volcado de memoria especifica, que es la ruta de acceso del módulo en la máquina que recopiló el volcado de memoria.
3. Las rutas de acceso de símbolos especificadas en **Herramientas** (o **Depurar**) > **Opciones** > **Depuración** > **Símbolos**. También puede abrir la página **Símbolos** desde el panel **Acciones** de la ventana **Dump File Summary** (Resumen del archivo de volcado de memoria). En esta página, puede agregar más ubicaciones para buscar.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>Uso de las páginas de archivos binarios, símbolos u orígenes no encontrados

Si Visual Studio no puede encontrar los archivos necesarios para depurar un módulo en el volcado de memoria, muestra una página **No se encontró ningún binario**, **No se encontraron símbolos** o **No Source Found** (No se encontró ningún origen). Estas páginas ofrecen información detallada sobre la causa del problema y proporcionan vínculos a acciones que pueden ayudarle a localizar los archivos. Consulte [Specify symbol (.pdb) and source files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) (Especificación de símbolo (.pdb) y archivos de origen).

## <a name="see-also"></a>Vea también

- [Depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)