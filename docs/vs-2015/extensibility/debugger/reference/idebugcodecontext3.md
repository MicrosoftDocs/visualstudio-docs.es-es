---
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 62b84bd77038c7a17b65f764bd303d6a6372a52c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154164"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Extiende la interfaz [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) para habilitar la recuperación de interfaces de módulo y de proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Implementado por los motores de depuración y consumido por el [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] paquete de depuración.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos de la `IDebugCodeContext2` interfaz, esta interfaz implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera una referencia a la interfaz del módulo de depuración.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera una referencia a la interfaz del proceso de depuración.|  
  
## <a name="remarks"></a>Observaciones  
 Se trata de una interfaz opcional que, por lo general, no tiene que implementarse.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
