---
title: IDebugSymbolProvider::GetNextAddress | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a682342410b32422bc87f180b00f017520322d8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119105"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
Obtiene la dirección de depuración que sigue a una dirección de depuración especificado en un método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetNextAddress(   
   IDebugAddress*  pAddress,  
   BOOL            fStatementOnly,  
   IDebugAddress** ppAddress  
);  
```  
  
```csharp  
int GetNextAddress(   
   IDebugAddress     pAddress,  
   bool              fStatementOnly,  
   out IDebugAddress ppAddress  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pAddress`  
 [in] Dirección de depuración especificado.  
  
 `fStatementOnly`  
 [in] Si es TRUE, limita las direcciones de depuración a una única instrucción.  
  
 `ppAddress`  
 [out] Devuelve la siguiente dirección de depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un válidas `HRESULT`, normalmente S_OK.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)