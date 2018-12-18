---
title: Compatibilidad de versiones de directivas de protección de análisis de código | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 840a12e7f4c0e3853e885a803dea5a92e05a5a27
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261487"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilidad de versiones para las directivas de inserción en el repositorio de análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si se debe evaluar y crear con versiones diferentes de las directivas de protección de análisis de código [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], debe conocer las diferencias en cómo [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] y [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] evaluar las directivas de protección.  
  
## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilidad de versiones de evaluación de directivas de protección  
  
-   Cuando se evalúan las directivas de protección de análisis de código en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], todas las reglas que existieron en [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] pero no existen en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] se omiten.  
  
-   Cuando se evalúan las directivas de protección de análisis de código en [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], todas las nuevas reglas que son exclusivas [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] se omiten.  
  
-   Si la directiva de protección de análisis de código especifica los ensamblados de reglas, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] omite todas las reglas que se especifican los ensamblados que no reconoce.  
  
-   Si la directiva de protección de análisis de código especifica los ensamblados de reglas que [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] no reconoce, se muestra un mensaje.  
  
## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilidad de versiones para la creación de directivas de protección  
  
-   Si crea una directiva de protección de análisis de código mediante el uso de la [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] versión de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], no puede usar el [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] versión de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] para modificarlo. Y además, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] no se puede evaluar la directiva.  
  
-   Si crea una directiva de protección de análisis de código mediante el uso de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] en [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], puede usar [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] modificar la base de datos y la directiva también se puede evaluar mediante [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]. Después de modificar la directiva mediante el uso de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], ya no se puede editar la directiva mediante el uso de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] en [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]. [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] puede evaluar las directivas sin problemas con nombres seguros no coincidentes.  
  
-   Para crear una directiva de protección de análisis de código con la configuración de las reglas que se aplica a ambos [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] y [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], debe crear la directiva en [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], realizar todos los cambios necesarios y guardar la directiva. Si los cambios en las reglas solo existen en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], modifique y guarde la directiva en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)].  
  
     Después de guardar la directiva en [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], ya no puede cambiar la configuración de reglas que existen en [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] solo.



