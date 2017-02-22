---
title: "DEBUG_REFERENCE_INFO | Microsoft Docs"
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
  - "DEBUG_REFERENCE_INFO"
helpviewer_keywords: 
  - "Estructura DEBUG_REFERENCE_INFO"
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_REFERENCE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

describe una referencia.  
  
## Sintaxis  
  
```cpp#  
typedef struct tagDEBUG_REFERENCE_INFO {   
   DEBUGREF_INFO_FLAGS dwFields;  
   BSTR                bstrName;  
   BSTR                bstrType;  
   BSTR                bstrValue;  
   DBG_ATTRIB_FLAGS    dwAttrib;  
   REFERENCE_TYPE.     dwRefType;  
   IDebugReference2*   m_pReference;  
} DEBUG_REFERENCE_INFO;  
```  
  
```c#  
public struct DEBUG_REFERENCE_INFO {   
   public uint             dwFields;  
   public string           bstrName;  
   public string           bstrType;  
   public string           bstrValue;  
   public ulong            dwAttrib;  
   public uint.            dwRefType;  
   public IDebugReference2 m_pReference;  
};  
```  
  
## Members  
 dwFields  
 Una combinación de marcadores de enumeración de [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) que especifica se completan los campos.  
  
 bstrName  
 El nombre definido por el usuario del objeto de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .  
  
 bstrType  
 El tipo de referencia como una cadena con formato.  
  
 bstrValue  
 El valor de referencia como una cadena con formato  
  
 dwAttrib  
 Una combinación de marcadores de enumeración de [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) que especifica los marcadores para los atributos de la propiedad de depuración.  
  
 dwRefType  
 Un valor de enumeración de [REFERENCE\_TYPE](../../../extensibility/debugger/reference/reference-type.md) que especifica si el tipo de referencia es seguro o débil.  
  
 m\_pReference  
 un objeto de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que especifica la información de referencia.  
  
## Comentarios  
 Esta estructura se pasa a una llamada al método de [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) que se completará.  Esta estructura también se devuelve como parte de una interfaz de [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) que, a su vez, se devuelve de una llamada al método de [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE\_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)