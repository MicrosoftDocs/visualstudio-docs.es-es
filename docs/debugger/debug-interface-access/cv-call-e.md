---
title: CV_call_e | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccdc9df86180883a5a3891563b22625fab4a2ad2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466388"
---
# <a name="cvcalle"></a>CV_call_e
Especifica la convención de llamada para una función.  
  
> [!NOTE]
>  Solo los valores de enumeración más comunes se documentan aquí. La enumeración completa está disponible en el archivo de encabezado cvconst.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>Elementos  
 CV_CALL_NEAR_C  
 Especifica una convención de llamada a funciones mediante una inserción están cerca de derecha a izquierda. La función llamada borra la pila.  
  
 CV_CALL_NEAR_FAST  
 Especifica una convención de llamada a funciones mediante una inserción de izquierda a derecha casi con registros. La función llamada usa la suma de bytes de parámetro para borrar la pila.  
  
 CV_CALL_NEAR_STD  
 Especifica una convención de llamada a funciones mediante una llamada estándar casi (inserción de derecha a izquierda).  
  
 CV_CALL_NEAR_SYS  
 Especifica una convención de llamada a funciones mediante una llamada del sistema están cerca.  
  
 CV_CALL_THISCALL  
 Especifica una convención de llamada a funciones utilizando `this` llamar (`this` registro pasa el puntero).  
  
 CV_CALL_CLRCALL  
 Especifica una convención de llamada a funciones usada por el Common Language Runtime (CLR) (también conocido como un código administrado convención de llamada).  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración son devueltos por una llamada a la [idiasymbol:: Get_callingconvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)