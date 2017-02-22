---
title: "NameSearchOptions | Microsoft Docs"
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
  - "NameSearchOptions (enumeración)"
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# NameSearchOptions
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica las opciones de búsqueda para el símbolo y los nombres de archivo.  
  
## Sintaxis  
  
```cpp#  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## Elementos \(Elements\)  
 `nsNone`  
 No se especifican opciones.  
  
 `nsfCaseSensitive`  
 Aplica una coincidencia de mayúsculas y minúsculas del nombre.  
  
 `nsfCaseInsensitive`  
 Aplica una coincidencia sin distinción entre mayúsculas y minúsculas del nombre.  
  
 `nsfFNameExt`  
 Trata nombres como rutas y aplica una coincidencia de nombre de filename.ext.  
  
 `nsfRegularExpression`  
 Aplica una coincidencia de mayúsculas y minúsculas de nombre mediante asteriscos \(\*\) y signos de interrogación \(?\) como caracteres comodín.  
  
 `nsfUndecoratedName`  
 Sólo se aplica a los símbolos que tienen nombres representativo y representativos.  
  
## Comentarios  
 los valores de esta enumeración se pasan a los métodos siguientes:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## Requisitos  
 encabezado: dia2.h  
  
## Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)