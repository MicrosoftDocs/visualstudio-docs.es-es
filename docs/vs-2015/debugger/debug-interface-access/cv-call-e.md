---
title: CV_call_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd1ee4c024894e5752277a5000d37745c88c4ac6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842866"
---
# <a name="cv_call_e"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica la Convención de llamada para una función.  
  
> [!NOTE]
> Aquí solo se documentan los valores de enumeración más comunes. La enumeración complete está disponible en el archivo de encabezado cvconst. h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 Especifica una Convención de llamada de función mediante una inserciones casi de derecha a izquierda. La función de llamada borra la pila.  
  
 CV_CALL_NEAR_FAST  
 Especifica una Convención de llamada de función que usa una inserciones casi de izquierda a derecha con registros. La función llamada usa la suma de bytes de parámetro para borrar la pila.  
  
 CV_CALL_NEAR_STD  
 Especifica una Convención de llamada de función mediante una llamada casi estándar (inserciones de derecha a izquierda).  
  
 CV_CALL_NEAR_SYS  
 Especifica una Convención de llamada de función mediante una llamada al sistema cercana.  
  
 CV_CALL_THISCALL  
 Especifica una Convención de llamada de función mediante `this` Call ( `this` el puntero pasó en Register).  
  
 CV_CALL_CLRCALL  
 Especifica una Convención de llamada de función utilizada por Common Language Runtime (CLR) (también conocida como Convención de llamada a código administrado).  
  
## <a name="remarks"></a>Notas  
 Los valores de esta enumeración son devueltos por una llamada al método [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst. h  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
