---
title: NameSearchOptions | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 32a5858d52f7d5ee2adfce48084fd096c4dae0a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="namesearchoptions"></a>NameSearchOptions
Especifica las opciones de búsqueda de nombres de archivo y símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
enum NameSearchOptions {   
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
  
## <a name="elements"></a>Elementos  
 `nsNone`  
 No se especifican opciones.  
  
 `nsfCaseSensitive`  
 Se aplica a una coincidencia de nombre distingue mayúsculas de minúsculas.  
  
 `nsfCaseInsensitive`  
 Se aplica a la coincidencia de nombres entre mayúsculas y minúsculas.  
  
 `nsfFNameExt`  
 Trata los nombres como las rutas de acceso y se aplica a la coincidencia de nombres nombreDeArchivo.ext.  
  
 `nsfRegularExpression`  
 Se aplica a una coincidencia de nombre distingue mayúsculas de minúsculas con asteriscos (*) y signos de interrogación (?) como caracteres comodín.  
  
 `nsfUndecoratedName`  
 Se aplica solo a los símbolos que tienen tanto no representativos y nombres representativos.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración se pasan a los métodos siguientes:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: dia2.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Idiasession:: FindFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)