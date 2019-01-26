---
title: Procesar el Administrador de depuración | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- machine debug manager
- debugging [Debugging SDK], Machine Debug Manager
ms.assetid: d0861e0c-b819-490c-9604-5e6d08ac291a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 441f5c470f97012da7c63f79f06dd08f810c1d0a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945338"
---
# <a name="process-debug-manager"></a>Administrador de depuración de procesos
El Administrador de depuración del proceso (PDM) es un componente de Visual Studio que administra programas y procesos, dejándolos disponibles para la sesión de depuración manager y los motores de depuración.  
  
 El PDM administra todos los procesos que se pueden depurar. Para poder ser depurados, un programa debe registrarse con el PDM. Este registro se realiza en el momento en que se inicia el programa, ya sea un puerto o un motor de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Procesos](../../extensibility/debugger/processes.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Puertos](../../extensibility/debugger/ports.md)   
 [Programas](../../extensibility/debugger/programs.md)   
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)