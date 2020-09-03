---
title: IDiaAddressMap::put_addressMapEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2f7fc6fd512fa121cf96cb64f4ce4b961772e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198682"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica si se debe usar el mapa de direcciones para traducir direcciones de símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 NewVal  
 de Establezca en `TRUE` para habilitar la traducción de símbolos o `FALSE` en deshabilitar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Los postprocesadores ejecutables a veces actualizan el archivo ejecutable. DIA contiene un mecanismo para admitir la traducción de símbolos al nuevo diseño.  
  
 Cuando se carga un archivo PDB, se habilita la asignación de direcciones almacenada en el archivo. Sin embargo, hay ocasiones en las que una aplicación cliente puede necesitar proporcionar su propio mapa de direcciones llamando al método [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Si el `set_addressMap` método es correcto, la aplicación cliente debe llamar al `put_addressMapEnabled` método con un `NewVal` parámetro de `TRUE` para habilitar el uso de ese mapa de direcciones.  
  
 Se puede recuperar el estado actual del mapa de direcciones que se está habilitando con una llamada al método [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .  
  
## <a name="see-also"></a>Consulte también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
