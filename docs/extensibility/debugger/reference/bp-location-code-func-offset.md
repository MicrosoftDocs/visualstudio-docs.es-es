---
title: BP_LOCATION_CODE_FUNC_OFFSET | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords: BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ccaf1b9c4aee385f26000bb6a397f32984dfe1a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="bplocationcodefuncoffset"></a>BP_LOCATION_CODE_FUNC_OFFSET
Describe la ubicación de desplazamiento de un punto de interrupción en una función en el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {   
   BSTR                     bstrContext;  
   IDebugFunctionPosition2* pFuncPos;  
} BP_LOCATION_CODE_FUNC_OFFSET;  
```  
  
## <a name="members"></a>Miembros  
 `bstrContext`  
 El contexto del punto de interrupción, normalmente un nombre de método o una función como se ve en una pila de llamadas.  
  
 `pFuncPos`  
 El [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) objeto que describe el nombre de la función y la posición relativa desde el principio de la función.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es un miembro de la [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) estructura como parte de una unión.  
  
 El `pFuncPos` miembro indica dónde se establecerá el punto de interrupción de función.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)