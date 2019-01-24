---
title: Proveedores de puerto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e134b9b4adeb45693a9841a0a867a9c3630bf2aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835109"
---
# <a name="port-suppliers"></a>Proveedores de puertos
En la arquitectura de depurador, un *proveedor del puerto*:  
  
- Está contenida en un servidor y proporciona puertos de solicitud a ese servidor.  
  
- Puede agregar y quitar los puertos del servidor que lo contiene.  
  
- Puede enumerar todos los puertos que proporcionó en el servidor.  
  
- Se representa mediante un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz, que está registrado con Visual Studio a través del registro. Esta interfaz se puede obtener mediante una llamada a [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proporciona un proveedor de puerto predeterminado y un puerto predeterminado. Si debe implementarse un puerto personalizado, un proveedor de puerto personalizado también debe implementarse para proporcionar esos puertos personalizados.  
  
## <a name="see-also"></a>Vea también  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Puertos](../../extensibility/debugger/ports.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)