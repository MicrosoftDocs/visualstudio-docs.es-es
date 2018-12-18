---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9957b0aaf81048c5040e3f7ff54f3fa9be742dc1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858568"
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
Especifica qué información se va a recuperar sobre un objeto de referencia de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## <a name="members"></a>Miembros  
 DEBUGREF_INFO_NAME  
 Inicializar o usar el `bstrName` campo en la estructura.  
  
 DEBUGREF_INFO_TYPE  
 Inicializar o usar el `bstrType` campo en la estructura.  
  
 DEBUGREF_INFO_VALUE  
 Inicializar o usar el `bstrValue` campo en la estructura.  
  
 DEBUGREF_INFO_ATTRIB  
 Inicializar o usar el `dwAttrib` campo en la estructura.  
  
 DEBUGREF_INFO_REFTYPE  
 Inicializar o usar el `dwRefType` campo en la estructura.  
  
 DEBUGREF_INFO_REF  
 Inicializar o usar el `pReference` campo en la estructura.  
  
 DEBUGREF_INFO_VALUE_AUTOEXPAND  
 El campo de valor debe contener el valor expandido automática, si está disponible para este tipo de objeto.  
  
 DEBUGREF_INFO_NONE  
 Indica que no se establecen marcas.  
  
 DEBUGREF_INFO_ALL  
 Indica una máscara de las marcas.  
  
## <a name="remarks"></a>Comentarios  
 Estas marcas se pasan a la [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) y [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) métodos para indicar qué campos de la [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructura deben inicializarse.  
  
 Utilizado para la `dwFields` miembro de la `DEBUG_REFERENCE_INFO` estructura para indicar qué campos se usan y válido cuando se devuelve la estructura.  
  
 Estos valores se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)