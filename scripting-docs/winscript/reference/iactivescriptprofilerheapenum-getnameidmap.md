---
title: IActiveScriptProfilerHeapEnum::GetNameIdMap | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 88514c93-850b-48d4-9a68-1e27d7411f0d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0761517236fbcc05655365d77ce2990e9d1c566
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilerheapenumgetnameidmap"></a>IActiveScriptProfilerHeapEnum::GetNameIdMap
Devuelve los nombres de cadena correspondiente a [PROFILER_HEAP_OBJECT_NAME_ID (tipo)](../../winscript/reference/profiler-heap-object-name-id-type.md) valores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetNameIdMap (    [out, size_is(,*pcelt)] LPCWSTR* pNameList[],     [out] UINT *pcelt);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pNameList`  
 [out] Una matriz de nombres asociados a [PROFILER_HEAP_OBJECT_NAME_ID (tipo)](../../winscript/reference/profiler-heap-object-name-id-type.md) valores.  
  
 `pcelt`  
 [out] El número de nombres de la matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 HRESULT.