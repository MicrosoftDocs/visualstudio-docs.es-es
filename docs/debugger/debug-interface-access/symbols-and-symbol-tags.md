---
title: "S&#237;mbolos y etiquetas de s&#237;mbolo | Microsoft Docs"
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
  - "símbolos [Kit de desarrollo DIA (SDK)]"
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# S&#237;mbolos y etiquetas de s&#237;mbolo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La información de depuración sobre un programa compilado se almacena en el archivo de base de datos de programa \(.pdb\) como símbolos que sean accesibles mediante la interfaz Access \(DIA\) SDK API de depuración.  todos los símbolos tienen [IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) y una propiedad de [IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) .  La propiedad de `symTag` indica el tipo de símbolo como definidos por la enumeración de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) .  la propiedad de `symIndexId` es un valor de `DWORD` que contiene el identificador único para cada instancia de un símbolo.  
  
 Los símbolos también tienen propiedades que pueden especificar información adicional sobre el símbolo así como referencias a otros símbolos, con más frecuencia [IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) o [IDiaSymbol::get\_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md).  Cuando se consulta una propiedad que contiene una referencia, la referencia se devuelve como un objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) .  Tales propiedades están emparejadas con otra propiedad por el mismo nombre pero añadidas como sufijo siempre con “id.”, por ejemplo, [IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) y [IDiaSymbol::get\_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md).  Las tablas del esquema de [Symbol Locations](../../debugger/debug-interface-access/symbol-locations.md), de [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), y de [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) las propiedades para cada uno de los tipos diferentes de símbolos.  Estas propiedades pueden tener información relevante sobre o referencias a otros símbolos.  Dado que las propiedades de `*Id` son identificadores ordinales simplemente numéricos de sus propiedades relacionadas, se omiten en otras conversaciones.  Se conocen sólo cuando necesario para la aclaración del parámetro.  
  
 Al intentar tener acceso a la propiedad, si no se produce ningún error y la propiedad de símbolos se ha asignado un valor, la propiedad “get” método devuelve `S_OK`.  Un valor devuelto de `S_FALSE` indica que la propiedad no es válida para el símbolo actual.  
  
## En esta sección  
 [Symbol Locations](../../debugger/debug-interface-access/symbol-locations.md)  
 Describe los distintos tipos de ubicaciones que un token puede tener.  
  
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Describe los tipos de símbolos que forman jerarquías léxicas como archivos, módulos, y funciones.  
  
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Describe los tipos de token que corresponden a los elementos de idioma como clases, matrices, y tipos de valor devuelto de la función.  
  
## Vea también  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)