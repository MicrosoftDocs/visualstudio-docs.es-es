---
title: 'Idiaaddressmap:: Put_imagealign | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c40e2f325ac30eb109f72615e5cc74a5d30e5eba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
Establece la alineación de la imagen.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 NewVal  
 [in] El nuevo valor de alineación de imagen para el ejecutable.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Imágenes (cargar archivos ejecutables) se alinean con los límites de memoria especificada. Esta alineación puede verse afectada por la arquitectura del sistema actual y por las opciones de tiempo de compilación y vinculación. Alineación de la imagen está siempre en límites de bytes. Los valores de alineación de imagen siguientes son válidos: los límites de 1, 2, 4, 8, 16, 32 y 64 bytes.  
  
 Alineación de la imagen actual se puede recuperar con una llamada a la [idiaaddressmap:: Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) método.  
  
> [!NOTE]
>  La imagen ya está cargada por el tiempo que se puede llamar a este método. El `put_imageAlign` método suele usarse cuando la imagen se han movido o se ha cambiado y se requiere una alineación nuevo.  
  
## <a name="see-also"></a>Vea también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)