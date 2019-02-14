---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce8861341f7eb568c9a886b5d0cadd2159674cb7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924787"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Recupera correspondiente para los nombres de cadena según identificadores de propiedad.  
  
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
 [in] Matriz de identificadores de propiedad que se va a obtener los nombres (`PROPID` se define en el archivo WTypes.h como un `ULONG`).  
  
 `rglpwstrName`  
 [in, out] Matriz de nombres de propiedad para los identificadores de propiedad especificado. La matriz debe estar previamente asignada para contener el número solicitado de nombres de propiedad y debe ser capaz de contener al menos `cpropid``BSTR` cadenas.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Los nombres de propiedad devuelta deben ser liberados (mediante una llamada a la `SysFreeString` función) cuando ya no son necesarios.  
  
## <a name="see-also"></a>Vea también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)