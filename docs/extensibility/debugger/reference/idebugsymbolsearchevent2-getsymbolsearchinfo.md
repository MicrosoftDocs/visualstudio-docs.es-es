---
title: "IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Llama a un controlador de eventos para recuperar resultados sobre un proceso de carga de símbolos.  
  
## Sintaxis  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```c#  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### Parámetros  
 `pModule`  
 \[out\]  Un objeto IDebugModule3 que representa el módulo en el que los símbolos se cargaron.  
  
 `pbstrDebugMessage`  
 \[in, out\]  Devuelve una cadena que contiene un mensaje de error de módulo.  Si no hay ningún error, esta cadena sólo contendrá el nombre de módulo pero nunca está vacía.  
  
> [!NOTE]
>  \[C\+\+\] `pbstrDebugMessage` no puede ser `NULL` y se debe liberar con `SysFreeString`.  
  
 `pdwModuleInfoFlags`  
 \[out\]  Una combinación de marcadores de enumeración de [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) que indica si algunos símbolos se cargaron.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  
  
## Comentarios  
 Cuando un controlador recibe el evento de [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) después de que se realiza un intento de cargar los símbolos de depuración para un módulo, el controlador puede llamar al thismethod para determinar los resultados de la carga.  
  
## Vea también  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)