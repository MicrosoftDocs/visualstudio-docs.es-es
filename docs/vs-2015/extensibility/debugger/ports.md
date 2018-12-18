---
title: Puertos | Microsoft Docs
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
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a72b9118c06930c328db631938271d4feb938027
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786248"
---
# <a name="ports"></a>Puertos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En cuanto a la arquitectura de depurador, un **puerto**:  
  
- Se está ejecutando un contenedor para un conjunto de procesos en un servidor. Por ejemplo, un puerto podría representar una conexión a un dispositivo basado en Windows CE mediante un cable serie o a un equipo en red que no son de DCOM. Un puerto especial, llamado puerto local, contiene todos los procesos que se ejecutan en el equipo local.  
  
- Puede identificarse por nombre o identificador.  
  
- Puede enumerar todos los procesos que se ejecutan en el puerto e iniciar y finalizar estos procesos.  
  
- Se representa mediante un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaz, que se crea pasando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argumento [agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Proporciona un puerto predeterminado que controla todos los procesos basados en Windows, nativos y administrados. Debe implementarse un puerto personalizado para las conexiones con dispositivos externos que no están basados en Windows. Para proporcionar dichos puertos personalizados, un proveedor de puerto personalizado también debe implementarse.  
  
## <a name="see-also"></a>Vea también  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Procesos](../../extensibility/debugger/processes.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

