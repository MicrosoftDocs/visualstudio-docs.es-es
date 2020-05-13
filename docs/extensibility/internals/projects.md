---
title: Proyectos de la página de la inser Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706214"
---
# <a name="projects"></a>Proyectos
En Visual Studio, los proyectos son los contenedores que los desarrolladores usan para organizar los archivos de código fuente y otros recursos que aparecen en el Explorador de **soluciones.** Normalmente, los proyectos son archivos (por ejemplo, un archivo .csproj para un proyecto de C) que almacenan referencias a archivos de código fuente y recursos como archivos de mapa de bits. Los proyectos le permiten organizar, compilar, depurar e implementar código fuente, referencias a servicios web y bases de datos y otros recursos. VSPackages puede ampliar el sistema de proyectos de Visual Studio de tres maneras principales: tipos de *proyecto,* *subtipos*de proyecto y *herramientas personalizadas.*

## <a name="in-this-section"></a>En esta sección
- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 *Los tipos* de proyecto agregan compatibilidad con nuevos tipos de proyectos, como lenguajes de programación. Por ejemplo, cada lenguaje que admite Visual Studio tiene su propio tipo de proyecto y el ejemplo de integración de IronPython incluye un tipo de proyecto para el lenguaje IronPython. Debe crear un tipo de proyecto para los lenguajes que no sean de C o Visual Basic para personalizar cómo se compilan, depuran, implementan y muestran los elementos en el **Explorador**de soluciones. Para obtener más información, vea [Tipos de proyecto](../../extensibility/internals/project-types.md).

- [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)

 *Los subtipos* de proyecto se basan en tipos de proyecto y se pueden usar para personalizar la forma en que se compilan, depuran e implementan los proyectos. Visual Studio usa subtipos de proyecto con proyectos de dispositivo inteligente; personalizan la implementación copiando un programa de nueva construcción desde un equipo de desarrollo al dispositivo de destino. Los tipos de proyecto de C- y Visual Basic se pueden usar como base para los subtipos de proyecto; Los tipos de proyecto C++ no pueden. Sus propios tipos de proyecto también se pueden utilizar como base para subtipos de proyecto. Para obtener más información, vea [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md).

- [Proyectos web](../../extensibility/internals/web-projects.md)

 Explica el proyecto Web, que a su vez crea aplicaciones web.

- [Nueva generación de proyectos: Bajo la capucha, primera parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) y nueva generación de [proyectos: Bajo la capucha, segunda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Explica lo que realmente ocurre cuando se crea un nuevo proyecto.

- [Muestras VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Contiene los ejemplos del VSSDK que tratan con proyectos y soluciones.

## <a name="related-sections"></a>Secciones relacionadas
- [Dentro de Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Explicar diferentes aspectos de la extensibilidad de Visual Studio.
