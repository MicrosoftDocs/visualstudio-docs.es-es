---
title: Método Iactivescriptprofilerheapenum | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0336286f-1dcd-4df9-adf5-76b59b4e74bb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1f8d709c98efba8551ffdd026b77234785c8de4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095737"
---
# <a name="iactivescriptprofilerheapenumnext-method"></a>IActiveScriptProfilerHeapEnum::Next Method
Obtiene el siguiente objeto u objetos en el conjunto de objetos del montón desde el [Iactivescriptprofilercontrol3 método](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Next (    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] PROFILER_HEAP_OBJECT** heapObjects,     [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 El número de objetos que se devolverán.  
  
 `heapObjects`  
 [out] La siguiente [PROFILER_HEAP_OBJECT (estructura)](../../winscript/reference/profiler-heap-object-structure.md) estructuras.  
  
 `pceltFetched`  
 [out] El número de objetos devueltos,  
  
## <a name="return-value"></a>Valor devuelto  
 HRESULT.