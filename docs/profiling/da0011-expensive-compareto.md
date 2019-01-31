---
title: 'DA0011: CompareTo que consume muchos recursos | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: 83708fa0e58381f50d1637e5f03255fc12376a7a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942443"
---
# <a name="da0011-expensive-compareto"></a>DA0011: CompareTo que consume muchos recursos

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