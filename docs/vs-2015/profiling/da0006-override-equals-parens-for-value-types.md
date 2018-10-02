---
title: 'DA0006: Reemplazar Equals() para tipos de valor | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4e7535775946c99d6b176f36ca10288a8bc9da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577468"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Reemplazar Equals() para tipos de valor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [DA0006: reemplazar Equals() para tipos de valor](https://docs.microsoft.com/visualstudio/profiling/da0006-override-equals-parens-for-value-types).  
  
Id. de regla | DA0006 |  
| Categoría |. Uso de .NET Framework |  
| Métodos de generación de perfiles | Muestreo |  
| Mensaje | Reemplaza Equals y el operador de igualdad en los tipos de valor. |  
| Tipo de mensaje | Advertencia |  
  
## <a name="cause"></a>Motivo  
 Las llamadas al método Equals o a los operadores de igualdad de un tipo de valor público constituyen una proporción considerable de los datos de generación de perfiles. Considere la posibilidad de implementar un método más eficaz.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Para los tipos de valor, la implementación heredada de Equals utiliza la biblioteca <xref:System.Reflection> y compara el contenido de todos los campos del tipo. Mediante el cálculo, la reflexión es cara y no es necesario comparar cada campo para comprobar si hay igualdad. Si espera que los usuarios comparen u ordenen instancias, o las utilicen como claves de tabla hash, el tipo de valor debe implementar Equals. Si el lenguaje de programación admite la sobrecarga de operadores, también debe proporcionar una implementación de los operadores de igualdad y desigualdad.  
  
 Para obtener más información sobre cómo reemplazar Equals y los operadores de igualdad, consulte [Instrucciones para implementar Equals y el operador de igualdad (==)](http://go.microsoft.com/fwlink/?LinkId=177818).  
  
## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia  
 Para obtener un ejemplo de la implementación de Equals y los operadores de igualdad, consulte la regla de análisis de código [CA1815: Reemplazar Equals y el operador Equals en los tipos de valores](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md).



