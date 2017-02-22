---
title: "TEXT_DOC_ATTR_2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TEXT_DOC_ATTR_2"
helpviewer_keywords: 
  - "TEXT_DOC_ATTR_2 (enumeración)"
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# TEXT_DOC_ATTR_2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

describe los atributos de un documento.  
  
## Sintaxis  
  
```cpp#  
typedef DWORD TEXT_DOC_ATTR_2;  
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
```c#  
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
## Members  
 TEXT\_DOC\_ATTR\_READONLY\_2  
 Indica que el documento es de solo lectura.  
  
## Comentarios  
  
> [!NOTE]
>  este valor no es realmente definido en el ensamblado para C\#.  En su lugar, debe copiar la definición en el archivo de código fuente.  
  
 Pasado como argumento al método de [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)