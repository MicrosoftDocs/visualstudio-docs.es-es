---
title: "IDebugDocumentHelper::GetScriptBlockInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.GetScriptBlockInfo
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::GetScriptBlockInfo"
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::GetScriptBlockInfo
Recupera el intervalo de los caracteres y del motor de script correspondiente a un bloque de script.  
  
## Sintaxis  
  
```  
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### Parámetros  
 `dwSourceContext`  
 \[in\] contexto de origen para obtener el bloque de script.  
  
 `ppasd`  
 \[out\] motor de script para obtener este bloque de script.  
  
 `piCharPos`  
 \[out\] ubicación de inicio del bloque de script.  
  
 `cChars`  
 \[out\] número de caracteres del bloque de script.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método recupera el intervalo de los caracteres y del motor de script correspondiente a un bloque de script.  
  
## Vea también  
 [IDebugDocumentHelper \(Interfaz\)](../../winscript/reference/idebugdocumenthelper-interface.md)