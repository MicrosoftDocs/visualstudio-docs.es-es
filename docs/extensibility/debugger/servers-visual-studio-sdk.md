---
title: Servidores (SDK de Visual Studio) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 404048e37f0a95ac1425250cfdcd098c4eb7f59d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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