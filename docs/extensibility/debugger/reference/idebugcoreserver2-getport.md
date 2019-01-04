---
title: IDebugCoreServer2::GetPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d9f2ba3699337191a9aa11b8b47d9e5f6101bf2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965400"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
Recupera un puerto específico.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetPort(   
   REFGUID       guidPort,  
   IDebugPort2** ppPort  
);  
```  
  
```csharp  
int GetPort(   
   ref Guid        guidPort,  
   out IDebugPort2 ppPort  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guidPort`  
 [in] GUID del puerto que desea recuperar.  
  
 `ppPort`  
 [out] Devuelve un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objeto que representa el puerto deseado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_PORTSUPPLIER_NO_PORT` si no hay ningún puerto con el identificador proporcionado.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)