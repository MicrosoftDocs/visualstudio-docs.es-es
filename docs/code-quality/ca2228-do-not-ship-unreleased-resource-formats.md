---
title: "CA2228: No enviar formatos de recursos no lanzados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotShipUnreleasedResourceFormats"
  - "CA2228"
helpviewer_keywords: 
  - "CA2228"
  - "DoNotShipUnreleasedResourceFormats"
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2228: No enviar formatos de recursos no lanzados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotShipUnreleasedResourceFormats|  
|Identificador de comprobación|CA2228|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Se compiló un archivo de recursos utilizando una versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que no se admite actualmente.  
  
## Descripción de la regla  
 Las versiones compatibles con .NET Framework no podrían utilizar los archivos de recursos compilados utilizando versiones preliminares de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, compile el recurso utilizando una versión compatible de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.