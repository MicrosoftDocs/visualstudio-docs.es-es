---
title: Supresión de las advertencias para proyectos y paquetes NuGet
ms.custom: SEO-VS-2020
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33abc359dea3e1c7982e5d1689debc1f8e881106
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038587"
---
# <a name="how-to-suppress-compiler-warnings"></a>Procedimiento Supresión de advertencias del compilador

Puede despejar un registro de compilación mediante el filtrado de uno o varios tipos de advertencias del compilador. Por ejemplo, quizá quiera revisar solo parte de los resultados generados al establecer el nivel de detalle del registro de la compilación en **Normal**, **Detallado** o **Diagnóstico**. Para obtener más información sobre el nivel de detalle, vea [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Suprimir advertencias específicas de Visual C# o F\#

Use la página de propiedades de **Compilación** para suprimir advertencias específicas para proyectos de C# y F#.

1. En el **Explorador de soluciones**, elija el proyecto en el que quiere suprimir las advertencias.

1. En la barra de menús, elija **Ver** > **Páginas de propiedades**.

1. Seleccione la página **Compilación**.

1. En el cuadro **Suprimir advertencias**, especifique los códigos de error de las advertencias que quiere suprimir, separados por punto y coma.

1. Recompilar la solución.

## <a name="suppress-specific-warnings-for-c"></a>Supresión de advertencias específicas de C++

Use la página de propiedades de **Propiedades de configuración** para suprimir advertencias específicas para proyectos de C++.

1. En el **Explorador de soluciones**, elija el proyecto o archivo de origen donde quiere suprimir advertencias.

1. En la barra de menús, elija **Ver** > **Páginas de propiedades**.

1. Elija la categoría **Propiedades de configuración**, seleccione la categoría **C/C++** y, después, seleccione la página **Opciones avanzadas**.

1. Realice uno de estos pasos:

    - En el cuadro **Deshabilitar advertencias específicas**, especifique los códigos de error de las advertencias que quiere suprimir, separados por un punto y coma.

    - En el cuadro **Deshabilitar advertencias específicas**, elija **Editar** para mostrar más opciones.

1. Elija el botón **Aceptar** y, después, recompile la solución.

## <a name="suppress-warnings-for-visual-basic"></a>Suprimir advertencias de Visual Basic

Edite el archivo *.vbproj* del proyecto para ocultar advertencias del compilador específicas para Visual Basic. Para suprimir las advertencias por *categoría*, puede usar la [página de propiedades de Compilación](../ide/reference/compile-page-project-designer-visual-basic.md). Para obtener más información, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Para suprimir las advertencias concretas para Visual Basic

En este ejemplo se muestra cómo modificar el archivo *.vbproj* para suprimir advertencias específicas del compilador.

1. En el **Explorador de soluciones**, elija el proyecto en el que quiere suprimir las advertencias.

1. En la barra de menús, elija **Proyecto** > **Descargar proyecto**.

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto haciendo clic con el botón derecho y, después, elija **Editar \<ProjectName>.vbproj**.

    El archivo del proyecto XML se abre en el editor de código.

1. Busque el elemento `<NoWarn>` de la configuración de la compilación con la que está compilando y agregue uno o varios números de advertencia como valor del elemento `<NoWarn>`. Si especifica varios números de advertencia, sepárelos con una coma.

     En el ejemplo siguiente se muestra el elemento `<NoWarn>` para la configuración de compilación de *Depuración* en una plataforma x86, con dos advertencias de compilador suprimidas:

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
        <PlatformTarget>x86</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <ErrorReport>prompt</ErrorReport>
        <NoWarn>40059,42024</NoWarn>
        <WarningLevel>1</WarningLevel>
      </PropertyGroup>
    ```

   > [!NOTE]
   > Los proyectos de .NET Core no contienen grupos de propiedades de configuración de compilación de forma predeterminada. Para suprimir las advertencias en un proyecto de .NET Core, agregue la sección de configuración de compilación al archivo manualmente. Por ejemplo:
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFramework>netcoreapp2.0</TargetFramework>
   >     <RootNamespace>VBDotNetCore_1</RootNamespace>
   >   </PropertyGroup>
   >   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
   >     <NoWarn>42016,41999,42017</NoWarn>
   >   </PropertyGroup>
   > </Project>
   > ```

1. Guarde los cambios en el archivo *.vbproj*.

1. En la barra de menús, elija **Proyecto** > **Recargar proyecto**.

1. En la barra de menús, elija **Compilación** > **Recompilar solución**.

    La ventana **Salida** ya no muestra las advertencias que ha especificado.

Para obtener más información, consulte la [opción del compilador /nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) para el compilador de línea de comandos de Visual Basic.

## <a name="suppress-warnings-for-nuget-packages"></a>Suprimir advertencias para paquetes NuGet

En algunos casos, puede que desee suprimir las advertencias del compilador de NuGet para un único paquete NuGet, en lugar de para un proyecto completo. La advertencia sirve para un propósito determinado, por lo que no es necesario que la suprima a nivel de proyecto. Por ejemplo, una de las advertencias de NuGet indica que el paquete podría no ser totalmente compatible con el proyecto. Si se suprime a nivel de proyecto y después agrega un paquete NuGet adicional, nunca podrá saber si era ese el que provocaba la advertencia de compatibilidad.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Para suprimir una advertencia concreta para un único paquete NuGet

1. En el **Explorador de soluciones**, seleccione el paquete NuGet para el que desea suprimir las advertencias del compilador.

   ![Paquete NuGet en el Explorador de soluciones](media/nuget-package-with-warning.png)

1. En el menú contextual que se abre al hacer clic con el botón derecho, seleccione **Propiedades**.

1. En el cuadro **NoWarn** de propiedades del paquete, escriba el número de advertencia que desea suprimir para este paquete. Si desea suprimir más de una advertencia, use una coma para separar los números de advertencia.

   ![Propiedades del paquete NuGet](media/nuget-properties-nowarn.png)

   La advertencia desaparece del **Explorador de soluciones** y la **Lista de errores**.

## <a name="see-also"></a>Vea también

- [Tutorial: Creación de una aplicación](../ide/walkthrough-building-an-application.md)
- [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)
