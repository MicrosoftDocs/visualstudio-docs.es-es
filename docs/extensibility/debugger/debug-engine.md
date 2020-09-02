---
title: Motor de depuración | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4cb00796f8db23a43cd81a06d80d0fac40f075e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739065"
---
# <a name="debug-engine"></a>Motor de depuración
Un motor DE depuración (DE) funciona con el intérprete o el sistema operativo para proporcionar servicios de depuración, como el control de ejecución, los puntos de interrupción y la evaluación de expresiones. El DE es responsable de supervisar el estado de un programa que se está depurando. Para ello, el método DE usa los métodos que están disponibles en el tiempo de ejecución admitido, ya sea de la CPU o de las API proporcionadas por el tiempo de ejecución.

 Por ejemplo, el Common Language Runtime (CLR) proporciona mecanismos para supervisar un programa en ejecución a través de las interfaces ICorDebugXXX. Un DE que admite CLR usa las interfaces de ICorDebugXXX adecuadas para realizar un seguimiento de un programa de código administrado que se está depurando. A continuación, comunica cualquier cambio de estado al administrador de depuración de la sesión (SDM), que reenvía la información al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

> [!NOTE]
> Un motor de depuración tiene como destino un tiempo de ejecución específico, es decir, el sistema en el que se ejecuta el programa que se está depurando. CLR es el tiempo de ejecución para el código administrado y el tiempo de ejecución de Win32 es para las aplicaciones Windows nativas. Si el lenguaje creado puede tener como destino uno de estos dos tiempos de ejecución, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ya proporciona los motores de depuración necesarios. Todo lo que tiene que implementar es un evaluador de expresiones.

## <a name="debug-engine-operation"></a>Operación del motor de depuración
 Los servicios DE supervisión se implementan a través DE las interfaces DE y pueden hacer que el paquete de depuración pase de un modo operativo a otro. Para obtener más información, vea [modos operativos](../../extensibility/debugger/operational-modes.md). Normalmente solo hay una implementación DE para cada entorno en tiempo de ejecución.

> [!NOTE]
> Aunque hay implementaciones independientes de de Transact-SQL y [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] , VBScript y [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] comparten un único de.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración permite que los motores de depuración se ejecuten de una de estas dos maneras: en el mismo proceso que el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell o en el mismo proceso que el programa de destino que se está depurando. Esta última forma normalmente se produce cuando el proceso que se está depurando es realmente un script que se ejecuta en un intérprete. El motor de depuración debe tener un conocimiento profundo del intérprete para poder supervisar el script. En este caso, el intérprete es realmente un tiempo de ejecución; los motores de depuración son para implementaciones en tiempo de ejecución específicas. Además, la implementación de un único DE se puede dividir entre los límites del proceso y del equipo (por ejemplo, la depuración remota).

 El DE expone las [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaces de depuración. Toda la comunicación se realiza a través de COM. Si el DE se carga en proceso, fuera de proceso o en otro equipo, no afecta a la comunicación de componentes.

 DE funciona con un componente del evaluador de expresiones para permitir que el de ese tiempo de ejecución concreto comprenda la sintaxis de las expresiones. El DE también trabaja con un componente de controlador de símbolos para tener acceso a la información de depuración simbólica generada por el compilador del lenguaje. Para obtener más información, consulte [evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md) y [proveedor de símbolos](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Vea también
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
- [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)
- [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)
