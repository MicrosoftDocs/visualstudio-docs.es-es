---
title: Información general acerca de la generación de perfiles de Active Script | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9413e8b6e6db0c81eb1853c24506d20c8d06f3e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571445"
---
# <a name="active-script-profiling-overview"></a>Información general acerca de la generación de perfiles de Active Script
[Active Script Profiler (Interfaces)](../winscript/reference/active-script-profiler-interfaces.md) permite generar perfiles de un motor de scripting. La generación de perfiles de Active Script consta de las partes siguientes:  
  
-   Motor de lenguaje  
  
-   Host  
  
-   generador de perfiles  
  
## <a name="language-engine"></a>Motor de lenguaje  
 El motor de lenguaje ejecuta el script. Proporciona diversos métodos que permiten generar el perfil del código de script a medida que se ejecuta. Cuando se habilita la generación de perfiles, el motor de lenguaje toma como argumento el identificador de clase (CLSID) del objeto COM del generador de perfiles. Crea una instancia del objeto COM del generador de perfiles y, después, llama al generador de perfiles cuando se producen varios eventos.  
  
 El motor de lenguaje implementa [IActiveScriptProfilerControl (Interfaz)](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
>  El entorno de ejecución del lenguaje [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] verifica la variable de entorno JS_PROFILER en creación para determinar si se debe habilitar la generación de perfiles. Si esta variable se establece en el CLSID del generador de perfiles, el entorno de ejecución del lenguaje crea una instancia del objeto COM del generador de perfiles mediante el valor de la variable para determinar qué generador de perfiles se debe crear.  
  
## <a name="host"></a>Host  
 El host crea el motor de lenguaje y le proporciona los scripts que se deben ejecutar. Un host inteligente también proporciona al documento el contexto que un depurador o un generador de perfiles puede utilizar para ofrecerle mejor información cuando esté depurando o generando perfiles.  
  
## <a name="profiler"></a>generador de perfiles  
 El generador de perfiles recibe las llamadas del motor del lenguaje cuando se producen varios eventos. El generador de perfiles debe registrarse como un objeto COM e implementar la interfaz [IActiveScriptProfilerCallback (Interfaz)](../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
## <a name="see-also"></a>Vea también  
 [Active Script Profiler (Interfaces)](../winscript/reference/active-script-profiler-interfaces.md)