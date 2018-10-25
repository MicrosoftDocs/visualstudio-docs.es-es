---
title: Proveedores de puerto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 173ff6b7550731262e8f4e3293b6f7c35eac4062
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858815"
---
# <a name="port-suppliers"></a>Proveedores de puertos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En cuanto a la arquitectura de depurador, un **proveedor del puerto**:  
  
- Está contenida en un servidor y proporciona puertos de solicitud a ese servidor.  
  
- Puede agregar y quitar los puertos del servidor que lo contiene.  
  
- Puede enumerar todos los puertos que proporcionó en el servidor.  
  
- Se representa mediante un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz, que está registrado con Visual Studio a través del registro. Esta interfaz se puede obtener mediante una llamada a [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Proporciona un proveedor de puerto predeterminado y un puerto predeterminado. Si debe implementarse un puerto personalizado, un proveedor de puerto personalizado también debe implementarse para proporcionar esos puertos personalizados.  
  
## <a name="see-also"></a>Vea también  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Puertos](../../extensibility/debugger/ports.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)

