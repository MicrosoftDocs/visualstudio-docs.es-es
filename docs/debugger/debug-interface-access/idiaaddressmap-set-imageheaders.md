---
title: 'Idiaaddressmap:: Set_imageheaders | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 74556e2e67478cef9b495d3740dc910b62cc8293
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
 [in] Número de bytes de datos de encabezado. Debe ser `n*sizeof(IMAGE_SECTION_HEADER)` donde `n` es el número de encabezados de la sección del archivo ejecutable.  
  
 datos]  
 [in] Una matriz de `IMAGE_SECTION_HEADER` estructuras que se usará como los encabezados de la imagen.  
  
 originalHeaders  
 [in] Establecido en `FALSE` si los encabezados de la imagen se corresponden con la nueva imagen, `TRUE` si reflejan la imagen original antes de realizar una actualización. Normalmente, esto se establecería en `TRUE` sólo en combinación con llamadas a la [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) método.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El `IMAGE_SECTION_HEADER` estructura se declara en Winnt.h y representa el formato de encabezado de sección de imagen del archivo ejecutable.  
  
 Cálculos de dirección virtual relativa dependen el `IMAGE_SECTION_HEADER` valores. Normalmente, el DIA recupera desde el archivo de programa (.pdb) de la base de datos. Si faltan estos valores, el DIA es no se puede calcular direcciones virtuales relativas y el [idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) método `FALSE`. El cliente, a continuación, debe llamar a la [idiaaddressmap:: Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) método para permitir a los cálculos de dirección virtual relativa después de proporcionar los encabezados que faltan de la imagen de la propia imagen.  
  
## <a name="see-also"></a>Vea también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [Idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)