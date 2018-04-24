---
title: 'CA2228: No enviar formatos de recursos no lanzados'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1928cb4626ea5d5af15ecf800a8842d66f3e244d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
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