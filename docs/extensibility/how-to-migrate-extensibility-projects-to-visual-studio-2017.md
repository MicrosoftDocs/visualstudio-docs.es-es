---
title: Procedimiento Migrar proyectos de extensibilidad a Visual Studio 2017 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: f5edad198727ea33d3bf293fa0ee1baf3afb5b3b
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823899"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Procedimiento Migrar proyectos de extensibilidad de Visual Studio 2017

Este documento explica cómo actualizar proyectos de extensibilidad a Visual Studio 2017. Además de describir cómo se actualizan los archivos de proyecto, también describe cómo actualizar desde la versión del manifiesto de extensión 2 (v2 VSIX) a la nueva versión 3 formato del manifiesto VSIX (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Instale Visual Studio 2017 con cargas de trabajo necesarias

Asegúrese de que la instalación incluye las cargas de trabajo siguientes:

* Desarrollo de escritorio de .NET
* Desarrollo de extensiones de Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Abra la solución VSIX en Visual Studio 2017

Todos los proyectos VSIX requerirán una actualización unidireccional de versión principal para Visual Studio 2017.

El archivo de proyecto (por ejemplo * *.csproj*) se actualizará:

* Ahora establezca MinimumVisualStudioVersion - 15.0
* OldToolsVersion (si existe previamente)-ahora está establecido en 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Actualizar el paquete Microsoft.VSSDK.BuildTools de NuGet

> [!Note]
> Si la solución no hace referencia el paquete Microsoft.VSSDK.BuildTools NuGet, puede omitir este paso.

Con el fin de compilar la extensión en las nuevas VSIX v3 formato (versión 3), la solución debe compilarse con las nuevas herramientas de VSSDK de compilación. Se instala con Visual Studio 2017, pero la extensión de v2 VSIX puede contener una referencia a una versión anterior a través de NuGet. Si es así, deberá instalar manualmente una actualización del paquete Microsoft.VSSDK.BuildTools de NuGet para la solución.

Para actualizar las referencias a Microsoft.VSSDK.BuildTools de NuGet:

* Haga doble clic en la solución y elija **administrar paquetes de NuGet para la solución**.
* Navegue hasta la **actualizaciones** ficha.
* Seleccione **Microsoft.VSSDK.BuildTools (última versión)** .
* Presione **actualización**.

![Herramientas de generación VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Realizar cambios en el manifiesto de la extensión VSIX

Para asegurarse de que la instalación del usuario de Visual Studio tiene todos los ensamblados necesarios para ejecutar la extensión, especificar todos los componentes de requisitos previos o paquetes en el archivo de manifiesto de extensión. Cuando un usuario intenta instalar la extensión, el VSIXInstaller comprobará para ver si están instalados todos los requisitos previos. Si faltan algunos, se pedirá al usuario para instalar los componentes que faltan como parte del proceso de instalación de extensión.

> [!Note]
> Como mínimo, todas las extensiones deben especificar el componente de editor principal de Visual Studio como un requisito previo.

* Editar el archivo de manifiesto de extensión (normalmente denominada *source.extension.vsixmanifest*).
* Asegúrese de `InstallationTarget` incluye 15.0.
* Incorporación de requisitos previos de instalación necesarios (como se muestra en el ejemplo siguiente).
  * Se recomienda que especificar solo identificadores de componentes de requisitos previos de instalación.
  * Consulte la sección al final de este documento para [instrucciones acerca de cómo identificar los identificadores de componente](#find-component-ids).

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opción: Use el diseñador para realizar cambios en el manifiesto de la extensión VSIX

En lugar de modificar directamente el XML del manifiesto, puede usar el nuevo **requisitos previos** ficha en el Diseñador de manifiestos para seleccionar los requisitos previos y el código XML se actualizará automáticamente.

> [!Note]
> El Diseñador de manifiestos, solo podrá seleccionar componentes (no las cargas de trabajo o los paquetes) que están instalados en la instancia actual de Visual Studio. Si necesita agregar un requisito previo para una carga de trabajo, el paquete o el componente que no está instalado actualmente, editar el manifiesto XML directamente.

* Abra *source.extension.vsixmanifest [Diseño]* archivo.
* Seleccione **requisitos previos** pestaña y presione **New** botón.

   ![Diseñador de manifiestos VSIX](media/vsix-manifest-designer.png)

* El **agregar nuevos requisitos previos** se abrirá la ventana.

   ![Agregar requisitos previos de vsix](media/add-vsix-prerequisite.png)

* Haga clic en la lista desplegable de **nombre** y seleccione el requisito previo deseado.
* Si es necesario, actualice la versión.

   > [!Note]
   > El campo de versión se rellenará previamente con la versión del componente instalada actualmente, con un intervalo que abarca hasta (pero no incluyendo) la próxima versión principal del componente.

   ![Agregar requisitos previos de roslyn](media/add-roslyn-prerequisite.png)

* Haga clic en **Aceptar**.

## <a name="update-debug-settings-for-the-project"></a>Actualizar la configuración de depuración del proyecto

Si desea depurar la extensión en una instancia experimental de Visual Studio, asegúrese de que la configuración del proyecto para **depurar** > **Iniciar acción** tiene el **iniciar externos programa:** valor establecido en el *devenv.exe* archivos de la instalación de Visual Studio 2017.

Podría parecer: *C:\Program archivos (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![iniciar programa externo](media/start-external-program.png)

> [!Note]
> La acción de inicio de depuración se suelen almacenar en la *. csproj.user* archivo. Este archivo normalmente se incluye en el *.gitignore* de archivo y, por lo tanto, no se guarda normalmente con otros archivos de proyecto cuando se confirma en el control de código fuente. Por lo tanto, si se han solucionado la solución actualizada desde el control de código fuente es probable que el proyecto no tendrá ningún valor establecido para la acción de inicio. Nuevos proyectos VSIX creados con Visual Studio 2017 tendrá un *. csproj.user* archivo creado con los valores predeterminados que apunta al directorio de instalación de Visual Studio actual. Sin embargo si va a migrar una extensión de v2 VSIX, es probable que el *. csproj.user* archivo contendrá las referencias al directorio de instalación de la versión de Visual Studio anterior. Establecer el valor de **depurar** > **Iniciar acción** permitirá que la instancia experimental de Visual Studio correcta iniciar cuando se intenta depurar la extensión.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Compruebe que la extensión se compila correctamente (como un VSIX v3)

* Compile el proyecto VSIX.
* Descomprima el archivo VSIX generado.
  * De forma predeterminada, el archivo VSIX reside en *bin/Debug* o *bin/Release,* como *[YourCustomExtension] .vsix*.
  * Cambiar el nombre de *.vsix* a *.zip* ver fácilmente el contenido.
* Comprobar la existencia de tres archivos:
  * *extension.vsixmanifest*
  * *manifest.json*
  * *catalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Compruebe si están instalados todos los requisitos previos necesarios

Para comprobar que la extensión VSIX se instala correctamente en un equipo con todos los requisitos previos instalados.

> [!Note]
> Antes de instalar cualquier extensión, cierre todas las instancias de Visual Studio.

Intento de instalar la extensión:

* On Visual Studio 2017

![Instalador de VSIX en Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Opcional: Compruebe en las versiones anteriores de Visual Studio.
  * Demuestra la compatibilidad con versiones anteriores.
  * Debería funcionar para Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Opcional: Compruebe que el Comprobador de versión del instalador de VSIX ofrece una opción de versiones.
  * Incluye las versiones anteriores de Visual Studio (si está instalado).
  * Incluye Visual Studio 2017.

Si Visual Studio se ha abierto recientemente, es posible que vea un cuadro de diálogo similar al siguiente:

![frente a los procesos en ejecución](media/vs-running-processes.png)

Espere a que los procesos que se va a cerrar o finalizar manualmente las tareas. Puede encontrar los procesos por el nombre de la lista, o con el PID que se muestra entre paréntesis.

> [!Note]
> Estos procesos no automáticamente apagará mientras se está ejecutando una instancia de Visual Studio. Asegúrese de que se cerró todas las instancias de Visual Studio en el equipo - incluidos los de otros usuarios, a continuación, seguir intentando realizar.

## <a name="check-when-missing-the-required-prerequisites"></a>Compruebe si faltan los requisitos previos necesarios

* Intente instalar la extensión en un equipo con Visual Studio 2017 que no contienen todos los componentes definidos en los requisitos previos (arriba).
* Compruebe que la instalación identifica el componente que falta/s y los muestra como un requisito previo en el VSIXInstaller.
* Nota: Si los requisitos previos deben instalarse con la extensión, se requerirá elevación.

![Falta un requisito previo de vsixinstaller](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Decidir sobre componentes

Al buscar las dependencias, encontrará que una dependencia se puede asignar a varios componentes. Para determinar qué dependencias debe especificar como el requisito previo, se recomienda elegir un componente que tiene una funcionalidad similar a la extensión y también tener en cuenta los usuarios y qué tipo de componentes desea más probable es que han instalado o no me importaría instalar. También se recomienda la creación de sus extensiones de forma que los requisitos previos necesarios satisfacen solo lo mínimo que permitirá que se ejecute la extensión y características adicionales que ellos sean inactivas si determinados componentes no se detectan.

Para proporcionar instrucciones adicionales, hemos identificado algunos tipos de extensión comunes y sus requisitos previos sugeridos:

Tipo de extensión | Nombre para mostrar | ID
--- | --- | ---
Editor | Editor de núcleo de Visual Studio | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# y Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Núcleo de carga de trabajo de escritorio administrado | Microsoft.VisualStudio.Component.ManagedDesktop.Core
instantáneas | Depurador Just-In-Time | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Encontrar identificadores de componente

La lista de componentes, ordenados por producto de Visual Studio está en [identificadores de componente y carga de trabajo de Visual Studio 2017](https://aka.ms/vs2017componentIDs). Utilizar estos identificadores de componente para los identificadores de requisitos previos en el manifiesto.

Si no está seguro de qué componente contiene un binario concreto, descargue el [componentes -> hoja de cálculo de asignación binarios](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Hay cuatro columnas en la hoja de Excel: **Nombre del componente**, **ComponentId**, **versión**, y **binario / nombres de archivo**.  Puede usar los filtros para buscar y encontrar los archivos binarios y componentes específicos.

Para todas las referencias, determinar cuáles están en el componente del editor (Microsoft.VisualStudio.Component.CoreEditor) core.  Como mínimo, se requiere el componente de editor principal que se especifican como un requisito previo para todas las extensiones. De las referencias que quedan que no están en el editor de núcleo, agregar filtros en la **binarios / nombres de archivos** sección para obtener los componentes que tienen cualquiera de los subconjuntos de esas referencias.

Ejemplos:

* Si tiene una extensión depuradora y sabe que el proyecto tiene una referencia a *VSDebugEng.dll* y *VSDebug.dll*, haga clic en el botón de filtro en el **archivos binarios o nombres de archivos**encabezado.  Busque "VSDebugEng.dll" y seleccione *Aceptar*.  A continuación, haga clic en el botón de filtro en el **archivos binarios o los nombres de archivos** encabezado nuevo y busque "VSDebug.dll".  Seleccione la casilla de verificación **Agregar selección actual al filtro** y seleccione **Aceptar**.  Ahora examine el **nombre del componente** para buscar un componente que es la mayoría relacionadas con el tipo de extensión. En este ejemplo, se eligió Just-In-Time del depurador y agréguelo a su vsixmanifest.
* Si sabe que el proyecto se ocupa de los elementos del depurador, puede buscar en "depurador" en el cuadro de búsqueda para ver los componentes que contienen el depurador en su nombre.

## <a name="specify-a-visual-studio-2017-release"></a>Especificar una versión de Visual Studio 2017

Si la extensión requiere una versión específica de Visual Studio 2017, por ejemplo, depende de una característica publicada en la versión 15.3, debe especificar el número de compilación en el proyecto de VSIX **InstallationTarget**. Por ejemplo, versión 15.3 tiene un número de compilación de '15.0.26730.3'. Puede ver la asignación de versiones para números de compilación [aquí](../install/visual-studio-build-numbers-and-release-dates.md). Con el número de versión 'versión ' 15.3 no funcionará correctamente.

Si la extensión requiere 15.3 o versiones posteriores, declararía la **InstallationTarget versión** como [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
