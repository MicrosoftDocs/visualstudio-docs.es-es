---
title: Información general sobre Visual Studio Abrir carpeta extensibility | Documentos de Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: d916ea30dd9b72a2d8bd59e8d3d34f9e73c74877
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="open-folder-extensibility"></a>Extensibilidad de carpeta abierta

El [Abrir carpeta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) característica permite a los usuarios abrir cualquier codebase en Visual Studio sin necesidad de archivos de proyecto o solución. Abrir carpeta proporciona que los funciones que los usuarios esperan desde Visual Studio, como:

* Búsqueda y la integración del explorador de soluciones
* Colores del Editor
* Ir a la navegación
* Buscar en la búsqueda de archivos

Cuando se usa con las cargas de trabajo como desarrollo .NET y C++, también se obtienen los usuarios:

* Intellisense enriquecido
* Funcionalidad específica del lenguaje

Con la carpeta abierta, autores de extensiones pueden crear características enriquecidas para ningún idioma. Existen API para admitir la creación, la depuración y la búsqueda de símbolos para cualquier archivo de un usuario del código base. Extender actual puede actualizar sus características de Visual Studio existentes para entender el código sin el respaldo de proyecto o una solución.

## <a name="an-api-without-project-systems"></a>Una API sin sistemas del proyecto

Históricamente, Visual Studio sólo las entienden los archivos en una solución y sus proyectos con los sistemas del proyecto. Un sistema de proyectos es responsable de las interacciones de usuario y la funcionalidad de un proyecto cargado. Comprende qué archivos de su proyecto contiene la representación visual del contenido del proyecto, dependencias de otros proyectos, y el archivo de proyecto de modificación de subyacente. Es a través de estas jerarquías y capacidades que otros componentes funcionan en nombre del usuario. No todas las bases de código también se representan en una estructura de proyecto y solución. Lenguajes de scripting y el código de código abierto escrito en C++ para Linux son buenos ejemplos. Con la carpeta abierta, Visual Studio proporciona a los usuarios una nueva manera de interactuar con su código fuente.

La API de carpeta abiertas están bajo el `Microsoft.VisualStudio.Workspace.*` espacio de nombres y están disponibles para extender generar y consumir datos o acciones alrededor de archivos dentro de la carpeta abierta. Extensiones pueden usar estas API para proporcionar funcionalidad de muchas áreas, incluyendo:

- [Áreas de trabajo](workspaces.md) : a partir de extensibilidad de punto de Abrir carpeta es el área de trabajo y sus API.
- [Archivo contextos y acciones](workspace-file-contexts.md) -archivo inteligencia de código concretos proporcionada a través de contextos de archivo.
- [Indización](workspace-indexing.md) : recopila y conservar los datos sobre las áreas de la carpeta abierta.
- [Servicios de lenguaje](workspace-language-services.md) -integrar servicios de lenguaje en áreas de trabajo de carpeta abierta.
- [Generar](workspace-build.md) -compatibilidad para áreas de trabajo de abrir la carpeta de compilación.

Características que usan los tipos siguientes se deben adoptar nuevas API para admitir la carpeta abierta:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Comentarios, comentarios, problemas

Abra la carpeta y el `Microsoft.VisualStudio.Workspace.*` API están en desarrollo activo. Si ve un comportamiento inesperado, a continuación, vea los problemas conocidos de la versión de interés. La Comunidad de desarrolladores es el lugar recomendado para votar y crear cualquier problema. Para cada comentarios, se recomienda encarecidamente obtener una descripción detallada del problema. Incluye la versión de Visual Studio que se va a desarrollar para, las API que está usando (lo que ha implementado y está interactuando con), el resultado esperado y el resultado real. Si es posible, incluir un volcado de memoria del proceso devenv.exe. Utilice el problema de GitHub para enviar comentarios en el objeto de seguimiento y la documentación relacionada.

## <a name="next-steps"></a>Pasos siguientes

* [Áreas de trabajo](workspaces.md) -obtener información sobre el área de trabajo de Abrir carpeta API.