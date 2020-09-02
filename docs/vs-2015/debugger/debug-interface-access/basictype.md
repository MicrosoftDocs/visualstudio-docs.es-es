---
title: BasicType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38de89b9774ac20f67b91e4ba864534122f4cdb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580842"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica el tipo básico del símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>Elementos  
 btNoType  
 No se ha especificado ningún tipo básico.  
  
 btVoid  
 El tipo básico es `void` .  
  
 btChar  
 El tipo básico es `char` (tipo C/C++).  
  
 btWChar  
 El tipo básico es un carácter ancho (Unicode) ( `WCHAR` ).  
  
 btInt  
 El tipo básico es `signed int` (tipo C/C++).  
  
 btUInt  
 El tipo básico es `unsigned int` (tipo C/C++).  
  
 btFloat  
 El tipo básico es un número de punto flotante ( `FLOAT` ).  
  
 btBCD  
 El tipo básico es un decimal con codificación binaria ( `BCD` ).  
  
 btBool  
 El tipo básico es un valor booleano ( `BOOL` ).  
  
 btLong  
 El tipo básico es `long int` (tipo C/C++).  
  
 btULong  
 El tipo básico es `unsigned long int` (tipo C/C++).  
  
 btCurrency  
 El tipo básico es Currency.  
  
 btDate  
 El tipo básico es fecha y hora ( `DATE` ).  
  
 btVariant  
 El tipo básico es una estructura de tipo variable ( `VARIANT` ).  
  
 btComplex  
 El tipo básico es un número complejo.  
  
 btBit  
 El tipo básico es un bit.  
  
 btBSTR  
 El tipo básico es una cadena básica o binaria ( `BSTR` ).  
  
 btHresult  
 El tipo básico es `HRESULT` .  
  
## <a name="remarks"></a>Comentarios  
 El método [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) devuelve los valores de esta enumeración.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst. h  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
