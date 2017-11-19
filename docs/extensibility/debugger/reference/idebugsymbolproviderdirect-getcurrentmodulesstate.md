---
title: IDebugSymbolProviderDirect::GetCurrentModulesState | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetCurrentModulesState
- IDebugSymbolProviderDirect::GetCurrentModulesState
ms.assetid: a0c85318-5686-4eed-b213-21f2b9e681e6
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 50cd7ec29f0d4ff8d5dd3a5adde3829d0b601f0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesstate"></a>IDebugSymbolProviderDirect::GetCurrentModulesState
Recupera información sobre el grupo de símbolos de los cuales el proveedor de símbolo es un miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetCurrentModulesState(  
    DWORD*          pState,  
    unsigned long * count  
);  
```  
  
```csharp  
int GetCurrentModulesState(  
    out uint pState,  
    out uint count  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pState`  
 [out] El estado del grupo de proveedor de símbolos.  
  
 `count`  
 [out] Número de módulos en el grupo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El estado se cambia cada vez que un módulo se agrega o se quita del grupo de símbolos. Por lo tanto, este método se puede utilizar para detectar si se ha modificado un grupo de símbolos.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)