---
title: "TEXT_DOCUMENT_ARRAY (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "TEXT_DOCUMENT_ARRAY (Estructura)"
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# TEXT_DOCUMENT_ARRAY (Estructura)
Matriz de objetos [IDebugDocumentText \(Interfaz\)](../../winscript/reference/idebugdocumenttext-interface.md).  Asignan miembros con CoTaskMemAlloc.  
  
## Sintaxis  
  
```  
typedef struct tagTEXT_DOCUMENT_ARRAY  
{  
    DWORD dwCount;  
    [size_is(dwCount)] IDebugDocumentText **Members;  
} TEXT_DOCUMENT_ARRAY;  
  
```  
  
## Members  
 `dwCount`  
 El número de documentos.  
  
 `Members`  
 El conjunto de documentos.  
  
## Vea también  
 [Active Script Debugger \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)