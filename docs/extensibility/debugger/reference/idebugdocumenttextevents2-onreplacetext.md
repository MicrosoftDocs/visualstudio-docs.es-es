---
title: "IDebugDocumentTextEvents2::onReplaceText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentTextEvents2::OnReplaceText"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents2::onReplaceText"
ms.assetid: cb39f025-66d8-4dc0-bef6-1bdc8e07db92
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentTextEvents2::onReplaceText
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Notifica al paquete de depuración que el texto se ha reemplazado en el documento.  
  
## Sintaxis  
  
```cpp#  
HRESULT onReplaceText(   
   TEXT_POSITION pos,  
   DWORD         dwNumToReplace  
);  
```  
  
```c#  
int onReplaceText(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToReplace  
);  
```  
  
#### Parámetros  
 `pos`  
 \[in\]  [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) indica donde el texto se ha reemplazado.  
  
 `dwNumToReplace`  
 \[in\]  Especifica el número de caracteres de texto que se ha reemplazado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)