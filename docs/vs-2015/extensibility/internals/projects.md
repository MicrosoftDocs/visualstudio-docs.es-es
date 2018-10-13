---
title: Proyectos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 44
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb67c01732f5347e13c09146379d2b79298d198d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236059"
---
# <a name="projects"></a>Proyectos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En Visual Studio, los proyectos son contenedores que los desarrolladores usan para organizar los archivos de código fuente y otros recursos que aparecen en **el Explorador de soluciones**. Normalmente, los proyectos son archivos (por ejemplo, un archivo .csproj para un proyecto de C#) que almacenan las referencias a archivos de código fuente y los recursos, como archivos de mapa de bits. Proyectos permiten organizar, compilar, depurar y distribuir el código fuente, las referencias a servicios Web y bases de datos y otros recursos. Los paquetes VSPackage pueden extender el sistema de proyectos de Visual Studio de tres maneras principales: *tipos de proyecto*, *subtipos de proyecto*, y *herramientas personalizadas*.  
  
## <a name="in-this-section"></a>En esta sección  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 *Tipos de proyecto* agregar compatibilidad para nuevos tipos de proyectos, como los lenguajes de programación. Por ejemplo, cada lenguaje compatible con Visual Studio tiene su propio tipo de proyecto y el ejemplo de integración de IronPython incluye un tipo de proyecto para el idioma de IronPython. Debe crear un tipo de proyecto para los idiomas que no sean de C# o Visual Basic para personalizar cómo elementos son creados, depurar, implementan y muestran en **el Explorador de soluciones**. Para obtener más información, consulte [tipos de proyecto](../../extensibility/internals/project-types.md).  
  
 [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)  
 *Subtipos de proyecto* se basan en tipos de proyecto y puede usarse para personalizar la forma en que los proyectos se compila, depurando e implementados. Visual Studio usa subtipos de proyecto con proyectos de Smart Device. Personalice la implementación mediante la copia de un programa recién creado desde un equipo de desarrollo al dispositivo de destino. Tipos de proyecto de Visual Basic y C# pueden usarse como base para los subtipos de proyecto; Tipos de proyectos de C++ no. También se pueden usar sus propios tipos de proyecto como base para los subtipos de proyecto. Para obtener más información, consulte [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
 [Proyectos web](../../extensibility/internals/web-projects.md)  
 Explica el proyecto Web, que a su vez crear aplicaciones Web.  
  
 [Nueva generación de proyectos: Aspectos técnicos, primera parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) y [nueva generación de proyectos: aspectos técnicos, segunda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Explica lo que realmente sucede cuando se crea un nuevo proyecto.  
  
 [Muestras de VSSDK](../../misc/vssdk-samples.md)  
 Describe los ejemplos de VSSDK que se encargan de proyectos y soluciones.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Dentro de Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Explica distintos aspectos de extensibilidad de Visual Studio.

