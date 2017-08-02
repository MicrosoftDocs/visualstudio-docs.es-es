---
title: "Cómo: migrar proyectos de extensibilidad en Visual Studio de 2017 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5b6334c38a6c058f274498c06f8e07c934931910
ms.openlocfilehash: efd17a3317302fedcb9bd42aded7a38adee2f75f
ms.lasthandoff: 03/22/2017

---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Cómo: migrar proyectos de extensibilidad en Visual Studio de 2017

Este documento explica cómo actualizar proyectos de extensibilidad a 2017 de Visual Studio. Además de describir cómo actualizar los archivos de proyecto, también se describe cómo actualizar desde la versión del manifiesto de extensión (VSIX v2) de 2 a la nueva versión 3 manifiesto formato VSIX (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Instale Visual Studio de 2017 con cargas de trabajo necesarios

Asegúrese de que la instalación incluye las cargas de trabajo siguientes:

* Desarrollo de escritorio de .NET
* Desarrollo de extensiones de Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Abra la solución VSIX en Visual Studio de 2017

Todos los proyectos VSIX requerirá una actualización de versión principal unidireccional a 2017 de Visual Studio.

Se actualizará el archivo de proyecto (por ejemplo, *.csproj):

* MinimumVisualStudioVersion - ahora establecida en 15.0
* OldToolsVersion (si existe previamente)-ahora está establecido en 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Actualización del paquete Microsoft.VSSDK.BuildTools NuGet

>**Nota:** si el paquete Microsoft.VSSDK.BuildTools NuGet no hace referencia a la solución, puede omitir este paso.

Para compilar la extensión en el nuevo v3 VSIX formato (versión 3), la solución se debe compilarse con las nuevas herramientas de compilación VSSDK. Se instala con Visual Studio de 2017, pero la extensión de v2 VSIX puede contener una referencia a una versión anterior a través de NuGet. Si es así, debe instalar manualmente una actualización del paquete Microsoft.VSSDK.BuildTools NuGet para su solución.

Para actualizar las referencias de NuGet para Microsoft.VSSDK.BuildTools:

* Haga doble clic en la solución y elija **administrar paquetes de NuGet para solución...**
* Navegue hasta la **actualizaciones** ficha.
* Seleccione Microsoft.VSSDK.BuildTools (última versión).
* Presione **actualización**.

![Herramientas de generación VSSDK](~/extensibility/media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Realice los cambios en el manifiesto de la extensión VSIX

Para asegurarse de que la instalación del usuario de Visual Studio tiene todos los ensamblados necesarios para ejecutar la extensión, especifique todos los componentes de requisitos previos o paquetes en el archivo de manifiesto de la extensión. Cuando un usuario intenta instalar la extensión, el VSIXInstaller comprobará para ver si están instalados todos los requisitos previos. Si faltan algunos, le pedirá al usuario para instalar los componentes que faltan como parte del proceso de instalación de extensión.

>**Nota:** como mínimo, todas las extensiones deben especificar el componente de editor principal de Visual Studio como un requisito previo.

* Edite el archivo de manifiesto de extensión (normalmente denominada source.extension.vsixmanifest).
* Asegúrese de `InstallationTarget` incluye 15.0.
* Agregar requisitos previos de instalación necesarios (como se muestra en el ejemplo siguiente).
  * Se recomienda que especificar sólo los identificadores de componentes de requisitos previos de instalación.
  * Consulte la sección al final de este documento para [instrucciones acerca de cómo identificar los identificadores de componentes](#finding-component-ids).

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opción: Usar el diseñador para realizar cambios en el manifiesto de la extensión VSIX

En lugar de modificar directamente el manifiesto XML, puede usar el nuevo **requisitos previos** ficha en el Diseñador de manifiestos para seleccionar los requisitos previos y el código XML se actualizará automáticamente.

>**Nota:** el Diseñador de manifiestos, sólo podrá seleccionar componentes (no las cargas de trabajo o paquetes) que están instalados en la instancia actual de Visual Studio. Si necesita agregar un requisito previo para una carga de trabajo, un paquete o un componente que no está instalado, edite el manifiesto XML directamente.

* Abra el archivo source.extension.vsixmanifest [Diseño].
* Seleccione **requisitos previos** ficha y presione **nuevo** botón.

  ![Diseñador de manifiestos VSIX](~/extensibility/media/vsix-manifest-designer.png)

* El **agregar nuevos requisitos previos** se abrirá la ventana.

  ![Agregar requisitos previos de vsix](~/extensibility/media/add-vsix-prerequisite.png)

* Haga clic en la lista desplegable de **nombre** y seleccione el requisito previo deseado.
* Si es necesario, actualice la versión.

  >Nota: El campo de versión se rellenará automáticamente con la versión del componente instalada actualmente, con un intervalo que abarca hasta (pero sin incluirlo) de la siguiente versión principal del componente.

  ![Agregar requisitos previos de roslyn](~/extensibility/media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="if-migrating-from-preview-4-or-preview-5"></a>Si la migración desde la vista previa de 4 o 5 de vista previa

* Reemplace `SetupDependencies` con `Prerequisites` y mover los elementos de la `Installer` elemento. `Prerequisites`Ahora frecuencia, sigue directamente dentro del `PackageManifest` elemento.
* [Opcional] Quitar el `GenerateVsixV3` elemento. (Se requiere en la vista previa de 5 sólo.) El `GenerateVsixV3` elemento se omite en las versiones superiores a 5 de vista previa.

## <a name="update-debug-settings-for-project"></a>Actualizar la configuración de depuración para el proyecto

Si desea depurar la extensión en una instancia experimental de Visual Studio, asegúrese de que la configuración del proyecto para **depurar** > **Iniciar acción** tiene la **programa externo de inicio:** valor al archivo de la instalación de Visual Studio de 2017 devenv.exe.

Podría ser similar:

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![programa externo de inicio](~/extensibility/media/start-external-program.png)

>**Nota:** normalmente se almacenan en la acción de inicio depurar el. csproj.user archivo. Este archivo normalmente se incluye en el archivo .gitignore y, por lo tanto, no se guarda normalmente con otros archivos de proyecto cuando se confirma al control de código fuente. Por lo tanto, si ha obtenido la solución actualizada desde el control de código fuente es probable que el proyecto no tendrá ningún valor establecido para la acción de inicio. Proyectos VSIX nuevos creados con Visual Studio de 2017 tendrá un. archivo csproj.user creado con valores predeterminados que señala al directorio de instalación de Visual Studio actual. Sin embargo si va a migrar una extensión de v2 VSIX, es probable que la. csproj.user archivo contendrá referencias al directorio de instalación de la versión anterior de Visual Studio. Establecer el valor de **depurar** > **Iniciar acción** permitirá la instancia experimental de Visual Studio correcta iniciar al intentar depurar la extensión.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Compruebe que la extensión se compila correctamente (como un v3 VSIX)

* Compile el proyecto VSIX.
* Descomprima el archivo VSIX generado.
  * En valor predeterminado, la vida del archivo VSIX en bin/Debug o bin/Release como .vsix [YourCustomExtension].
  * Cambie el nombre .vsix .zip para ver fácilmente el contenido.
* Comprobar la existencia de tres archivos:
  * Extension.vsixmanifest
  * manifest.JSON
  * Catalog.JSON

## <a name="check-when-all-required-prerequisites-are-installed"></a>Compruebe si están instalados todos los requisitos previos

Compruebe que la extensión VSIX se instala correctamente en un equipo con todos los requisitos previos instalados.

>**Nota:** antes de instalar cualquier extensión, cierre todas las instancias de Visual Studio.

Ha intentado instalar la extensión:

* En Visual Studio de 2017

![Instalador VSIX en Visual Studio de 2017](~/extensibility/media/vsixinstaller-vs-2017.png)

* Opcional: Compruebe en las versiones anteriores de Visual Studio.
  * Proporciona compatibilidad con versiones anteriores.
  * Debería funcionar para Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Opcional: Compruebe que el Comprobador de versión del instalador de VSIX ofrece una opción de versiones.
  * Incluye las versiones anteriores de Visual Studio (si está instalado).
  * Incluye 2017 de Visual Studio.

Si Visual Studio se ha abierto recientemente, podría ver un cuadro de diálogo similar al siguiente:

![frente a procesos en ejecución](~/extensibility/media/vs-running-processes.png)

Espere a que los procesos que se va a cerrar o finalizar manualmente las tareas. Puede encontrar los procesos por el nombre o con el PID aparece entre paréntesis.

>**Nota:** estos procesos no apagará automáticamente mientras se ejecuta una instancia de Visual Studio. Asegúrese de que cerró todas las instancias de Visual Studio en el equipo, los de otros usuarios, incluidos entonces seguirá intentando.

## <a name="check-when-missing-the-required-prerequisites"></a>Compruebe si faltan los requisitos previos necesarios

* Intente instalar la extensión en un equipo con Visual Studio 2017 que no contienen todos los componentes definidos en los requisitos previos (arriba).
* Compruebe que la instalación identifica el componente que falta/s y muestra como un requisito previo en el VSIXInstaller.
* Nota: Se requiere elevación si los requisitos previos deben instalarse con la extensión.

![vsixinstaller falta un requisito previo](~/extensibility/media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>Selección de componentes

Al buscar las dependencias, encontrará que una dependencia podría asignar a varios componentes. Para determinar qué dependencias debe especificar como el requisito previo, se recomienda que elija un componente que tiene una funcionalidad similar a la extensión y también tener en cuenta los usuarios y qué tipo de componentes sería probablemente han instalado o no me importaría instalar. También se recomienda compilar sus extensiones de manera que los requisitos previos necesarios satisfacen sólo lo mínimo que le permitirá ejecutar la extensión y características adicionales que se inactivas si algunos componentes no se detectan.

Para proporcionar más orientación, hemos identificado algunos tipos comunes de extensión y sus requisitos previos sugeridos:

Tipo de extensión | Nombre para mostrar |    Id.
--- | --- | ---
Editor | Editor de Visual Studio core    | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# y Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Núcleo de la carga de trabajo de escritorio administrado | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Depurador | Depurador Just-In-Time | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>Buscar Id.

La lista de componentes, ordenados por producto de Visual Studio está en [carga de trabajo de Visual Studio 2017 e Id. de componente](https://aka.ms/vs2017componentIDs). Utilizar estos identificadores de componente para sus identificadores de requisitos previos en el manifiesto.

Si no sabe qué componente contiene una descarga específica binaria, el [componentes-> hoja de cálculo de asignación binaria](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Hay cuatro columnas en la hoja de Excel: **nombre de componente**, **ComponentId**, **versión**, y **binario o nombres de archivo**.  Puede usar los filtros para buscar y encontrar los archivos binarios y componentes específicos.

Para todas las referencias, determinar cuáles están en el componente editor (Microsoft.VisualStudio.Component.CoreEditor) principal.  Como mínimo, es necesario que el componente básico de editor se especifica como un requisito previo para todas las extensiones. Las referencias que quedan que no están en el editor principal, agregar filtros en el **archivos binarios o nombres de archivos** sección encontrar componentes que tienen alguna del subconjunto de esas referencias.

Ejemplos:

* Si tiene una extensión depuradora y sabe que el proyecto tiene una referencia a VSDebugEng.dll y VSDebug.dll, haga clic en el botón de filtro en el **archivos binarios y nombres de archivos** encabezado.  Busque "VSDebugEng.dll" y haga clic en Aceptar.  A continuación, haga clic en el botón de filtro en el **archivos binarios y nombres de archivos** encabezado nuevo y busque "VSDebug.dll".  Seleccione la casilla de verificación "Agregar la selección actual al filtro" y haga clic en Aceptar.  Ahora examine el **nombre de componente** para encontrar un componente más relacionadas con el tipo de extensión. En este ejemplo, se eligió Just-In-Time del depurador y agregarlo a su vsixmanifest.
* Si sabe que el proyecto se trata con elementos del depurador, puede buscar en "debugger" en el cuadro de búsqueda del filtro para ver qué componentes contienen a depurador en su nombre.

