---
title: BP_LOCATION_CODE_FILE_LINE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29fbb041a90118e7725ed3140e6583c7ac756a07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153467"
---
# <a name="bp_location_code_file_line"></a>BP_LOCATION_CODE_FILE_LINE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Contiene los datos de la ubicación de un punto de interrupción en una línea específica de un archivo de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_FILE_LINE {   
   BSTR                     bstrContext;  
   IDebugDocumentPosition2* pDocPos;  
} BP_LOCATION_CODE_FILE_LINE;  
```  
  
## <a name="members"></a>Miembros  
 `bstrContext`  
 Contexto del punto de interrupción, normalmente un nombre de método o función tal y como se ha detectado en una pila de llamadas.  
  
 `pDocPos`  
 El objeto [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) que representa la posición del documento del punto de interrupción.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es miembro de la estructura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una Unión.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
