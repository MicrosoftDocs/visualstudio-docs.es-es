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
ms.openlocfilehash: 14562654e0fd3f3567d6f598f84cf2c966b1b8cb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344894"
---
# <a name="iactivescriptprofilerheapenum-interface"></a>IActiveScriptProfilerHeapEnum (Interfaz)
Un iterador en el montón de objetos asociados con un motor de scripts, recopilado por el [Iactivescriptprofilercontrol3 método](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## <a name="methods"></a>Métodos  
 [IActiveScriptProfilerHeapEnum::Next (Método)](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 Obtiene el siguiente objeto u objetos en el conjunto de objetos de montón recopilados por el [Iactivescriptprofilercontrol3 método](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [IActiveScriptProfilerHeapEnum::GetOptionalInfo (Método)](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 Obtiene información opcional sobre el objeto especificado en el conjunto de objetos de montón recopilados por el [Iactivescriptprofilercontrol3 método](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo (Método)](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 Libera especificado [PROFILER_HEAP_OBJECT (estructura)](../../winscript/reference/profiler-heap-object-structure.md) estructuras y sus asociados [PROFILER_HEAP_OBJECT_OPTIONAL_INFO (estructura)](../../winscript/reference/profiler-heap-object-optional-info-structure.md) elementos.  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 Devuelve los nombres de cadena correspondiente a [PROFILER_HEAP_OBJECT_NAME_ID (tipo)](../../winscript/reference/profiler-heap-object-name-id-type.md) valores...