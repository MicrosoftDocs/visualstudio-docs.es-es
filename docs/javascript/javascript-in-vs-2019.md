---
title: JavaScript y TypeScript en Visual Studio 2019
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 199a27dbfef2b7297563e87d973137e2acd9c745
ms.sourcegitcommit: eef26de3d7a5c971baedbecf3b4941fb683ddb2d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544294"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript y TypeScript en Visual Studio 2019

## <a name="overview"></a>Información general

Visual Studio 2019 proporciona compatibilidad enriquecida para el desarrollo con JavaScript, tanto con el uso de JavaScript directamente como con el uso del [lenguaje de programación TypeScript](http://www.typescriptlang.org/), que se desarrolló para ofrecer una experiencia de desarrollo con JavaScript más productiva y entretenida, sobre todo al desarrollar proyectos a escala. Puede escribir código JavaScript o TypeScript en Visual Studio para muchos tipos de aplicaciones y servicios.

## <a name="javascript-language-service"></a>Servicio de lenguaje JavaScript

La experiencia de JavaScript en Visual Studio 2019 la impulsa el mismo motor que ofrece compatibilidad con TypeScript. Esto ofrece mayor compatibilidad con características, mejoras e integración inmediata y lista para usar.

La opción para restaurar el servicio de lenguaje JavaScript heredado ya no está disponible. Ahora, los usuarios tienen el nuevo servicio de lenguaje JavaScript de fábrica. El nuevo servicio de lenguaje se basa exclusivamente en el servicio de lenguaje TypeScript, que funciona con análisis estático. Esto nos permite ofrecerle herramientas mejoradas, por lo que el código de JavaScript puede beneficiarse de IntelliSense con más funcionalidades según las definiciones de tipo. El nuevo servicio es ligero y consume menos memoria que el servicio heredado, lo que ofrece un mejor rendimiento a medida que se escale el código. También se ha mejorado el rendimiento del servicio de lenguaje para administrar proyectos más grandes.

## <a name="typescript-support"></a>Compatibilidad con TypeScript

Visual Studio 2019 ofrece varias opciones para la integración de la compilación con TypeScript en el proyecto:

* [El paquete NuGet de TypeScript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). Cuando se instala el paquete NuGet de TypeScript 3.2 o posterior en el proyecto, se carga la versión correspondiente del servicio de lenguaje TypeScript en el editor.
* [El paquete npm de TypeScript](https://www.npmjs.com/package/typescript). Cuando se instala el paquete npm de TypeScript 2.1 o posterior en el proyecto, se carga la versión correspondiente del servicio de lenguaje TypeScript en el editor.
* TypeScript SDK, disponible de forma predeterminada en el instalador de Visual Studio, así como una descarga independiente del SDK desde [VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017).

> [!TIP]
> Para los proyectos desarrollados en Visual Studio 2019, le animamos a usar el paquete NuGet de TypeScript o el paquete de npm de TypeScript para una mayor portabilidad entre distintas plataformas y entornos.

Un uso habitual del paquete NuGet es compilar TypeScript mediante la CLI de .NET Core. A menos que se edite manualmente el archivo del proyecto para importar destinos de compilación desde una instalación TypeScript SDK, el paquete NuGet es la única manera de habilitar la compilación de TypeScript mediante comandos de la CLI de .NET Core, como `dotnet build` y `dotnet publish`.

## <a name="remove-default-imports-aspnet-core-projects"></a>Eliminación de importaciones predeterminadas (proyectos de ASP.NET Core)

En proyectos anteriores que usan el [formato de estilo que no es de SDK](https://docs.microsoft.com/nuget/resources/check-project-format), puede que tenga que quitar algunos elementos de archivo del proyecto.

Si se usa el paquete NuGet para la compatibilidad con MSBuild de un proyecto, el archivo del proyecto no debe importar `Microsoft.TypeScript.Default.props` ni `Microsoft.TypeScript.targets`. Los archivos los importa el paquete NuGet, por lo que incluirlos por separado podría provocar un comportamiento no intencionado.

1. Haga clic con el botón derecho en el proyecto y elija **Descargar proyecto**.

1. Haga clic con el botón derecho en el proyecto y elija **Editar\<*nombre de archivo del proyecto*\>** .

   El archivo del proyecto se abre.

1. Quite las referencias a `Microsoft.TypeScript.Default.props` y `Microsoft.TypeScript.targets`.

   Las importaciones que se van a quitar tienen un aspecto similar al siguiente:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```

## <a name="projects"></a>Proyectos

Las aplicaciones de JavaScript para UWP ya no se admiten en Visual Studio 2019. No puede crear ni abrir proyectos de JavaScript para UWP (archivos con extensión *.jsproj*). Para más información, consulte nuestra documentación sobre la [creación de aplicaciones web progresivas (PWA) que se ejecuten correctamente en Windows](/microsoft-edge/progressive-web-apps/get-started).
