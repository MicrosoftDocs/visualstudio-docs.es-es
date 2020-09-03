---
title: Proyectos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b7a9299321d2aa80eebb564bf9b926f07ab0108
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706214"
---
# <a name="projects"></a>Proyectos
En Visual Studio, los proyectos son los contenedores que los desarrolladores usan para organizar los archivos de código fuente y otros recursos que aparecen en **Explorador de soluciones**. Normalmente, los proyectos son archivos (por ejemplo, un archivo. csproj para un proyecto de C#) que almacenan referencias a archivos de código fuente y recursos como archivos de mapa de bits. Los proyectos permiten organizar, compilar, depurar e implementar código fuente, referencias a servicios web y bases de datos, y a otros recursos. Los VSPackages pueden extender el sistema de proyectos de Visual Studio de tres maneras principales: *tipos de proyecto*, *subtipos de proyecto*y *herramientas personalizadas*.

## <a name="in-this-section"></a>En esta sección
- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Los *tipos de proyecto* agregan compatibilidad para los nuevos tipos de proyectos, como los lenguajes de programación. Por ejemplo, cada idioma que Visual Studio admite tiene su propio tipo de proyecto, y el ejemplo de integración de IronPython incluye un tipo de proyecto para el lenguaje IronPython. Debe crear un tipo de proyecto para lenguajes distintos de C# o Visual Basic para personalizar cómo se compilan, depuran, implementan y muestran los elementos en **Explorador de soluciones**. Para obtener más información, vea [tipos de proyecto](../../extensibility/internals/project-types.md).

- [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)

 Los *subtipos de proyecto* se basan en tipos de proyecto y se pueden usar para personalizar la manera en que se compilan, depuran e implementan los proyectos. Visual Studio usa subtipos de proyecto con proyectos de Smart Device. personalizan la implementación mediante la copia de un programa recién compilado de un equipo de desarrollo en el dispositivo de destino. Los tipos de proyecto de C# y Visual Basic se pueden usar como base para los subtipos de proyecto; Los tipos de proyecto de C++ no pueden. Sus propios tipos de proyecto también se pueden usar como base para los subtipos de proyecto. Para obtener más información, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).

- [Proyectos web](../../extensibility/internals/web-projects.md)

 Explica el proyecto Web, que a su vez crea aplicaciones Web.

- [Nueva generación de proyectos: debajo del capó, parte uno](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) y [nueva generación de proyectos: debajo del capó, parte 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Explica lo que ocurre realmente cuando se crea un nuevo proyecto.

- [Ejemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Contiene los ejemplos del VSSDK que se ocupan de los proyectos y las soluciones.

## <a name="related-sections"></a>Secciones relacionadas
- [Dentro de Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Explicar distintos aspectos de la extensibilidad de Visual Studio.
