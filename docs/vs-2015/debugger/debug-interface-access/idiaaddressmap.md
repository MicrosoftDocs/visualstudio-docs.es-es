---
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 012d6b1ca06b06f56239048fee712d898a79efa9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547512"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proporciona control sobre cómo el SDK de DIA calcula las direcciones virtuales virtuales y relativas para los objetos de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDiaAddressMap` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Indica si se ha establecido un mapa de direcciones para una sesión determinada.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Especifica si se debe usar el mapa de direcciones para traducir direcciones de símbolos.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Indica si el cálculo y el uso de direcciones virtuales relativas están habilitadas.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Permite al cliente habilitar o deshabilitar el cálculo de direcciones virtuales relativas.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Recupera la alineación de la imagen actual.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Establece la alineación de la imagen.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Establece los encabezados de la imagen para habilitar la traducción de direcciones virtuales relativas.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Proporciona un mapa de direcciones para admitir las traducciones del diseño de la imagen.|  
  
## <a name="remarks"></a>Comentarios  
 El control proporcionado por esta interfaz se encapsula en dos conjuntos de datos que se proporcionan: encabezados de imagen y mapas de direcciones. La mayoría de los clientes usan el método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) para encontrar la información de depuración adecuada para una imagen y el método normalmente puede detectar todos los encabezados necesarios y asigna los datos en sí. Sin embargo, algunos clientes implementan el procesamiento especializado y buscan datos. Estos clientes usan los métodos de la `IDiaAddressMap` interfaz para proporcionar el SDK de dia con los resultados de la búsqueda.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Esta interfaz está disponible desde el objeto de sesión DIA. El cliente llama al `QueryInterface` método en la interfaz de objeto de sesión dia, normalmente [IDiaSession](../../debugger/debug-interface-access/idiasession.md), para recuperar la `IDiaAddressMap` interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2. h  
  
 Biblioteca: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
