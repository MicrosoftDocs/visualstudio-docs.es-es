---
title: Procedimiento Configuración de proyectos para plataformas de destino
description: Sepa que Visual Studio permite configurar las aplicaciones para distintas plataformas de destino, incluidas las de 64 bits.
ms.custom: SEO-VS-2020
ms.date: 08/16/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 323d118b73649c8c23d9b4a2e3ace2fd2fc6fdea
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136763"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Procedimiento Configuración de proyectos para plataformas de destino

Visual Studio permite configurar las aplicaciones para distintas plataformas de destino, incluidas las de 64 bits. Para más información sobre la compatibilidad con plataformas de 64 bits en Visual Studio, vea [Aplicaciones de 64 bits](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Configurar plataformas de destino con el Administrador de configuración

El **Administrador de configuración** proporciona una forma de agregar rápidamente nuevas plataformas de destino para el proyecto. Si selecciona una de las plataformas que se incluyen con Visual Studio, las propiedades del proyecto se modifican a fin de compilarlo para esa plataforma.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Para configurar un proyecto para una plataforma de destino de 64 bits

1. En la barra de menús, elija **Compilar** > **Administrador de configuración** .

2. En la lista **Plataforma de soluciones activas** , elija una plataforma de 64 bits para la solución de destino y luego elija el botón **Cerrar** .

    1. Si la plataforma que quiere no aparece en la lista **Plataforma de soluciones activas** , seleccione **Nueva** .

         Aparecerá el cuadro de diálogo **Nueva plataforma de solución** .

    2. En la lista **Escriba o seleccione la nueva plataforma** , elija **x64** .

        > [!NOTE]
        > Si asigna un nuevo nombre a la configuración, es posible que tenga que modificar la configuración del **Diseñador de proyectos** para seleccionar la plataforma correcta como destino.

    3. Si quiere copiar la configuración de una configuración de plataforma actual, selecciónela y luego elija el botón **Aceptar** .

Se actualizarán las propiedades de todos los proyectos que tienen como destino la plataforma de 64 bits y la próxima compilación del proyecto se optimizará para plataformas de 64 bits.

> [!NOTE]
> El nombre de la plataforma **Win32** se utiliza para los proyectos de C++, y significa **x86** . Visual Studio tiene en cuenta las plataformas de nivel de proyecto y las plataformas de nivel de solución, y las plataformas de proyecto provienen de los sistemas de proyecto específicos del lenguaje. Los proyectos de C++ utilizan **Win32** y **x64** , pero las plataformas de solución usan **x86** y **x64** . Al elegir **x86** como la configuración de la solución, Visual Studio selecciona la plataforma **Win32** para los proyectos de C++. Para ver la configuración de la plataforma de nivel de proyecto y de la plataforma de nivel de solución, abra **Administrador de configuración** y anote las dos configuraciones de plataforma. La plataforma de nivel de solución se muestra en la lista desplegable **Plataforma de soluciones activas** y en la tabla se muestra la plataforma de nivel de proyecto para cada proyecto.
> ![Captura de pantalla que muestra la plataforma de solución y la plataforma de proyecto](media/project-platform-win32.png)

## <a name="target-platforms-in-the-project-designer"></a>Configurar plataformas de destino en el Diseñador de proyectos

El **Diseñador de proyectos** también proporciona una forma de configurar distintas plataformas para el proyecto de destino. Si la selección de una de las plataformas incluidas en la lista del cuadro de diálogo **Nueva plataforma de solución** no funciona para la solución, puede crear un nombre de configuración personalizado y modificar la configuración en el **Diseñador de proyectos** a fin de configurar el proyecto para la plataforma de destino apropiada.

La realización de esta tarea varía según el lenguaje de programación utilizado. Para obtener más información, vea los siguientes vínculos:

- Para proyectos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], vea [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- Para proyectos de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], vea [Compilar (Página, Diseñador de proyectos) (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Para proyectos de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], vea [/clr (Compilación de Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="manually-editing-the-project-file"></a>Edición manual del archivo del proyecto

A veces hay que modificar manualmente el archivo de proyecto debido a alguna configuración personalizada. Un ejemplo de esto es cuando existen condiciones que no se pueden especificar en el IDE, como cuando hay referencias diferentes para dos plataformas distintas, como en el siguiente ejemplo.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Ejemplo: Referencia a ensamblados y DLL de x86 y x64

Puede que tenga un ensamblado .NET o DLL que tenga las versiones tanto x86 como x64. Para configurar el proyecto para que use estas referencias, primero agregue la referencia y, después, abra el archivo de proyecto y edítelo para agregar un elemento `ItemGroup` con una condición que haga referencia a la configuración y a la plataforma de destino.  Por ejemplo, supongamos que el archivo binario al que está haciendo referencia es ClassLibrary1 y que hay varias rutas de acceso distintas para las configuraciones Debug y Release, así como las versiones x86 y x64.  Use cuatro elementos `ItemGroup` con todas las combinaciones de configuraciones, como aquí:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
    <Platforms>AnyCPU;x64;x86</Platforms>
  </PropertyGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
  
  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
</Project>
```

::: moniker range="vs-2017"
> [!NOTE]
> En Visual Studio 2017, debe descargar el proyecto para poder editar el archivo de proyecto. Para descargar el proyecto, haga clic con el botón derecho en el nodo del proyecto y elija **Descargar proyecto** . Cuando haya terminado de editar, guarde los cambios y vuelva a cargar el proyecto; para ello, haga clic con el botón derecho en el nodo del proyecto y elija **Volver a cargar el proyecto** .
::: moniker-end

Para más información sobre el archivo de proyecto, vea [Referencia de esquemas del archivo del proyecto MSBuild](../msbuild/msbuild-project-file-schema-reference.md).

## <a name="see-also"></a>Vea también

- [Descripción de las plataformas de compilación](../ide/understanding-build-platforms.md)
- [/platform (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [Aplicaciones de 64 bits](/dotnet/framework/64-bit-apps)
- [Compatibilidad de 64 bits del IDE de Visual Studio](../ide/visual-studio-ide-64-bit-support.md)
- [Descripción del archivo de proyecto](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
