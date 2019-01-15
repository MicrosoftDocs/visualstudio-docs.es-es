---
title: Get_addressmapenabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc632a0eda039c5f3268d2007f45d7cddd096baa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896661"
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Indica si se ha establecido un mapa de direcciones para una sesión determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pRetVal  
 [out] Devuelve `TRUE` si está habilitada la asignación de dirección.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Ejecutable procesadores posterior a la actualización a veces el archivo ejecutable. DIA contiene un mecanismo para admitir la traducción de símbolos para el nuevo diseño.  
  
 Las aplicaciones cliente pueden establecer la asignación de dirección para una sesión determinada mediante la obtención de la [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) interfaz desde el [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interfaz y una llamada a la [IDiaAddressMap::set_ addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) método seguido por una llamada a la [Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) método. El `get_addressMapEnabled` método devuelve los resultados de llamar a la `put_addressMapEnabled` método.  
  
## <a name="see-also"></a>Vea también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)