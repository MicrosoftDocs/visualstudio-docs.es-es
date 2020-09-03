---
title: Compatibilidad de versiones para directivas de protección de análisis de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 075981569cbee05e90afe17b3afc9558d7bbb270
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609312"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilidad de versiones para las directivas de protección de análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si debe evaluar y crear directivas de protección de análisis de código con diferentes versiones de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , debe conocer las diferencias en cómo [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] y [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] evaluar las directivas de protección.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilidad de versiones para evaluar directivas de protección

- Cuando se evalúan las directivas de protección de análisis de código en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , se omiten las reglas que existían en [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] pero que no existen en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] .

- Cuando se evalúan las directivas de protección de análisis de código en [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] se omiten todas las nuevas reglas que son exclusivas de.

- Si la Directiva de inserción en el repositorio del análisis de código especifica los ensamblados de reglas, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] omite todas las reglas especificadas por los ensamblados que no reconoce.

- Si la Directiva de inserción en el repositorio del análisis de código especifica los ensamblados de reglas que [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] no reconoce, se muestra un mensaje.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilidad de versiones para la creación de directivas de inserción en el repositorio

- Si ha creado una directiva de protección de análisis de código mediante la [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] versión de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , no puede utilizar la [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] versión de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] para modificarla. Además, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] no puede evaluar la Directiva.

- Si ha creado una directiva de protección de análisis de código con [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] en [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , puede usar [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] para modificarla, y también puede evaluar la directiva [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] . Después de modificar la Directiva con [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , ya no se puede editar la Directiva mediante [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] en [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] . [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] puede evaluar las directivas sin problemas con nombres seguros no coincidentes.

- Para crear una directiva de protección de análisis de código con la configuración de reglas que se aplica tanto a [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] como a [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , debe crear la Directiva en [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , realizar todos los cambios necesarios y guardar la Directiva. Si los cambios en las reglas solo existen en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , modifique y guarde la Directiva en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] .

     Después de guardar la Directiva en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , ya no podrá cambiar la configuración de las reglas que solo existen en [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] .
