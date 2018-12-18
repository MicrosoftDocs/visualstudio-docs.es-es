---
title: IActiveScriptProfilerHeapEnum (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4761e8c7d4cc9c3372c7906e1503b8dbd059ca33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724715"
---
# <a name="iactivescriptprofilerheapenum-interface"></a>IActiveScriptProfilerHeapEnum (Interfaz)
Un iterador en el montón de objetos asociados a un motor de scripts, recopilado por el [método iactivescriptprofilercontrol3:: Enumheap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## <a name="methods"></a>Métodos  
 [IActiveScriptProfilerHeapEnum::Next (Método)](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 Obtiene el siguiente objeto u objetos en el conjunto de objetos del montón recopilados por el [método iactivescriptprofilercontrol3:: Enumheap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [IActiveScriptProfilerHeapEnum::GetOptionalInfo (Método)](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 Obtiene información adicional en el objeto especificado en el conjunto de objetos del montón recopilados por el [método iactivescriptprofilercontrol3:: Enumheap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo (Método)](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 Libera especificado [PROFILER_HEAP_OBJECT (estructura)](../../winscript/reference/profiler-heap-object-structure.md) estructuras y sus asociados [PROFILER_HEAP_OBJECT_OPTIONAL_INFO (estructura)](../../winscript/reference/profiler-heap-object-optional-info-structure.md) elementos.  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 Devuelve los nombres de cadena correspondiente a [PROFILER_HEAP_OBJECT_NAME_ID (tipo)](../../winscript/reference/profiler-heap-object-name-id-type.md) valores...