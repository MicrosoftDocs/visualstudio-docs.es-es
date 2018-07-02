---
title: 'DA0013: Uso alto de String.Split o String.Substring | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c218dd9a7ee3266de2cf9e07933ed69aa23e73e7
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749887"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Uso alto de String.Split o String.Substring
|||  
|-|-|  
|Identificador de regla|DA0013|  
|Categoría|Guía de uso de .NET Framework|  
|Métodos de generación de perfiles|Muestreo|  
|Mensaje|Considere reducir el uso de las funciones String.Split y String.Substring.|  
|Tipo de regla|Advertencia|  
  
## <a name="cause"></a>Motivo  
 Las llamadas a los métodos System.String.Split o System.String.Substring son una parte significativa de los datos de generación de perfiles. Considere la posibilidad de usar System.String.IndexOf o System.String.IndexOfAny si va a comprobar la existencia de una subcadena en una cadena.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El método Split funciona en un objeto String y devuelve una nueva matriz de cadenas que contiene las subcadenas del original. La función asigna memoria para el objeto de matriz devuelto y asigna un nuevo objeto String para cada elemento de matriz que encuentra. De forma similar, el método Substr opera en un objeto String y devuelve una nueva cadena que es equivalente a la subcadena solicitada.  
  
 Si administrar asignaciones de memoria es fundamental en su aplicación, considere la posibilidad de utilizar alternativas a los métodos String.Split y String.Substr. Por ejemplo, puede usar el método IndexOf o IndexOfAny para localizar una subcadena concreta dentro de una cadena de caracteres sin crear una nueva instancia de la clase String.  
  
## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia  
 Haga doble clic en el mensaje en la ventana **Lista de errores** para navegar a la vista [Detalles de la función](../profiling/function-details-view.md) de los datos del perfil de muestreo. Examine las funciones de llamada para encontrar las secciones del programa que hacen un uso más frecuente de los métodos System.String.Split o System.String.Substr. Si es posible, use el método IndexOf o IndexOfAny para localizar una subcadena concreta dentro de una cadena de caracteres sin crear una nueva instancia de la clase String.