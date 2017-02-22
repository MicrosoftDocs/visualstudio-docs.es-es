---
title: "DA0004: Alto uso del procesador | Microsoft Docs"
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
  - "vs.performance.rules.DAHighProcessorUsage"
  - "vs.performance.rules.DA0004"
  - "vs.performance.DA0004"
  - "vs.performance.4"
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0004: Alto uso del procesador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0004|  
|Categoría|Uso de Herramientas de generación de perfiles|  
|Métodos de generación de perfiles|Instrumentación<br /><br /> Muestreo|  
|Mensaje|El uso del procesador es superior al 75% de forma constante.  Considere el uso del modo de muestreo para aplicaciones enlazadas a la CPU.|  
|Tipo de regla|Información|  
  
 Cuando genere perfiles usando métodos de muestreo, memoria de .NET o contención de recursos, debe recopilar al menos 10 muestras para desencadenar esta regla.  
  
## Motivo  
 La utilización del procesador \(CPU\) fue considerablemente alta a la hora de generar perfiles de datos recopilados mediante el método de instrumentación.  Puede utilizar el método de generación de perfiles mediante muestreo al generar perfiles de una aplicación enlazada con la CPU.  
  
## Descripción de la regla  
 Durante proceso de la generación de perfiles, el procesador \(o procesadores\) estuvieron siempre muy ocupados.  Una alta utilización de la CPU puede indicar una aplicación enlazada con la CPU.  Los perfiles instrumentados normalmente no son la manera más efectiva de investigar escenarios del uso de la CPU.  El muestreo es normalmente más efectivo cuando genera perfiles de aplicaciones que pasan la mayor parte del tiempo ejecutando instrucciones en el procesador.  
  
## Cómo corregir infracciones  
 Considere la generación de perfiles en la aplicación de nuevo mediante el método de muestreo en lugar del método de instrumentación, a menos que requiera un control de tiempos de la función o esté más interesado en entender las operaciones de entrada\/salida que los cuellos de botella que se producen en el procesador.