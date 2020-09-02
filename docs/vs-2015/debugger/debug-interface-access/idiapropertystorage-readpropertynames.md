---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537425"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera los nombres de cadena correspondientes para los identificadores de propiedad especificados.  
  
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
 de Número de identificadores de propiedad en `rgpropid` .  
  
 `rgpropid`  
 de Matriz de identificadores de propiedad para los que se van a obtener los nombres ( `PROPID` se define en WTypes. h como un `ULONG` ).  
  
 `rglpwstrName`  
 [in, out] Matriz de nombres de propiedad para los identificadores de propiedad especificados. La matriz debe estar asignada previamente para contener el número solicitado de nombres de propiedad y debe poder contener al menos `cpropid``BSTR` cadenas.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Los nombres de propiedad devueltos deben liberarse (llamando a la `SysFreeString` función) cuando ya no se necesiten.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
