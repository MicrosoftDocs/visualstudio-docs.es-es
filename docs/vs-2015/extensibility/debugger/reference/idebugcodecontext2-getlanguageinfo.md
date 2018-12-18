---
title: IDebugCodeContext2::GetLanguageInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afd29868fa0f1e8c766e5ed1504c6e5152b9118f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776439"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene la información de idioma para este contexto de código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in, out] Devuelve una cadena que contiene el nombre del lenguaje, por ejemplo, "C++".  
  
 `pguidLanguage`  
 [in, out] Devuelve el GUID para el idioma del contexto del código, por ejemplo, `guidCPPLang`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Al menos uno de los parámetros debe devolver un valor distinto de null.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)

