---
title: "Puertos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "puertos"
  - "depurar [SDK de depuración], puertos"
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Puertos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En términos de arquitectura del depurador, **un puerto**:  
  
-   Es un contenedor para un conjunto de procesos que se ejecutan en un servidor.  Por ejemplo, un puerto podría representar una conexión a un dispositivo basado en Windows CE por un cable serie, o un equipo conectado de no\-DCOM.  un puerto especial, denominado el puerto local, contiene todos los procesos que se ejecutan en el equipo local.  
  
-   Puede identificarse por nombre o identificador.  
  
-   Puede enumerar todos los procesos en ejecución en el puerto y iniciar y finalizar estos procesos.  
  
-   Se representa mediante una interfaz de [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , creada pasando un argumento de [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) a [Agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 fuentes de[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un puerto predeterminado que administra todos los procesos basada en Windows, nativo y administrado.  Un puerto personalizado debe implementar para las conexiones con dispositivos externos que no están basadas en Windows.  Para proporcionar tales puertos personalizados, un proveedor de puerto también debe ser implementado.  
  
## Vea también  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Procesos](../../extensibility/debugger/processes.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)