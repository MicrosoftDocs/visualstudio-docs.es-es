---
title: "IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2::ReloadSymbols"
helpviewer_keywords: 
  - "IDebugModule2::ReloadSymbols (método)"
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

OBSOLETO.  NOT UTILICE.  Cargar los símbolos para este módulo.  
  
## Sintaxis  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```c#  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### Parámetros  
 `pszUrlToSymbols`  
 \[in\]  La ruta de acceso al almacén de símbolos.  
  
 `pbstrDebugMessage`  
 \[out\]  Devuelve un mensaje informativo, como un estado o un mensaje de error, que se muestran a la derecha del nombre del módulo en la ventana módulos.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  Un motor de depuración siempre debe devolver `E_FAIL`.  
  
## Comentarios  
 Este método ya no se admite.  Implemente el método de [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) en su lugar.  
  
## Vea también  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)