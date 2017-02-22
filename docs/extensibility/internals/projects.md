---
title: "Proyectos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "soluciones [Visual Studio]"
  - "herramientas personalizadas [Visual Studio SDK]"
  - "subtipos de proyecto [Visual Studio SDK]"
  - "proyectos [Visual Studio SDK]"
  - "tipos de proyecto [Visual Studio SDK]"
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 43
caps.handback.revision: 40
ms.author: "gregvanl"
manager: "ghogen"
---
# Proyectos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], los proyectos son los contenedores que los desarrolladores usan para organizar los archivos de código fuente y otros recursos que aparecen en **el Explorador de soluciones**. Normalmente, los proyectos son archivos, por ejemplo, un archivo .csproj para un [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proyecto, que almacenan las referencias a recursos como archivos de mapa de bits y los archivos de código fuente. Proyectos permiten organizar, compilar, depurar y distribuir el código fuente, las referencias a servicios Web y bases de datos y otros recursos. VSPackages puede ampliar el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sistema de proyectos de tres maneras principales: *tipos de proyecto*, *subtipos de proyecto*, y *herramientas personalizadas*.  
  
 Para obtener un ejemplo de extremo a extremo de un sistema de proyectos de lenguaje, vea el Visual Studio IronPython ejemplo profundización en el [Muestras de VSSDK](../../misc/vssdk-samples.md).  
  
## En esta sección  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 *Los tipos de proyecto* agregar compatibilidad para nuevos tipos de proyectos, como los lenguajes de programación. Por ejemplo, cada lenguaje que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite tiene su propio tipo de proyecto y el ejemplo de integración de IronPython incluye un tipo de proyecto para el idioma de IronPython. Debe crear un tipo de proyecto para idiomas distintos de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], para personalizar cómo elementos se genera, depurar, implementan y muestra en **el Explorador de soluciones**. Para obtener más información, vea [Tipos de proyecto](../../extensibility/internals/project-types.md) y [Muestras de VSSDK](../../misc/vssdk-samples.md).  
  
 [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)  
 *Subtipos de proyecto* se basan en tipos de proyecto y puede utilizarse para personalizar la forma de proyectos se genera, depure y se implemente.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliza los subtipos de proyecto con proyectos de Smart Device. personalizan implementación mediante la copia de un programa recién creado desde un equipo de desarrollo al dispositivo de destino. El [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipos de proyecto se pueden utilizar como base para los subtipos de proyecto; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] no tipos de proyecto. Sus propios tipos de proyecto también pueden utilizarse como base para los subtipos de proyecto. Para obtener más información, consulta [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
 [Proyectos Web](../../extensibility/internals/web-projects.md)  
 Explica el proyecto Web, que a su vez crear aplicaciones Web.  
  
 [Nueva generación de proyecto: En realidad, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) y [Nueva generación de proyecto: Bajo el capó, segunda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Explica lo que sucede realmente cuando se crea un nuevo proyecto.  
  
 [Muestras de VSSDK](../../misc/vssdk-samples.md)  
 Describe los ejemplos en el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] que tratar con proyectos y soluciones.  
  
## Secciones relacionadas  
 [NIB: proyectos como contenedores](http://msdn.microsoft.com/es-es/87d40f63-f487-4767-8963-64beec27ba1b)  
 Describe la relación entre los proyectos y elementos de proyecto.