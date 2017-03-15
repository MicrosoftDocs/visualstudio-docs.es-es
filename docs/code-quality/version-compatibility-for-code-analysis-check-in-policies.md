---
title: "Compatibilidad de versiones para las directivas de protecci&#243;n de an&#225;lisis de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "directivas de protección, compatibilidad de versiones para el análisis de código"
  - "compatibilidad de versiones, directiva de protección de los análisis de código"
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# Compatibilidad de versiones para las directivas de protecci&#243;n de an&#225;lisis de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si debe evaluar y crear directivas de protección de análisis de código con versiones diferentes de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], debe conocer las diferencias existentes en el modo en que [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] y [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] evalúan las directivas de protección.  
  
## Compatibilidad de versiones para la evaluación de directivas de protección  
  
-   Cuando se evalúan las directivas de protección de análisis del código en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], se omiten todas las reglas que existen en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] pero no existen en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].  
  
-   Cuando se evalúan las directivas de protección de análisis del código en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], se omiten todas las nuevas reglas que son exclusivas de [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].  
  
-   Si la directiva de protección de análisis del código especifica ensamblados de reglas, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] omite todas las reglas especificadas por los ensamblados que no reconoce.  
  
-   Si la directiva de protección de análisis del código especifica ensamblados de reglas que [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] no reconoce, se muestra un mensaje.  
  
## Compatibilidad de versiones para la creación de directivas de protección  
  
-   Si ha creado una directiva de protección de análisis de código con la versión [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], no puede usar la versión [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] para modificarla.  Además, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] tampoco podrá evaluar la directiva.  
  
-   Si ha creado una directiva de protección de análisis de código con [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], puede usar [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] para modificarla y también puede evaluarla con [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].  Después de modificar la directiva mediante [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], puede no podrá modificarla con [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)].  [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] puede evaluar las directivas sin problemas con nombres seguros no coincidentes.  
  
-   Para crear una directiva de protección de análisis del código con valores de regla para [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] y [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], debe crear la directiva en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], realizar todos los cambios necesarios y guardar la directiva.  Si sólo hay cambios en las reglas en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], modifique y guarde la directiva en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].  
  
     Cuando haya guardado la directiva en [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], ya no podrá cambiar los valores de las reglas que sólo existen en [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)].