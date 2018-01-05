---
title: 'Idiaaddressmap:: Put_relativevirtualaddressenabled | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2bfaf90afcd2129379d1ce7ae3f2d8afb619ca1e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Direcciones de los objetos de depuración descritos por interfaces DIA y en relación con la imagen del archivo ejecutable base, se pueden recuperar como direcciones virtuales relativas.  
  
 El uso de RVA se habilita cuando segmentos inicialmente se cargan desde un archivo PDB. Para obtener el estado actual del uso de RVA, llame a la [idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) método.  
  
 El `put_relativeVirtualAddress` método debe llamarse para habilitar RVA después de una llamada correcta a la [idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) método estableció nuevos encabezados de imagen.  
  
## <a name="see-also"></a>Vea también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)