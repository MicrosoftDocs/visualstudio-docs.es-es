---
title: "IDebugEnumField::GetStringFromValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField::GetStringFromValue"
helpviewer_keywords: 
  - "IDebugEnumField::GetStringFromValue (método)"
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método obtiene el nombre de la constante de enumeración con su valor.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```c#  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### Parámetros  
 `value`  
 \[in\]  El valor por el que se obtiene el nombre de la constante de la enumeración.  
  
 `pbstrValue`  
 \[out\]  devuelve el nombre de la constante de la enumeración.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` si el valor no tiene ningún nombre asociado, o devuelve un código de error.  
  
## Comentarios  
 Si hay más de un nombre asociado con el mismo valor, el nombre definido en la enumeración se devolverá.  
  
## Vea también  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)