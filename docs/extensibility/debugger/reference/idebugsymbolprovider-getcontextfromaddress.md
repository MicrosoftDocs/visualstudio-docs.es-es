---
title: IDebugSymbolProvider::GetContextFromAddress | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugSymbolProvider::GetContextFromAddress
helpviewer_keywords: IDebugSymbolProvider::GetContextFromAddress method
ms.assetid: 7a27d56f-20d4-4e5c-af7b-7307d3aff0a1
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cae89cc03bdb5056906d9c9d9c925bc1a77427b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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