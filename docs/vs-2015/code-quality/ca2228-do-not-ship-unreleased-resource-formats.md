---
title: 'CA2228: No enviar formatos de recursos no lanzados | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2e49953a95da10653cd29132e003fa36de5b8d4c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142439"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: No enviar formatos de recursos no lanzados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|Identificador de comprobación|CA2228|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Se generó un archivo de recursos utilizando una versión de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que no se admite actualmente.

## <a name="rule-description"></a>Descripción de la regla
 Archivos de recursos que se compilaron con versiones preliminares de los [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] no podrían utilizar las versiones compatibles de .NET Framework.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, genere el recurso utilizando una versión compatible de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.
