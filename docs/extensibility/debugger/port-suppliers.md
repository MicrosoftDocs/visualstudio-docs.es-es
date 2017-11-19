---
title: Puerto proveedores | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41c797d2c04c630d5aee7ff5ca2c0d5fc084026a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="port-suppliers"></a>Proveedores de puertos
En cuanto a la arquitectura del depurador, una **proveedor del puerto**:  
  
-   Está incluido en un servidor y proporciona puertos de solicitud a ese servidor.  
  
-   Puede agregar y quitar puertos del servidor que lo contiene.  
  
-   Puede enumerar todos los puertos que se suministra al servidor.  
  
-   Se representa mediante un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz, que está registrado con Visual Studio a través del registro. Esta interfaz se puede obtener mediante una llamada a [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Proporciona un proveedor de puerto predeterminado y un puerto predeterminado. Si debe implementarse un puerto personalizado, un proveedor de puerto personalizado también debe implementarse para proporcionar esos puertos personalizados.  
  
## <a name="see-also"></a>Vea también  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Puertos](../../extensibility/debugger/ports.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)