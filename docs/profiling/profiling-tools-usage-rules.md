---
title: "Reglas de uso de herramientas de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Reglas de uso de herramientas de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las reglas de rendimiento de la categoría Uso de herramientas de generación de perfiles proporciona directrices de uso del generador de perfiles para recopilar datos eficazmente.  
  
|||  
|-|-|  
|[DA0002: Falta VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|La generación de perfiles de línea de comandos podría contener datos incompletos para los binarios de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Esto se podría producir si no se establecen las variables de entorno correctas.|  
|[DA0003: Muchas muestras de kernel](../profiling/da0003-many-kernel-samples.md)|Se registraron muchos ejemplos de generación de perfiles que se produjeron fuera de la ejecución del binario de destino.  Para recopilar datos más precisos, considere el uso del método de instrumentación.|  
|[DA0004: Alto uso del procesador](../profiling/da0004-high-processor-usage.md)|Los datos de la generación de perfiles sugiere que los procesadores no mantuvieron una ocupación coherente durante la misma.  Para recopilar datos más precisos, considere el uso del método de muestreo.|  
|[DA0008: Pocos ejemplos recolectados](../profiling/da0008-few-samples-collected.md)|El número de ejemplos recopilado en la ejecución de la generación de perfiles no fue lo bastante alto como para ser estadísticamente significativo.  Considere generar los perfiles de nuevo y ejecutar la aplicación durante más tiempo.  También puede usar el método de instrumentación para recopilar los datos.|  
|[DA0026: Tiempo de procesamiento excesivo de la CPU de kernel](../Topic/DA0026:%20Excessive%20kernel%20CPU%20time%20processing.md)|Una cantidad significativa del tiempo de la ejecución de la generación de perfiles se produjo en el modo kernel del procesador.  Considere hacer el muestreo utilizando las llamadas al sistema como métrica, en lugar de utilizar el tiempo como métrica.|  
|[DA0029: Versión de CLR incompatible](../profiling/da0029-unsupported-clr-version.md)|El binario generado está utilizando una versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que el generador de perfiles no admite.  Los informes del generador de perfiles no pueden resolver los nombres de símbolos.|  
|[DA0030: Recopilar las medidas de interacción de capas para los proyectos de base de datos](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|Se recopiló un número significativo de llamadas a los métodos en el espacio de nombres <xref:System.Data?displayProperty=fullName>.  Para incluir los datos sobre llamadas a la base de datos, considere recopilar datos de interacción de capas en las ejecuciones del perfil.|