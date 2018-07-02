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
ms.openlocfilehash: a670eb3145f3fd2ab9478dc68e0490cdeda8ac56
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749965"
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
 La técnica de hash permite localizar rápidamente un elemento determinado en una colección grande. Dado que las tablas hash pueden ser grandes y tienen que admitir velocidades de acceso muy altas, deben ser eficaces. Una implicación de este requisito es que los métodos GetHashCode en .NET Framework no deben asignar memoria. La asignación de memoria aumenta la carga en el recolector de elementos no utilizados y expone al método a posibles retrasos si es necesario ejecutar la recopilación de elementos no utilizados como resultado de la solicitud de asignación.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Reduzca la complejidad del método.