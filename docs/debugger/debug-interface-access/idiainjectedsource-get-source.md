---
title: 'Idiainjectedsource:: Get_source | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9d3019d7a2a36f032f4c1e68fa1e60adbe2fede
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
Recupera los bytes de código de origen.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cbData`  
 [in] El número de bytes que representa el tamaño del búfer de datos.  
  
 `pcbData`  
 [out] Devuelve el número de bytes que representa los bytes devueltos. Si `data` es `NULL`, a continuación, `pcbData` es el número total de bytes de datos disponibles.  
  
 `data[]`  
 [out] Búfer que va a rellenar con los bytes de origen.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)