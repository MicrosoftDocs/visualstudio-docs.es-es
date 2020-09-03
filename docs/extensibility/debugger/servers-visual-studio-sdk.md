---
title: Servidores (SDK de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32fdbb5afca40c3b4fced468d2f9ef0ea5226c00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712899"
---
# <a name="servers-visual-studio-sdk"></a>Servidores (Visual Studio SDK)
En la arquitectura del depurador, un *servidor*:

- Es un contenedor de puertos y proveedores de puertos y comunica puertos y proveedores de puertos con el administrador de depuración de sesión (SDM) y los motores de depuración.

- Puede identificarse por nombre y enumerar los puertos y los proveedores de puertos.

- Se representa mediante una interfaz [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , que solo implementa Visual Studio (una instancia de un servidor para cada instancia de Visual Studio en ejecución).

## <a name="see-also"></a>Vea también
- [Puertos](../../extensibility/debugger/ports.md)
- [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
