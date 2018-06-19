---
title: IDebugSymbolProvider::GetContextFromAddress | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetContextFromAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetContextFromAddress method
ms.assetid: 7a27d56f-20d4-4e5c-af7b-7307d3aff0a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9a82f69c0a671628a29148c7b09c47db48dc787
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120506"
---
# <a name="idebugsymbolprovidergetcontextfromaddress"></a>IDebugSymbolProvider::GetContextFromAddress
Este método asigna una dirección de depuración en un contexto de documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetContextFromAddress(   
   IDebugAddress*           pAddress,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```csharp  
int GetContextFromAddress(  
   IDebugAddress              pAddress,   
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pAddress`  
 [in] La dirección de depuración tal como está representado por un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz.  
  
 `ppDocContext`  
 [out] Devuelve un contexto de documento tal como está representado por un [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)