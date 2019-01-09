---
title: PROFILER_HEAP_OBJECT_FLAGS (enumeración) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0f517743-cc4a-4911-add3-a43680071a1f
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 833f3d100b2529ca4f356b50cddad6b6501297ce
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097492"
---
# <a name="profilerheapobjectflags-enumeration"></a>PROFILER_HEAP_OBJECT_FLAGS (Enumeración)
Marcas que representan información básica sobre el objeto de montón. Utilizado en el [PROFILER_HEAP_OBJECT (estructura)](../../winscript/reference/profiler-heap-object-structure.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT            = 0x00000001,    PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT               = 0x00000002,    PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED           = 0x00000004,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL              = 0x00000008,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN      = 0x00000010,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH     = 0x00000020,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE      = 0x00000040,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE      = 0x00000080,    PROFILER_HEAP_OBJECT_FLAGS_NEW_STATE_UNAVAILABLE = 0x00000100,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE        = 0x00000200,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS    = 0x00000400,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE        = 0x00000800,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE       = 0x00001000,} PROFILER_HEAP_OBJECT_FLAGS;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT|0x00000001|Se ha asignado este objeto de pila después de la solicitud anterior de enumeración de montón. [PROFILER_HEAP_OBJECT_ID (tipo)](../../winscript/reference/profiler-heap-object-id-type.md) valores se pueden reutilizar si el objeto se recopila.|  
|PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT|0x00000002|Este objeto de pila es un objeto raíz del gráfico de objetos.|  
|PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED|0x00000004|Este objeto de pila es de un sitio de script que se ha cerrado.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL|0x00000008|Este objeto de pila se asignó fuera del montón de colección de elementos no utilizados de JavaScript.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN|0x00000010|Este objeto de pila se asignó fuera del montón de la colección de elementos no utilizados y la implementa IUnknown.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH|0x00000020|Este objeto de pila se ha asignado fuera del montón de la colección de elementos no utilizados e implementa la interfaz IDISPATCH.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE|0x00000040|El tamaño de este objeto de pila es aproximado.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE|x00000080|El tamaño de este objeto de pila no está disponible.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE|0x00000200|El objeto de montón es una instancia de Windows en tiempo de ejecución.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS|0x00000400|El objeto de montón es una clase en tiempo de ejecución de Windows en tiempo de ejecución.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE|0x00000800|El objeto de montón es un delegado de Windows en tiempo de ejecución.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE|0x00001000|El objeto de montón está en el espacio de nombres de Windows en tiempo de ejecución.|