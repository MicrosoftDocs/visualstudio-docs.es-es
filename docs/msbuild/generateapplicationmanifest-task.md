---
title: GenerateApplicationManifest (Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateApplicationManifest task
- HostInBrowser property (MSBuild)
- GenerateApplicationManifest task [MSBuild]
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 446f4728f92d5a486afea1a7c03c8d5006690bfc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589310"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest (tarea)
Genera un manifiesto de aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o un manifiesto nativo. Un manifiesto nativo describe un componente al definir una identidad única para dicho componente e identificar todos los ensamblados y archivos que lo conforman. Un manifiesto de aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] extiende un manifiesto nativo indicando el punto de entrada de la aplicación y especificando el nivel de seguridad de la aplicación.

## <a name="parameters"></a>Parámetros
En la tabla siguiente se describen los parámetros de la tarea `GenerateApplicationManifest`.

| Parámetro | Descripción |
|---------------------------------| - |
| `AssemblyName` | Parámetro `String` opcional.<br /><br /> Especifica el campo `Name` de la identidad del ensamblado para el manifiesto generado. Si no se especifica este parámetro, el nombre se deduce de los parámetros `EntryPoint` o `InputManifest`. Si no se puede crear ningún nombre, la tarea produce un error. |
| `AssemblyVersion` | Parámetro `String` opcional.<br /><br /> Especifica el campo `Version` de la identidad del ensamblado para el manifiesto generado. Si no se especifica este parámetro, se utiliza un valor predeterminado de "1.0.0.0". |
| `ClrVersion` | Parámetro `String` opcional.<br /><br /> Especifica la versión mínima de Common Language Runtime (CLR) requerida por la aplicación. El valor predeterminado es la versión de CLR utilizada por el sistema de compilación. Si la tarea va a generar un manifiesto nativo, este parámetro se omite. |
| `ConfigFile` | Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica el elemento que contiene el archivo de configuración de la aplicación. Si la tarea va a generar un manifiesto nativo, este parámetro se omite. |
| `Dependencies` | Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica una lista de elementos que define el conjunto de ensamblados dependientes para el manifiesto generado. Cada elemento puede describirse con más detalle mediante metadatos de elemento para indicar el estado de implementación adicional y el tipo de dependencia. Para obtener más información, vea [Metadatos de elementos](#item-metadata). |
| `Description` | Parámetro `String` opcional.<br /><br /> Especifica la descripción para la aplicación o componente. |
| `EntryPoint` | Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica un elemento único que indica el punto de entrada para el ensamblado del manifiesto generado.<br /><br /> Para un manifiesto de aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], este parámetro especifica el ensamblado que se inicializa cuando se ejecuta la aplicación. |
| `ErrorReportUrl` | Parámetro <xref:System.String?displayProperty=fullName> opcional.<br /><br /> Especifica la dirección URL de la página web que se muestra en los cuadros de diálogo durante los informes de errores de las instalaciones ClickOnce. |
| `FileAssociations` | Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica una lista de uno o varios tipos de archivo asociados al manifiesto de implementación de ClickOnce.<br /><br /> Las asociaciones de archivo son válidas únicamente cuando el destino es .NET Framework 3.5 o posterior. |
| `Files` | Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Los archivos que se incluirán en el manifiesto. Especifique la ruta de acceso completa para cada archivo. |
| `HostInBrowser` | Parámetro <xref:System.Boolean> opcional.<br /><br /> Si es `true`, la aplicación se aloja en un explorador (como las aplicaciones de explorador web de WPF). |
| `IconFile` | Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Indica el archivo de icono de la aplicación. El icono de la aplicación se expresa en el manifiesto de aplicación generado y se usa para el menú **Inicio** y el cuadro de diálogo **Agregar o quitar programas**. Si no se especifica esta entrada, se usa un icono predeterminado. Si la tarea va a generar un manifiesto nativo, este parámetro se omite. |
| `InputManifest` | Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Indica un documento XML de entrada que sirve de base para el generador de manifiestos. De este modo, los datos estructurados como la seguridad de la aplicación o las definiciones personalizadas del manifiesto pueden reflejarse en el manifiesto de salida. El elemento raíz del documento XML debe ser un nodo de ensamblado en el espacio de nombres asmv1. |
| `IsolatedComReferences` | Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los componentes COM que se aislarán en el manifiesto generado. Este parámetro permite aislar los componentes COM para la implementación de "COM sin registro". Funciona generando automáticamente un manifiesto con definiciones estándar de registro de COM. Sin embargo, los componentes COM se deben registrar en el equipo de compilación para que funcione correctamente. |
| `ManifestType` | Parámetro `String` opcional.<br /><br /> Especifica el tipo de manifiesto que se va a generar. Este parámetro puede tener los valores siguientes:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Si no se especifica este parámetro, la tarea tiene como valor predefinido `ClickOnce`. |
| `MaxTargetPath` | Parámetro `String` opcional.<br /><br /> Especifica la longitud máxima permitida de la ruta de acceso de un archivo en una implementación de aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Si se especifica este valor, se comprobará si la longitud de cada ruta de archivo de la aplicación rebasa este límite. Cualquier elemento que supere el límite producirá una advertencia de compilación. Si no se especifica esta entrada o es cero, no se realiza ninguna comprobación. Si la tarea va a generar un manifiesto nativo, este parámetro se omite. |
| `OSVersion` | Parámetro `String` opcional.<br /><br /> Especifica la versión mínima del sistema operativo (SO) necesaria para la aplicación. Por ejemplo, el valor "5.1.2600.0" indica que el sistema operativo es Windows XP. Si no se especifica este parámetro, se utiliza el valor "4.10.0.0" que indica Windows 98 Segunda edición, sistema operativo mínimo admitido por .NET Framework. Si la tarea va a generar un manifiesto nativo, este dato se omite. |
| `OutputManifest` | Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el nombre del archivo de manifiesto de salida generado. Si no se especifica este parámetro, el nombre del archivo de salida se deduce de la identidad del manifiesto generado. |
| `Platform` | Parámetro `String` opcional.<br /><br /> Especifica la plataforma de destino de la aplicación. Este parámetro puede tener los valores siguientes:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Si no se especifica este parámetro, la tarea tiene como valor predefinido `AnyCPU`. |
| `Product` | Parámetro `String` opcional.<br /><br /> Especifica el nombre de la aplicación. Si no se especifica este parámetro, el nombre se deduce de la identidad del manifiesto generado. Este nombre se usa para el nombre del acceso directo del menú **Inicio** y forma parte del nombre que aparece en el cuadro de diálogo **Agregar o quitar programas**. |
| `Publisher` | Parámetro `String` opcional.<br /><br /> Especifica el publicador de la aplicación. Si no se especifica este parámetro, el nombre se deduce del usuario registrado o de la identidad del manifiesto generado. Este nombre se usa para el nombre de la carpeta del menú **Inicio** y forma parte del nombre que aparece en el cuadro de diálogo **Agregar o quitar programas**. |
| `RequiresMinimumFramework35SP1` | Parámetro `Boolean` opcional.<br /><br /> Si es true, la aplicación requiere .NET Framework 3.5 SP1 o una versión más reciente. |
| `TargetCulture` | Parámetro `String` opcional.<br /><br /> Identifica la referencia cultural de la aplicación y especifica el campo `Language` de la identidad del ensamblado para el manifiesto generado. Si no se especifica este parámetro, se supone que la aplicación es invariable en cuanto a la referencia cultural. |
| `TargetFrameworkMoniker` | Parámetro `String` opcional.<br /><br /> Especifica el moniker de la plataforma de destino. |
| `TargetFrameworkProfile` | Parámetro `String` opcional.<br /><br /> Especifica el perfil de la plataforma de destino. |
| `TargetFrameworkSubset` | Parámetro `String` opcional.<br /><br /> Especifica el nombre del subconjunto de .NET Framework de destino. |
| `TargetFrameworkVersion` | Parámetro `String` opcional.<br /><br /> Especifica la versión de .NET Framework de destino del proyecto. |
| `TrustInfoFile` | Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Indica un documento XML que especifica la seguridad de la aplicación. El elemento raíz en el documento XML debe ser un nodo trustInfo en el espacio de nombres asmv2. Si la tarea va a generar un manifiesto nativo, este parámetro se omite. |
| `UseApplicationTrust` | Parámetro `Boolean` opcional.<br /><br /> Si es true, las propiedades `Product`, `Publisher` y `SupportUrl` se escriben en el manifiesto de aplicación. |

## <a name="remarks"></a>Comentarios
Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.GenerateManifestBase>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de los parámetros de la clase Task, vea [Task Base (Clase)](../msbuild/task-base-class.md).

Para obtener información sobre cómo usar la tarea `GenerateDeploymentManifest`, vea [GenerateApplicationManifest (Tarea)](../msbuild/generateapplicationmanifest-task.md).

Las entradas para las dependencias y archivos se pueden ampliar aún más con metadatos del elemento para especificar el estado de implementación adicional para cada elemento.

## <a name="item-metadata"></a>Metadatos de elementos

|Nombre de los metadatos|Descripción|
|-------------------|-----------------|
|`DependencyType`|Indica si se publica e instala la dependencia con la aplicación o un requisito previo. Estos metadatos son válidos para todas las dependencias, pero no se utilizan para los archivos. Los valores disponibles para estos metadatos son:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> El valor predeterminado es Install.|
|`AssemblyType`|Indica si la dependencia es un ensamblado administrado o nativo. Estos metadatos son válidos para todas las dependencias, pero no se utilizan para los archivos. Los valores disponibles para estos metadatos son:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` es el valor predeterminado, que indica que el generador del manifiesto determinará automáticamente el tipo de ensamblado.|
|`Group`|Indica el grupo para la descarga adicional de archivos a petición. La aplicación define el nombre de grupo y puede ser cualquier cadena. Una cadena vacía indica que el archivo no forma parte de un grupo de descargas, que es el valor predeterminado. Los archivos que no pertenecen a un grupo forman parte de la descarga inicial de la aplicación. Los archivos que pertenecen a un grupo solo se descargan previa solicitud explícita de la aplicación usando <xref:System.Deployment.Application>.<br /><br /> Estos metadatos son válidos para todos los archivos donde `IsDataFile` es `false` y todas las dependencias donde `DependencyType` es `Install`.|
|`TargetPath`|Especifica cómo debería definirse la ruta de acceso en el manifiesto generado. Este atributo es válido para todos los archivos. Si no se especifica este atributo, se usa la especificación del elemento. Este atributo es válido para todos los archivos y dependencias con un valor `DependencyType` de `Install`.|
|`IsDataFile`|Un valor de metadatos `Boolean` que indica si el archivo es un archivo de datos. Un archivo de datos es especial en cuanto a que migra entre las actualizaciones de la aplicación. Estos metadatos solo son válidos para los archivos. El valor predeterminado es `False`.|

## <a name="example"></a>Ejemplo
En este ejemplo se utiliza la tarea `GenerateApplicationManifest` para generar un manifiesto de aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] y la tarea `GenerateDeploymentManifest` para generar un manifiesto de implementación para una aplicación con un único ensamblado. A continuación, utiliza la tarea `SignFile` para firmar los manifiestos.

Esto ilustra el escenario de generación de manifiestos más sencillo posible donde los manifiestos de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se generan para un único programa. Un nombre e identidad predeterminados se deducen del ensamblado para el manifiesto.

> [!NOTE]
> En el ejemplo siguiente, todos los archivos binarios de aplicación se compilan previamente para centrar la atención en aspectos de la generación del manifiesto. En este ejemplo se produce una implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] totalmente funcional.
>
> [!NOTE]
> Para obtener más información sobre la propiedad `Thumbprint` usada en la tarea `SignFile` de este ejemplo, vea [SignFile (Tarea)](../msbuild/signfile-task.md).

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe" />
    </ItemGroup>

    <PropertyGroup>
        <Thumbprint>
             <!-- Insert generated thumbprint here -->
        </Thumbprint>
    </PropertyGroup>

    <Target Name="Build">

        <GenerateApplicationManifest
            EntryPoint="@(EntryPoint)">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

        <GenerateDeploymentManifest
            EntryPoint="@(ApplicationManifest)">
            <Output
                ItemName="DeployManifest"
                TaskParameter="OutputManifest"/>
        </GenerateDeploymentManifest>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(ApplicationManifest)"/>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(DeployManifest)"/>

    </Target>
</Project>
```

## <a name="example"></a>Ejemplo
En este ejemplo se usan las tareas `GenerateApplicationManifest` y `GenerateDeploymentManifest` para generar los manifiestos de aplicación e implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para una aplicación con un único ensamblado, especificando el nombre y la identidad de los manifiestos.

Este ejemplo es similar al ejemplo anterior, excepto que el nombre y la identidad de los manifiestos están especificados explícitamente. Asimismo, este ejemplo se configura como una aplicación en línea en vez de como una aplicación instalada.

> [!NOTE]
> En el ejemplo siguiente, todos los archivos binarios de aplicación se compilan previamente para centrar la atención en aspectos de la generación del manifiesto. En este ejemplo se produce una implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] totalmente funcional.
>
> [!NOTE]
> Para obtener más información sobre la propiedad `Thumbprint` usada en la tarea `SignFile` de este ejemplo, vea [SignFile (Tarea)](../msbuild/signfile-task.md).

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe" />
    </ItemGroup>

    <PropertyGroup>
        <Thumbprint>
             <!-- Insert generated thumbprint here -->
        </Thumbprint>
    </PropertyGroup>

    <Target Name="Build">

        <GenerateApplicationManifest
            AssemblyName="SimpleWinApp.exe"
            AssemblyVersion="1.0.0.0"
            EntryPoint="@(EntryPoint)"
            OutputManifest="SimpleWinApp.exe.manifest">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

        <GenerateDeploymentManifest
                AssemblyName="SimpleWinApp.application"
                AssemblyVersion="1.0.0.0"
                EntryPoint="@(ApplicationManifest)"
                Install="false"
                OutputManifest="SimpleWinApp.application">
                <Output
                    ItemName="DeployManifest"
                    TaskParameter="OutputManifest"/>
        </GenerateDeploymentManifest>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(ApplicationManifest)"/>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(DeployManifest)"/>

    </Target>
</Project>
```

## <a name="example"></a>Ejemplo
En este ejemplo se usan las tareas `GenerateApplicationManifest` y `GenerateDeploymentManifest` para generar los manifiestos de aplicación e implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para una aplicación con varios archivos y ensamblados.

> [!NOTE]
> En el ejemplo siguiente, todos los archivos binarios de aplicación se compilan previamente para centrar la atención en aspectos de la generación del manifiesto. En este ejemplo se produce una implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] totalmente funcional.
>
> [!NOTE]
> Para obtener más información sobre la propiedad `Thumbprint` usada en la tarea `SignFile` de este ejemplo, vea [SignFile (Tarea)](../msbuild/signfile-task.md).

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe" />
    </ItemGroup>

    <PropertyGroup>
        <Thumbprint>
             <!-- Insert generated thumbprint here -->
        </Thumbprint>
        <DeployUrl>
            <!-- Insert the deployment URL here -->
        </DeployUrl>
        <SupportUrl>
            <!-- Insert the support URL here -->
        </SupportUrl>
    </PropertyGroup>

    <Target Name="Build">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe"/>
        <Dependency Include="ClassLibrary1.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Install</DependencyType>
        </Dependency>
        <Dependency Include="ClassLibrary2.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Install</DependencyType>
            <Group>Secondary</Group>
        </Dependency>
        <Dependency Include="MyAddIn1.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Install</DependencyType>
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>
        </Dependency>
        <Dependency Include="ClassLibrary3.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Prerequisite</DependencyType>
        </Dependency>

        <File Include="Text1.txt">
            <TargetPath>Text\Text1.txt</TargetPath>
            <Group>Text</Group>
        </File>
        <File Include="DataFile1.xml ">
            <TargetPath>Data\DataFile1.xml</TargetPath>
            <IsDataFile>true</IsDataFile>
        </File>

        <IconFile Include="Heart.ico"/>
        <ConfigFile Include="app.config">
            <TargetPath>SimpleWinApp.exe.config</TargetPath>
        </ConfigFile>
        <BaseManifest Include="app.manifest"/>
    </ItemGroup>

    <Target Name="Build">

        <GenerateApplicationManifest
            AssemblyName="SimpleWinApp.exe"
            AssemblyVersion="1.0.0.0"
            ConfigFile="@(ConfigFile)"
            Dependencies="@(Dependency)"
            Description="TestApp"
            EntryPoint="@(EntryPoint)"
            Files="@(File)"
            IconFile="@(IconFile)"
            InputManifest="@(BaseManifest)"
            OutputManifest="SimpleWinApp.exe.manifest">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

        <GenerateDeploymentManifest
            AssemblyName="SimpleWinApp.application"
            AssemblyVersion="1.0.0.0"
            DeploymentUrl="$(DeployToUrl)"
            Description="TestDeploy"
            EntryPoint="@(ApplicationManifest)"
            Install="true"
            OutputManifest="SimpleWinApp.application"
            Product="SimpleWinApp"
            Publisher="Microsoft"
            SupportUrl="$(SupportUrl)"
            UpdateEnabled="true"
            UpdateInterval="3"
            UpdateMode="Background"
            UpdateUnit="weeks">
            <Output
                ItemName="DeployManifest"
                TaskParameter="OutputManifest"/>
        </GenerateDeploymentManifest>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(ApplicationManifest)"/>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(DeployManifest)"/>

    </Target>
</Project>
```

## <a name="example"></a>Ejemplo
En este ejemplo se usa la tarea `GenerateApplicationManifest` para generar un manifiesto nativo para la aplicación *Test.exe*, que hace referencia al componente *Alpha.dll* nativo y a un componente COM aislado *Bravo.dll*.

En este ejemplo se genera *Test.exe.manifest*, que hace que la aplicación XCOPY se pueda implementar y aprovecha el COM sin registro.

> [!NOTE]
> En el ejemplo siguiente, todos los archivos binarios de aplicación se compilan previamente para centrar la atención en aspectos de la generación del manifiesto. En este ejemplo se produce una implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] totalmente funcional.

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <File Include="Test.exe" />
        <Dependency Include="Alpha.dll">
            <AssemblyType>Native</AssemblyType>
            <DependencyType>Install</DependencyType>
        </Dependency>
        <ComComponent Include="Bravo.dll" />
    </ItemGroup>

    <Target Name="Build">
        <GenerateApplicationManifest
            AssemblyName="Test.exe"
            AssemblyVersion="1.0.0.0"
            Dependencies="@(Dependency)"
            Files="@(File)"
            IsolatedComReferences="@(ComComponent)"
            ManifestType="Native">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

    </Target>
</Project>
```

## <a name="see-also"></a>Vea también
- [Tareas](../msbuild/msbuild-tasks.md)
- [Tarea GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)
- [SignFile (Tarea)](../msbuild/signfile-task.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
