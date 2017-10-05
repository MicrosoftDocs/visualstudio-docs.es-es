---
title: IDebugStackFrame2::GetLanguageInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
caps.latest.revision: 10
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
ms.openlocfilehash: 460979d28bfc9244726ea3345c8a435de87a6c29
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo
Obtiene el idioma asociado a este marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetLanguageInfo (   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo (   
   ref string pbstrLanguage,  
   ref Guid   pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrLanguage`  
 [out] Devuelve el nombre del idioma que implementa el método asociado a este marco de pila.  
  
 `pguidLanguage`  
 [out] Devuelve el `GUID` del lenguaje. Para el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] idiomas, por ejemplo, la siguiente puede devolver:  
  
-   `guidVBScriptLang`  
  
-   `guidJScriptLang`  
  
-   `guidCPPLang`  
  
-   `guidVBLang`  
  
-   `guidSQLLang`  
  
-   `guidScriptLang`  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
