---
title: "DEBUG_PROPERTY_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_PROPERTY_INFO"
helpviewer_keywords: 
  - "Estructura DEBUG_PROPERTY_INFO"
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# DEBUG_PROPERTY_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contiene información sobre una propiedad de depuración.  
  
## Sintaxis  
  
```cpp#  
typedef struct tagDEBUG_PROPERTY_INFO {   
   DEBUGPROP_INFO_FLAGS dwValidFields;  
   BSTR                 bstrFullName;  
   BSTR                 bstrName;  
   BSTR                 bstrType;  
   BSTR                 bstrValue;  
   IDebugProperty2*     pProperty;  
   DBG_ATTRIB_FLAGS     dwAttrib;  
} DEBUG_PROPERTY_INFO;  
```  
  
```c#  
public struct DEBUG_PROPERTY_INFO {   
   public uint            dwValidFields;  
   public string          bstrFullName;  
   public string          bstrName;  
   public string          bstrType;  
   public string          bstrValue;  
   public IDebugProperty2 pProperty;  
   public ulong           dwAttrib;  
};  
```  
  
## Members  
 dwValidFields  
 Una combinación de marcadores de enumeración de [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) que especifica se completan los campos.  
  
 bstrFullName  
 el nombre completo de la propiedad.  
  
 bstrName  
 El nombre de propiedad en un contexto.  
  
 bstrType  
 El tipo de propiedad como una cadena con formato.  
  
 bstrValue  
 El valor de propiedad como una cadena con formato.  
  
 pProperty  
 el objeto de [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) descrito por esta estructura.  
  
 dwAttrib  
 Una combinación de marcadores de enumeración de [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) que describe los atributos de esta propiedad.  
  
## Comentarios  
 Una propiedad es un objeto de naturaleza jerárquica que tenga un nombre, un tipo, y un valor.  Por ejemplo, una propiedad puede describir variables locales, parámetros, variables y expresiones de reloj, y registros.  
  
 Esta estructura se pasa al método de [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) donde se completa.  esta estructura también se devuelve como parte de una lista de esta estructura de la interfaz de [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) que, a su vez, se devuelve de una llamada a los métodos de [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) y de [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)