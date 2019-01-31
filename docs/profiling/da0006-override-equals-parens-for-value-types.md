---
title: 'DA0006: Reemplazar Equals() para tipos de valor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e87fe52e1bdf3fda37f9eda964364e7b5cc13dec
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942469"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Reemplazar Equals() para tipos de valor

|||  
|-|-|  
|Identificador de regla|DA0006|  
|Categoría|Uso de .NET Framework|  
|Métodos de generación de perfiles|Muestreo|  
|Mensaje|Reemplaza Equals y el operador de igualdad en los tipos de valores.|  
|Tipo de mensaje|Advertencia|  

## <a name="cause"></a>Motivo  
 Las llamadas al método Equals o los operadores de igualdad de un tipo de valor público constituyen una proporción considerable de los datos de generación de perfiles. Considere la posibilidad de implementar un método más eficaz.  

## <a name="rule-description"></a>Descripción de la regla  
 Para los tipos de valor, la implementación heredada de Equals utiliza la biblioteca <xref:System.Reflection> y compara el contenido de todos los campos del tipo. Mediante el cálculo, la reflexión es cara y no es necesario comparar cada campo para comprobar si hay igualdad. Si espera que los usuarios comparen u ordenen instancias, o las utilicen como claves de tabla hash, el tipo de valor debe implementar Equals. Si el lenguaje de programación admite la sobrecarga de operadores, también debe proporcionar una implementación de los operadores de igualdad y desigualdad.  

 Para obtener más información sobre cómo reemplazar Equals y los operadores de igualdad, consulte [Instrucciones para implementar Equals y el operador de igualdad (==)](http://go.microsoft.com/fwlink/?LinkId=177818).  

## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia  
 Para obtener un ejemplo de la implementación de Equals y los operadores de igualdad, vea la regla de análisis de código [CA1815: Invalidar Equals y el operador Equals en los tipos de valores](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)