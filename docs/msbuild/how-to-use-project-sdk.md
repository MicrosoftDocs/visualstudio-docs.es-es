---
title: Referencia a un SDK de un proyecto de MSBuild| Microsoft Docs
description: Obtenga información sobre cómo usar los SDK de un proyecto de MSBuild para simplificar el uso de los kits de desarrollo de software que requieren la importación de propiedades y destinos.
ms.custom: SEO-VS-2020
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6303efce016a9e678e4c9e8aa62c91aa116e44f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914226"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Cómo: Usar SDK de proyecto de MSBuild

En MSBuild 15.0 se presentó el concepto de "SDK de proyecto", que simplifica el uso de kits de desarrollo de software en los que es necesario importar propiedades y destinos.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Durante la evaluación del proyecto, MSBuild agrega importaciones implícitas en la parte superior e inferior del archivo del proyecto:

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

## <a name="reference-a-project-sdk"></a>Referencia a un SDK de proyecto

Hay tres maneras de hacer referencia a un SDK de proyecto:

- Use el atributo `Sdk` en el elemento `<Project/>`:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Una importación implícita se agrega a la parte superior e inferior del proyecto, como se ha explicado antes.
    
    Para especificar una versión concreta del SDK, anéxela al atributo `Sdk`:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

- Use el elemento `<Sdk/>` de nivel superior:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Una importación implícita se agrega a la parte superior e inferior del proyecto, como se ha explicado antes.
   
   El atributo `Version` no es necesario.

- Use el elemento `<Import/>` en cualquier parte de su proyecto:

    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```

   La inclusión explícita de las importaciones en el proyecto permite ejercer un control total sobre el orden.

   Al usar el elemento `<Import/>`, puede especificar también un atributo `Version` opcional. Por ejemplo, puede especificar `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Resolución de SDK de proyecto

Al evaluar la importación, MSBuild resuelve de forma dinámica la ruta de acceso al SDK del proyecto en función del nombre y la versión especificados.  MSBuild también tiene una lista de solucionadores de SDK registrados, que son complementos que ubican los SDK de proyecto en el equipo. Entre estos complementos se incluyen los siguientes:

- Una resolución basada en NuGet que consulta las fuentes de paquetes configuradas para los paquetes NuGet que coinciden con el identificador y la versión del SDK especificado.

   Este solucionador solo está activo si ha especificado una versión opcional. Se puede usar para cualquier SDK de proyecto personalizado.
   
- Un solucionador del SDK de .NET que resuelve los SDK de MSBuild que se instalan con el [SDK de .NET](/dotnet/core/sdk/).

   Este solucionador busca SDK de proyecto como `Microsoft.NET.Sdk` y `Microsoft.NET.Sdk.Web` que forman parte del producto.
   
- Una resolución predeterminada que resuelve los SDK que se instalaron con MSBuild.

El solucionador del SDK basado en NuGet admite la especificación de una versión en su archivo [global.json](/dotnet/core/tools/global-json), lo que permite controlar la versión del SDK de proyecto en un solo lugar y no en cada proyecto individual:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Durante una compilación, solo se puede usar una versión de cada SDK de proyecto. Si hace referencia a dos versiones diferentes del mismo SDK de proyecto, MSBuild emite una advertencia. Se recomienda **no** especificar una versión en los proyectos si se ha especificado una versión en el archivo *global.json*.

## <a name="see-also"></a>Vea también

- [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)
- [Personalizar una compilación](../msbuild/customize-your-build.md)
- [Paquetes, metapaquetes y marcos de trabajo](/dotnet/core/packages)
- [Adiciones al formato csproj para .NET Core](/dotnet/core/tools/csproj)
