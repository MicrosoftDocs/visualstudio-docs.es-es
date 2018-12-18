---
title: NameSearchOptions | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: c4b8771ad1bf2ee97ec1f22636a4684bc9aa7ee8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950347"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Especifica las opciones de búsqueda para los nombres de archivo y símbolos.  
  
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
 Se aplica a una coincidencia de mayúsculas y minúsculas del nombre.  
  
 `nsfFNameExt`  
 Trata los nombres como rutas de acceso y se aplica a la coincidencia de nombres nombreDeArchivo.ext.  
  
 `nsfRegularExpression`  
 Se aplica a una coincidencia de mayúsculas y minúsculas del nombre con asteriscos (*) y signos de interrogación (?) como caracteres comodín.  
  
 `nsfUndecoratedName`  
 Solo se aplica a los símbolos que tienen tanto no representativos y nombres representativos.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración se pasan a los métodos siguientes:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: dia2.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Idiasession](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)