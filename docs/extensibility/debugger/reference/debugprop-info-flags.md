---
title: "DEBUGPROP_INFO_FLAGS | Microsoft Docs"
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
  - "DEBUGPROP_INFO_FLAGS"
helpviewer_keywords: 
  - "Enumeración DBGPROP_INFO_FLAGS"
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUGPROP_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica qué información se va a recuperar información sobre un objeto de la propiedad de depuración.  
  
## Sintaxis  
  
```cpp#  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## Members  
 DEBUGPROP\_INFORMATION\_FULLNAME  
 Inicializa y usan el campo de `bstrFullName` .  
  
 DEBUGPROP\_INFORMATION\_NAME  
 Inicializa y usan el campo de `bstrName` .  
  
 DEBUGPROP\_INFORMATION\_TYPE  
 Inicializa y usan el campo de `bstrType` .  
  
 DEBUGPROP\_INFORMATION\_VALUE  
 Inicializa y usan el campo de `bstrValue` .  
  
 DEBUGPROP\_INFORMATION\_ATTRIB  
 Inicializa y usan el campo de `dwAttrib` .  
  
 DEBUGPROP\_INFORMATION\_PROP,  
 Inicializa y usan el campo de`pProperty` que contiene una interfaz de [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) .  
  
 DEBUGPROP\_INFORMATION\_VALUE\_AUTOEXPAND  
 Especifica que el campo value debe contener el valor auto\-expandido, si está disponible, para este tipo de objeto.  
  
 DEBUGPROP\_INFORMATION\_VALUE\_NOFUNCEVAL  
 Obsoleto.  
  
 DEBUGPROP\_INFORMATION\_VALUE\_RAW  
 No devuelve ningún valor o miembros embellecidos \(es decir, no da formato a los valores\).  
  
 DEBUGPROP\_INFORMATION\_VALUE\_NO\_TOSTRING  
 No devuelve ningún valor sintetizada especial \(por ejemplo, no llame `ToString()` en un objeto para generar un valor\).  
  
 DEBUGPROP\_INFORMATION\_NONE  
 Especifica que no se establece ningún marcador.  
  
 DEBUGPROP\_INFORMATION\_STANDARD  
 Inicializa y el uso `dwAttrib`, `bstrName`, `bstrType`, y los campos de `bstrValue` .  
  
 DEBUGPROP\_INFORMATION\_All  
 indica una máscara de todos los indicadores.  
  
## Comentarios  
 Estos valores se pasan a los métodos de [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), de [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), y de [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) para indicar qué campos se deben inicializar la estructura de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .  
  
 Estos valores se utilizan también para el miembro de `dwFields` de la estructura de `DEBUG_PROPERTY_INFO` para indicar qué campos de estructura son utilizados y válidos cuando se devuelve la estructura.  
  
 estos valores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)