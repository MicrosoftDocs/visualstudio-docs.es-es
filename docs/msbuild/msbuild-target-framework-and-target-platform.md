---
title: Versión de .NET Framework de destino y plataforma de destino de MSBuild | Microsoft Docs
description: Obtenga información sobre cómo crear un proyecto de MSBuild para que se ejecute en una versión de .NET Framework de destino, y una arquitectura de software o plataforma de destino.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d29c4e4659e8e6a5564e3fb41f54615bf29171d2
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049102"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Versión de .NET Framework de destino y plataforma de destino de MSBuild

Un proyecto se puede compilar para su ejecución en una *plataforma de destino* , que es una versión determinada de .NET Framework, y en una *plataforma de destino* , que es una arquitectura de software determinada.  Por ejemplo, puede diseñar una aplicación para que se ejecute en .NET Framework 2.0 en una plataforma de 32 bits compatible con la familia de procesadores 80x86 ("x86"). La combinación de la plataforma de destino y la plataforma de destino se denomina *contexto de destino*.

> [!IMPORTANT]
> En este artículo se muestra la forma antigua de especificar una plataforma de destino. Los proyectos de estilo SDK permiten diferentes plataformas de destino, como netstandard. Para más información, consulte [Plataformas de destino](/dotnet/standard/frameworks).

## <a name="target-framework-and-profile"></a>Marco y perfil de destino

 Un marco de destino es la versión concreta de .NET Framework para la que se ha compilado el proyecto. Es necesario especificar una versión del marco de trabajo de destino, ya que esto permite habilitar las características del compilador y las referencias de ensamblado exclusivas de esa versión del marco.

 Actualmente, se pueden usar las versiones siguientes de .NET Framework:

- .NET Framework 2.0 (incluido en Visual Studio 2005)

- .NET Framework 3.0 (incluido en Windows Vista)

- .NET Framework 3.5 (incluido en Visual Studio 2008)

- .NET Framework 4.5.2

- .NET Framework 4.6 (incluido en Visual Studio 2015)

- .NET Framework 4.6.1

- .NET Framework 4.6.2

- .NET Framework 4.7

- .NET Framework 4.7.1

- .NET Framework 4.7.2

- .NET Framework 4.8

Las versiones de .NET Framework difieren entre sí en la lista de ensamblados a los que se puede hacer referencia en cada una de ellas. Por ejemplo, solo puede compilar aplicaciones de Windows Presentation Foundation (WPF) si el proyecto tiene como destino.NET Framework 3.0 o versiones posteriores.

El marco de trabajo de destino se especifica en la propiedad `TargetFrameworkVersion` del archivo de proyecto. Puede cambiar la plataforma de destino de un proyecto mediante las páginas de propiedades del proyecto en el entorno de desarrollo integrado (IDE) de Visual Studio. Para obtener más información, vea [Cómo: Usar una versión de .NET Framework como destino](../ide/visual-studio-multi-targeting-overview.md). Los valores disponibles para `TargetFrameworkVersion` son `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v4.6.1`, `v4.6.2`, `v4.7`, `v4.7.1`, `v4.7.2` y `v4.8`.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 Un *perfil objetivo* es un subconjunto de una plataforma de destino. Por ejemplo, .NET Framework 4 Client Profile no incluye referencias a los ensamblados de MSBuild.

 > [!NOTE]
 > Los perfiles objetivo solo se aplican a las [bibliotecas de clases portables](/dotnet/standard/cross-platform/cross-platform-development-with-the-portable-class-library).

 El perfil de destino se especifica en la propiedad `TargetFrameworkProfile` de un archivo de proyecto. Puede cambiar el perfil objetivo mediante el control de plataforma de destino en las páginas de propiedades del proyecto del IDE.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>Plataforma de destino

 Una *plataforma* es una combinación de hardware y de software que define un entorno en tiempo de ejecución determinado. Por ejemplo,

- `x86` designa un sistema operativo Windows de 32 bits que se ejecuta en un procesador Intel 80x86 o su equivalente.

- `x64` designa un sistema operativo Windows de 64 bits que se ejecuta en un procesador Intel x64 o su equivalente.

- `Xbox` designa la plataforma Microsoft Xbox 360.

Una *plataforma de destino* es la plataforma específica para la que se ha compilado el proyecto. La plataforma de destino se especifica en la propiedad de compilación `PlatformTarget` de un archivo de proyecto. Puede cambiar la plataforma de destino mediante las páginas de propiedades del proyecto o el **Administrador de configuración** del IDE.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

Una *configuración de destino* es un subconjunto de una plataforma de destino. Por ejemplo, la configuración `Debug` de `x86` no incluye la mayoría de las optimizaciones de código. La configuración de destino se especifica en la propiedad de compilación `Configuration` de un archivo de proyecto. Puede cambiar la configuración de destino mediante las páginas de propiedades del proyecto o el **Administrador de configuración**.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
</PropertyGroup>

```

## <a name="see-also"></a>Vea también

- [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md)
