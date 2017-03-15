---
title: "Valores de datos de asignaci&#243;n de memoria y de duraci&#243;n de objetos en las herramientas de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "método de generación de perfiles de memoria de .NET"
  - "herramientas de generación de perfiles, método de memoria .NET"
ms.assetid: a22445b3-39a6-4919-8506-2b5b0ceaf77e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Valores de datos de asignaci&#243;n de memoria y de duraci&#243;n de objetos en las herramientas de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El método de generación de perfiles de *Asignación de memoria .NET* de las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] recopila información sobre el tamaño y el número de objetos creados en una asignación o destruidos en una recolección de elementos no utilizados e información adicional sobre *la llamada de pila* cuando se produjo el evento.  Una *pila de llamadas* es una estructura dinámica que almacena información sobre las funciones que se ejecutan en el procesador.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 El generador de perfiles de memoria interrumpe el procesador del equipo en cada asignación de un objeto de .NET Framework en una aplicación de la que se ha generado el perfil.  Cuando también se recopilan datos de duración de objetos, el generador de perfiles interrumpe el procesador después de cada recolección de elementos no utilizados de .NET Framework.  Los datos se agregan para cada función perfilada y para cada tipo de objeto.  
  
## Datos de asignación  
 Cuando se produce un evento .memory, se incrementan los recuentos y tamaños totales de los objetos de memoria asignados o destruidos.  
  
 Cuando se produce un evento de asignación de .memory, el generador de perfiles incrementa los recuentos de muestra de cada función de la pila de llamadas.  Cuando se recopilan datos, solamente una función de la pila de llamadas está ejecutando actualmente el código de su cuerpo de la función.  Las demás funciones de la pila son elementos primarios en la jerarquía de las llamadas de función que están esperando la vuelta de las funciones a las que llamaron.  
  
-   En el evento de asignación, el generador de perfiles incrementa el recuento de muestras *exclusivas* de la función que está ejecutando actualmente sus instrucciones.  Dado que una muestra exclusiva forma también parte del número de muestras totales \(*inclusivas*\) de la función, también se incrementa el recuento de muestras inclusivas de la función actualmente activa.  
  
-   El generador de perfiles incrementa el recuento de muestras inclusivas del resto de las funciones de la pila de llamadas.  
  
## Datos de duración  
 El recolector de elementos no utilizados de .NET Framework administra la asignación y liberación de la memoria de la aplicación.  Para optimizar el rendimiento del recolector de elementos no utilizados, el montón administrado se divide en tres generaciones: 0, 1 y 2.  El recolector de elementos no utilizados del tiempo de ejecución almacena los nuevos objetos en la generación 0.  Los objetos que sobreviven a las recolecciones se promueven y se almacenan en las generaciones 1 y 2.  
  
 El recolector de elementos no utilizados recupera memoria desasignando una generación completa de objetos.  Para los objetos creados por la aplicación para la que se generan perfiles, la vista Duración del objeto muestra el número y el tamaño de los objetos, así como la generación cuando se recuperan.