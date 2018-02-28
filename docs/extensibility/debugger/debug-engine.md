---
title: "Motor de depuración | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 70e572b73f8474f77a17989c790f2e7336f9d7a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="debug-engine"></a>Motor de depuración
Un motor de depuración (Alemania) funciona con el sistema operativo o intérprete para proporcionar servicios de depuración como la evaluación de expresión, control y los puntos de interrupción de ejecución. La DE es responsable de supervisar el estado de un programa que se está depurando. Para lograr esto, la DE utiliza los métodos que sean a su disposición en el tiempo de ejecución admitida, si de la CPU o de la API proporcionada por el runtime.  
  
 Por ejemplo, common language runtime (CLR) proporciona mecanismos para supervisar un programa en ejecución a través de las interfaces de ICorDebugXXX. Un Alemania que admita CLR usa las interfaces de ICorDebugXXX adecuadas para realizar un seguimiento de un programa de código administrado que se está depurando. Se comunica, a continuación, los cambios de estado para el Administrador de depuración de sesión (SDM), que reenvía dicha información a la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
> [!NOTE]
>  Un motor de depuración tiene como destino un runtime concreto, es decir, el sistema en el que el programa que se está depurando se ejecuta. CLR es el tiempo de ejecución para código administrado y el tiempo de ejecución de Win32 es para aplicaciones nativas de Windows. Si el idioma se crea uno de estos dos tiempos de ejecución, puede tener como destino [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ya proporciona los motores de depuración es necesario. Lo único que debe implementar es un evaluador de expresiones.  
  
## <a name="debug-engine-operation"></a>Funcionamiento del motor de depuración  
 Los servicios de supervisión se implementan a través de las interfaces de Alemania y pueden hacer que el paquete de depuración para la transición entre distintos modos de funcionamiento. Para obtener más información, consulte [modos de funcionamiento](../../extensibility/debugger/operational-modes.md). Normalmente hay sólo una implementación DE por cada entorno de tiempo de ejecución.  
  
> [!NOTE]
>  Mientras haya implementaciones DE independientes para Transact-SQL y [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript y [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] comparten un único Alemania.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]habilita la depuración depurar motores para ejecutar una de dos maneras: en el mismo proceso que el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de shell o en el mismo proceso que el programa de destino que se está depurando. El segundo formulario normalmente se produce cuando el proceso que se está depurando es realmente un script que se ejecuta en un intérprete, y el motor de depuración debe tener un conocimiento profundo del intérprete de con el fin de supervisar la secuencia de comandos. Tenga en cuenta que en este caso, el intérprete es realmente un tiempo de ejecución; motores de depuración son para las implementaciones en tiempo de ejecución específica. Además, la implementación de un único DE se puede dividir en los límites del procesos o equipos (por ejemplo, depuración remota).  
  
 La muestra DE la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaces de depuración. Es toda la comunicación a través de COM. Si se carga el Alemania en proceso, fuera de proceso o en otro equipo, no afecta la comunicación de componentes.  
  
 La DE funciona con un componente de evaluador de expresiones para habilitar el Alemania durante ese tiempo de ejecución determinado comprender la sintaxis de expresiones. La DE también funciona con un componente de controlador de símbolos para tener acceso a la información de depuración simbólica generada por el compilador de lenguaje. Para obtener más información, consulte [evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md) y [proveedor símbolo](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Vea también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)   
 [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)   
 [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)