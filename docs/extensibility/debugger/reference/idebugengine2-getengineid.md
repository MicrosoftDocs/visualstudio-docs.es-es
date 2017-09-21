---
title: "IDebugEngine2::GetEngineID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::GetEngineID"
helpviewer_keywords: 
  - "IDebugEngine2::GetEngineID"
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::GetEngineID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el GUID del motor \(DE\) de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetEngineID(   
   GUID* pguidEngine  
);  
```  
  
```c#  
int GetEngineID(   
   out Guid pguidEngine  
);  
```  
  
#### Parámetros  
 `pguidEngine`  
 \[out\]  Devuelve el GUID de.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Algunos ejemplos de GUID típico son `guidScriptEng`, `guidNativeEng`, o `guidSQLEng`.  Los nuevos motores de depuración creen su propio GUID para identificar.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto simple de `CEngine` que implemente la interfaz de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) .  
  
```cpp#  
HRESULT CEngine::GetEngineId(GUID *pguidEngine){    
   if (pguidEngine) {    
      // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.    
      // Other languages would require their own guidDifferentEngine to be  
      //defined in the Batdbg.idl file.    
      *pguidEngine = guidBatEng;    
      return NOERROR; // This is typically S_OK.    
   } else {  
      return E_INVALIDARG;    
   }    
}    
```  
  
## Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)