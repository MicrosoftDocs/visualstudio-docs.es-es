---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fb684d0ff68e5ede6b0847ef9aeba1821ecafcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745332"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
Especifica el idioma del código fuente de la aplicación o del módulo vinculado.

## <a name="syntax"></a>Sintaxis

```C++
typedef enum CV_CFL_LANG {
    CV_CFL_C       = 0x00,
    CV_CFL_CXX     = 0x01,
    CV_CFL_FORTRAN = 0x02,
    CV_CFL_MASM    = 0x03,
    CV_CFL_PASCAL  = 0x04,
    CV_CFL_BASIC   = 0x05,
    CV_CFL_COBOL   = 0x06,
    CV_CFL_LINK    = 0x07,
    CV_CFL_CVTRES  = 0x08,
    CV_CFL_CVTPGD  = 0x09,
    CV_CFL_CSHARP  = 0x0A,
    CV_CFL_VB      = 0x0B,
    CV_CFL_ILASM   = 0x0C,
    CV_CFL_JAVA    = 0x0D,
    CV_CFL_JSCRIPT = 0x0E,
    CV_CFL_MSIL    = 0x0F,
    CV_CFL_HLSL    = 0x10
} CV_CFL_LANG;
```

## <a name="elements"></a>Elementos
El lenguaje de aplicación CV_CFL_C es C.

El idioma de la C++aplicación CV_CFL_CXX es.

El lenguaje de aplicación CV_CFL_FORTRAN es FORTRAN.

El lenguaje de aplicación de CV_CFL_MASM es Microsoft macro Assembler.

El lenguaje de la aplicación CV_CFL_PASCAL es Pascal.

El lenguaje de la aplicación CV_CFL_BASIC es básico.

El lenguaje de la aplicación CV_CFL_COBOL es COBOL.

La aplicación CV_CFL_LINK es un módulo generado por el enlazador.

La aplicación CV_CFL_CVTRES es un módulo de recursos convertido con la herramienta CVTRES.

La aplicación CV_CFL_CVTPGD es un módulo con optimización POGO generado con la herramienta CVTPGD.

El idioma de la C#aplicación CV_CFL_CSHARP es.

El idioma de la aplicación CV_CFL_VB es Visual Basic.

El lenguaje de aplicación CV_CFL_ILASM es un ensamblado de lenguaje intermedio (es decir, un ensamblado de Common Language Runtime (CLR)).

El lenguaje de aplicación CV_CFL_JAVA es Java.

El lenguaje de la aplicación CV_CFL_JSCRIPT es JScript.

El lenguaje de aplicación CV_CFL_MSIL es un lenguaje intermedio de Microsoft (MSIL) desconocido, posiblemente como resultado del uso del modificador [/LTCG (generación de código en tiempo de vínculo)](/cpp/build/reference/ltcg-link-time-code-generation) .

El idioma de la aplicación CV_CFL_HLSL es el idioma del sombreador de alto nivel.

## <a name="remarks"></a>Comentarios
Los valores de esta enumeración son devueltos por una llamada al método [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .

## <a name="requirements"></a>Requisitos
Encabezado: cvconst. h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
