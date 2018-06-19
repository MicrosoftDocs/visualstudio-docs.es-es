---
title: 'Iactivescriptprofilercontrol5:: Enumheap2 (método) | Documentos de Microsoft'
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
ms.openlocfilehash: 5c493acdb2843877c506d9d84e145a79ac2d60d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724665"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2 (Método)
Devuelve una interfaz ([IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) que se puede utilizar para recorrer en iteración los objetos de montón del GC en el contexto del motor de script asociado.  
  
 Puede llamar a este método en cualquier depuración o modo de lanzamiento. Este método debe llamarse al subproceso de interfaz de usuario está inactivo. Después de haber llamado al método, no hay ninguna operación debería realizarse con el motor de secuencia de comandos excepto [IActiveScriptProfilerHeapEnum::Next método](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) hasta [IActiveScriptProfilerHeapEnum::Next método](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)devuelva S_FALSE o [IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) se libera el puntero de interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parámetros  
 enumFlags  
 Valor que especifica si se expone información adicional sobre un objeto que se apunta en una relación de objeto. Información adicional puede indicar si el objeto al que señala es un método de captador o un establecedor. Para obtener más información, consulte [PROFILER_HEAP_ENUM_FLAGS (enumeración)](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Devuelve el [IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor HRESULT. Los valores posibles son los siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|La enumeración de montón que se completó correctamente.|  
|`E_OUTOFMEMORY`|No había memoria suficiente realizar la enumeración del montón.|  
|`E_FAIL`|Se produjo un error interno.|