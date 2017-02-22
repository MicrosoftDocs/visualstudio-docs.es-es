---
title: "LocationType | Microsoft Docs"
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
  - "LocationType (enumeración)"
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# LocationType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Indica el tipo de información de ubicación contenida en uno.  
  
## Sintaxis  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## Elementos \(Elements\)  
 `LocIsNull`  
 La información de ubicación no está disponible.  
  
 `LocIsStatic`  
 la ubicación es estática.  
  
 `LocIsTLS`  
 La ubicación se encuentra en almacenamiento local de subprocesos.  
  
 `LocIsRegRel`  
 la ubicación es registro\-relativa.  
  
 `LocIsThisRel`  
 La ubicación es `this`\- relativa.  
  
 `LocIsEnregistered`  
 La ubicación se encuentra en un registro.  
  
 `LocIsBitField`  
 La ubicación se encuentra en un campo de bits.  
  
 `LocIsSlot`  
 La ubicación es una entrada de Lenguaje intermedio de Microsoft \(MSIL\).  
  
 `LocIsIlRel`  
 la ubicación es MSIL\-relativa.  
  
 `LocInMetaData`  
 La ubicación se encuentra en metadatos.  
  
 `LocIsConstant`  
 La ubicación se encuentra en un valor constante.  
  
 `LocTypeMax`  
 El número de tipos de la ubicación de esta enumeración.  
  
## Comentarios  
 Las propiedades disponibles en la interfaz de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) dependen de la ubicación del símbolo en el archivo de imagen.  Para obtener más información, vea [Symbol Locations](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Los valores de esta enumeración son devueltos por una llamada al método de [IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .  
  
## Requisitos  
 encabezado: cvconst.h  
  
## Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Symbol Locations](../../debugger/debug-interface-access/symbol-locations.md)