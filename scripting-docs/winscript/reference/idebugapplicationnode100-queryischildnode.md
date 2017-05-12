---
title: "IDebugApplicationNode100::QueryIsChildNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::QueryIsChildNode"
ms.assetid: 4f36f435-0f34-4f9e-bba3-e75285fd7bbb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationNode100::QueryIsChildNode
Determina si el documento especificado pertenece a uno de los nodos secundarios de este nodo.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 \(Interfaz\)](../../winscript/reference/idebugapplicationnode100-interface.md) es implementado por PDM v10.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
HRESULT QueryIsChildNode(  
        [in] IDebugDocument* pSearchKey  
        );  
```  
  
#### Parámetros  
 `pSearchKey`  
 La clave de búsqueda.  
  
## Vea también  
 [IDebugApplicationNode100 \(Interfaz\)](../../winscript/reference/idebugapplicationnode100-interface.md)