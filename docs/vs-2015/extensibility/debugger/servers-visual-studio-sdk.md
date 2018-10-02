---
title: Servidores (SDK de Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e79e5e00bb4708359c19fd6a2ff95c7f31fd1179
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47583113"
---
# <a name="servers-visual-studio-sdk"></a>Servidores (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [servidores (Visual Studio SDK)](https://docs.microsoft.com/visualstudio/extensibility/debugger/servers-visual-studio-sdk).  
  
En cuanto a la arquitectura de depurador, un **server**:  
  
-   Es un contenedor de puertos y los proveedores de puertos y se usa para comunicar los puertos y proveedores de puertos para el Administrador de depuración de la sesión (SDM) y motores de depuración.  
  
-   Puede identificarse por su nombre y enumerar los proveedores de puertos y sus puertos.  
  
-   Se representa mediante un [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interfaz, que solo se implementa mediante Visual Studio (una instancia de un servidor para cada instancia de Visual Studio en ejecución).  
  
## <a name="see-also"></a>Vea también  
 [Puertos](../../extensibility/debugger/ports.md)   
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)

