---
title: Método Iactivescriptprofilercontrol3 | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6120b8fdd913b4acee2e3ee6774d770aa75b1f5a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992967"
---
# <a name="iactivescriptprofilercontrol3enumheap-method"></a>IActiveScriptProfilerControl3::EnumHeap (Método)
Devuelve una interfaz ([IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) que puede utilizarse para recorrer en iteración los objetos del montón GC en el contexto del motor de script asociado.  
  
 Puede llamar a este método en la depuración o modo de lanzamiento. Este método debe llamarse al subproceso de interfaz de usuario está inactivo. Después de haber llamado al método, debe realizarse ninguna operación en el motor de scripts excepto [Iactivescriptprofilerheapenum método](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) hasta [Iactivescriptprofilerheapenum método](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)devuelve S_FALSE o [IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) se libera el puntero de interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parámetros  
 ppEnum  
 [out] Devuelve el [IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Valor devuelto  
 HRESULT.