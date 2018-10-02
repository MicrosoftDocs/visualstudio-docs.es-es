---
title: IDebugProgramNameChangedEvent2 | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 75c92a1c339161f3391727522016144d8156aa09
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581210"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugProgramNameChangedEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramnamechangedevent2).  
  
Se envían desde el motor de depuración (DE) el Administrador de depuración de la sesión (SDM) cuando cambia el nombre de un programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgramNameChangedEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz para informar de que ha cambiado el nombre del programa. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para tener acceso a la **IDebugEvent2** interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 La DE crea y envía este objeto de evento para notificar un cambio de nombre de programa. La DE envía este evento mediante el [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada que proporciona el SDM cuando adjunta al programa que se está depurando. El proveedor de puerto personalizado, envía este evento mediante que interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

