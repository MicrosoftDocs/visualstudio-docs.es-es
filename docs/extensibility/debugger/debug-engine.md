---
title: "Motor de depuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motores de depuración"
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Motor de depuraci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un motor de depuración \(DE\) ejecuta el intérprete o el sistema operativo para proporcionar servicios de depuración como control de ejecución, puntos de interrupción, y evaluación de la expresión.  El OF es responsable de supervisar el estado de un programa que se depura.  Para hacer realizar esto, el OF utiliza los métodos están disponibles en tiempo de ejecución compatible, si de CPU o de las API proporcionadas por el tiempo de ejecución.  
  
 Por ejemplo, los mecanismos \(CLR\) de fuentes de Common Language Runtime para controlar un programa en ejecución a través de interfaces de ICorDebugXXX.  Un OF que admite CLR utiliza las interfaces adecuadas de ICorDebugXXX para realizar el seguimiento de un programa de código administrado que se está depurando.  A continuación se comunica cualquier cambio de estado al administrador \(SDM\) de la depuración de sesión, que transmite a tal información [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el IDE.  
  
> [!NOTE]
>  Un motor de depuración tiene como destino un runtime concreto, es decir, el sistema en el que el programa que se ejecuta depurando.  CLR es el tiempo de ejecución para el código administrado, y el runtime de Win32 es para las aplicaciones para Windows nativas.  Si el lenguaje que cree puede el destino uno de estos dos runtime, fuentes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ya los motores necesarios de depuración.  Todo lo que tiene que implementar es evaluador de expresiones.  
  
## Funcionamiento del motor de depuración  
 Los servicios de supervisión se implementan a través de interfaces y pueden producir el paquete de depuración para la transición entre distintos modos operativos.  Para obtener más información, vea [Modos de funcionamiento](../../extensibility/debugger/operational-modes.md).  Normalmente hay sólo un OF implementation el entorno en tiempo de ejecución.  
  
> [!NOTE]
>  Cuando hay OF independiente implementations para Transact\-SQL y [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript y [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] comparten un único OF.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de depuración permisos depurar los motores para ejecutar una de dos maneras: en el mismo proceso que el shell de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], o en el mismo proceso que el programa de destino que se depura.  El último formulario aparece normalmente cuando el proceso que se está depurando es realmente una ejecución del script en un intérprete, y el motor de depuración debe tener conocimientos más el intérprete para controlar el script.  Observe que en este caso, este es realmente un runtime; los motores de depuración son para las implementaciones concretas en tiempo de ejecución.  Además, la implementación de un único OF puede dividirse a través de los límites de procesos y de equipo \(por ejemplo, depuración remota\).  
  
 El OF expone [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que las interfaces de depuración.  Toda la comunicación es con COM.  Si el OF está en proceso cargado, fuera de proceso, o en otro equipo, no afecta a la comunicación componente.  
  
 El OF funciona con un componente del evaluador de expresiones para habilitar el OF por ese runtime determinado para entender la sintaxis de expresiones.  El OF también funciona con un componente de controlador de símbolos para tener acceso a información de depuración simbólica generada por el compilador del lenguaje.  Para obtener más información, vea [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md) y [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md).  
  
## Vea también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)   
 [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)   
 [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)