---
title: Get_addressmapenabled | Microsoft Docs
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
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 385542d16cebc389175d9c61d32a44992979ccc4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207654"
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indica si se ha establecido un mapa de direcciones para una sesión determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)



