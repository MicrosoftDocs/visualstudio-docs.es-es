---
title: BP_LOCATION_CODE_FILE_LINE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c4c114919d74fba7a28c9d3ea11fc5bb9947d6a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866030"
---
# <a name="bplocationcodefileline"></a>BP_LOCATION_CODE_FILE_LINE
Contiene los datos para la ubicación de un punto de interrupción en una línea específica en un archivo de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _BP_LOCATION_CODE_FILE_LINE {   
   BSTR                     bstrContext;  
   IDebugDocumentPosition2* pDocPos;  
} BP_LOCATION_CODE_FILE_LINE;  
```  
  
## <a name="members"></a>Miembros  
 `bstrContext`  
 El contexto del punto de interrupción, normalmente un nombre de método o una función como se muestra en una pila de llamadas.  
  
 `pDocPos`  
 El [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) objeto que representa la posición del documento del punto de interrupción.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es un miembro de la [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) estructura como parte de una unión.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)