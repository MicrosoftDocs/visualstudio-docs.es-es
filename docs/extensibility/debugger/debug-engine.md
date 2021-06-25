---
title: Depuración del motor | Microsoft Docs
description: Obtenga información sobre cómo funciona un motor de depuración con el intérprete o el sistema operativo para proporcionar servicios como el control de ejecución, los puntos de interrupción y la evaluación de expresiones.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 87c4648ed37ef4fad0d79b7048593ff0c5b7d6d0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905714"
---
# <a name="debug-engine"></a>Motor de depuración
Un motor de depuración (DE) funciona con el intérprete o el sistema operativo para proporcionar servicios de depuración como el control de ejecución, los puntos de interrupción y la evaluación de expresiones. El DE es responsable de supervisar el estado de un programa que se está depurando. Para ello, el DE usa los métodos disponibles en el tiempo de ejecución admitido, ya sea desde la CPU o desde las API proporcionadas por el tiempo de ejecución.

 Por ejemplo, Common Language Runtime (CLR) proporciona mecanismos para supervisar un programa en ejecución a través de las interfaces ICorDebugXXX. Un DE que admite CLR usa las interfaces ICorDebugXXX adecuadas para realizar un seguimiento de un programa de código administrado que se está depurando. A continuación, comunica los cambios de estado al administrador de depuración de sesión (SDM), que reenvía dicha información al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

> [!NOTE]
> Un motor de depuración tiene como destino un tiempo de ejecución específico, es decir, el sistema en el que se ejecuta el programa que se depura. CLR es el tiempo de ejecución del código administrado y el tiempo de ejecución de Win32 es para aplicaciones nativas de Windows. Si el lenguaje que cree puede tener como destino uno de estos dos entornos de ejecución, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ya proporciona los motores de depuración necesarios. Todo lo que tiene que implementar es un evaluador de expresiones.

## <a name="debug-engine-operation"></a>Operación del motor de depuración
 Los servicios de supervisión se implementan a través de las interfaces DE y pueden hacer que el paquete de depuración pase entre diferentes modos operativos. Para obtener más información, vea [Modos operativos.](../../extensibility/debugger/operational-modes.md) Normalmente solo hay una implementación de DE por entorno en tiempo de ejecución.

> [!NOTE]
> Aunque hay implementaciones de DE independientes para Transact-SQL y [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] , VBScript y [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] comparten un único DE.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] La depuración permite que los motores de depuración ejecuten una de estas dos maneras: ya sea en el mismo proceso que el shell o en el mismo proceso que el programa de destino que se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está depurando. Este último formulario suele producirse cuando el proceso que se depura es realmente un script que se ejecuta bajo un intérprete. El motor de depuración debe tener conocimientos profundos del intérprete para poder supervisar el script. En este caso, el intérprete es realmente un tiempo de ejecución; Los motores de depuración son para implementaciones de tiempo de ejecución específicas. Además, la implementación de un solo DE se puede dividir entre los límites de proceso y máquina (por ejemplo, depuración remota).

 DE expone las interfaces [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de depuración. Toda la comunicación se hace a través de COM. Si el DE se carga en proceso, fuera de proceso o en otro equipo, no afecta a la comunicación de componentes.

 De funciona con un componente de evaluador de expresiones para permitir que el de ese tiempo de ejecución determinado comprenda la sintaxis de las expresiones. De también funciona con un componente de controlador de símbolos para tener acceso a la información de depuración simbólica generada por el compilador del lenguaje. Para obtener más información, vea [Evaluador de expresiones y](../../extensibility/debugger/expression-evaluator.md) [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Consulta también
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
- [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)
- [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)
