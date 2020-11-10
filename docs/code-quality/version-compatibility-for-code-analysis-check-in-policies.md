---
title: Compatibilidad de versiones para las directivas de protección de análisis de código
ms.date: 11/04/2016
description: Obtenga información sobre cómo Team System 2008 Team Foundation Server y Team Foundation Server 2010 evalúan las directivas de protección de Visual Studio de manera diferente.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a681f510da270bc22ae4bc983103f9a5735a127
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436880"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilidad de versiones para las directivas de protección de análisis de código

Si debe evaluar y crear directivas de protección de análisis de código con diferentes versiones de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , debe conocer las diferencias en cómo [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] y [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] evaluar las directivas de protección.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilidad de versiones para evaluar directivas de Check-In

- Cuando se evalúan las directivas de protección de análisis de código en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , se omiten las reglas que existían en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] pero que no existen en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] .

- Cuando se evalúan las directivas de protección de análisis de código en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] se omiten todas las nuevas reglas que son exclusivas de.

- Si la Directiva de inserción en el repositorio del análisis de código especifica los ensamblados de reglas, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] omite todas las reglas especificadas por los ensamblados que no reconoce.

- Si la Directiva de inserción en el repositorio del análisis de código especifica los ensamblados de reglas que [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] no reconoce, se muestra un mensaje.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilidad de versiones para la creación de directivas de Check-In

- Si ha creado una directiva de protección de análisis de código mediante la [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] versión de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , no puede utilizar la [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] versión de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] para modificarla. Además, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] no puede evaluar la Directiva.

- Si ha creado una directiva de protección de análisis de código con [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , puede usar [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] para modificarla, y también puede evaluar la directiva [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] . Después de modificar la Directiva con [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , ya no se puede editar la Directiva mediante [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] . [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] puede evaluar las directivas sin problemas con nombres seguros no coincidentes.

- Para crear una directiva de protección de análisis de código con la configuración de reglas que se aplica tanto a [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] como a [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , debe crear la Directiva en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , realizar todos los cambios necesarios y guardar la Directiva. Si los cambios en las reglas solo existen en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , modifique y guarde la Directiva en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] .

   Después de guardar la Directiva en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , ya no podrá cambiar la configuración de las reglas que solo existen en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] .
