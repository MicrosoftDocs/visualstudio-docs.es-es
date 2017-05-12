---
title: "Informaci&#243;n general acerca de la generaci&#243;n de perfiles de Active Script | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Generación de perfiles de Active Script"
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Informaci&#243;n general acerca de la generaci&#243;n de perfiles de Active Script
[Active Script Profiler \(Interfaces\)](../winscript/reference/active-script-profiler-interfaces.md) habilita la generación de perfiles de un motor de script.  La generación de perfiles activo de script consta de las siguientes partes:  
  
-   Motor de lenguaje  
  
-   Host  
  
-   Generador  
  
## Motor de lenguaje  
 El motor de lenguaje ejecuta el script.  Proporciona métodos que permiten generar perfiles de script mientras se ejecuta.  Cuando se habilita la generación de perfiles, el motor de lenguaje toma el identificador de clase \(CLSID\) del objeto COM del generador de perfiles como argumento.  Crea una instancia del objeto COM del generador de perfiles y después llamadas en el generador de perfiles a los distintos eventos.  
  
 El motor de lenguaje implementa [IActiveScriptProfilerControl \(Interfaz\)](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
>  El tiempo de ejecución del lenguaje de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] comprueba la variable de entorno JS\_PROFILER en creación para determinar si la generación de perfiles esté habilitado.  Si esta variable se establece en el CLSID del generador de perfiles, el tiempo de ejecución de lenguaje crea una instancia del objeto COM del generador de perfiles, utilizando el valor de la variable para determinar qué generador a crear.  
  
## Host  
 El host crea el motor del lenguaje y proporciona el motor de lenguaje con scripts que se ejecutarán.  Un host inteligente también proporciona el contexto del documento que se puede utilizar por un depurador o un generador de perfiles para proporcionar una mejor información cuando se depura o de generación de perfiles.  
  
## Generador  
 El generador de perfiles recibe las llamadas del motor de lenguaje cuando los distintos eventos.  El generador de perfiles se debe registrar como un objeto COM y debe implementar la interfaz de [IActiveScriptProfilerCallback \(Interfaz\)](../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
## Vea también  
 [Active Script Profiler \(Interfaces\)](../winscript/reference/active-script-profiler-interfaces.md)