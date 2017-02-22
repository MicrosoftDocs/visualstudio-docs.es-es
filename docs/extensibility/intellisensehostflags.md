---
title: "IntelliSenseHostFlags | Microsoft Docs"
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
  - "IntellisenseHostFlags"
helpviewer_keywords: 
  - "IntelliSense, IntellisenseHostFlags (enumeración)"
  - "IntellisenseHostFlags (enumeración)"
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica las marcas de host de IntelliSense.  
  
## Sintaxis  
  
```cpp#  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### Parámetros  
  
|Miembros|Descripción|  
|--------------|-----------------|  
|`IHF_READONLYCONTEXT`|Búfer de contexto es de solo lectura.|  
|`IHF_NOSEPARATESUBJECT`|No hay texto de asunto. Búfer de contexto contiene el destino de IntelliSense \(implica `!IHF_READONLYCONTEXT`\).|  
|`IHF_SINGLELINESUBJECT`|Texto del asunto no es capaz múltiples líneas.|  
|`IHF_FORCECOMMITTOCONTEXT`|Igual a `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Edición \(en el asunto o el contexto\) debe realizarse en el modo sobrescribir.|  
  
## Requisitos  
 SingleFileeditor.idl  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop>