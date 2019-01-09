---
title: Método IActiveScriptProfilerControl5::EnumHeap2 | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21661953edbdba2314b88aad5fb55451b06b51a8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097635"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2 (Método)
Devuelve una interfaz ([IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) que puede utilizarse para recorrer en iteración los objetos del montón GC en el contexto del motor de script asociado.  
  
 Puede llamar a este método en la depuración o modo de lanzamiento. Este método debe llamarse al subproceso de interfaz de usuario está inactivo. Después de haber llamado al método, debe realizarse ninguna operación en el motor de scripts excepto [Iactivescriptprofilerheapenum método](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) hasta [Iactivescriptprofilerheapenum método](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)devuelve S_FALSE o [IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) se libera el puntero de interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parámetros  
 enumFlags  
 Valor que especifica si se expone información adicional sobre un objeto designado en una relación de objeto. Información adicional puede indicar si el objeto al que señala es un método de captador o establecedor. Para obtener más información, consulte [PROFILER_HEAP_ENUM_FLAGS (enumeración)](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Devuelve el [IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor HRESULT. Los valores posibles son los siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|La enumeración de montón que se completó correctamente.|  
|`E_OUTOFMEMORY`|No había suficiente memoria disponible para realizar la enumeración del montón.|  
|`E_FAIL`|Se ha producido un error interno.|