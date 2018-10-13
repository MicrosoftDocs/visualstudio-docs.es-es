---
title: Put_relativevirtualaddressenabled | Microsoft Docs
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
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7eec1adc7ce13fa1ffb454e9a5d1b6fbd830bff4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214661"
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Permite al cliente habilitar o deshabilitar el cálculo y el uso de direcciones virtuales relativas (RVA).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)



