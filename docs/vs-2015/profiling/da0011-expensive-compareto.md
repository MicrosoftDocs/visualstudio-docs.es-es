---
title: 'DA0011: CompareTo consume muchos recursos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ed433612498a6b7d4b87291311d7fd6efcb0974
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918383"
---
# <a name="da0011-expensive-compareto"></a>DA0011: CompareTo consume muchos recursos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente sobre Visual Studio, vea [DA0011: CompareTo caro](/visualstudio/profiling/da0011-expensive-compareto).  
  
|||  
|-|-|  
|Id. de regla|DA0011|  
|Categoría|Uso de .NET Framework|  
|Métodos de generación de perfiles|Muestreo<br /><br /> Memoria de .NET|  
|Mensaje|Las funciones CompareTo deben consumir pocos recursos y no asignar ninguna memoria. Reduzca la complejidad de la función CompareTo si es posible.|  
|Tipo de regla|advertencia|  
  
## <a name="cause"></a>Motivo  
 El método CompareTo del tipo consume muchos recursos o asigna memoria.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Los métodos CompareTo deben ser eficaces y no deben asignar memoria.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Reduzca la complejidad del método CompareTo.
