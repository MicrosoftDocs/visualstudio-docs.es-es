---
title: IDiaPropertyStorage::ReadPropertyNames | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 95f535bd314ec998c83ec9c02aab2190646f3c53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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