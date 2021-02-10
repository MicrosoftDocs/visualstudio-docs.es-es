---
title: 'DA0013: Uso intenso de String.Split o String.Substring | Microsoft Docs'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5d5ec92544809a83825451494b01fd62a0868ee4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916797"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Uso intenso de String.Split o String.Substring

|Elemento|Valor|
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
