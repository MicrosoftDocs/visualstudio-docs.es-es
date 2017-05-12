---
title: "IDispError::GetHelpInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetHelpInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetHelpInfo"
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetHelpInfo
Devuelve la ruta de acceso del archivo de Ayuda y el Id. de contexto del tema que explica el error, si es posible.  
  
## Sintaxis  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### Parámetros  
 `pbstrFileName`  
 \[out\] vinculadas contener la ruta completa del archivo de Ayuda.  Si no hay ningún archivo de Ayuda o un error, el valor devuelto es NULL.  
  
 `pdwContext`  
 \[out\] Id. de contexto de Ayuda para obtener el error.  Si no hay ningún archivo de Ayuda \(si `pbstrFileName` es NULL\), este parámetro no tiene ningún significado.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|Un error proveedor\- concreto producido.|  
|`E_INVALIDARG`|`pbstrFileName` o `pdwContext` fue NULL.|  
|`E_OUTOFMEMORY`|El proveedor no pudo asignar memoria suficiente en el que devolver la ruta de acceso del archivo de Ayuda.|  
  
## Comentarios  
 Este método devuelve la ruta de acceso del archivo de Ayuda y el Id. de contexto del tema que explica el error, si es posible.  
  
> [!NOTE]
>  Este método no está implementado.  
  
## Vea también  
 [IDispError \(Interfaz\)](../../winscript/reference/idisperror-interface.md)