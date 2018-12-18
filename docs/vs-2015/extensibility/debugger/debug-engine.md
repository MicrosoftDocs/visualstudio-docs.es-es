---
title: Motor de depuración | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf2335b907601bb17276b06ae1bef033a1641515
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733331"
---
# <a name="debug-engine"></a>Motor de depuración
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un motor de depuración (DE) funciona con el sistema operativo o intérprete para proporcionar servicios de depuración, como la evaluación de expresión, los puntos de interrupción y control de ejecución. La DE es responsable de supervisar el estado de un programa que se está depurando. Para lograr esto, la DE usa los métodos que sean a su disposición en el runtime compatible, si de la CPU o de API proporcionado por el tiempo de ejecución.  
  
 Por ejemplo, common language runtime (CLR) proporciona mecanismos para supervisar un programa en ejecución mediante las interfaces de ICorDebugXXX. A DE compatible con CLR usa las interfaces de ICorDebugXXX adecuadas para realizar un seguimiento de un programa de código administrado que se está depurando. Se comunica a continuación, los cambios de estado para el Administrador de sesión de depuración (SDM), que reenvía dicha información a la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
> [!NOTE]
>  Un motor de depuración tiene como destino un tiempo de ejecución específico, es decir, el sistema en el que el programa que se está depurando se ejecuta. CLR es el tiempo de ejecución para código administrado y el tiempo de ejecución de Win32 es para aplicaciones nativas de Windows. Si el idioma que cree puede tener como destino uno de estos dos tiempos de ejecución, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ya suministra los motores de depuración necesarias. Lo único que debe implementar es un evaluador de expresiones.  
  
## <a name="debug-engine-operation"></a>Operación del motor de depuración  
 Los servicios de supervisión se implementan a través de las interfaces DE y pueden hacer que el paquete de depuración en la transición entre distintos modos de funcionamiento. Para obtener más información, consulte [modos operativos](../../extensibility/debugger/operational-modes.md). Normalmente hay solo una implementación DE cada entorno de tiempo de ejecución.  
  
> [!NOTE]
>  Aunque hay otras implementaciones DE para Transact-SQL y [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)], VBScript y [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] comparten una única DE.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depuración permite depurar motores para ejecutar de dos maneras: ya sea en el mismo proceso que la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] de shell o en el mismo proceso que el programa de destino que se está depurando. La segunda forma normalmente se produce cuando el proceso que se está depurando es realmente un script que se ejecuta en un intérprete y el motor de depuración debe tener un conocimiento profundo del intérprete para supervisar la secuencia de comandos. Tenga en cuenta que en este caso, el intérprete es realmente un tiempo de ejecución; motores de depuración son para las implementaciones en tiempo de ejecución específica. Además, se puede dividir la implementación de un único DE a través de límites de proceso y máquinas (por ejemplo, depuración remota).  
  
 La muestra DE la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfaces de depuración. Es toda la comunicación a través de COM. Si se carga la DE en proceso, fuera de proceso o en otro equipo, no afecta la comunicación de componentes.  
  
 La DE funciona con un componente de evaluador de expresión para habilitar la DE para ese tiempo de ejecución concreto comprender la sintaxis de expresiones. La DE también funciona con un componente de controlador de símbolos para tener acceso a la información de depuración simbólica generada por el compilador de lenguaje. Para obtener más información, consulte [evaluador](../../extensibility/debugger/expression-evaluator.md) y [proveedor de símbolos](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Vea también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)   
 [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)   
 [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)

