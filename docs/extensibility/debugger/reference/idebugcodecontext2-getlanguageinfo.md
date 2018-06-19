---
title: IDebugCodeContext2::GetLanguageInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 915c6009d796209e34abc38fe5769ebdd90635d8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106700"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Obtiene la información de idioma para este contexto de código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrLanguage`  
 [entrada, salida] Devuelve una cadena que contiene el nombre del idioma, como "C++".  
  
 `pguidLanguage`  
 [entrada, salida] Devuelve el GUID para el idioma del contexto del código, por ejemplo, `guidCPPLang`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Al menos uno de los parámetros debe devolver un valor distinto de null.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)