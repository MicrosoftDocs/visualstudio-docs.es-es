---
title: IDiaAddressMap::put_imageAlign | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e0fa57c38c8451bde84d96ab32bc7980c5e2d8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842667"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Establece la alineación de la imagen.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 NewVal  
 de Nuevo valor de alineación de imagen para el ejecutable.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Notas  
 Las imágenes (ejecutables cargados) se alinean con los límites de memoria especificados. Esta alineación puede verse afectada por la arquitectura actual del sistema y las opciones de tiempo de compilación y de vínculo. La alineación de la imagen siempre está en los límites de bytes. Los siguientes valores de alineación de imagen son válidos: 1, 2, 4, 8, 16, 32 y 64 bytes.  
  
 La alineación de la imagen actual se puede recuperar con una llamada al método [IDiaAddressMap:: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) .  
  
> [!NOTE]
> La imagen ya se ha cargado en el momento en que se puede llamar a este método. `put_imageAlign`Normalmente, el método se usa cuando la imagen se ha cambiado o se ha cambiado y se requiere una nueva alineación.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
