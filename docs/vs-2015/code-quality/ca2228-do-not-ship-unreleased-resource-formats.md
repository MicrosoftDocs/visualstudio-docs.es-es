---
title: 'CA2228: No enviar formatos de recursos no lanzados | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: eb5e595062ca39ba644499012981c78d7a986ced
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917545"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: No enviar formatos de recursos no lanzados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|Identificador de comprobación|CA2228|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Se generó un archivo de recursos utilizando una versión de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que no se admite actualmente.

## <a name="rule-description"></a>Descripción de la regla
 Archivos de recursos que se compilaron con versiones preliminares de los [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] no podrían utilizar las versiones compatibles de .NET Framework.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, genere el recurso utilizando una versión compatible de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.



