---
title: Proyectos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: "43"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c175d85b55734df841f30d131639c3bfeed40361
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="projects"></a>Proyectos
En Visual Studio, los proyectos son los contenedores que los desarrolladores usan para organizar los archivos de código fuente y otros recursos que aparecen en **el Explorador de soluciones**. Normalmente, los proyectos son archivos (por ejemplo, un archivo .csproj para un proyecto de C#) que almacenan las referencias a archivos de código fuente y los recursos como los archivos de mapa de bits. Proyectos permiten organizar, compilar, depurar y distribuir el código fuente, las referencias a servicios Web y bases de datos y otros recursos. Paquetes VSPackage puede extender el sistema de proyectos de Visual Studio de tres maneras principales: *tipos de proyecto*, *subtipos de proyecto*, y *herramientas personalizadas*.  
  
## <a name="in-this-section"></a>En esta sección  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 *Tipos de proyecto* agregar compatibilidad con nuevos tipos de proyectos, como los lenguajes de programación. Por ejemplo, cada lenguaje compatible con Visual Studio tiene su propio tipo de proyecto, y el ejemplo de integración de IronPython incluye un tipo de proyecto para el idioma de IronPython. Debe crear un tipo de proyecto para lenguajes distintos de C# o Visual Basic para personalizar cómo se compila, se depurando, se implementan y se muestra en elementos **el Explorador de soluciones**. Para obtener más información, consulte [tipos de proyecto](../../extensibility/internals/project-types.md).  
  
 [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)  
 *Subtipos de proyecto* se basan en tipos de proyecto y puede usarse para personalizar la forma en que se generan, depurar e implementa los proyectos. Visual Studio usa subtipos de proyecto con los proyectos de Smart Device; personalizan implementación mediante la copia de un programa recién creado desde un equipo de desarrollo al dispositivo de destino. Tipos de proyecto de Visual Basic y C# pueden utilizarse como base para los subtipos de proyecto; No pueden tener tipos de proyectos de C++. Sus propios tipos de proyecto también pueden utilizarse como base para los subtipos de proyecto. Para obtener más información, consulte [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
 [Proyectos web](../../extensibility/internals/web-projects.md)  
 Explica el proyecto Web, que a su vez crear aplicaciones Web.  
  
 [Nueva generación de proyecto: Under the Hood, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) y [nueva generación de proyecto: Under the Hood, segunda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Explica lo que sucede realmente cuando se crea un nuevo proyecto.  
  
 [Muestras de VSSDK](http://aka.ms/vs2015sdksamples)  
 Contiene los ejemplos en el VSSDK que se encargan de proyectos y soluciones.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Dentro de Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Explica los diferentes aspectos de la extensibilidad de Visual Studio.