---
title: BasicType | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df12ce7ff026215e7051142c2cbba47cb82ffc25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="basictype"></a>BasicType
Especifica el tipo básico del símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
enum BasicType {   
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
 Se especifica ningún tipo básico.  
  
 btVoid  
 Tipo básico es una `void`.  
  
 btChar  
 Tipo básico es un `char` (tipo de C o C++).  
  
 btWChar  
 Tipo básico es un carácter (Unicode) ancho (`WCHAR`).  
  
 btInt  
 Es de tipo básico `signed int` (tipo de C o C++).  
  
 btUInt  
 Es de tipo básico `unsigned int` (tipo de C o C++).  
  
 btFloat  
 Tipo básico es un número de punto flotante (`FLOAT`).  
  
 btBCD  
 Tipo básico es un decimal codificado en binario (`BCD`).  
  
 btBool  
 Tipo básico es un valor booleano (`BOOL`).  
  
 btLong  
 Tipo básico es un `long int` (tipo de C o C++).  
  
 btULong  
 Tipo básico es un `unsigned long int` (tipo de C o C++).  
  
 btCurrency  
 Tipo básico es la moneda.  
  
 btDate  
 Tipo básico es la fecha y hora (`DATE`).  
  
 btVariant  
 Tipo básico es una estructura de tipo de variable (`VARIANT`).  
  
 btComplex  
 Tipo básico es un número complejo.  
  
 btBit  
 Tipo básico es un bit.  
  
 btBSTR  
 Tipo básico es una cadena básica o binaria (`BSTR`).  
  
 btHresult  
 Tipo básico es una `HRESULT`.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración son devueltos por la [idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)