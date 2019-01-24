---
title: IActiveScriptProfilerHeapEnum::GetNameIdMap | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 88514c93-850b-48d4-9a68-1e27d7411f0d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cdff1983524b9234d536a23378d300a0b815522d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092643"
---
# <a name="iactivescriptprofilerheapenumgetnameidmap"></a>IActiveScriptProfilerHeapEnum::GetNameIdMap
Devuelve los nombres de cadena correspondiente a [PROFILER_HEAP_OBJECT_NAME_ID (tipo)](../../winscript/reference/profiler-heap-object-name-id-type.md) valores.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetNameIdMap (    [out, size_is(,*pcelt)] LPCWSTR* pNameList[],     [out] UINT *pcelt);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pNameList`  
 [out] Una matriz de nombres asociado [PROFILER_HEAP_OBJECT_NAME_ID (tipo)](../../winscript/reference/profiler-heap-object-name-id-type.md) valores.  
  
 `pcelt`  
 [out] El número de nombres de la matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 HRESULT.