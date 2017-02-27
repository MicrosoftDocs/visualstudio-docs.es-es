---
title: "DA0502: M&#225;ximo consumo de CPU por parte del proceso que se va a perfilar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DA0502"
  - "vs.performance.DA0502"
  - "vs.performance.502"
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DA0502: M&#225;ximo consumo de CPU por parte del proceso que se va a perfilar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0502|  
|Categoría|Supervisión de recursos|  
|Método de generación de perfiles|Todos|  
|Mensaje|Esta regla es solo informativa.  El contador Process\(\)\\% Processor Time mide el consumo de CPU del proceso del que se está generando el perfil.  El valor indicado es el máximo observado de todos los intervalos de medición.|  
|Tipo de regla|Informativa|  
  
 Cuando genere perfiles usando métodos de muestreo, memoria de .NET o contención de recursos, debe recopilar al menos 10 muestras para desencadenar esta regla.  
  
## Descripción de la regla  
 Este mensaje indica el porcentaje de tiempo máximo que un procesador estuvo ocupado ejecutando instrucciones de la aplicación.  El valor indicado es el valor máximo indicado de todos los intervalos de medida en los que estaba activo el proceso para el que se generan perfiles.  El porcentaje puede ser superior al 100% en un equipo con más de un procesador.  
  
## Cómo usar los datos de la regla  
 Utilice el valor de la regla para comparar el rendimiento de distintas versiones o compilaciones del programa o para entender el rendimiento de la aplicación en otros escenarios de generación de perfiles.