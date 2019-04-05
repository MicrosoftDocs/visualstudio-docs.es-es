---
title: Servidores (SDK de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 81de310320fe45c06f2a233d7c8d742f9d55405e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58986644"
---
# <a name="servers-visual-studio-sdk"></a>Servidores (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En cuanto a la arquitectura de depurador, un **server**:  
  
-   Es un contenedor de puertos y los proveedores de puertos y se usa para comunicar los puertos y proveedores de puertos para el Administrador de depuración de la sesión (SDM) y motores de depuración.  
  
-   Puede identificarse por su nombre y enumerar los proveedores de puertos y sus puertos.  
  
-   Se representa mediante un [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interfaz, que solo se implementa mediante Visual Studio (una instancia de un servidor para cada instancia de Visual Studio en ejecución).  
  
## <a name="see-also"></a>Vea también  
 [Puertos](../../extensibility/debugger/ports.md)   
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
