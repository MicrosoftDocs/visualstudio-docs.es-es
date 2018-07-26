---
title: Proveedores de puerto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 5385e006bcd2f79ab7b1c2e723e696b833991f36
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252354"
---
# <a name="port-suppliers"></a>Proveedores de puertos
En la arquitectura de depurador, un *proveedor del puerto*:  
  
-   Está contenida en un servidor y proporciona puertos de solicitud a ese servidor.  
  
-   Puede agregar y quitar los puertos del servidor que lo contiene.  
  
-   Puede enumerar todos los puertos que proporcionó en el servidor.  
  
-   Se representa mediante un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz, que está registrado con Visual Studio a través del registro. Esta interfaz se puede obtener mediante una llamada a [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proporciona un proveedor de puerto predeterminado y un puerto predeterminado. Si debe implementarse un puerto personalizado, un proveedor de puerto personalizado también debe implementarse para proporcionar esos puertos personalizados.  
  
## <a name="see-also"></a>Vea también  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Puertos](../../extensibility/debugger/ports.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)