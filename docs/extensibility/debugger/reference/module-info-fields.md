---
title: MODULE_INFO_FIELDS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d96175501d0e75ee1949847c69909c23a3b08582
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
Especifica las marcas de la información del módulo de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## <a name="members"></a>Miembros  
 MIF_NONE  
 Inicializar o utilizar ninguno de los campos de la estructura.  
  
 MIF_NAME  
 Inicializar o utilizar el `m_bstrName` campo el [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estructura.  
  
 MIF_URL  
 Inicializar o utilizar el `m_bstrUrl` campo el `MODULE_INFO` estructura.  
  
 MIF_VERSION  
 Inicializar o utilizar el `m_bstrVersion` campo el `MODULE_INFO` estructura.  
  
 MIF_DEBUGMESSAGE  
 Inicializar o utilizar el `m_bstrDebugMessage` campo el `MODULE_INFO` estructura.  
  
 MIF_LOADADDRESS  
 Inicializar o utilizar el `m_addrLoadAddress` campo el `MODULE_INFO` estructura.  
  
 MIF_PREFFEREDADDRESS  
 Inicializar o utilizar el `m_addrPreferredLoadAddress` campo el `MODULE_INFO` estructura.  
  
 MIF_SIZE  
 Inicializar o utilizar el `m_dwSize` campo el `MODULE_INFO` estructura.  
  
 MIF_LOADORDER  
 Inicializar o utilizar el `m_dwLoadOrder` campo el `MODULE_INFO` estructura.  
  
 MIF_TIMESTAMP  
 Inicializar o utilizar el `m_TimeStamp` campo el `MODULE_INFO` estructura.  
  
 MIF_URLSYMBOLLOCATION  
 Inicializar o utilizar el `m_bstrUrlSymbolLocation` campo el `MODULE_INFO` estructura.  
  
 MIF_FLAGS  
 Inicializar o utilizar el `m_dwModuleFlags` campo el `MODULE_INFO` estructura.  
  
 MIF_ALLFIELDS  
 Inicializar o utilizar todos los campos en el `MODULE_INFO` estructura.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pasan como argumento a la [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) método para indicar qué campos de la [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estructura deben inicializarse.  
  
 Estos valores también se usan en el `MODULE_INFO` estructura para indicar qué campos se utilizan y válido.  
  
 Estas marcas se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)