---
title: Información general sobre la extensibilidad de carpetas abiertas de Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: overview
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: d213a7add358c46f7088f504d8c54352cda44a1c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905974"
---
# <a name="open-folder-extensibility"></a>Abrir extensibilidad de carpetas

La característica [Abrir carpeta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) permite a los usuarios abrir cualquier código base en Visual Studio sin necesidad de archivos de proyecto o de solución. Abrir carpeta proporciona las características que los usuarios esperan de Visual Studio, como:

* Explorador de soluciones integración y búsqueda
* Coloración del editor
* Ir a navegación
* Buscar en archivos-búsqueda

Cuando se usa con cargas de trabajo como para el desarrollo de .NET y C++, los usuarios también obtienen:

* IntelliSense enriquecido
* Funcionalidad específica del lenguaje

Con abrir carpeta, los autores de extensiones pueden crear características enriquecidas para cualquier lenguaje. Hay API que admiten la compilación, la depuración y la búsqueda de símbolos para cualquier archivo en el código base de un usuario. Los extensores actuales pueden actualizar sus características de Visual Studio existentes para comprender el código sin la copia de seguridad de proyectos o de una solución.

## <a name="an-api-without-project-systems"></a>Una API sin sistemas de proyecto

Históricamente, Visual Studio solo entendió archivos en una solución y sus proyectos con sistemas de proyecto. Un sistema de proyectos es responsable de la funcionalidad y las interacciones de los usuarios de un proyecto cargado. Comprende los archivos que contiene el proyecto, la representación visual del contenido del proyecto, las dependencias de otros proyectos y la modificación del archivo de proyecto subyacente. A través de estas jerarquías y capacidades que otros componentes funcionan en nombre del usuario. No todos los códigos base se representan bien en una estructura de proyecto y de solución. Los lenguajes de scripting y el código de código abierto escritos en C++ para Linux son buenos ejemplos. Con abrir carpeta, Visual Studio proporciona a los usuarios una nueva forma de interactuar con el código fuente.

Las API de Open folder están bajo el `Microsoft.VisualStudio.Workspace.*` espacio de nombres y están disponibles para que los extensores generen y consuman datos o acciones en torno a los archivos de la carpeta abierta. Las extensiones pueden usar estas API para proporcionar funcionalidad para muchas áreas, entre las que se incluyen:

- [Áreas de trabajo](workspaces.md) : el punto de inicio de la extensibilidad de carpetas abiertas es el área de trabajo y sus API.
- [Contextos de archivo y acciones](workspace-file-contexts.md) : inteligencia de código específico del archivo que se proporciona a través de contextos de archivo.
- [Indexación](workspace-indexing.md) : recopilar y conservar datos sobre áreas de trabajo de carpeta abiertas.
- [Servicios de lenguaje](workspace-language-services.md) : integre los servicios de lenguaje en áreas de trabajo de carpeta abiertas.
- [Compilación](workspace-build.md) : compatibilidad con la compilación de áreas de trabajo de carpeta abierta.

Las características que usan los siguientes tipos deberán adoptar nuevas API para admitir la carpeta abierta:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Comentarios, comentarios, problemas

Abra la carpeta y las `Microsoft.VisualStudio.Workspace.*` API están en desarrollo activo. Si ve un comportamiento inesperado, consulte los problemas conocidos de la versión de interés. La [comunidad de desarrolladores](https://developercommunity.visualstudio.com) es el lugar recomendado para votar y crear cualquier problema. Para cada comentario, se recomienda una descripción detallada del problema. Incluya la versión de Visual Studio para la que está desarrollando, las API que está usando (lo que ha implementado y con qué está interactuando), el resultado esperado y el resultado real. Si es posible, incluya un volcado del proceso de devenv.exe. Use el seguimiento de problemas de GitHub para proporcionar comentarios sobre esta documentación relacionada con.

## <a name="next-steps"></a>Pasos siguientes

* [Áreas de trabajo](workspaces.md) : Obtenga información sobre la API de área de trabajo abrir carpeta.