---
title: Método Iactivescriptprofilerheapenum | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcba1214a0c57e738dec41cdc4976f478802fedc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088808"
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>IActiveScriptProfilerHeapEnum::GetOptionalInfo (Método)
Obtiene información opcional sobre el objeto especificado (en el conjunto de objetos de montón devueltos desde el [Iactivescriptprofilercontrol3 método](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)).  
  
 No debe liberar la memoria asignada devuelta a los objetos devueltos. En su lugar, debe llamar a la [Iactivescriptprofilerheapenum método](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetOptionalInfo (    [in] PROFILER_HEAP_OBJECT* heapObject,    [in] ULONG celt,    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `heapObject`  
 El [PROFILER_HEAP_OBJECT (estructura)](../../winscript/reference/profiler-heap-object-structure.md) para que se va a devolver la información.  
  
 `celt`  
 El número de [PROFILER_HEAP_OBJECT_OPTIONAL_INFO (estructura)](../../winscript/reference/profiler-heap-object-optional-info-structure.md) estructuras para devolver.  
  
 `optionalInfo`  
 [out] Una matriz de [PROFILER_HEAP_OBJECT_OPTIONAL_INFO (estructura)](../../winscript/reference/profiler-heap-object-optional-info-structure.md) estructuras para el objeto especificado.  
  
## <a name="return-value"></a>Valor devuelto  
 HRESULT.