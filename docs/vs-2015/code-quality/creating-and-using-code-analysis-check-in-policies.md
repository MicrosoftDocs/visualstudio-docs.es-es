---
title: Crear y usar directivas de protección de análisis de código | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2aef2183cde96bfb5faa1bb62fa341f901dd7018
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987646"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Crear y usar directivas de inserción en el repositorio del análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se usa el Control de versiones de Team Foundation (TFVC), puede crear una directiva de protección de análisis de código para .NET Framework y los proyectos de código (C o C++) nativos en un proyecto de equipo. Puede usar la directiva de protección de análisis de código para controlar y mejorar la calidad del código que está protegido en la base de código.  
  
 La directiva se supera cuando la compilación local está actualizada y se ha ejecutado el análisis de código en los archivos de código fuente más recientes. Como mínimo, las reglas de análisis de código que están habilitadas en el proyecto de código deben contener las mismas reglas que las que se definen en la directiva de comprobación de proyecto de equipo. Las reglas que se han especificado como errores en la configuración del proyecto de equipo también deben especificarse como errores en el proyecto de código  
  
> [!IMPORTANT]
>  No se puede aplicar directivas de protección de análisis de código para proyectos de sitio web. Se pueden aplicar a los proyectos de aplicación web.  
  
 Crear directivas de protección de análisis de código mediante el uso de la configuración del proyecto de equipo de [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Las directivas de protección se especifican y aplican en un proyecto de equipo, pero las ejecuciones de análisis de código se configuran y ejecutar proyectos de código individuales en equipos de desarrollo local. En esta sección se describe cómo especificar directivas análisis de código en el repositorio para un proyecto de equipo y cómo implementar directivas de análisis de código personalizado para el código administrado.  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Crear o actualizar directivas de protección de análisis de código estándar](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Explica los pasos que utilizan para establecer y modificar una directiva de análisis de código para un proyecto de equipo.  
  
 [Implementar directivas de inserción en el repositorio personalizadas para el código administrado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Explica los pasos que usan para crear una regla personalizada establecida para la directiva de protección de un proyecto de equipo y para sincronizar los proyectos de código del proyecto de equipo con la directiva de protección.  
  
 [Compatibilidad de versiones para las directivas de protección de análisis de código](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Explica los problemas de compatibilidad de protección de análisis de código entre las versiones de [!INCLUDE[vstsLong](../includes/vstslong-md.md)].  
  
 [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Explica cómo agregar palabras y tokens al diccionario al que se hace referencia en las reglas de nomenclatura de análisis de código.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Establecer y aplicar pruebas de calidad](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [Mejorar la calidad del código con directivas de protección del proyecto de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
