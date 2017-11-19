---
title: 'CA2228: No enviar formatos de recursos no lanzados | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 959d88751ff250e54f6a3f89f0b4b0554add96d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: No enviar formatos de recursos no lanzados
|||  
|-|-|  
|TypeName|DoNotShipUnreleasedResourceFormats|  
|Identificador de comprobación|CA2228|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Se generó un archivo de recursos utilizando una versión de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que no se admite actualmente.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Archivos de recursos que se compilaron con versiones preliminares de las [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] podría no ser capaces de usar las versiones compatibles de .NET Framework.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, genere el recurso utilizando una versión compatible de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.