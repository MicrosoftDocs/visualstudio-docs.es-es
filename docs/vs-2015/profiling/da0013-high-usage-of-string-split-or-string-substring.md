---
title: 'DA0013: Uso alto de String.Split o String.Substring | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6ff05e7e8cc74eacb00b5ec8ff42bd48faaa12c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159196"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Uso intenso de String.Split o String.Substring
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identificador de regla | DA0013 |  
| Categoría |. Instrucciones de uso de .NET Framework |  
| Métodos de generación de perfiles | Muestreo |  
| Mensaje | Considere la posibilidad de reducir el uso de las funciones String. Split y String. substring. |  
| Tipo de regla | ADVERTENCIA |  
  
## <a name="cause"></a>Motivo  
 Las llamadas a los métodos System.String.Split o System.String.Substring son una parte significativa de los datos de generación de perfiles. Considere la posibilidad de utilizar System.String.IndexOf o System.String.IndexOfAny si va a probar la existencia de una subcadena en una cadena.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El método Split funciona en un objeto String y devuelve una nueva matriz de cadenas que contiene las subcadenas del original. La función asigna memoria para el objeto de matriz devuelto y asigna un nuevo objeto String para cada elemento de matriz que encuentra. De forma similar, el método Substr opera en un objeto String y devuelve una nueva cadena que es equivalente a la subcadena que se solicitó.  
  
 Si administrar asignaciones de memoria es fundamental en su aplicación, considere la posibilidad de utilizar alternativas a los métodos String.Split y String.Substr. Por ejemplo, puede utilizar el método IndexOf o IndexOfAny para localizar una subcadena concreta dentro de una cadena de caracteres sin crear una nueva instancia de la clase String.  
  
## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia  
 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a la vista [Detalles de la función](../profiling/function-details-view.md) de los datos del perfil de muestreo. Examine las funciones de llamada para encontrar las secciones del programa que hacen un uso más frecuente de los métodos System.String.Split o System.String.Substr. Si es posible, utilice el método IndexOf o IndexOfAny para localizar una subcadena concreta dentro de una cadena de caracteres sin crear una nueva instancia de la clase String.
