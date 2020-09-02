---
title: 'IDebugProcess2:: Enumthreads (| Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3e9b6447827baa80da2843c992a8d2233dd1a4b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188023"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera una lista de todos los subprocesos que se ejecutan en el proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 enuncia Devuelve un objeto [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) que contiene una lista de todos los subprocesos de todos los programas del proceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Este método enumera los subprocesos que se ejecutan en cada programa y, a continuación, los combina en una vista de proceso de los subprocesos. Un único subproceso puede ejecutarse en varios programas; Este método enumera el subproceso solo una vez.  
  
 Este método presenta una lista de los subprocesos del proceso sin duplicados. De lo contrario, para enumerar los subprocesos que se ejecutan en un programa determinado, use el método [enumthreads (](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) .  
  
## <a name="see-also"></a>Consulte también  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
