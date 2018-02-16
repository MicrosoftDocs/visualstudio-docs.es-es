---
title: "Crear y usar directivas de protección de análisis de código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b7187ef8d3342ad050c66debf939e9c6a6213957
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Crear y usar directivas de inserción en el repositorio del análisis de código
Cuando se usa el Control de versiones de Team Foundation (TFVC), puede crear una directiva de protección de análisis de código para .NET Framework y los proyectos de código (C/C ++) nativo en un proyecto de equipo. Puede usar la directiva de protección de análisis de código para controlar y mejorar la calidad del código que está protegido en la base de código.  
  
 La directiva pasa cuando la compilación local está actualizada y se ha ejecutado el análisis de código en los archivos de origen más recientes. Como mínimo, las reglas de análisis de código que están habilitadas en el proyecto de código deben contener las mismas reglas que las que se definen en la directiva de protección de proyecto de equipo. Las reglas que se han especificado como errores en la configuración del proyecto de equipo también deben especificarse como errores en el proyecto de código  
  
> [!IMPORTANT]
>  No se puede aplicar directivas de protección de análisis de código para proyectos de sitios web. Se pueden aplicar a los proyectos de aplicación web.  
  
 Crear directivas de protección de análisis de código mediante el uso de la configuración de proyecto de equipo de [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]. Directivas de protección se especifican y se aplican en un proyecto de equipo, pero se configuran y ejecutan para proyectos de código individuales en equipos de desarrollo local series de análisis de código. Esta sección describe cómo especificar directivas análisis de código en el repositorio para un proyecto de equipo y cómo implementar directivas de análisis de código personalizado para el código administrado.  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Crear o actualizar directivas de protección de análisis de código estándar](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Explica los pasos que utilizan para establecer y modificar una directiva de análisis de código para un proyecto de equipo.  
  
 [Implementar directivas de protección personalizadas para el código administrado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Explica los pasos que utilizan para crear una regla personalizada establecida para la directiva de protección de un proyecto de equipo y para sincronizar los proyectos de código del proyecto de equipo con la directiva de protección.  
  
 [Compatibilidad de versiones para las directivas de protección de análisis de código](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Explica los problemas de compatibilidad en el repositorio de análisis de código entre las versiones de [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)].  
  
 [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Explica cómo agregar palabras y tokens al diccionario al que se hace referencia en las reglas de nomenclatura de análisis de código.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Mejorar la calidad del código con directivas de protección del proyecto de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)