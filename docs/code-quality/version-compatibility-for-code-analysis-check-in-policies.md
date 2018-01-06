---
title: "Compatibilidad de versiones de directivas de protección de análisis de código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 323024cdb420d48c40b7a676bc4e698af7622b67
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilidad de versiones para las directivas de inserción en el repositorio de análisis de código
Si debe evaluar y crear con versiones diferentes de las directivas de protección de análisis de código [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], debe conocer las diferencias en cómo [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] y [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] evaluar las directivas de protección.  
  
## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilidad de versiones de evaluación de directivas de protección  
  
-   Cuando se evalúan las directivas de protección de análisis de código en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], todas las reglas que existían en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] pero no existen en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] se omiten.  
  
-   Cuando se evalúan las directivas de protección de análisis de código en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], todas las nuevas reglas que son exclusivas de [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] se omiten.  
  
-   Si la directiva de protección de análisis de código especifica ensamblados de reglas, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] omite todas las reglas especificadas por los ensamblados que no reconoce.  
  
-   Si la directiva de protección de análisis de código especifica ensamblados de reglas que [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] no reconoce, se muestra un mensaje.  
  
## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilidad de versiones para la creación de directivas de protección  
  
-   Si crea una directiva de protección de análisis de código mediante el uso de la [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] versión de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], no puede usar el [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] versión de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] para modificarlo. Además, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] no se puede evaluar la directiva.  
  
-   Si crea una directiva de protección de análisis de código mediante el uso de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], puede usar [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] modificar la base de datos y la directiva también se puede evaluar [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Después de modificar la directiva mediante el uso de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], ya no se puede modificar la directiva mediante [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]puede evaluar las directivas sin problemas con nombres seguros no coincidentes.  
  
-   Para crear una directiva de protección de análisis de código con la configuración de reglas que se aplica a ambos [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] y [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], debe crear la directiva en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], realizar todos los cambios necesarios y guardar la directiva. Si los cambios realizados en las reglas solo existan en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], modificar y guardar la directiva en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].  
  
     Después de guardar la directiva de [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], ya no se puede cambiar la configuración para las reglas que existen en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] solo.