---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8523dfb795f63abdecd9be1f08ec68371355fbde
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759565"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera correspondiente para los nombres de cadena según identificadores de propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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



