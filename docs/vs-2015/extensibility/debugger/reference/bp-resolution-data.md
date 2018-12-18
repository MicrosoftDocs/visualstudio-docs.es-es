---
title: BP_RESOLUTION_DATA | Microsoft Docs
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
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02d64bd1fcef350fba50832168a6c5d2e41144d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771563"
---
# <a name="bpresolutiondata"></a>BP_RESOLUTION_DATA
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Describe el resultado de un punto de interrupción de datos de enlace.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 El nombre de la función ha enlazado el punto de interrupción de datos en (si existe).  
  
 `bstrImage`  
 El nombre del módulo (por ejemplo, MyModule.dll) en el punto de interrupción de datos enlazado.  
  
 `dwFlags`  
 Un valor de la [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) enumeración, que describe cómo se implementa el punto de interrupción de datos.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es un miembro de la [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) estructura, que se activa en un miembro de la [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) estructura devuelta por la [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)

