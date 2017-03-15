---
title: "Crear y usar directivas de protecci&#243;n del an&#225;lisis de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "análisis de código, directivas de protección"
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 39
caps.handback.revision: 39
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Crear y usar directivas de protecci&#243;n del an&#225;lisis de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando use el control de versiones de Team Foundation \(TFVC\), puede crear una directiva de protección de análisis de código para los proyectos de código nativo \(C\/C\+\+\) y .NET Framework en un proyecto de equipo.  Puede usar la directiva de protección de análisis de código para controlar y mejorar la calidad del código protegido en el código base.  
  
 La directiva se supera cuando se actualiza la compilación local y se ha ejecutado el análisis de código en los archivos de código fuente más recientes.  Como mínimo, las reglas de análisis de código habilitadas en el proyecto de código deben contener las mismas reglas que las que se definen en la directiva de protección del proyecto de equipo.  Las reglas especificadas como errores en la Configuración del proyecto de equipo también deben especificarse como errores en el proyecto de código  
  
> [!IMPORTANT]
>  Las directivas de protección de análisis de código no se pueden aplicar a los proyectos de sitio web.  Pueden aplicarse a los proyectos de aplicación web.  
  
 Las directivas de protección de análisis de código se crean a través de la Configuración del proyecto de equipo de [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)].  Las directivas de protección se especifican y aplican en un proyecto de equipo, pero las ejecuciones de análisis de código se configuran y llevan a cabo en proyectos de código individuales de equipos de desarrollo locales.  En esta sección se describe cómo se especifican las directivas de protección de análisis de código de un proyecto de equipo y cómo se implementan directivas de análisis de código personalizadas en el código administrado.  
  
## En esta sección  
 [Cómo: Crear o actualizar directivas de protección de análisis de código estándar](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Explica los pasos que se siguen para establecer y modificar una directiva de análisis de código de un proyecto de equipo.  
  
 [Implementar directivas de protección personalizadas para el código administrado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Explica los pasos que debe seguir para crear un conjunto de reglas personalizadas para la directiva de protección de un proyecto de equipo y para sincronizar los proyectos de código del proyecto de equipo con la directiva de protección.  
  
 [Compatibilidad de versiones para las directivas de protección de análisis de código](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Explica los problemas de compatibilidad de protección de análisis de código entre versiones de [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)].  
  
 [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Explica cómo se agregan palabras y tokens al diccionario al que se hace referencia en las reglas de nomenclatura de análisis de código.  
  
## Secciones relacionadas  
 [Set and Enforce Quality Gates](../Topic/Set%20and%20Enforce%20Quality%20Gates.md)  
  
 [Mejorar la calidad del código con directivas de protección de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)