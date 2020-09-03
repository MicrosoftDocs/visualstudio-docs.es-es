---
title: Namesearchoptions (| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6d721ebc5849fc459d24173ad0500b4b1c12260f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182976"
---
# <a name="namesearchoptions"></a>NameSearchOptions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica las opciones de búsqueda para los nombres de símbolos y archivos.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
## <a name="elements"></a>Elementos  
 `nsNone`  
 No se especifican opciones.  
  
 `nsfCaseSensitive`  
 Aplica una coincidencia de nombre que distingue entre mayúsculas y minúsculas.  
  
 `nsfCaseInsensitive`  
 Aplica una coincidencia de nombre que no distingue mayúsculas de minúsculas.  
  
 `nsfFNameExt`  
 Trata los nombres como rutas de acceso y aplica una coincidencia de nombre de archivo. ext.  
  
 `nsfRegularExpression`  
 Aplica una coincidencia de nombres que distingue entre mayúsculas y minúsculas mediante asteriscos (*) y signos de interrogación (?) como caracteres comodín.  
  
 `nsfUndecoratedName`  
 Solo se aplica a símbolos que tienen nombres no representativos y representativos.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración se pasan a los métodos siguientes:  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2. h  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession:: Findchildren (](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession:: findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
