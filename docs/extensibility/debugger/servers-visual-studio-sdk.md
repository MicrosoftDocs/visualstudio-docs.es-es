---
title: Servidores (SDK de Visual Studio) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2904641e8188abc6ef2382b2da272a9f96fd0f81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="servers-visual-studio-sdk"></a>Servidores (SDK de Visual Studio)
En cuanto a la arquitectura del depurador, una **server**:  
  
-   Es un contenedor de puertos y proveedores de puertos y se usa para comunicar los puertos y proveedores de puertos para el Administrador de sesión de depuración (SDM) y los motores de depuración.  
  
-   Puede identificarse por su nombre y enumerar sus puertos y los proveedores de puertos.  
  
-   Se representa mediante un [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interfaz, que solo se implementa mediante Visual Studio (una instancia de un servidor para cada instancia de ejecución de Visual Studio).  
  
## <a name="see-also"></a>Vea también  
 [Puertos](../../extensibility/debugger/ports.md)   
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)