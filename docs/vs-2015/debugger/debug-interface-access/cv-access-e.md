---
title: CV_access_e | Microsoft Docs
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
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5096c90727a1c8ffcf871853d1f59610a2baff37
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574284"
---
# <a name="cvaccesse"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CV_access_e](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/cv-access-e).  
  
Especifica el ámbito de visibilidad (nivel de acceso) de las funciones miembro y variables.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Elementos  
 CV_private  
 Miembro tiene acceso privado.  
  
 CV_protected  
 Miembro de acceso protegido.  
  
 CV_public  
 Miembro tiene acceso público.  
  
## <a name="remarks"></a>Comentarios  
 El `friend` especificador de acceso no se incluye aquí porque se usa normalmente por funciones no miembro que tienen acceso a elementos privados y protegidos de la clase. Use la [Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) método para buscar símbolos con `SymTagFriend` acceso.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)



