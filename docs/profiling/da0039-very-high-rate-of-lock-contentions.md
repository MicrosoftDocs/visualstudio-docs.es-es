---
title: "DA0039: Tasa muy alta de contenciones de bloqueo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.39"
  - "vs.performance.DA0039"
  - "vs.performance.rules.DA0039"
ms.assetid: 5a9fc57d-9097-413b-af0c-8726b1a57048
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DA0039: Tasa muy alta de contenciones de bloqueo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0039|  
|Categoría|Uso de .NET Framework|  
|Métodos de generación de perfiles|Muestreo<br /><br /> Instrumentación<br /><br /> Memoria de .NET|  
|Mensaje|Hay una frecuencia muy alta de contenciones de bloqueo de .NET.  Investigue la razón de esta contención de bloqueo ejecutando un perfil de simultaneidad.|  
|Tipo de regla|Advertencia|  
  
 Cuando genere perfiles usando métodos de muestreo, memoria de .NET o contención de recursos, debe recopilar al menos 25 muestras para desencadenar esta regla.  
  
## Motivo  
 Los datos de rendimiento del sistema recopilados con los datos de generación de perfiles indican que se produjo una tasa excesivamente alta de contenciones de bloqueo durante la ejecución de la aplicación.  Puede volver a generar los perfiles mediante el método de generación de perfiles de simultaneidad para detectar la causa de la contención.  
  
## Descripción de la regla  
 Los bloqueos se utilizan para proteger secciones críticas de código que deben ser ejecutadas consecutivamente por un subproceso cada vez en una aplicación multiproceso.  Microsoft .NET Common Language Run\-time \(CLR\) proporciona un conjunto completo de primitivas de sincronización y bloqueo.  Por ejemplo, el lenguaje C\# admite una instrucción lock \(SyncLock en Visual Basic\).  Una aplicación administrada puede llamar a los métodos Monitor.Exit y Monitor.Enter del espacio de nombres System.Threading para adquirir y liberar un bloqueo directamente.  .NET Framework admite primitivas de sincronización y bloqueo adicionales, incluidas clases compatibles con Mutex, ReaderWriterLock y Semaphore.  Para obtener más información, vea [Información general de sincronización Malla](http://go.microsoft.com/fwlink/?LinkId=177867) en la guía del desarrollador de.NET Framework en el sitio web de MSDN.  Las clases de .NET Framework están superpuestas a los servicios de sincronización de nivel inferior integrados en el sistema operativo Windows.  Estos incluyen objetos de sección críticos y muchas funciones de espera y de señalización de eventos distintas.  Para obtener más información, vea [Sincronización](http://go.microsoft.com/fwlink/?LinkId=177869) la sección de Win32 y COM development en MSDN Library  
  
 Debajo de las clases de .NET Framework y los objetos nativos de Windows que se utilizan para la sincronización y el bloqueo hay ubicaciones de memoria compartidas que se deben cambiar mediante operaciones entrelazadas.  Las operaciones entrelazadas utilizan instrucciones específicas del hardware que funcionan en ubicaciones de memoria compartidas para cambiar su estado mediante operaciones atómicas.  Está garantizado que las operaciones atómicas son coherentes en todos los procesadores del equipo.  Los bloqueos y WaitHandles son objetos .NET que utilizan de forma automática operaciones entrelazadas al establecerse o restablecerse.  Puede haber otras estructuras de datos de memoria compartida en su aplicación que también exijan que utilice operaciones entrelazadas para actualizarse de una manera segura para subprocesos.  Para obtener más información, vea [Operaciones entrelazadas](http://go.microsoft.com/fwlink/?LinkId=177870) en la sección de .NET Framework de MSND library  
  
 La sincronización y el bloqueo son mecanismos que se emplean para garantizar que las aplicaciones multiproceso se ejecutan correctamente.  Cada subproceso de una aplicación multiproceso es una unidad de ejecución independiente programada de forma independiente por el sistema operativo.  Se produce una contención de bloqueo siempre que un subproceso que está intentando adquirir un bloqueo se retrasa porque otro subproceso está conteniendo el bloqueo.  
  
 Los bloqueos suelen estar anidados.  La anidación se produce cuando un subproceso que ejecuta una sección crítica realiza una función que a continuación exige otro bloqueo.  Cierta cantidad de anidamiento de bloqueo es inevitable.  Su sección crítica puede llamar a un método de .NET Framework que confíe en los bloqueos para asegurarse de que es seguro para subprocesos.  Una llamada de alguna sección crítica de su aplicación a un método de Framework que también bloquee mediante un controlador de bloqueo diferente hace que los bloqueos se aniden.  Las condiciones de bloqueo anidadas pueden dar lugar a problemas de rendimiento muy difíciles de desentrañar y corregir.  
  
 Esta regla se desencadena cuando las mediciones tomadas durante una generación de perfiles indican que hay una cantidad excesivamente alta de contención de bloqueo.  Las contenciones de bloqueo retrasan la ejecución de los subprocesos que están esperando al bloqueo.  Incluso se deberían investigar las cantidades bastante pequeñas de contención de bloqueo en pruebas unitarias o en pruebas de carga que se ejecuten en hardware de gama baja.  
  
> [!NOTE]
>  Cuando la tasa de contenciones del bloqueo indicada en los datos de generación de perfiles es elevada aunque no excesiva, se genera el mensaje informativo [DA0038: Tasa alta de contenciones de bloqueo](../profiling/da0038-high-rate-of-lock-contentions.md) en lugar de este mensaje de advertencia.  
  
## Cómo investigar una advertencia  
 Haga doble clic en el mensaje para navegar a la vista [Marcas](../profiling/marks-view.md) de los datos de generación de perfiles.  Busque la columna **LocksAndThreads de .NET CLR\\Tasa de contención por segundo**.  Determine si hay fases concretas de la ejecución de programas en las que la contención de bloqueo sea mayor que en otras.  
  
 Esta regla solo se desencadena cuando no está utilizando el método de generación de perfiles de simultaneidad.  El método de generación de perfiles de simultaneidad es la mejor herramienta para diagnosticar problemas de rendimiento relacionados con la contención de bloqueo en su aplicación.  Recopile datos de generación de perfiles de simultaneidad para entender el comportamiento de bloqueo de su aplicación.  Esto incluye entender qué bloqueos están muy contenidos, cuánto se retrasa el tiempo de ejecución de subprocesos a la espera de los bloqueos contenidos y qué código concreto hay implicado.  La generación de perfiles de simultaneidad recopila datos en todas las contenciones de bloqueo, incluido el comportamiento de bloqueo de funciones nativas de Windows, clases de .NET Framework y cualquier otra biblioteca de otro fabricante a la que haga referencia su aplicación.  Para obtener información sobre la generación de perfiles de simultaneidad del IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vea [Recopilar datos de simultaneidad de subprocesos y procesos](../profiling/collecting-thread-and-process-concurrency-data.md).  Para obtener vínculos a información sobre la generación de perfiles de simultaneidad de la línea de comandos, vea la sección **Using the Concurrency Method to Collect Resource Contention and Thread Activity Data** de [Usar los métodos de generación de perfiles desde la línea de comandos](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).