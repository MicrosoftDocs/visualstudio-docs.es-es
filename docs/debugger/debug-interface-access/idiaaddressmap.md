---
title: "IDiaAddressMap | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaAddressMap (interfaz)"
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Proporciona control sobre cómo el diámetro SDK calcula las direcciones virtuales y relativas para los objetos de depuración.  
  
## Sintaxis  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDiaAddressMap`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaAddressMap::get\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Indica si la configuración de direcciones se ha establecido para una sesión determinada.|  
|[IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Especifica si la configuración de direcciones se debe utilizar para traducir a direcciones de símbolos.|  
|[IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|indica si el cálculo y el uso de direcciones virtuales relativas está habilitado.|  
|[IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|permite que el cliente habilite o deshabilite el cálculo de direcciones virtuales relativas.|  
|[IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|recupera la alineación actual de la imagen.|  
|[IDiaAddressMap::put\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|establece la alineación de la imagen.|  
|[IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|establece encabezados de imagen para habilitar la traducción de direcciones virtuales relativas.|  
|[IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Proporciona una configuración de direcciones las traducciones admiten el diseño de la imagen.|  
  
## Comentarios  
 El control proporcionado por esta interfaz se encapsula en dos conjuntos de datos que se proporciona: encabezados de imagen y configuraciones de direcciones.  La mayoría de los clientes utilizan el método de [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) para buscar información de depuración correcta para una imagen y el método puede detectar normalmente todos los encabezados y datos de mapas necesarios propio.  Sin embargo la implementación de algunos clientes especializado el procesamiento y buscar los datos.  tales clientes utilizan los métodos de la interfaz de `IDiaAddressMap` para proporcionar el diámetro SDK con los resultados de la búsqueda.  
  
## Notas para los llamadores  
 Esta interfaz está disponible el objeto de sesión del diámetro.  El cliente llama al método de `QueryInterface` en la interfaz del objeto de sesión del diámetro, normalmente [IDiaSession](../../debugger/debug-interface-access/idiasession.md), para recuperar la interfaz de `IDiaAddressMap` .  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)