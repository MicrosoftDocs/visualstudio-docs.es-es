---
title: "IDebugEnumField::GetValueFromStringCaseInsensitive | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField::GetValueFromStringCaseInsensitive"
helpviewer_keywords: 
  - "IDebugEnumField::GetValueFromStringCaseInsensitive (método)"
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEnumField::GetValueFromStringCaseInsensitive
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método usa una búsqueda sin distinción entre mayúsculas y minúsculas para devolver el valor asociado al nombre de una constante de enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```c#  
int GetValueFromStringCaseInsensitive(  
   string    pszValue,   
   out ulong pValue  
);  
```  
  
#### Parámetros  
 `pszValue`  
 \[in\]  Una cadena que especifica el nombre para que obtenga el valor.  Observe que para C\+\+, es una cadena de caracteres anchos.  
  
 `pValue`  
 \[out\]  devuelve el valor numérico asociado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE`, si el nombre no es parte de la enumeración, o un código de error.  
  
## Comentarios  
 Este método no distingue entre mayúsculas y minúsculas.  Si una búsqueda con distinción entre mayúsculas y minúsculas es necesaria \(por ejemplo, en un lenguaje como C\+\+ donde se distingue entre mayúsculas y minúsculas los nombres\), utilice [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).  
  
## Vea también  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)