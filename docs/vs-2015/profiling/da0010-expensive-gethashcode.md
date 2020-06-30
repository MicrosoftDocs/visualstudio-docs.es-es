---
title: 'DA0010: GetHashCode consume muchos recursos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af234cd130d06c2a76c5ddbc958a67eb064d9128
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547581"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: GetHashCode consume muchos recursos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente sobre Visual Studio, vea [DA0010: GetHashCode percaro](/visualstudio/profiling/da0010-expensive-gethashcode).  

|Elemento|Value|  
|-|-|  
|Identificador de regla|DA0010|  
|Category|Uso de .NET Framework|  
|Métodos de generación de perfiles|Muestreo<br /><br /> Memoria de .NET|  
|Message|Las funciones GetHashCode deben consumir pocos recursos y no asignar ninguna memoria. Reduzca la complejidad de la función de código hash si es posible.|  
|Tipo de mensaje|Advertencia|  
  
## <a name="cause"></a>Causa  
 Las llamadas al método GetHashCode del tipo constituyen una proporción considerable de los datos de generación de perfiles o el método asigna memoria.  
  
## <a name="rule-description"></a>Descripción de la regla  
 La técnica de hash permite localizar rápidamente un elemento determinado en una colección grande. Dado que las tablas hash pueden ser muy grandes y deben admitir altas tasas de acceso, las tablas hash deben ser muy eficaces. Una implicación de este requisito es que los métodos GetHashCode en .NET Framework no deben asignar memoria. La asignación de memoria aumenta la carga en el recolector de elementos no utilizados y expone al método a posibles retrasos si es necesario ejecutar la recopilación de elementos no utilizados como resultado de la solicitud de asignación.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Reduzca la complejidad del método.
