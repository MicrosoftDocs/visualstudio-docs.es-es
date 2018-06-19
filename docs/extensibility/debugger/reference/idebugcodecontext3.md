---
title: IDebugCodeContext3 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 451e61ab7d6f74c83898987cdbecad2a9e13b06c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108513"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Extiende la [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfaz para habilitar la recuperación de las interfaces de módulo y proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Implementado por motores de depuración y utilizado por el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] paquete de depuración.  
  
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