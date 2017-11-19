---
title: BP_RESOLUTION_DATA | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_RESOLUTION_DATA
helpviewer_keywords: BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 501418785547a3133305c612f5bd69dc0a118f29
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="bpresolutiondata"></a>BP_RESOLUTION_DATA
Describe el resultado de enlazar un punto de interrupción de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _BP_RESOLUTION_DATA {   
   BSTR              bstrDataExpr;  
   BSTR              bstrFunc;  
   BSTR              bstrImage;  
   BP_RES_DATA_FLAGS dwFlags;  
} BP_RESOLUTION_DATA;  
```  
  
```csharp  
public struct BP_RESOLUTION_DATA {   
   public string bstrDataExpr;  
   public string bstrFunc;  
   public string bstrImage;  
   public uint   dwFlags;  
};  
```  
  
## <a name="members"></a>Miembros  
 `bstrDataExpr`  
 La expresión de datos que se ha enlazado.  
  
 `bstrFunc`  
 El nombre de la función (si existe) se enlaza el punto de interrupción de datos en.  
  
 `bstrImage`  
 El nombre del módulo (archivo MyModule.dll, por ejemplo) que se enlaza el punto de interrupción de datos en.  
  
 `dwFlags`  
 Un valor de la [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) enumeración, que describe cómo se implementa el punto de interrupción de datos.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es un miembro de la [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) estructura, que se activa en un miembro de la [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) estructura devuelta por la [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)(método).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)