---
title: Compatibilidad de versiones para las directivas de protección de análisis de código
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8385e2b36d09f029c4b8625e58cd99ecc06ea226
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649021"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilidad de versiones para las directivas de protección de análisis de código

Si debe evaluar y crear directivas de protección de análisis de código con versiones diferentes de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], debe conocer las diferencias en el modo en que [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] y [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] evaluar las directivas de protección.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilidad de versiones para evaluar directivas de protección

- Cuando se evalúan las directivas de protección de análisis de código en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], se omiten las reglas que existían en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] pero que no existen en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

- Cuando se evalúan las directivas de protección de análisis de código en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], se omiten todas las nuevas reglas que son exclusivas de [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

- Si la Directiva de inserción en el repositorio del análisis de código especifica los ensamblados de reglas, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] omite todas las reglas especificadas por los ensamblados que no reconoce.

- Si la Directiva de inserción en el repositorio del análisis de código especifica los ensamblados de reglas que [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] no reconoce, se muestra un mensaje.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilidad de versiones para la creación de directivas de inserción en el repositorio

- Si ha creado una directiva de protección de análisis de código mediante la versión [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], no puede usar la versión [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] para modificarla. Además, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] no pueden evaluar la Directiva.

- Si ha creado una directiva de protección de análisis de código mediante [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], puede usar [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] para modificarla, y la Directiva también puede ser evaluada por [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Después de modificar la Directiva mediante el uso de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], ya no puede editar la Directiva con [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] puede evaluar las directivas sin problemas con nombres seguros no coincidentes.

- Para crear una directiva de protección de análisis de código con la configuración de reglas que se aplica tanto a [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] como a [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], debe crear la Directiva en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], realizar todos los cambios necesarios y guardar la Directiva. Si los cambios en las reglas solo existen en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], modifique y guarde la Directiva en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

   Después de guardar la Directiva en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], ya no podrá cambiar la configuración de las reglas que solo existen en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)].
