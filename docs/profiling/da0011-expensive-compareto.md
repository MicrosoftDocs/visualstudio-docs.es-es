---
title: 'DA0011: CompareTo consume muchos recursos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0eb4566fd4c8a513b1492cecffc16cb94a1fd83
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779433"
---
# <a name="da0011-expensive-compareto"></a>DA0011: CompareTo consume muchos recursos

|||
|-|-|
|Identificador de regla|DA0011|
|Categoría|Uso de .NET Framework|
|Métodos de generación de perfiles|Muestreo<br /><br /> Memoria de .NET|
|Mensaje|Las funciones CompareTo deben consumir pocos recursos y no asignar ninguna memoria. Reduzca la complejidad de la función CompareTo si es posible.|
|Tipo de regla|Advertencia|

## <a name="cause"></a>Motivo
 El método CompareTo del tipo consume muchos recursos o asigna memoria.

## <a name="rule-description"></a>Descripción de la regla
 Los métodos CompareTo deben ser eficaces y no deben asignar memoria.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Reduzca la complejidad del método CompareTo.
