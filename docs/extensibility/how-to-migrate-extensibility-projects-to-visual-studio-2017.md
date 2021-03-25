---
title: Migrar proyectos de extensibilidad a Visual Studio 2017
titleSuffix: ''
description: Obtenga información sobre cómo actualizar proyectos de extensibilidad a Visual Studio 2017 y cómo actualizar desde la versión 2 del manifiesto de la extensión al manifiesto de la versión 3 de VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: d50624dc4c0d96c20323afb3c7d065121a4baacb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069977"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Cómo: migrar proyectos de extensibilidad a Visual Studio 2017

En este documento se explica cómo actualizar proyectos de extensibilidad a Visual Studio 2017. Además de describir cómo actualizar los archivos de proyecto, también describe cómo actualizar desde la versión 2 del manifiesto de extensión (VSIX V2) al nuevo formato de manifiesto VSIX de la versión 3 (VSIX V3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Instalación de Visual Studio 2017 con las cargas de trabajo necesarias

Asegúrese de que la instalación incluye las siguientes cargas de trabajo:

* Desarrollo de escritorio de .NET
* Desarrollo de extensiones de Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Abrir la solución VSIX en Visual Studio 2017

Todos los proyectos VSIX requerirán una actualización unidireccional de la versión principal a Visual Studio 2017.

El archivo de proyecto (por ejemplo, **. csproj*) se actualizará:

* MinimumVisualStudioVersion: ahora se establece en 15,0
* OldToolsVersion (si ya existe): ahora se establece en 14,0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Actualización del paquete NuGet Microsoft. VSSDK. BuildTools

> [!Note]
> Si la solución no hace referencia al paquete NuGet Microsoft. VSSDK. BuildTools, puede omitir este paso.

Para compilar la extensión en el nuevo formato VSIX V3 (versión 3), la solución deberá compilarse con las nuevas herramientas de compilación de VSSDK. Esto se instalará con Visual Studio 2017, pero la extensión VSIX V2 podría estar manteniendo una referencia a una versión anterior a través de NuGet. Si es así, tendrá que instalar manualmente una actualización del paquete NuGet Microsoft. VSSDK. BuildTools para la solución.

Para actualizar las referencias de NuGet a Microsoft. VSSDK. BuildTools:

* Haga clic con el botón derecho en la solución y elija **administrar paquetes NuGet para la solución**.
* Vaya a la pestaña **actualizaciones** .
* Seleccione **Microsoft. VSSDK. BuildTools (versión más reciente)**.
* Presione **Actualizar**.

![Herramientas de compilación de VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Realizar cambios en el manifiesto de la extensión VSIX

Para asegurarse de que la instalación del usuario de Visual Studio tiene todos los ensamblados necesarios para ejecutar la extensión, especifique todos los componentes de requisitos previos o paquetes en el archivo de manifiesto de la extensión. Cuando un usuario intenta instalar la extensión, VSIXInstaller comprobará si están instalados todos los requisitos previos. Si faltan algunos, se solicitará al usuario que instale los componentes que faltan como parte del proceso de instalación de la extensión.

> [!Note]
> Como mínimo, todas las extensiones deben especificar el componente editor principal de Visual Studio como requisito previo.

* Edite el archivo de manifiesto de la extensión (normalmente denominado *source. Extension. vsixmanifest*).
* Asegúrese de que `InstallationTarget` incluye 15,0.
* Agregue los requisitos previos de instalación necesarios (como se muestra en el ejemplo siguiente).
  * Se recomienda especificar solo identificadores de componente para los requisitos previos de instalación.
  * Vea la sección al final de este documento para obtener [instrucciones sobre cómo identificar identificadores de componente](#find-component-ids).

Ejemplo:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opción: usar el diseñador para realizar cambios en el manifiesto de la extensión VSIX

En lugar de editar directamente el manifiesto XML, puede usar la nueva pestaña **requisitos previos** en el diseñador de manifiestos para seleccionar los requisitos previos y el código XML se actualizará automáticamente.

> [!Note]
> El diseñador de manifiestos solo le permitirá seleccionar componentes (no cargas de trabajo o paquetes) que estén instalados en la instancia actual de Visual Studio. Si necesita agregar un requisito previo para una carga de trabajo, un paquete o un componente que no está instalado actualmente, edite el XML del manifiesto directamente.

* Abra el archivo *source. Extension. vsixmanifest [diseño]* .
* Seleccione la pestaña **requisitos previos** y presione el botón **nuevo** .

   ![Diseñador de manifiestos VSIX](media/vsix-manifest-designer.png)

* Se abrirá la ventana **Agregar nuevo requisito previo** .

   ![Agregar requisito previo de VSIX](media/add-vsix-prerequisite.png)

* Haga clic en la lista desplegable **nombre** y seleccione el requisito previo deseado.
* Actualice la versión si es necesario.

   > [!Note]
   > El campo versión se rellenará automáticamente con la versión del componente instalado actualmente, con un intervalo que abarca hasta la siguiente versión principal del componente (sin incluirlo).

   ![agregar requisitos previos de Roslyn](media/add-roslyn-prerequisite.png)

* Haga clic en **Aceptar**.

## <a name="update-debug-settings-for-the-project"></a>Actualizar la configuración de depuración del proyecto

Si desea depurar la extensión en una instancia experimental de Visual Studio, asegúrese de que la acción de inicio de la configuración del proyecto para **depurar**  >   tiene el **programa externo de Inicio:** valor establecido en el archivo de *devenv.exe* de la instalación de Visual Studio 2017.

Podría ser similar a la siguiente: *c:\Archivos de programa (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![iniciar programa externo](media/start-external-program.png)

> [!Note]
> La acción de inicio de depuración normalmente se almacena en el archivo *. csproj. User* . Este archivo normalmente se incluye en el archivo *. gitignore* y, por lo tanto, no se guarda normalmente con otros archivos de proyecto cuando se confirma en el control de código fuente. Como tal, si ha extraído la solución desde el control de código fuente, es probable que el proyecto no tenga valores establecidos para la acción de inicio. Los nuevos proyectos VSIX creados con Visual Studio 2017 tendrán un archivo *. csproj. User* creado con los valores predeterminados que apuntan al directorio de instalación actual de Visual Studio. Sin embargo, si va a migrar una extensión VSIX V2, es probable que el archivo *. csproj. User* contenga referencias al directorio de instalación de la versión anterior de Visual Studio. Establecer el valor de la acción de inicio de **depuración**  >   permitirá que se inicie la instancia experimental de Visual Studio correcta al intentar depurar la extensión.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Comprobar que la extensión se compila correctamente (como VSIX V3)

* Compile el Proyecto VSIX.
* Descomprima el VSIX generado.
  * De forma predeterminada, el archivo VSIX reside dentro de *bin/Debug* o *bin/Release* como *[YourCustomExtension]. vsix*.
  * Cambie el nombre de *. vsix* a *. zip* para ver fácilmente el contenido.
* Compruebe la existencia de tres archivos:
  * *Extension. vsixmanifest*
  * *manifest.jsen*
  * *catalog.jsen*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Comprobar si están instalados todos los requisitos previos necesarios

Compruebe que VSIX se instala correctamente en una máquina con todos los requisitos previos necesarios instalados.

> [!Note]
> Antes de instalar cualquier extensión, cierre todas las instancias de Visual Studio.

Intente instalar la extensión:

* En Visual Studio 2017

![Instalador de VSIX en Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Opcional: Compruebe en las versiones anteriores de Visual Studio.
  * Demuestra la compatibilidad con versiones anteriores.
  * Debería funcionar para Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Opcional: Compruebe que el comprobador de versiones del instalador de VSIX ofrece una serie de versiones.
  * Incluye versiones anteriores de Visual Studio (si está instalado).
  * Incluye Visual Studio 2017.

Si Visual Studio se ha abierto recientemente, podría ver un cuadro de diálogo similar al siguiente:

![procesos en ejecución de vs](media/vs-running-processes.png)

Espere a que los procesos se cierren o finalice manualmente las tareas. Puede buscar los procesos por el nombre de la lista o por el PID indicado entre paréntesis.

> [!Note]
> Estos procesos no se cerrarán automáticamente mientras se ejecuta una instancia de Visual Studio. Asegúrese de que ha cerrado todas las instancias de Visual Studio en el equipo, incluidas las de otros usuarios, y continúe con el reintento.

## <a name="check-when-missing-the-required-prerequisites"></a>Compruebe si faltan los requisitos previos necesarios

* Intente instalar la extensión en una máquina con Visual Studio 2017 que no contenga todos los componentes definidos en los requisitos previos (arriba).
* Compruebe que la instalación identifica los componentes que faltan y los enumera como un requisito previo en VSIXInstaller.
* Nota: la elevación será necesaria si es necesario instalar los requisitos previos con la extensión.

![vsixinstaller falta un requisito previo](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Decidir componentes

Al buscar las dependencias, verá que una dependencia podría asignarse a varios componentes. Para determinar las dependencias que se deben especificar como requisitos previos, se recomienda elegir un componente que tenga una funcionalidad similar a la de la extensión y también tener en cuenta a los usuarios y qué tipo de componentes tienen más probabilidades de instalarse o no. También se recomienda crear las extensiones de una forma en la que los requisitos previos necesarios cumplan solo el mínimo que permitirá la ejecución de la extensión y que las características adicionales las tengan inactivas si no se detectan determinados componentes.

Para proporcionar más instrucciones, hemos identificado algunos tipos de extensión comunes y sus requisitos previos sugeridos:

Tipo de extensión | Display Name (Nombre para mostrar) | ID
--- | --- | ---
Editor | Editor de núcleo de Visual Studio | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# y Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Núcleo de carga de trabajo de escritorio administrado | Microsoft.VisualStudio.Component.ManagedDesktop.Core
instantáneas | Depurador Just-In-Time | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Buscar identificadores de componente

La lista de componentes ordenados por producto de Visual Studio se encuentra en [identificadores de componente y carga de trabajo de Visual studio 2017](../install/workload-and-component-ids.md?view=vs-2019&preserve-view=true). Use estos identificadores de componente para los identificadores de requisitos previos en el manifiesto.

Si no está seguro de qué componente contiene un archivo binario específico, descargue la [hoja de cálculo de asignación binaria de componentes >](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Hay cuatro columnas en la hoja de Excel: **nombre de componente**, **ComponentID**, **versión** y **nombres de archivo/binarios**.  Puede usar los filtros para buscar y buscar componentes y binarios específicos.

En el caso de todas las referencias, determine cuáles están en el componente editor básico (Microsoft. VisualStudio. Component. CoreEditor).  Como mínimo, se requiere que el componente editor de núcleos se especifique como requisito previo para todas las extensiones. De las referencias que se dejan en el editor principal, agregue filtros en la sección **nombres de archivos binarios o archivos** para buscar componentes que tienen cualquiera de los subconjuntos de esas referencias.

Ejemplos:

* Si tiene una extensión del depurador y sabe que el proyecto tiene una referencia a *VSDebugEng.dll* y *VSDebug.dll*, haga clic en el botón filtro del encabezado **archivos binarios/nombres de archivo** .  Busque "VSDebugEng.dll" y seleccione *Aceptar*.  A continuación, haga clic en el botón filtro del encabezado **archivos binarios/nombres** de nuevo y busque "VSDebug.dll".  Active la casilla **Agregar selección actual para filtrar** y haga clic en **Aceptar**.  Ahora examine el **nombre del componente** para encontrar un componente más relacionado con el tipo de extensión. En este ejemplo, elegiría el depurador Just-in-Time y lo agregaría a su vsixmanifest.
* Si sabe que el proyecto trata los elementos del depurador, puede buscar en "depurador" en el cuadro Buscar filtro para ver qué componentes contienen el depurador en su nombre.

## <a name="specify-a-visual-studio-2017-release"></a>Especificar una versión de Visual Studio 2017

Si la extensión requiere una versión específica de Visual Studio 2017, por ejemplo, depende de una característica publicada en 15,3, debe especificar el número de compilación en el **admitir** de VSIX. Por ejemplo, la versión 15,3 tiene un número de compilación de "15.0.26730.3". [Aquí](../install/visual-studio-build-numbers-and-release-dates.md)puede ver la asignación de versiones a los números de compilación. El uso del número de versión ' 15,3 ' no funcionará correctamente.

Si la extensión requiere 15,3 o superior, declararía la **versión de admitir** como [15.0.26730.3, 16,0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```