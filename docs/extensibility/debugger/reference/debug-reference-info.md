---
title: DEBUG_REFERENCE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 330ed06d4993d8bbe8b8a889e8f052c8bc7e7049
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906727"
---
# <a name="debugreferenceinfo"></a>DEBUG_REFERENCE_INFO
Describe una referencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
  
```csharp  
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
  
## <a name="members"></a>Miembros  
 dwFields  
 Una combinación de marcas de la [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) enumeración que especifica qué campos se rellenan.  
  
 bstrName  
 El nombre especificado por el usuario de la [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto.  
  
 bstrType parámetro  
 El tipo de referencia como una cadena con formato.  
  
 bstrValue parámetro  
 El valor de referencia como una cadena con formato  
  
 dwAttrib  
 Una combinación de marcas de la [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) enumeración que especifica las marcas para los atributos de propiedad de depuración.  
  
 dwRefType  
 Un valor de la [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) enumeración que especifica si el tipo de referencia es fuerte o débil.  
  
 m_pReference  
 Un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que especifica la información de referencia.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura se pasa a una llamada a la [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) método que deben rellenarse. Esta estructura también se devuelve como parte de una lista de los [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) interfaz que, a su vez, se devuelve desde una llamada a la [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)