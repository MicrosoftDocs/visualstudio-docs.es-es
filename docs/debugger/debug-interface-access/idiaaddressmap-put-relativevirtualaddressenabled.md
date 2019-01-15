---
title: Put_relativevirtualaddressenabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6a973c5ba66dbe63cf0c9751effbfd73c45b5b29
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963339"
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Permite al cliente habilitar o deshabilitar el cálculo y el uso de direcciones virtuales relativas (RVA).  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 NewVal  
 [in] Establecido en `TRUE` para habilitar, o `FALSE` a deshabilitar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Las direcciones para los objetos de depuración que se describen las interfaces de DIA y en relación con la imagen del archivo ejecutable base, se pueden recuperar como direcciones virtuales relativas.  
  
 El uso de RVA está habilitado cuando segmentos inicialmente se cargan desde un archivo PDB. Para obtener el estado actual del uso de RVA, llame a la [Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) método.  
  
 El `put_relativeVirtualAddress` método debe llamarse para habilitar RVA después de una llamada correcta a la [Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) método estableció nuevos encabezados de la imagen.  
  
## <a name="see-also"></a>Vea también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)