---
title: JavaScript y TypeScript en Visual Studio 2019
ms.date: 03/27/2019
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
ms.openlocfilehash: 3000510c6bb6079629a3df05909417593569c932
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232267"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript y TypeScript en Visual Studio 2019

## <a name="overview"></a>Información general

Visual Studio 2019 proporciona compatibilidad enriquecida para el desarrollo con JavaScript, tanto con el uso de JavaScript directamente como con el uso del [lenguaje de programación TypeScript](http://www.typescriptlang.org), que se desarrolló para ofrecer una experiencia de desarrollo con JavaScript más productiva y entretenida, sobre todo al desarrollar proyectos a escala. Puede escribir código JavaScript o TypeScript en Visual Studio para muchos tipos de aplicaciones y servicios.

## <a name="javascript-language-service"></a>Servicio de lenguaje JavaScript

La experiencia de JavaScript en Visual Studio 2019 la impulsa el mismo motor que ofrece compatibilidad con TypeScript. Esto ofrece mayor compatibilidad con características, mejoras e integración inmediata y lista para usar.

La opción para restaurar el servicio de lenguaje JavaScript heredado ya no está disponible. Ahora, los usuarios tienen el nuevo servicio de lenguaje JavaScript de fábrica. El nuevo servicio de lenguaje se basa exclusivamente en el servicio de lenguaje TypeScript, que funciona con análisis estático. Esto nos permite ofrecerle herramientas mejoradas, por lo que el código de JavaScript puede beneficiarse de IntelliSense con más funcionalidades según las definiciones de tipo. El nuevo servicio es ligero y consume menos memoria que el servicio heredado, lo que ofrece un mejor rendimiento a medida que se escale el código. También se ha mejorado el rendimiento del servicio de lenguaje para administrar proyectos más grandes.

## <a name="typescript-support"></a>Compatibilidad con TypeScript

Visual Studio 2019 ofrece varias opciones para la integración de la compilación con TypeScript en el proyecto:

* [El paquete NuGet de TypeScript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). Cuando se instala el paquete NuGet de TypeScript 3.2 o posterior en el proyecto, se carga la versión correspondiente del servicio de lenguaje TypeScript en el editor.
* TypeScript SDK, disponible de forma predeterminada en el instalador de Visual Studio, así como una descarga independiente del SDK desde [VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017).
* [El paquete npm de TypeScript](https://www.npmjs.com/package/typescript). Cuando se instala el paquete npm de TypeScript 2.1 o posterior en el proyecto, se carga la versión correspondiente del servicio de lenguaje TypeScript en el editor.

Para los proyectos desarrollados en Visual Studio 2019, le animamos a usar los paquetes npm y NuGet de TypeScript para una mayor portabilidad entre distintas plataformas y entornos.

## <a name="projects"></a>Proyectos

Las aplicaciones de JavaScript para UWP ya no se admiten en Visual Studio 2019. No puede crear ni abrir proyectos de JavaScript para UWP (archivos con extensión *.jsproj*). Para más información, consulte nuestra documentación sobre la [creación de aplicaciones web progresivas (PWA) que se ejecuten correctamente en Windows](https://docs.microsoft.com/microsoft-edge/progressive-web-apps/get-started).
