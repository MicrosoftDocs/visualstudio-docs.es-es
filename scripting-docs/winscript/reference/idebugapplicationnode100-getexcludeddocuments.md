---
title: "IDebugApplicationNode100::GetExcludedDocuments | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::GetExcludedDocuments"
ms.assetid: d44583a7-0b0b-4799-b075-837ad1da1946
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100::GetExcludedDocuments
Obtiene los documentos de texto que son ocultados por el filtro especificado.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 \(Interfaz\)](../../winscript/reference/idebugapplicationnode100-interface.md) es implementado por PDM v10.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
HRESULT GetExcludedDocuments(  
        [in] APPLICATION_NODE_EVENT_FILTER filter,  
        [out] TEXT_DOCUMENT_ARRAY* pDocuments  
        );  
```  
  
#### Parámetros  
 `filter`  
 El filtro.  
  
 `pDocuments`  
 El conjunto de documentos.  
  
## Vea también  
 [IDebugApplicationNode100 \(Interfaz\)](../../winscript/reference/idebugapplicationnode100-interface.md)