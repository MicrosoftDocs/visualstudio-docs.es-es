---
title: 'DA0011: CompareTo consume muchos recursos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0726ef4eb93d3e962e5fa39fe9cc7acbdbfbe8ca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210449"
---
# <a name="da0011-expensive-compareto"></a>DA0011: CompareTo consume muchos recursos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio 2017, consulte [DA0011: CompareTo consume muchos recursos](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto) en docs.microsoft.com.  
  
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

