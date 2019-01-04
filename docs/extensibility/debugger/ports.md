---
title: Puertos | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 77a0b954242a65e6f462a0548eeac0bc551e1083
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873611"
---
# <a name="ports"></a>Puertos
En la arquitectura de depurador, un *puerto*:  
  
- Se está ejecutando un contenedor para un conjunto de procesos en un servidor. Por ejemplo, un puerto podría representar una conexión a un dispositivo basado en Windows CE mediante un cable serie o a un equipo en red que no son de DCOM. Un puerto especial, llamado puerto local, contiene todos los procesos que se ejecutan en el equipo local.  
  
- Puede identificarse por nombre o identificador.  
  
- Puede enumerar todos los procesos que se ejecutan en el puerto e iniciar y finalizar estos procesos.  
  
- Se representa mediante un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaz, que se crea pasando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argumento [agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proporciona un puerto predeterminado que controla todos los procesos basados en Windows, nativos y administrados. Un puerto personalizado debe configurarse para las conexiones con dispositivos externos que no están basados en Windows. Para proporcionar dichos puertos personalizados, debe configurar un proveedor de puerto personalizado.  
  
## <a name="see-also"></a>Vea también  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Procesos](../../extensibility/debugger/processes.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)