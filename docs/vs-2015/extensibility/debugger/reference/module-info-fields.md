---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a0ab7baf5a878cecdf3cb1644187fd50a5e6be3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222396"
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica las marcas de la información de depuración del módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 Inicializar o usar ninguno de los campos de la estructura.  
  
 MIF_NAME  
 Inicializar o usar el `m_bstrName` campo el [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estructura.  
  
 MIF_URL  
 Inicializar o usar el `m_bstrUrl` campo el `MODULE_INFO` estructura.  
  
 MIF_VERSION  
 Inicializar o usar el `m_bstrVersion` campo el `MODULE_INFO` estructura.  
  
 MIF_DEBUGMESSAGE  
 Inicializar o usar el `m_bstrDebugMessage` campo el `MODULE_INFO` estructura.  
  
 MIF_LOADADDRESS  
 Inicializar o usar el `m_addrLoadAddress` campo el `MODULE_INFO` estructura.  
  
 MIF_PREFFEREDADDRESS  
 Inicializar o usar el `m_addrPreferredLoadAddress` campo el `MODULE_INFO` estructura.  
  
 MIF_SIZE  
 Inicializar o usar el `m_dwSize` campo el `MODULE_INFO` estructura.  
  
 MIF_LOADORDER  
 Inicializar o usar el `m_dwLoadOrder` campo el `MODULE_INFO` estructura.  
  
 MIF_TIMESTAMP  
 Inicializar o usar el `m_TimeStamp` campo el `MODULE_INFO` estructura.  
  
 MIF_URLSYMBOLLOCATION  
 Inicializar o usar el `m_bstrUrlSymbolLocation` campo el `MODULE_INFO` estructura.  
  
 MIF_FLAGS  
 Inicializar o usar el `m_dwModuleFlags` campo el `MODULE_INFO` estructura.  
  
 MIF_ALLFIELDS  
 Inicializar o usar todos los campos en el `MODULE_INFO` estructura.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pasan como argumento a la [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) método para indicar qué campos de la [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estructura deben inicializarse.  
  
 Estos valores también se usan en el `MODULE_INFO` estructura para indicar qué campos se usan y válido.  
  
 Estas marcas se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)

