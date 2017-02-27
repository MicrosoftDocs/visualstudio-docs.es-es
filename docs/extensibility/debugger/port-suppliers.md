---
title: "Proveedores de puertos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proveedores de puertos"
  - "depurar [SDK de depuración], proveedores de puerto"
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Proveedores de puertos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En términos de arquitectura del depurador, **un proveedor de puerto**:  
  
-   Está contenido en un servidor y proporciona puertos a petición a ese servidor.  
  
-   Puede agregar y quitar puertos de servidor el contener.  
  
-   Puede mostrar todos los puertos que ha proporcionado al servidor.  
  
-   Se representa mediante una interfaz de [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , que se registra con Visual Studio a través del registro.  Esta interfaz puede obtenerse llamando a [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona un proveedor de puerto predeterminado y un puerto predeterminado.  Si un puerto personalizado debe implementar, un proveedor de puerto también necesita implementarse para proporcionar los puertos personalizados.  
  
## Vea también  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Puertos](../../extensibility/debugger/ports.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)