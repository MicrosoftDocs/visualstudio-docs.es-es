---
title: IDiaPropertyStorage::ReadPropertyNames | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: a13ac0e3a1af8dc20fe63f832e7a19d7bf40c271
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465582"
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