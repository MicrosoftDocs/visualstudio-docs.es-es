---
title: IDebugSymbolProviderDirect::GetMethodFromAddress | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: a2979c305bd8db9700f55e799de26fe4ce1422d6
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

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
 [in] Depurar dirección representada por la [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz.  
  
 `pGuid`  
 [out] Identificador único del módulo.  
  
 `pAppID`  
 [out] Identificador del dominio de aplicación.  
  
 `pTokenClass`  
 [out] Símbolo (token) que representa la clase contenedora.  
  
 `pTokenMethod`  
 [out] Símbolo (token) representa el módulo.  
  
 `pdwOffset`  
 [out] Posición de desplazamiento en bytes desde el principio de la `pAddress` parámetro.  
  
 `pdwVersion`  
 [out] Número de versión del método.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
