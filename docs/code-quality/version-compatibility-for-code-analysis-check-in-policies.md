---
title: Compatibilidad de versiones para las directivas de protección de análisis de código
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fc164dea10a74bbff725ee153f298c820f1c203
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825195"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilidad de versiones para las directivas de protección de análisis de código

Si se debe evaluar y crear con versiones diferentes de las directivas de protección de análisis de código [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], debe conocer las diferencias en cómo [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] y [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] evaluar las directivas de protección.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilidad de versiones de evaluación de directivas de protección

- Cuando se evalúan las directivas de protección de análisis de código en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], todas las reglas que existieron en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] pero no existen en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] se omiten.

- Cuando se evalúan las directivas de protección de análisis de código en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], todas las nuevas reglas que son exclusivas [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] se omiten.

- Si la directiva de protección de análisis de código especifica los ensamblados de reglas, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] omite todas las reglas que se especifican los ensamblados que no reconoce.

- Si la directiva de protección de análisis de código especifica los ensamblados de reglas que [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] no reconoce, se muestra un mensaje.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilidad de versiones para la creación de directivas de protección

- Si crea una directiva de protección de análisis de código mediante el uso de la [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] versión de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], no puede usar el [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] versión de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] para modificarlo. Y además, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] no se puede evaluar la directiva.

- Si crea una directiva de protección de análisis de código mediante el uso de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], puede usar [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] modificar la base de datos y la directiva también se puede evaluar mediante [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Después de modificar la directiva mediante el uso de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], ya no se puede editar la directiva mediante el uso de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] puede evaluar las directivas sin problemas con nombres seguros no coincidentes.

- Para crear una directiva de protección de análisis de código con la configuración de las reglas que se aplica a ambos [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] y [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], debe crear la directiva en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], realizar todos los cambios necesarios y guardar la directiva. Si los cambios en las reglas solo existen en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], modifique y guarde la directiva en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

   Después de guardar la directiva en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], ya no puede cambiar la configuración de reglas que existen en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] solo.