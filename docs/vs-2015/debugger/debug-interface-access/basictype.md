---
title: BasicType | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 633fb76a8177f239b988554a5d15bee09e00c2d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745032"
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
 Se especifica ningún tipo básico.  
  
 btVoid  
 Tipo básico es un `void`.  
  
 btChar  
 Tipo básico es un `char` (tipo de C o C++).  
  
 btWChar  
 Es de tipo básico de caracteres anchos (Unicode) (`WCHAR`).  
  
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
 Tipo básico es un poco.  
  
 btBSTR  
 Tipo básico es una cadena binaria o básica (`BSTR`).  
  
 btHresult  
 Tipo básico es un `HRESULT`.  
  
## <a name="remarks"></a>Comentarios  
 Devuelven los valores de esta enumeración la [Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)



