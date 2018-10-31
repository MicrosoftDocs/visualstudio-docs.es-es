---
title: 'CA2228: No enviar formatos de recursos no lanzados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 71667a9d00dd1935e8eaeb281c5f0c6834208702
ms.sourcegitcommit: 401be39a42ffe007593528b5bba62583ca9fcafd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "50244403"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: No enviar formatos de recursos no lanzados

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|Identificador de comprobación|CA2228|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un archivo de recursos se creó con una versión de .NET Framework que no se admite actualmente.

## <a name="rule-description"></a>Descripción de la regla
 Archivos de recursos que se compilaron con versiones preliminares de .NET Framework no podrían utilizables las versiones compatibles de .NET Framework.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, genere el recurso utilizando una versión compatible de .NET Framework.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.
