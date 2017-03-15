---
title: "DA0013: Uso alto de String.Split o String.Substring | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DAAvoidStringSubstr"
  - "vs.performance.DA0013"
  - "vs.performance.rules.DA0013"
helpviewer_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DA0013"
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0013: Uso alto de String.Split o String.Substring
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0013|  
|Categoría|Orientación de uso de .NET Framework|  
|Métodos de generación de perfiles|Muestreo|  
|Mensaje|Considere reducir el uso de las funciones String.Split y String.Substring.|  
|Tipo de regla|Advertencia|  
  
## Motivo  
 Las llamadas a los métodos System.String.Substring o System.String.Split constituyen una proporción considerable de los datos de generación de perfiles.  Si está comprobando la existencia de una subcadena en una cadena, puede utilizar System.String.IndexOf o System.String.IndexOfAny.  
  
## Descripción de la regla  
 El método Split funciona en un objeto String y devuelve una nueva matriz de cadenas que contiene las subcadenas del original.  La función asigna memoria para el objeto de matriz devuelto y asigna un nuevo objeto String para cada elemento de matriz que encuentra.  De igual forma, el método Substr funciona en un objeto String y devuelve una nueva cadena que es equivalente a la subcadena que se solicitó.  
  
 Si administrar asignaciones de memoria es fundamental en su aplicación, considere el uso de alternativas a los métodos String.Substr y String.Split.  Por ejemplo, puede usar el método IndexOfAny o IndexOf para buscar una subcadena concreta dentro de una cadena de caracteres sin crear una nueva instancia de la clase String.  
  
## Cómo investigar una advertencia  
 Haga doble clic en el mensaje de la ventana Lista de errores para navegar a la [Vista Detalles de la función](../profiling/function-details-view.md) de los datos de muestreo de perfiles.  Examine las funciones de llamada para encontrar las secciones del programa que usan más frecuentemente los métodos System.String.Split o System.String.Substr.  Si es posible, use el método IndexOfAny o IndexOf para buscar una subcadena concreta dentro de una cadena de caracteres sin crear una nueva instancia de la clase String.