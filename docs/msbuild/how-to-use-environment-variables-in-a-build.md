---
title: Procedimiento Usar variables de entorno en una compilación | Microsoft Docs
description: Obtenga información sobre cómo acceder a las variables de entorno de los archivos de proyectos de MSBuild y usar estas variables de entorno para establecer opciones de compilación sin modificar el archivo del proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c7c81f36d37d071593a013067f661451b8916caa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914201"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Cómo: Usar variables de entorno en una compilación

Al compilar proyectos, a menudo es necesario establecer las opciones de compilación mediante información que no está en el archivo del proyecto o en los archivos que componen el proyecto. Normalmente, esta información se almacena en variables de entorno.

## <a name="reference-environment-variables"></a>Referencia a variables de entorno

 Todas las variables de entorno están disponibles para el archivo del proyecto Microsoft Build Engine (MSBuild) como propiedades.

> [!NOTE]
> Si el archivo del proyecto contiene una definición explícita de una propiedad que tiene el mismo nombre que una variable de entorno, la propiedad en el archivo del proyecto invalida el valor de la variable de entorno.

#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Para utilizar una variable de entorno en un proyecto de MSBuild

- Haga referencia a la variable de entorno del mismo modo que lo haría con una variable declarada en el archivo del proyecto. Por ejemplo, el código siguiente hace referencia a la variable de entorno BIN_PATH:

   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`

  Puede utilizar un atributo `Condition` para proporcionar un valor predeterminado a una propiedad si no se ha establecido la variable de entorno.

#### <a name="to-provide-a-default-value-for-a-property"></a>Para proporcionar un valor predeterminado a una propiedad

- Utilice un atributo `Condition` en una propiedad para establecer el valor solo si la propiedad no tiene ningún valor. Por ejemplo, el código siguiente establece la propiedad `ToolsPath` en *c:\tools* solo si la variable de entorno `ToolsPath` no está establecida:

     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`

    > [!NOTE]
    > Los nombres de propiedades no distinguen mayúsculas de minúsculas, por lo que `$(ToolsPath)` y `$(TOOLSPATH)` hacen referencia a la misma propiedad o variable de entorno.

## <a name="example"></a>Ejemplo

 El siguiente archivo del proyecto utiliza variables de entorno para especificar la ubicación de los directorios.

```xml
<Project DefaultTargets="FakeBuild">
    <PropertyGroup>
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">
            C:\Tools
        </ToolsPath>
    </PropertyGroup>
    <Target Name="FakeBuild">
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Vea también

- [MSBuild](../msbuild/msbuild.md)
- [Propiedades de MSBuild](../msbuild/msbuild-properties.md)
- [Cómo: Compilar los mismos archivos de código fuente con diferentes opciones](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
