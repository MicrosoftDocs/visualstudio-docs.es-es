---
title: "Iactivescriptprofilercontrol3:: Enumheap (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d6fc79a9d6d35e35181c3505e07af2d9a1962c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol3enumheap-method"></a>IActiveScriptProfilerControl3::EnumHeap (Método)
Devuelve una interfaz ([IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) que se puede utilizar para recorrer en iteración los objetos de montón del GC en el contexto del motor de script asociado.  
  
 Puede llamar a este método en cualquier depuración o modo de lanzamiento. Este método debe llamarse al subproceso de interfaz de usuario está inactivo. Después de haber llamado al método, no hay ninguna operación debería realizarse con el motor de secuencia de comandos excepto [IActiveScriptProfilerHeapEnum::Next método](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) hasta [IActiveScriptProfilerHeapEnum::Next método](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)devuelva S_FALSE o [IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) se libera el puntero de interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parámetros  
 ppEnum  
 [out] Devuelve el [IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Valor devuelto  
 HRESULT.