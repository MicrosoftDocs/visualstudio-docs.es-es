---
title: Usar métodos de generación de perfiles para recopilar datos de rendimiento desde la línea de comandos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e8dbaf62043897292afbb2805879e0447f3048a
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276707"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Usar métodos de generación de perfiles para recopilar datos de rendimiento desde la línea de comandos
La elección de herramientas de línea de comandos y opciones de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depende de factores como el tipo de aplicación de la que está generando perfiles, el método de generación de perfiles que desea utilizar y si se escribe la aplicación de destino en código nativo o de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 En este tema se organiza los temas de procedimientos de línea de comandos según el método de generación de perfiles que elija.  
  
## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Usar el método de muestreo para recopilar estadísticas de rendimiento  
 El método de muestreo de las herramientas de generación de perfiles recopila datos de rendimiento a intervalos especificados en un proceso de generación de perfiles. Los datos de muestreo pueden proporcionar información sobre los problemas de rendimiento relacionadas con la CPU y pueden ser una buena forma de empezar a explorar el rendimiento de una aplicación.  
  
 Puede iniciar el generador de perfiles y la aplicación al mismo tiempo, o puede adjuntar el generador de perfiles a una instancia en ejecución de una aplicación.  
  
|Tarea|Tipo de aplicación de destino|  
|----------|-----------------------------|  
|**Ejecutar una aplicación**|-   [Aplicaciones independientes](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|  
|**Adjuntar a un proceso en ejecución**|-   [Aplicaciones independientes de .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Aplicaciones independientes nativas](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [Aplicaciones web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET Services](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Servicios nativos](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Usar el método de instrumentación para recopilar datos de tiempo detallados  
 El método de instrumentación de las herramientas de generación de perfiles recopila datos de rendimiento de copias de binarios de aplicación que contienen sondeos de software para registrar información de rendimiento. Los datos de instrumentación se recopilan al comienzo y al final de cada función instrumentada y en cada llamada a otras funciones desde la función instrumentada. El método de instrumentación es útil para detectar problemas de rendimiento con problemas de E/S como el uso de disco.  
  
 El binario instrumentado se crea con la herramienta [VInstr.exe](../profiling/vsinstr.md). Después de inicializar el generador de perfiles, los datos se recopilan automáticamente desde los binarios instrumentados al ejecutar la aplicación de destino.  
  
 **Tipo de aplicación de destino**  
  
-   [Componentes independientes de .NET Framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)  
  
-   [Componentes independientes nativos](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)  
  
-   [Aplicaciones web ASP.NET compiladas estáticamente](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)  
  
-   [Aplicaciones web ASP.NET compiladas dinámicamente](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)  
  
-   [.NET Services](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Servicios nativos](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Usar métodos de memoria de .NET para recopilar datos de asignación de memoria y de duración de objetos  
 El método de memoria de .NET de herramientas de generación de perfiles permite recopilar datos de asignación de memoria de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e información sobre la duración de objetos en el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Puede iniciar la aplicación de destino mediante el generador de perfiles, adjuntar el generador de perfiles a una instancia en ejecución de una aplicación y crear versiones instrumentadas de la aplicación para recopilar información de tiempo detallada junto con los datos de memoria de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
|Tarea|Tipo de aplicación de destino|  
|----------|-----------------------------|  
|**Ejecutar una aplicación**|-   [Aplicaciones de .NET Framework independiente](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|  
|**Adjuntar a un proceso en ejecución**|-   [Aplicaciones independientes de .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [Aplicaciones web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET Services](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentar módulos**|-   [Componentes independientes de .NET Framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Aplicaciones web ASP.NET compiladas estáticamente](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [Aplicaciones web ASP.NET compiladas dinámicamente](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [.NET Services](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Usar el método de simultaneidad para recopilar datos de contención de recursos y de actividad de subprocesos  
 El método de simultaneidad de las herramientas de generación de perfiles permite recopilar la contención de recursos y datos de actividad de procesos y subprocesos de aplicaciones multiproceso.  
  
 Puede iniciar la aplicación mediante el generador de perfiles, o puede adjuntar el generador de perfiles a una instancia en ejecución de una aplicación.  
  
|Tarea|Tipo de aplicación de destino|  
|----------|-----------------------------|  
|**Ejecutar una aplicación**|-   [Aplicación de .NET Framework independiente](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Aplicación nativa independiente](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|  
|**Adjuntar a un proceso en ejecución**|-   [Aplicación independiente de .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Aplicación independiente nativa](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [Aplicación web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET Service](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Servicio nativo](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Agregar datos de interacción de capas a una ejecución de generación de perfiles  
 Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos. Vea [Recopilación de datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>Vea también  
 [Generación de perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)