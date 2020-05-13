---
title: Motor de depuración (Debug Engine) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739065"
---
# <a name="debug-engine"></a>Motor de depuración
Un motor de depuración (DE) funciona con el intérprete o el sistema operativo para proporcionar servicios de depuración como control de ejecución, puntos de interrupción y evaluación de expresiones. El DE es responsable de supervisar el estado de un programa que se está depurando. Para lograr esto, la DE utiliza los métodos que están disponibles para él en el tiempo de ejecución admitido, ya sea desde la CPU o desde las API proporcionadas por el tiempo de ejecución.

 Por ejemplo, Common Language Runtime (CLR) proporciona mecanismos para supervisar un programa en ejecución a través de las interfaces ICorDebugXXX. Un DE que admite CLR usa las interfaces ICorDebugXXX adecuadas para realizar un seguimiento de un programa de código administrado que se está depurando. A continuación, comunica cualquier cambio de estado al administrador de depuración [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de sesión (SDM), que reenvía dicha información al IDE.

> [!NOTE]
> Un motor de depuración tiene como destino un tiempo de ejecución específico, es decir, el sistema en el que se ejecuta el programa que se está depurando. CLR es el tiempo de ejecución del código administrado y el tiempo de ejecución de Win32 es para aplicaciones nativas de Windows. Si el lenguaje que crea puede tener [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] como destino uno de estos dos tiempos de ejecución, ya proporciona los motores de depuración necesarios. Todo lo que tiene que implementar es un evaluador de expresiones.

## <a name="debug-engine-operation"></a>Funcionamiento del motor de depuración
 Los servicios de supervisión se implementan a través de las interfaces DE y pueden hacer que el paquete de depuración pase entre diferentes modos operativos. Para obtener más información, consulte [Modos operativos](../../extensibility/debugger/operational-modes.md). Normalmente, solo hay una implementación DE por entorno en tiempo de ejecución.

> [!NOTE]
> Aunque hay implementaciones DE independientes [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]para Transact-SQLTransact-SQL y , VBScript y [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] comparten una sola DE.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]la depuración permite que los motores de depuración se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ejecuten de dos maneras: en el mismo proceso que el shell o en el mismo proceso que el programa de destino que se está depurando. Este último formulario suele producirse cuando el proceso que se está depurando es en realidad un script que se ejecuta bajo un intérprete. El motor de depuración debe tener un conocimiento íntimo del intérprete para supervisar el script. En este caso, el intérprete es en realidad un tiempo de ejecución; los motores de depuración son para implementaciones en tiempo de ejecución específicas. Además, la implementación de una única DE se puede dividir entre los límites del proceso y de la máquina (por ejemplo, la depuración remota).

 El DE expone [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las interfaces de depuración. Toda la comunicación es a través de COM. Si el DE se carga en proceso, fuera de proceso o en otro equipo, no afecta a la comunicación de componentes.

 El DE funciona con un componente de evaluador de expresiones para permitir que la DE de ese tiempo de ejecución determinado comprenda la sintaxis de las expresiones. El DE también funciona con un componente de controlador de símbolos para tener acceso a la información de depuración simbólica generada por el compilador de lenguaje. Para obtener más información, consulte Evaluador de [expresiones](../../extensibility/debugger/expression-evaluator.md) y Proveedor de [símbolos](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Vea también
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
- [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)
- [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)
