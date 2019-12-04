---
title: Información general acerca de la generación de perfiles de Active Script | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3b85410af965fdb9fe4785efe2cf12051e19436e
ms.sourcegitcommit: af9bbf9116a63c0631ff2f4f3a878564aa63cd8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2019
ms.locfileid: "74797354"
---
# <a name="active-script-profiling-overview"></a>Información general acerca de la generación de perfiles de Active Script
[Active Script Profiler (Interfaces)](../winscript/reference/active-script-profiler-interfaces.md) permite generar perfiles de un motor de scripting. La generación de perfiles de Active Script consta de las partes siguientes:  
  
- Motor de lenguaje  
  
- administrador de flujos de trabajo  
  
- Profiler  
  
## <a name="language-engine"></a>Motor de lenguaje  
 El motor de lenguaje ejecuta el script. Proporciona diversos métodos que permiten generar el perfil del código de script a medida que se ejecuta. Cuando se habilita la generación de perfiles, el motor de lenguaje toma como argumento el identificador de clase (CLSID) del objeto COM del generador de perfiles. Crea una instancia del objeto COM del generador de perfiles y, después, llama al generador de perfiles cuando se producen varios eventos.  
  
 El motor de lenguaje implementa [IActiveScriptProfilerControl (Interfaz)](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
> El entorno de ejecución del lenguaje [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] verifica la variable de entorno JS_PROFILER en creación para determinar si se debe habilitar la generación de perfiles. Si esta variable se establece en el CLSID del generador de perfiles, el entorno de ejecución del lenguaje crea una instancia del objeto COM del generador de perfiles mediante el valor de la variable para determinar qué generador de perfiles se debe crear.  
  
## <a name="host"></a>administrador de flujos de trabajo  
 El host crea el motor de lenguaje y le proporciona los scripts que se deben ejecutar. Un host inteligente también proporciona al documento el contexto que un depurador o un generador de perfiles puede utilizar para ofrecerle mejor información cuando esté depurando o generando perfiles.  
  
## <a name="profiler"></a>Profiler  
 El generador de perfiles recibe las llamadas del motor del lenguaje cuando se producen varios eventos. El generador de perfiles se debe registrar como un objeto COM y debe implementar la [interfaz iactivescriptprofilercallback (](../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
## <a name="see-also"></a>Vea también  
 [Active Script Profiler (Interfaces)](../winscript/reference/active-script-profiler-interfaces.md)