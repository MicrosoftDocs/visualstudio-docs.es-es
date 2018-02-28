---
title: FIELD_INFO_FIELDS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 95812aa634e799b5594c0cae9f4d2c3d397ca945
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
Especifica qué información debe recuperar sobre un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>Miembros  
 FIF_FULLNAME  
 Inicializar o utilizar el `bstrFullName` campo el [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) estructura.  
  
 FIF_NAME  
 Inicializar o utilizar el `bstrName` campo el `FIELD_INFO` estructura.  
  
 FIF_TYPE  
 Inicializar o utilizar el `bstrType` campo el `FIELD_INFO` estructura.  
  
 FIF_MODIFIERS  
 Inicializar o utilizar el `bstrModifiers` campo el `FIELD_INFO` estructura.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores también se pasan como argumento a la [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método para especificar qué campos de la [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) estructura deben inicializarse.  
  
 Estos valores también se usan en el `dwFields` miembro de la `FIELD_INFO` estructura para indicar qué campos se utilizan y válido.  
  
 Estas marcas se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)