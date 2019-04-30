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
ms.openlocfilehash: 9f6a93cc87be2369ba3bc96bf6682caeb4a727c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889177"
---
# <a name="process-debug-manager"></a>Administrador de depuración de procesos
El Administrador de depuración del proceso (PDM) es un componente de Visual Studio que administra programas y procesos, dejándolos disponibles para la sesión de depuración manager y los motores de depuración.

 El PDM administra todos los procesos que se pueden depurar. Para poder ser depurados, un programa debe registrarse con el PDM. Este registro se realiza en el momento en que se inicia el programa, ya sea un puerto o un motor de depuración.

## <a name="see-also"></a>Vea también
- [Procesos](../../extensibility/debugger/processes.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [Puertos](../../extensibility/debugger/ports.md)
- [Programas](../../extensibility/debugger/programs.md)
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)