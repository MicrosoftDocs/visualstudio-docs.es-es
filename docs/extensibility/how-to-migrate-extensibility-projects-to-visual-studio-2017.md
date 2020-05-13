---
title: 'Cómo: Migrar proyectos de extensibilidad a Visual Studio 2017 Microsoft Docs'
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b0cae0261b185ee08400e5f3d25735634663f54a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710980"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Cómo: Migrar proyectos de extensibilidad a Visual Studio 2017

En este documento se explica cómo actualizar proyectos de extensibilidad a Visual Studio 2017. Además de describir cómo actualizar los archivos de proyecto, también describe cómo actualizar de la versión 2 del manifiesto de extensión (VSIX v2) al nuevo formato de manifiesto VSIX de la versión 3 (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Instale Visual Studio 2017 con las cargas de trabajo necesarias

Asegúrese de que la instalación incluye las siguientes cargas de trabajo:

* Desarrollo de escritorio de .NET
* Desarrollo de extensiones de Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Abrir solución VSIX en Visual Studio 2017

Todos los proyectos VSIX requerirán una actualización unidireccional de la versión principal a Visual Studio 2017.

El archivo de proyecto (por ejemplo **.csproj*) se actualizará:

* MinimumVisualStudioVersion - ahora establecido en 15.0
* OldToolsVersion (si existe anteriormente) - ahora establecido en 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Actualice el paquete NuGet Microsoft.VSSDK.BuildTools

> [!Note]
> Si la solución no hace referencia al paquete NuGet Microsoft.VSSDK.BuildTools, puede omitir este paso.

Para compilar la extensión en el nuevo formato VSIX v3 (versión 3), la solución tendrá que compilarse con las nuevas herramientas de compilación de VSSDK. Esto se instalará con Visual Studio 2017, pero la extensión VSIX v2 podría contener una referencia a una versión anterior a través de NuGet. Si es así, deberá instalar manualmente una actualización del paquete NuGet Microsoft.VSSDK.BuildTools para la solución.

Para actualizar las referencias de NuGet a Microsoft.VSSDK.BuildTools:

* Haga clic con el botón derecho en la solución y elija **Administrar paquetes NuGet para la solución**.
* Vaya a la pestaña **Actualizaciones.**
* Seleccione **Microsoft.VSSDK.BuildTools (última versión).**
* Pulse **Actualizar**.

![Herramientas de compilación de VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Realice cambios en el manifiesto de extensión VSIX

Para asegurarse de que la instalación del usuario de Visual Studio tiene todos los ensamblados necesarios para ejecutar la extensión, especifique todos los componentes o paquetes de requisitos previos en el archivo de manifiesto de extensión. Cuando un usuario intenta instalar la extensión, VSIXInstaller comprobará si todos los requisitos previos están instalados. Si faltan algunos, se le pedirá al usuario que instale los componentes que faltan como parte del proceso de instalación de la extensión.

> [!Note]
> Como mínimo, todas las extensiones deben especificar el componente del editor principal de Visual Studio como requisito previo.

* Edite el archivo de manifiesto de extensión (normalmente denominado *source.extension.vsixmanifest*).
* Asegúrese `InstallationTarget` incluye 15.0.
* Agregue los requisitos previos de instalación necesarios (como se muestra en el ejemplo siguiente).
  * Se recomienda especificar solo los identificadores de componente para los requisitos previos de instalación.
  * Consulte la sección al final de este documento para [obtener instrucciones sobre la identificación](#find-component-ids)de id de componente.

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opción: Utilice el diseñador para realizar cambios en el manifiesto de extensión VSIX

En lugar de editar directamente el XML de manifiesto, puede usar la nueva pestaña **Requisitos previos** del Diseñador de manifiestos para seleccionar los requisitos previos y el XML se actualizará automáticamente.

> [!Note]
> El Diseñador de manifiestos solo le permitirá seleccionar Componentes (no Cargas de trabajo o Paquetes) que están instalados en la instancia actual de Visual Studio. Si necesita agregar un requisito previo para una carga de trabajo, paquete o componente que no está instalado actualmente, edite el manifiesto XML directamente.

* Abra el archivo *source.extension.vsixmanifest [Design].*
* Seleccione la pestaña **Requisitos previos** y pulse el botón **Nuevo.**

   ![Diseñador de manifiestos VSIX](media/vsix-manifest-designer.png)

* Se abrirá la ventana **Agregar nuevo requisito previo.**

   ![añadir vsix requisito previo](media/add-vsix-prerequisite.png)

* Haga clic en el menú desplegable para **Nombre** y seleccione el requisito previo deseado.
* Actualice la versión si es necesario.

   > [!Note]
   > El campo de versión se rellenará previamente con la versión del componente instalado actualmente, con un rango que abarca hasta (pero sin incluir) la siguiente versión principal del componente.

   ![añadir roslyn prerrequisito](media/add-roslyn-prerequisite.png)

* Presione **Aceptar**.

## <a name="update-debug-settings-for-the-project"></a>Actualizar la configuración de depuración para el proyecto

Si desea depurar la extensión en una instancia experimental de Visual **Debug** > Studio, asegúrese de que la configuración del proyecto para la**acción Depurar inicio** tiene el valor Iniciar programa **externo:** establecido en el archivo *devenv.exe* de la instalación de Visual Studio 2017.

Podría tener el siguiente aspecto: C:-Archivos de programa *(x86)-Microsoft Visual Studio-2017-Enterprise-Common7-IDE-devenv.exe*

![iniciar programa externo](media/start-external-program.png)

> [!Note]
> La acción de inicio de depuración se almacena normalmente en el archivo *.csproj.user.* Este archivo se incluye normalmente en el archivo *.gitignore* y, por lo tanto, normalmente no se guarda con otros archivos de proyecto cuando se confirma en el control de código fuente. Por lo tanto, si ha extraído la solución fresca del control de código fuente, es probable que el proyecto no tenga ningún valor establecido para Iniciar acción. Los nuevos proyectos VSIX creados con Visual Studio 2017 tendrán un archivo *.csproj.user* creado con valores predeterminados que apuntan al directorio de instalación de Visual Studio actual. Sin embargo, si va a migrar una extensión VSIX v2, es probable que el archivo *.csproj.user* contenga referencias al directorio de instalación de la versión anterior de Visual Studio. Establecer el valor de **la** > **acción Depurar inicio** permitirá que se inicie la instancia experimental de Visual Studio correcta cuando intente depurar la extensión.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Compruebe que la extensión se compila correctamente (como VSIX v3)

* Compile el proyecto VSIX.
* Descomprima el VSIX generado.
  * De forma predeterminada, el archivo VSIX se encuentra dentro de *bin/Debug* o *bin/Release* como *[YourCustomExtension].vsix*.
  * Cambie el nombre de *.vsix* a *.zip* para ver fácilmente el contenido.
* Compruebe la existencia de tres archivos:
  * *extension.vsixmanifest*
  * *manifest.json*
  * *catalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Compruebe cuándo se instalan todos los requisitos previos necesarios

Compruebe que VSIX se instala correctamente en un equipo con todos los requisitos previos necesarios instalados.

> [!Note]
> Antes de instalar cualquier extensión, cierre todas las instancias de Visual Studio.

Intente instalar la extensión:

* En Visual Studio 2017

![Instalador de VSIX en Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Opcional: compruebe las versiones anteriores de Visual Studio.
  * Demuestra compatibilidad con versiones anteriores.
  * Debería funcionar para Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Opcional: Compruebe que VSIX Installer Version Checker ofrece una selección de versiones.
  * Incluye versiones anteriores de Visual Studio (si está instalado).
  * Incluye Visual Studio 2017.

Si Visual Studio se abrió recientemente, es posible que vea un cuadro de diálogo como este:

![vs procesos en ejecución](media/vs-running-processes.png)

Espere a que los procesos se cierren o finalice manualmente las tareas. Puede encontrar los procesos por el nombre de la lista o con el PID que aparece entre paréntesis.

> [!Note]
> Estos procesos no se apagarán automáticamente mientras se ejecuta una instancia de Visual Studio. Asegúrese de que ha apagado todas las instancias de Visual Studio en el equipo, incluidas las de otros usuarios, y, a continuación, continúe reintentando.

## <a name="check-when-missing-the-required-prerequisites"></a>Compruebe cuando falte los requisitos previos requeridos

* Intente instalar la extensión en un equipo con Visual Studio 2017 que NO CONTENGA todos los componentes definidos en los requisitos previos (arriba).
* Compruebe que la instalación identifica los componentes que faltan y los enumera como requisito previo en VSIXInstaller.
* Nota: La elevación será necesaria si es necesario instalar algún requisito previo con la extensión.

![vsixinstaller falta requisito previo](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Decidir sobre los componentes

Al buscar las dependencias, encontrará que una dependencia podría asignarse a varios componentes. Para determinar qué dependencias debe especificar como requisito previo, le sugerimos que elija un componente que tenga una funcionalidad similar a la extensión y que también tenga en cuenta los usuarios y qué tipo de componentes probablemente tendrían instalados o no les importaría instalar. También le sugerimos que la creación de las extensiones de una manera en la que los requisitos previos necesarios satisfagan solo el mínimo que permitirá que se ejecute la extensión y para características adicionales las tenga inactivas si no se detectan determinados componentes.

Para proporcionar orientación adicional, hemos identificado algunos tipos de extensión comunes y sus requisitos previos sugeridos:

Tipo de extensión | Display Name (Nombre para mostrar) | id
--- | --- | ---
Editor | Editor de núcleo de Visual Studio | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# y Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Núcleo de carga de trabajo de escritorio administrado | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Depurador | Depurador Just-In-Time | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Buscar iDescomponentes

La lista de componentes ordenados por producto de Visual Studio se encuentra en la carga de trabajo y los identificadores de componentes de [Visual Studio 2017.](/visualstudio/install/workload-and-component-ids?view=vs-2019) Utilice estos SDK de componentes para los ides de requisitos previos en el manifiesto.

Si no está seguro de qué componente contiene un binario específico, descargue la hoja de [cálculo de asignación binaria >](https://aka.ms/vs2017componentid-binaries)componente .

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Hay cuatro columnas en la hoja de Excel: **Nombre de componente**, **ComponentId**, **Versión**y **Nombres binarios /de archivo**.  Puede utilizar los filtros para buscar y encontrar componentes y binarios específicos.

Para todas las referencias, primero determine cuáles están en el componente del editor principal (Microsoft.VisualStudio.Component.CoreEditor).  Como mínimo, requerimos que el componente del editor principal se especifique como requisito previo para todas las extensiones. De las referencias que quedan que no están en el editor principal, agregue filtros en la sección **Binarios / Nombres** de archivos para buscar componentes que tengan cualquiera de los subconjuntos de esas referencias.

Ejemplos:

* Si tiene una extensión de depurador y sabe que el proyecto tiene una referencia a *VSDebugEng.dll* y *VSDebug.dll*, haga clic en el botón de filtro en el **encabezado Binaries / Files Names** .  Busque "VSDebugEng.dll" y seleccione *Aceptar*.  A continuación, haga clic en el botón de filtro en el **binarios / archivos nombres** encabezado de nuevo y busque "VSDebug.dll".  Active la casilla **Agregar selección actual para filtrar** y seleccione **Aceptar**.  Ahora examine el Nombre de **componente** para encontrar el componente que esté más relacionado con el tipo de extensión. En este ejemplo, elegiría el depurador Just-In-Time y lo agregaría a su vsixmanifest.
* Si sabe que el proyecto se ocupa de los elementos del depurador, puede buscar en "depurador" en el cuadro de búsqueda de filtro para ver qué componentes contienen el depurador en su nombre.

## <a name="specify-a-visual-studio-2017-release"></a>Especificar una versión de Visual Studio 2017

Si la extensión requiere una versión específica de Visual Studio 2017, por ejemplo, depende de una característica publicada en 15.3, debe especificar el número de compilación en el destino de **instalación**de VSIX . Por ejemplo, la versión 15.3 tiene un número de compilación de '15.0.26730.3'. Puede ver la asignación de versiones para generar números [aquí.](../install/visual-studio-build-numbers-and-release-dates.md) El uso del número de versión '15.3' no funcionará correctamente.

Si la extensión requiere 15.3 o superior, declararía la **versión InstallationTarget** como [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
