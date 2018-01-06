---
title: Puertos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6378ddc2663e4ecf239c78ede96f0c1bc12d77a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ports"></a>Puertos
En cuanto a la arquitectura del depurador, una **puerto**:  
  
-   Es un contenedor para un conjunto de procesos que se ejecuta en un servidor. Por ejemplo, un puerto podría representar una conexión a un dispositivo basado en Windows CE mediante un cable serie, o a un equipo en red no DCOM. Un puerto especial, denominado el puerto local, contiene todos los procesos que se ejecutan en el equipo local.  
  
-   Puede identificarse por nombre o identificador.  
  
-   Puede enumerar todos los procesos que se ejecutan en el puerto e iniciar y finalizar estos procesos.  
  
-   Se representa mediante un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaz, que se crea pasando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argumento pasado a [agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Proporciona un puerto predeterminado que controla todos los procesos basados en Windows, nativos y administrados. Un puerto personalizado debe implementarse para las conexiones con dispositivos externos que no están basados en Windows. Para proporcionar estos puertos personalizados, un proveedor de puerto personalizado también debe implementarse.  
  
## <a name="see-also"></a>Vea también  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Procesos](../../extensibility/debugger/processes.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)