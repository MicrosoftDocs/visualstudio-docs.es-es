---
title: Introducción a extensibilidad de Visual Studio Abrir carpeta | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2bb74703f639848d643f536edf620e30b1836310
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806495"
---
# <a name="open-folder-extensibility"></a>Extensibilidad de carpeta abierta

El [Abrir carpeta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) característica permite a los usuarios abrir cualquier código base en Visual Studio sin necesidad de archivos de proyecto o solución. Abrir carpeta proporciona que los funciones que los usuarios esperan de Visual Studio, como:

* Búsqueda y la integración del explorador de soluciones
* Coloración de editor
* Ir a la navegación
* Buscar en la búsqueda de archivos

Cuando se usa con las cargas de trabajo como en el caso de desarrollo .NET y C++, también se muestra:

* Rich Intellisense
* Funcionalidad específica del lenguaje

Con Abrir carpeta, los autores de extensiones pueden crear características enriquecidas para cualquier lenguaje. Existen API para admitir la creación, depuración y búsqueda de símbolos para cualquier archivo de un usuario del código base. Los extensores actuales pueden actualizar sus características de Visual Studio existentes para entender el código sin el respaldo de una solución o proyectos.

## <a name="an-api-without-project-systems"></a>Una API sin sistemas del proyecto

Históricamente, Visual Studio solo entiende los archivos en una solución y sus proyectos con los sistemas del proyecto. Un sistema de proyectos es responsable de las interacciones de usuario y la funcionalidad de un proyecto cargado. Entienda lo que su proyecto de archivos contiene la representación visual del contenido del proyecto, las dependencias en otros proyectos, y el archivo de proyecto de modificación de subyacente. Es a través de estas jerarquías y capacidades que otros componentes funcionan en nombre del usuario. No todos los códigos base también se representan en una estructura de proyecto y solución. Lenguajes de scripting y de código abierto escrito en C++ para Linux son buenos ejemplos. Con Abrir carpeta, Visual Studio proporciona a los usuarios una nueva forma de interactuar con su código fuente.

La API de carpeta abiertas están bajo el `Microsoft.VisualStudio.Workspace.*` espacio de nombres y están disponibles para que los extensores producir y consumir datos o acciones en torno a los archivos de carpeta abierta. Las extensiones pueden usar estas API para proporcionar la funcionalidad para muchas áreas, como:

- [Las áreas de trabajo](workspaces.md) : la extensibilidad de Abrir carpeta de punto de inicio es el área de trabajo y sus API.
- [Contextos y las acciones de archivo](workspace-file-contexts.md) -proporcionada a través de los contextos de archivo de inteligencia de código específico de archivos.
- [Indexación](workspace-indexing.md) : recopilar y conservar los datos sobre las áreas de trabajo de la carpeta abierta.
- [Servicios de lenguaje](workspace-language-services.md) -integrar servicios de lenguaje en las áreas de trabajo de la carpeta abierta.
- [Compilar](workspace-build.md) -crear compatibilidad para las áreas de trabajo de la carpeta abierta.

Las características que usan los siguientes tipos debe adoptar nuevas API para admitir la carpeta abierta:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Comentarios, comentarios y problemas

Abra la carpeta y el `Microsoft.VisualStudio.Workspace.*` API están en desarrollo activo. Si ve un comportamiento inesperado, a continuación, consulte los problemas conocidos de la versión de interés. [Comunidad de desarrolladores](https://developercommunity.visualstudio.com) es el lugar recomendado para votar y crear cualquier problema. Para cada tipo de comentarios, se recomienda encarecidamente obtener una descripción detallada del problema. Incluir la versión de Visual Studio que está desarrollando, las API que está usando (lo que ha implementado y está interactuando con), el resultado esperado y el resultado real. Si es posible, incluir un volcado del proceso devenv.exe. Utilice el problema de GitHub de seguimiento para enviar comentarios sobre este y documentación relacionada.

## <a name="next-steps"></a>Pasos siguientes

* [Las áreas de trabajo](workspaces.md) -Obtenga información sobre la API de área de trabajo de carpeta abierta.