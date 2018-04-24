---
title: 'DA0010: GetHashCode consume muchos recursos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: add91942b6a97bf9da496d1664b2a799a9c50d1c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: GetHashCode consume muchos recursos
|||  
|-|-|  
|Identificador de regla|DA0010|  
|Categoría|Uso de .NET Framework|  
|Métodos de generación de perfiles|Muestreo<br /><br /> Memoria de .NET|  
|Mensaje|Las funciones GetHashCode deben consumir pocos recursos y no asignar ninguna memoria. Reduzca la complejidad de la función de código hash si es posible.|  
|Tipo de mensaje|Advertencia|  
  
## <a name="cause"></a>Motivo  
 Las llamadas al método GetHashCode del tipo constituyen una proporción considerable de los datos de generación de perfiles o el método asigna memoria.  
  
## <a name="rule-description"></a>Descripción de la regla  
 La técnica de hash permite localizar rápidamente un elemento determinado en una colección grande. Dado que las tablas hash pueden ser muy grandes y tienen que admitir velocidades de acceso muy altas, deben ser extremadamente eficaces. Una implicación de este requisito es que los métodos GetHashCode en .NET Framework no deben asignar memoria. La asignación de memoria aumenta la carga en el recolector de elementos no utilizados y expone al método a posibles retrasos si es necesario ejecutar la recopilación de elementos no utilizados como resultado de la solicitud de asignación.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Reduzca la complejidad del método.