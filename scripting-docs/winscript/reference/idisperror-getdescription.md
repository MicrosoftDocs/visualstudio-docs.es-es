---
title: "IDispError::GetDescription | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetDescription
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetDescription"
ms.assetid: 04deaea6-0265-4e34-952e-634edba0e923
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetDescription
Devuelve una descripción del error.  
  
## Sintaxis  
  
```  
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### Parámetros  
 `pbstrDescription`  
 \[out\] vinculadas contener una breve descripción del error.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 El texto se devuelve en el lenguaje especificado por el identificador. de configuración regional \(LCID\) pasado a `IDispatchEx::InvokeEx` para el método que encontró el error.  
  
> [!NOTE]
>  Este método no está implementado.  
  
## Vea también  
 [IDispError \(Interfaz\)](../../winscript/reference/idisperror-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)