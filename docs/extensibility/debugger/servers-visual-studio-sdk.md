---
title: "Servidores (SDK de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servidores, depurar"
  - "depurar [SDK de depuración], servidores"
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Servidores (SDK de Visual Studio)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En términos de arquitectura del depurador, **un servidor**:  
  
-   Es un contenedor de puertos y proveedores de puerto y se utiliza para comunicarse puertos y los proveedores de puerto a la sesión del administrador \(SDM\) y depurar los motores.  
  
-   Puede identificarse por nombre, y muestra los puertos y proveedores de puerto.  
  
-   Se representa mediante una interfaz de [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , que implementan únicamente por Visual Studio \(una instancia de un servidor para cada instancia de Visual Studio\).  
  
## Vea también  
 [Puertos](../../extensibility/debugger/ports.md)   
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)