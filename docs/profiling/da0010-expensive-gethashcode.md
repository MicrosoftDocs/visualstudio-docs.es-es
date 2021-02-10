---
title: 'DA0010: GetHashCode consume muchos recursos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fc9c1b35a78a8d9453ab35f201a120bc75134768
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916829"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: GetHashCode que consume muchos recursos

|Elemento|Valor|
|-|-|
|Identificador de regla|DA0010|
|Categoría|Uso de .NET Framework|
|Métodos de generación de perfiles|Muestreo<br /><br /> Memoria de .NET|
|Mensaje|Las funciones GetHashCode deben consumir pocos recursos y no asignar ninguna memoria. Reduzca la complejidad de la función de código hash si es posible.|
|Tipo de mensaje|Advertencia|

## <a name="cause"></a>Motivo
 Las llamadas al método GetHashCode del tipo constituyen una proporción considerable de los datos de generación de perfiles o el método asigna memoria.

## <a name="rule-description"></a>Descripción de la regla
 La técnica de hash permite localizar rápidamente un elemento determinado en una colección grande. Dado que las tablas hash pueden ser grandes y tienen que admitir velocidades de acceso muy altas, deben ser eficaces. Una implicación de este requisito es que los métodos GetHashCode en .NET Framework no deben asignar memoria. La asignación de memoria aumenta la carga en el recolector de elementos no utilizados y expone al método a posibles retrasos si es necesario ejecutar la recopilación de elementos no utilizados como resultado de la solicitud de asignación.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Reduzca la complejidad del método.
