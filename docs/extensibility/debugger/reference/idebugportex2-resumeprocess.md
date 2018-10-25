---
title: IDebugPortEx2::ResumeProcess | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::ResumeProcess
helpviewer_keywords:
- IDebugPortEx2::ResumeProcess
ms.assetid: e80a6960-9456-4764-9320-e7b1bd57fe5d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47364a88ca5e49a691120b198ce32b74e9d895d8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905550"
---
# <a name="idebugportex2resumeprocess"></a>IDebugPortEx2::ResumeProcess
Reanuda la ejecución de un proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT ResumeProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```cpp  
int ResumeProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pPortProcess`  
 [in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa el proceso que se va a reanudar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)