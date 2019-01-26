---
title: Servidores (SDK de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea7b54d8a27f061c1ef5d023f309ddab8295db90
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989606"
---
# <a name="servers-visual-studio-sdk"></a>Servidores (Visual Studio SDK)
En la arquitectura de depurador, un *server*:  
  
-   Es un contenedor de puertos y los proveedores de puertos y comunica los puertos y proveedores de puertos para el Administrador de depuración de la sesión (SDM) y los motores de depuración.  
  
-   Puede identificarse por su nombre y enumerar los proveedores de puertos y sus puertos.  
  
-   Se representa mediante un [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interfaz, que solo se implementa mediante Visual Studio (una instancia de un servidor para cada instancia de Visual Studio en ejecución).  
  
## <a name="see-also"></a>Vea también  
 [Puertos](../../extensibility/debugger/ports.md)   
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)