---
title: MODULE_INFO | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fd49230165282dd656252c4edaabfbaa31d43340
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="moduleinfo"></a>MODULE_INFO
Describe un determinado módulo (archivo DLL, EXE o ensamblado).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct tagMODULE_INFO {   
   MODULE_INFO_FIELDS dwValidFields;  
   BSTR               m_bstrName;  
   BSTR               m_bstrUrl;  
   BSTR               m_bstrVersion;  
   BSTR               m_bstrDebugMessage;  
   UINT64             m_addrLoadAddress;  
   UINT64             m_addrPreferredLoadAddress;  
   DWORD              m_dwSize;  
   DWORD              m_dwLoadOrder;  
   FILETIME           m_TimeStamp;  
   BSTR               m_bstrUrlSymbolLocation;  
   MODULE_FLAGS       m_dwModuleFlags;  
} MODULE_INFO;  
```  
  
```csharp  
public struct MODULE_INFO {   
   public uint     dwValidFields;  
   public string   m_bstrName;  
   public string   m_bstrUrl;  
   public string   m_bstrVersion;  
   public string   m_bstrDebugMessage;  
   public ulong    m_addrLoadAddress;  
   public ulong    m_addrPreferredLoadAddress;  
   public uint     m_dwSize;  
   public uint     m_dwLoadOrder;  
   public FILETIME m_TimeStamp;  
   public string   m_bstrUrlSymbolLocation;  
   public uint     m_dwModuleFlags;  
};  
```  
  
## <a name="members"></a>Miembros  
 dwValidFields  
 Una combinación de indicadores de la [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) enumeración que especifica qué campos se rellenan.  
  
 m_bstrName  
 Nombre del módulo.  
  
 m_bstrUrl  
 La dirección URL del módulo.  
  
 m_bstrVersion  
 La versión del módulo.  
  
 m_bstrDebugMessage  
 Un mensaje opcional sobre el módulo, por ejemplo, "símbolos no se puede cargar."  
  
 m_addrLoadAddress  
 La dirección de carga del módulo.  
  
 m_addrPreferredLoadAddress  
 La dirección de carga preferido del módulo.  
  
 m_dwSize  
 El tamaño del módulo.  
  
 m_dwLoadOrder  
 El orden de carga del módulo.  
  
 m_TimeStamp  
 La hora en que se modificó por última vez el archivo de símbolos.  
  
 m_bstrUrlSymbolLocation  
 La ubicación del archivo de símbolos (por ejemplo, ".\\") especificados en el módulo. Se utiliza como una ubicación inicial para buscar símbolos para un módulo.  
  
 m_dwModuleFlags  
 Una combinación de indicadores de la [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) enumeración que describe el módulo.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura se pasa a la [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) método donde se rellena.  
  
 Esta estructura corresponde a cada módulo mostrado en el **módulos** ventana.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)