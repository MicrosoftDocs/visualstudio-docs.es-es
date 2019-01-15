---
title: Set_imageheaders | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6593092fc155a375480f082a1f82dc53a1d851fa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834144"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
Conjuntos de encabezados para habilitar la traducción de dirección virtual relativa de la imagen.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 cbData  
 [in] Número de bytes de datos de encabezado. Debe ser `n*sizeof(IMAGE_SECTION_HEADER)` donde `n` es el número de encabezados de sección en el archivo ejecutable.  
  
 data[]  
 [in] Una matriz de `IMAGE_SECTION_HEADER` estructuras que se usará como los encabezados de la imagen.  
  
 originalHeaders  
 [in] Establecido en `FALSE` si los encabezados de la imagen son de la nueva imagen, `TRUE` si reflejan la imagen original antes de una actualización. Normalmente, esto se establecería en `TRUE` sólo en combinación con llamadas a la [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) método.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El `IMAGE_SECTION_HEADER` estructura se declara en Winnt.h y representa el formato de encabezado de sección de imagen del archivo ejecutable.  
  
 Dependen de los cálculos de dirección virtual relativa del `IMAGE_SECTION_HEADER` valores. Normalmente, el DIA recupera desde el archivo de programa (.pdb) de la base de datos. Si faltan estos valores, el DIA no puede calcular direcciones virtuales relativas y el [Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) devuelve del método `FALSE`. El cliente, a continuación, debe llamar a la [Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) método para habilitar los cálculos de dirección virtual relativa después de proporcionar los encabezados que faltan de la imagen de la propia imagen.  
  
## <a name="see-also"></a>Vea también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)