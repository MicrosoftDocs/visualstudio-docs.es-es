---
title: CV_access_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ce5997555b37cf5ab30f091e7124b5025284c0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164375"
---
# <a name="cv_access_e"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica el ámbito de visibilidad (nivel de acceso) de las funciones miembro y variables.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Elementos  
 CV_private  
 El miembro tiene acceso privado.  
  
 CV_protected  
 El miembro tiene acceso protegido.  
  
 CV_public  
 El miembro tiene acceso público.  
  
## <a name="remarks"></a>Observaciones  
 El `friend` especificador de acceso no se incluye aquí porque normalmente lo usan las funciones no miembro que tienen acceso a los elementos privados y protegidos de la clase. Use el método [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) para buscar símbolos con `SymTagFriend` acceso.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst. h  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol:: get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
