---
title: "IDiaPropertyStorage::ReadMultiple | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaPropertyStorage::ReadMultiple"
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lee especificado las propiedades del conjunto actual de la propiedad.  
  
## Sintaxis  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### Parámetros  
 `cpspec`  
 \[in\]  Recuento de propiedades especificadas en la matriz de `rgpspec` .  si cero, el método no devuelve ninguna propiedad pero devuelve `S_OK` como código correcto.  
  
 `rgpspec`  
 \[in\]  Una matriz de propiedades que se va a leer.  Las propiedades se pueden especificar mediante un identificador de propiedad o por un nombre de cadena opcional.  No es necesario especificar propiedades en ningún orden determinado de la matriz.  La matriz puede contener propiedades duplicadas, lo que da como resultado valores de propiedad duplicados en return para propiedades simples.  las propiedades No\-simples deben devolver el acceso denegado en un intento de abrirlos una segunda vez.  La matriz puede contener una combinación de id. de la propiedad e id. de la cadena.  Esta matriz debe tener al menor número de `cpspec` de valores de propiedad.  
  
 `rgvar`  
 \[in, out\]  Una matriz de estructuras de `PROPVARIANT` \(en el espacio de nombres Microsoft.VisualStudio.OLE.Interop\) que se completan con los valores de cada propiedad.  La matriz debe ser por lo menos elementos de `cpspec` de tamaño.  El llamador no necesita inicializar los valores de la matriz.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  Devuelve `S_FALSE` si uno o más de las propiedades no se encontraron.  si no devuelve un código de error.  
  
## Comentarios  
 Si una propiedad no se encuentra, la entrada correspondiente en la matriz de `rgvar` contiene `VARIANT` con el tipo de `VT_EMPTY`.  
  
## Vea también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)