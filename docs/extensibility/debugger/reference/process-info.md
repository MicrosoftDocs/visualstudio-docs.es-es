---
title: "PROCESS_INFO | Microsoft Docs"
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
  - "PROCESS_INFO"
helpviewer_keywords: 
  - "Estructura PROCESS_INFO"
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# PROCESS_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contiene información sobre un proceso.  
  
## Sintaxis  
  
```cpp#  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```c#  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## Members  
 Campos  
 Una combinación de marcadores de enumeración de [PROCESS\_INFO\_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) que especifican se completan los campos.  
  
 bstrFileName  
 El nombre completo del proceso.  Equivalente a llamar al método de [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) con el parámetro `GN_FILENAME`.  
  
 bstrBaseName  
 El nombre de archivo y la extensión del proceso.  Equivalente a llamar al método de `IDebugProcess2::Getname` con el parámetro `GN_BASENAME`.  
  
 bstrTitle  
 El título del proceso, si existe.  Equivalente a llamar al método de `IDebugProcess2::Getname` con el parámetro `GN_TITLE`.  
  
 ProcessId  
 la estructura de [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) que identifica el proceso.  Equivalente a llamar al método de [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) .  
  
 dwSessionId  
 El identificador de la sesión de depuración que este proceso se ejecuta en.  
  
 bstrAttachedSessionName  
 El nombre asociado de la sesión.  Equivalente a llamar al método de [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) .  
  
 CreationTime  
 El tiempo que el proceso se ha creado.  
  
 Marcadores  
 Una combinación de marcadores de enumeración de [PROCESS\_INFO\_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) que especifican las propiedades del proceso.  
  
## Comentarios  
 Esta estructura se pasa al método de [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) donde se completa.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS\_INFO\_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS\_INFO\_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)