---
title: Proyectos de compatibilidad con múltiples versiones (multi-targeting)
description: Este documento se proporciona información general sobre cómo configurar proyectos de compatibilidad con múltiples versiones en Visual Studio para Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "75439047"
---
# <a name="projects-with-multiple-target-frameworks"></a>Proyectos con varias plataformas de destino
Con Visual Studio para Mac, puede configurar un proyecto Xamarin o .NET Core para que se ejecute en cualquiera de las versiones de .NET Framework, y en cualquiera de las distintas plataformas del sistema. Por ejemplo, puede establecer como destino un proyecto para que se ejecute en .NET Framework 4.6 y en .NET Core 3.1. 

Para obtener más información sobre los marcos de destino, vea [Versiones de .NET Framework de destino](/dotnet/standard/frameworks).

> [!NOTE] 
> Este tema se aplica a Visual Studio para Mac. Para Visual Studio en Windows, consulte [Información general sobre destinos de Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="targeting-multiple-frameworks"></a>Elección como destino de varias plataformas

Las plataformas de destino se especifican en el archivo del proyecto, que puede editar. Para ello, haga clic con el botón derecho en el proyecto y elija el comando **Herramientas > Editar archivo**. Cuando especifique una única plataforma de destino, use el elemento TargetFramework. En el siguiente archivo de proyecto de aplicación de consola se muestra cómo elegir como destino .NET Core 3.0:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Use el elemento TargetFrameworks plural con varias plataformas de destino:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

Obtenga más información sobre cómo [elegir como destino varias plataformas](/dotnet/standard/frameworks#how-to-specify-target-frameworks).

## <a name="working-with-code-in-a-multi-target-project"></a>Trabajo con código en un proyecto de varios destinos
Al editar un archivo C# en un proyecto con varias plataformas de destino, puede especificar la plataforma de destino que desea usar para guiar la experiencia del editor (por ejemplo, mostrar advertencias si usa una API no compatible con esta plataforma). Puede cambiar la plataforma de destino mediante el selector **Plataforma de destino** que se encuentra en la esquina superior izquierda de la ventana del editor.

![Uso del selector de plataformas de destino para cambiar la versión de la plataforma de destino, que se encuentra en la parte superior de la ventana del editor](media/project-multitargeting-framework-selector.png)

A veces es necesario llamar a diferentes API en función de la plataforma a la que se destina la aplicación. Para ello, puede escribir código de condición para compilar código para una plataforma específica:

```C#
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

Al escribir código, verá advertencias en las sugerencias de finalización automática de IntelliSense, lo que le permite saber si faltan API específicas para cualquiera de las plataformas de destino que admite la aplicación.

![Un mensaje de advertencia que se muestra en IntelliSense es, por ejemplo, cuando una API no va a funcionar en una plataforma de destino especificada. Texto de ejemplo: namespace System.Buffers, SharedUtils (netstandard2.0) - Not Available. Puede usar la barra de navegación para cambiar el contexto.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Consulte también

- [Información general sobre destinos de Framework (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Plataformas de destino en proyectos de estilo SDK](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
