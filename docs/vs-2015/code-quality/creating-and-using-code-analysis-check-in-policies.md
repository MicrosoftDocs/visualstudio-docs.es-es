---
title: Crear y usar directivas de protección de análisis de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8e31ff799edc93d250eeeab57b349873a63ecf14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667714"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Crear y usar directivas de inserción en el repositorio del análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al usar Control de versiones de Team Foundation (TFVC), puede crear una directiva de protección de análisis de código para los proyectos de código .NET Framework y nativo (C/C++) en un proyecto de equipo. Puede usar la Directiva de protección de análisis de código para controlar y mejorar la calidad del código que se protege en la base de código.

 La Directiva pasa cuando la compilación local está actualizada y se ha ejecutado el análisis de código en los archivos de código fuente más recientes. Como mínimo, las reglas de análisis de código que están habilitadas en el proyecto de código deben contener las mismas reglas que las que se definen en la Directiva de protección del proyecto de equipo. Las reglas que se han especificado como errores en la configuración del proyecto de equipo también deben especificarse como errores en el proyecto de código.

> [!IMPORTANT]
> Las directivas de protección de análisis de código no se pueden aplicar a proyectos de sitios Web. Se pueden aplicar a los proyectos de aplicación Web.

 Las directivas de protección de análisis de código se crean mediante la configuración del proyecto de equipo de [!INCLUDE[esprscc](../includes/esprscc-md.md)] . Las directivas de inserción en el repositorio se especifican y se aplican para un proyecto de equipo, pero las ejecuciones de análisis de código se configuran y ejecutan en proyectos de código individuales en equipos de desarrollo locales. En esta sección se describe cómo especificar directivas de protección de análisis de código para un proyecto de equipo y cómo implementar directivas de análisis de código personalizadas para código administrado.

## <a name="in-this-section"></a>En esta sección
 [Cómo: crear o actualizar directivas de protección de análisis de código estándar](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md) Explica los pasos que se usan para establecer y modificar una directiva de análisis de código para un proyecto de equipo.

 [Implementar directivas de protección personalizadas para código administrado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md) Explica los pasos que se usan para crear un conjunto de reglas personalizado para la Directiva de protección de un proyecto de equipo y para sincronizar los proyectos de código del proyecto de equipo con la Directiva de inserción en el repositorio.

 [Compatibilidad de versiones para las directivas de protección de análisis de código](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md) Explica los problemas de compatibilidad de protección de los análisis de código entre las versiones de [!INCLUDE[vstsLong](../includes/vstslong-md.md)] .

 [Cómo: personalizar el Diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md) Explica cómo agregar palabras y tokens al diccionario al que se hace referencia en las reglas de nomenclatura de análisis de código.

## <a name="related-sections"></a>Secciones relacionadas
 [Establecer y aplicar pruebas de calidad](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)

 [Mejorar la calidad del código con directivas de protección del proyecto de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
