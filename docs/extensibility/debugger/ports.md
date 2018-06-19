---
title: Puertos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a350e0579f7e60d8a7ffc3e879d79364cfdf0317
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099449"
---
# <a name="ports"></a>Puertos
En cuanto a la arquitectura del depurador, una **puerto**:  
  
-   Es un contenedor para un conjunto de procesos que se ejecuta en un servidor. Por ejemplo, un puerto podría representar una conexión a un dispositivo basado en Windows CE mediante un cable serie, o a un equipo en red no DCOM. Un puerto especial, denominado el puerto local, contiene todos los procesos que se ejecutan en el equipo local.  
  
-   Puede identificarse por nombre o identificador.  
  
-   Puede enumerar todos los procesos que se ejecutan en el puerto e iniciar y finalizar estos procesos.  
  
-   Se representa mediante un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaz, que se crea pasando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argumento pasado a [agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proporciona un puerto predeterminado que controla todos los procesos basados en Windows, nativos y administrados. Un puerto personalizado debe implementarse para las conexiones con dispositivos externos que no están basados en Windows. Para proporcionar estos puertos personalizados, un proveedor de puerto personalizado también debe implementarse.  
  
## <a name="see-also"></a>Vea también  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Procesos](../../extensibility/debugger/processes.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)