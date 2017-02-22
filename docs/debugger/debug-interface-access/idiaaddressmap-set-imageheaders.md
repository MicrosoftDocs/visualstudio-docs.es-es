---
title: "IDiaAddressMap::set_imageHeaders | Microsoft Docs"
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
  - "IDiaAddressMap::set_imageHeaders (método)"
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

establece encabezados de imagen para habilitar la traducción relativa de la dirección virtual.  
  
## Sintaxis  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### Parámetros  
 cbData  
 \[in\]  Número de bytes de datos del encabezado.  Debe ser `n*sizeof(IMAGE_SECTION_HEADER)` donde es el número `n` de encabezados de sección en el ejecutable.  
  
 datos \[\]  
 \[in\]  Una matriz de estructuras de `IMAGE_SECTION_HEADER` que se utilizarán como los encabezados de imagen.  
  
 originalHeaders  
 \[in\]  Establezca en `FALSE` si los encabezados de imagen son de la nueva imagen, `TRUE` si reflejan la imagen original antes de una actualización.  Normalmente, esto se establecería a `TRUE` solo junto con llamadas al método de [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 La estructura de `IMAGE_SECTION_HEADER` se declara en Winnt.h y representa el formato del encabezado de la sección de la imagen del ejecutable.  
  
 los cálculos de dirección virtual relativos dependen de los valores de `IMAGE_SECTION_HEADER` .  Normalmente, el diámetro recupera estos del archivo de base de datos de programa \(.pdb\).  Si faltan estos valores, el diámetro no puede calcular direcciones virtuales relativas y el método de [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) devuelve `FALSE`.  El cliente debe llamar al método de [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) para habilitar los cálculos de dirección virtual relativos después de proporcionar los encabezados de imagen que falta de la imagen propio.  
  
## Vea también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)