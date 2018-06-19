---
title: IDebugSymbolProvider::GetAddressesFromPosition | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 129ed233361991f5e58a258c73838bc9739112de
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118536"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Este método asigna una posición del documento en una matriz de direcciones de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromPosition(   
   IDebugDocumentPosition2  pDocPos,  
   bool                     fStatmentOnly,  
   out IEnumDebugAddresses  ppEnumBegAddresses,  
   out IEnumDebugAddresses  ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pDocPos`  
 [in] La posición del documento.  
  
 `fStatmentOnly`  
 [in] Si es TRUE, limita las direcciones de depuración a una única instrucción.  
  
 `ppEnumBegAddresses`  
 [out] Devuelve un enumerador para las direcciones iniciales de depuración asociada a esta instrucción o línea.  
  
 `ppEnumEndAddresses`  
 [out] Devuelve un [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) enumerador para las direcciones de depuración final asociado a esta instrucción o línea.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, una posición del documento indica un intervalo de líneas de código fuente. Este método proporciona la fecha inicial y final de las direcciones de depuración asociadas con estas líneas. Algunos lenguajes permiten las instrucciones que abarcan varias líneas o líneas que contiene más de una instrucción. Este método proporciona una marca para limitar las direcciones de depuración a una única instrucción.  
  
 Es posible que una sola instrucción tener varias direcciones de depuración, como en el caso de plantillas.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)