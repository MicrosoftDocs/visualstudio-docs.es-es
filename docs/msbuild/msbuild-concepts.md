---
title: Conceptos de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 961f7df72476293c101ceeacbafbb31c1084fb20
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892887"
---
# <a name="msbuild-concepts"></a>Conceptos de MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proporciona un esquema XML básico que puede utilizar para controlar cómo la plataforma de compilación compila el software. Para especificar los componentes de la compilación y cómo se van a compilar, utilice estos cuatro elementos de MSBuild: propiedades, elementos, tareas y destinos.  

## <a name="related-topics"></a>Temas relacionados  

| Title | Descripción |
| - | - |
| [Propiedades de MSBuild](../msbuild/msbuild-properties.md) | Presenta las propiedades y las colecciones de propiedades. Las propiedades son pares clave-valor que se pueden utilizar para configurar compilaciones. |
| [Elementos de MSBuild](../msbuild/msbuild-items.md) | Presenta elementos y colecciones de elementos. Los elementos son entradas del sistema de compilación y suelen representar archivos. |
| [Destinos de MSBuild](../msbuild/msbuild-targets.md) | Explica cómo agrupar las tareas entre sí en un orden concreto y habilitar las secciones del proceso de compilación para que se las pueda llamar desde la línea de comandos. |
| [Tareas de MSBuild](../msbuild/msbuild-tasks.md) | Muestra la forma de crear una unidad de código ejecutable que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] puede usar para realizar operaciones de compilación indivisibles. |
| [Comparar propiedades y elementos](../msbuild/comparing-properties-and-items.md) | Compara los elementos y las propiedades de MSBuild. Ambos se utilizan para pasar información a las tareas, evaluar condiciones y almacenar valores a los que se puede hacer referencia en el archivo del proyecto. |
| [Caracteres especiales de MSBuild](../msbuild/msbuild-special-characters.md) | Explica cómo escapar algunos caracteres que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se reserva para usos especiales en contextos concretos. |
| [Tutorial: Crear un archivo del proyecto de MSBuild desde el principio](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Muestra la forma de crear un archivo básico del proyecto de forma incremental, utilizando solo un editor de texto. |
| [Tutorial: Usar MSBuild](../msbuild/walkthrough-using-msbuild.md) | Presenta los bloques de compilación de MSBuild y muestra la forma de escribir, manipular y depurar proyectos de MSBuild sin cerrar el Entorno de desarrollo integrado (IDE) de Visual Studio. |
| [Referencia de MSBuild](../msbuild/msbuild-reference.md) | Vínculos a documentos que contienen información de referencia. |
| [MSBuild](../msbuild/msbuild.md) | Ofrece información general sobre el esquema XML de un archivo del proyecto y muestra cómo controla los procesos que compilan el software. |

