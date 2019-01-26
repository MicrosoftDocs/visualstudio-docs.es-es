---
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa229c88ff62d96ee1e91e503dcbdd7c35c1cfc1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944597"
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Especifica qué información se va a recuperar sobre un objeto de propiedad de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
  
```csharp  
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
  
## <a name="members"></a>Miembros  
 DEBUGPROP_INFO_FULLNAME  
 Inicializar o usar el `bstrFullName` campo.  
  
 DEBUGPROP_INFO_NAME  
 Inicializar o usar el `bstrName` campo.  
  
 DEBUGPROP_INFO_TYPE  
 Inicializar o usar el `bstrType` campo.  
  
 DEBUGPROP_INFO_VALUE  
 Inicializar o usar el `bstrValue` campo.  
  
 DEBUGPROP_INFO_ATTRIB  
 Inicializar o usar el `dwAttrib` campo.  
  
 DEBUGPROP_INFO_PROP,  
 Inicializar o usar el `pProperty` campo que contiene un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaz.  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 Especifica que el campo de valor debe contener el valor expandido automática, si está disponible para este tipo de objeto.  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 Desusado.  
  
 DEBUGPROP_INFO_VALUE_RAW  
 No se devuelven los valores beautified o miembros (es decir, no dan formato a los valores).  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 No devuelven valores sintetizados especiales (por ejemplo, no llame a `ToString()` en un objeto para generar un valor).  
  
 DEBUGPROP_INFO_NONE  
 Especifica que no se establecen marcas.  
  
 DEBUGPROP_INFO_STANDARD  
 Inicializar o usar el `dwAttrib`, `bstrName`, `bstrType`, y `bstrValue` campos.  
  
 DEBUGPROP_INFO_All  
 Indica una máscara de todas las marcas.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pasan a la [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), y [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) métodos para indicar cuáles son los campos que se inicialice la [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructura.  
  
 Estos valores también se usan para la `dwFields` miembro de la `DEBUG_PROPERTY_INFO` estructura para indicar qué campos de la estructura se usan y válido cuando se devuelve la estructura.  
  
 Estos valores se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)