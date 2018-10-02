---
title: IDebugCodeContext3 | Documentos de Microsoft
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
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7064cddbf81a01e7d55d64249d4ff4da6e585728
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579081"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugCodeContext3](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcodecontext3).  
  
Extiende la [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfaz para habilitar la recuperación de las interfaces de módulo y el proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Implementado por los motores de depuración y utilizado por el [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] paquete de depuración.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos en el `IDebugCodeContext2` interfaz, esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera una referencia a la interfaz del módulo de depuración.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera una referencia a la interfaz del proceso de depuración.|  
  
## <a name="remarks"></a>Comentarios  
 Se trata de una interfaz opcional que normalmente no tiene que implementarse.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

