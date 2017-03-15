---
title: Conceptos de MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: f6c59188abc8cbb9909c12438bc58fa9301d8af9
ms.openlocfilehash: 9a53328adf662b1c47dc1bf2317764562f2e204e
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-concepts"></a>Conceptos de MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proporciona un esquema XML básico que puede utilizar para controlar cómo la plataforma de compilación compila el software. Para especificar los componentes de la compilación y cómo se van a compilar, utilice estos cuatro elementos de MSBuild: propiedades, elementos, tareas y destinos.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Propiedades de MSBuild](../msbuild/msbuild-properties.md)|Presenta las propiedades y las colecciones de propiedades. Las propiedades son pares clave-valor que se pueden utilizar para configurar compilaciones.|  
|[Elementos](../msbuild/msbuild-items.md)|Describe los conceptos generales en que se basa el formato de archivo de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] y la manera de encajar las piezas.|  
|[Destinos](../msbuild/msbuild-targets.md)|Explica cómo agrupar las tareas entre sí en un orden concreto y habilitar las secciones del proceso de compilación para que se las pueda llamar desde la línea de comandos.|  
|[Tareas](../msbuild/msbuild-tasks.md)|Muestra la forma de crear una unidad de código ejecutable que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] puede usar para realizar operaciones de compilación indivisibles.|  
|[Comparar propiedades y elementos](../msbuild/comparing-properties-and-items.md)|Compara los elementos y las propiedades de MSBuild. Ambos se utilizan para pasar información a las tareas, evaluar condiciones y almacenar valores a los que se puede hacer referencia en el archivo del proyecto.|  
|[Caracteres especiales de MSBuild](../msbuild/msbuild-special-characters.md)|Explica cómo escapar algunos caracteres que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se reserva para usos especiales en contextos concretos.|  
|[Tutorial: Crear un archivo del proyecto de MSBuild desde el principio](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Muestra la forma de crear un archivo básico del proyecto de forma incremental, utilizando solo un editor de texto.|  
|[Tutorial: Usar MSBuild](../msbuild/walkthrough-using-msbuild.md)|Presenta los bloques de compilación de MSBuild y muestra la forma de escribir, manipular y depurar proyectos de MSBuild sin cerrar el Entorno de desarrollo integrado (IDE) de Visual Studio.|  
|[Referencia de MSBuild](../msbuild/msbuild-reference.md)|Vínculos a documentos que contienen información de referencia.|  
|[MSBuild](../msbuild/msbuild.md)|Ofrece información general sobre el esquema XML de un archivo del proyecto y muestra cómo controla los procesos que compilan el software.|
