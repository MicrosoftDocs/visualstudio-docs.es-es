---
title: IDebugProcess2::EnumThreads | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7a517e3b99571487ebdebff1ea1d49f86e47ae2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851301"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera una lista de todos los subprocesos que se ejecutan en el proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) objeto que contiene una lista de todos los subprocesos de todos los programas en el proceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método enumera los subprocesos que se ejecutan en cada programa y, a continuación, las combina en una vista de proceso de los subprocesos. Un solo subproceso puede ejecutarse en varios programas; Este método enumera solo una vez ese subproceso.  
  
 Este método presenta una lista de los subprocesos del proceso sin duplicados. En caso contrario, para enumerar los subprocesos que se ejecutan en un programa determinado, utilice el [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)

