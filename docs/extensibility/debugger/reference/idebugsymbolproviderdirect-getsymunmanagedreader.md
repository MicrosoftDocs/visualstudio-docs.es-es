---
title: IDebugSymbolProviderDirect::GetSymUnmanagedReader | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetSymUnmanagedReader
- IDebugSymbolProviderDirect::GetSymUnmanagedReader
ms.assetid: 147bacfa-f66c-43e0-8a72-e601058dc57f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 311b03657cef0d0ec6785cad332cbf7c9530b48e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolproviderdirectgetsymunmanagedreader"></a>IDebugSymbolProviderDirect::GetSymUnmanagedReader
Recupera un lector de símbolos para código no administrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetSymUnmanagedReader (  
   ULONG32    ulAppDomainID,  
   GUID       guidModule,  
   IUnknown** ppSymUnmanagedReader  
);  
```  
  
```csharp  
int GetSymUnmanagedReader (  
   uint       ulAppDomainID,  
   Guid       guidModule,  
   out object ppSymUnmanagedReader  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ulAppDomainID`  
 [in] Identificador del dominio de aplicación.  
  
 `guidModule`  
 [in] Identificador único del módulo.  
  
 `ppSymUnmanagedReader`  
 [out] Devuelve un objeto que representa el lector de símbolos para código no administrado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)