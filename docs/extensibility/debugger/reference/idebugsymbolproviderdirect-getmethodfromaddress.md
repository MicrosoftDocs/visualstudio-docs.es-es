---
title: IDebugSymbolProviderDirect::GetMethodFromAddress | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f1a72e455092243ba4188121f5b671096d430517
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53832085"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Recupera información sobre el método en la dirección de depuración especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```csharp  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pAddress`  
 [in] Depurar dirección representada por el [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz.  
  
 `pGuid`  
 [out] Identificador único del módulo.  
  
 `pAppID`  
 [out] Identificador del dominio de aplicación.  
  
 `pTokenClass`  
 [out] Token que representa la clase contenedora.  
  
 `pTokenMethod`  
 [out] Token representa el módulo.  
  
 `pdwOffset`  
 [out] Posición de desplazamiento en bytes desde el principio de la `pAddress` parámetro.  
  
 `pdwVersion`  
 [out] Número de versión del método.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)