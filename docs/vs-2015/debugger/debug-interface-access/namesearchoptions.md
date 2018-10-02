---
title: NameSearchOptions | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64f74880fe27cc71634508cbb6b272aea16517d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578352"
---
# <a name="namesearchoptions"></a>NameSearchOptions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [NameSearchOptions](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/namesearchoptions).  
  
Especifica las opciones de búsqueda para los nombres de archivo y símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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



