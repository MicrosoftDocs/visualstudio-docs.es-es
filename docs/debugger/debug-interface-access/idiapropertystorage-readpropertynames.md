---
title: IDiaPropertyStorage::ReadPropertyNames | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1624e3577128556a098f96fd41c9ba1dc1eb84e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Recupera correspondiente para los nombres de cadena tiene identificadores de propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cpropid`  
 [in] Número de identificadores de propiedad en `rgpropid`.  
  
 `rgpropid`  
 [in] Matriz de identificadores de propiedad para la que se va a obtener los nombres (`PROPID` se define en el archivo WTypes.h como un `ULONG`).  
  
 `rglpwstrName`  
 [entrada, salida] Matriz de nombres de propiedad para los identificadores de propiedad especificado. La matriz debe estar previamente asignada para contener el número solicitado de nombres de propiedad y debe ser capaz de contener por lo menos `cpropid``BSTR` cadenas.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Los nombres de propiedad devuelto deben ser liberados (mediante una llamada a la `SysFreeString` función) cuando ya no se necesitan.  
  
## <a name="see-also"></a>Vea también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)