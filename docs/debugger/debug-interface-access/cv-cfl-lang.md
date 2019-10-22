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
ms.openlocfilehash: 1f02545f1c19b57e46af302fbc0b2abaa7445612
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555055"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
Especifica el lenguaje de código fuente de la aplicación o un módulo vinculado.

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
Idioma de la aplicación CV_CFL_C es C.

Idioma de la aplicación CV_CFL_CXX es C++.

Idioma de la aplicación CV_CFL_FORTRAN es FORTRAN.

Idioma de la aplicación CV_CFL_MASM es Microsoft Macro Assembler.

Idioma de la aplicación CV_CFL_PASCAL es Pascal.

Lenguaje de la aplicación CV_CFL_BASIC es BASIC.

Idioma de la aplicación CV_CFL_COBOL es COBOL.

Aplicación CV_CFL_LINK es un módulo generada por el vinculador.

Aplicación CV_CFL_CVTRES es un módulo de recursos con la herramienta CVTRES puede convertido.

Aplicación CV_CFL_CVTPGD es un módulo POGO optimizado generado con la herramienta CVTPGD.

Idioma de la aplicación CV_CFL_CSHARP es C#.

Idioma de la aplicación CV_CFL_VB es Visual Basic.

Idioma de aplicación CV_CFL_ILASM es el ensamblado de lenguaje intermedio (es decir, los ensamblados de Common Language Runtime (CLR)).

Idioma de la aplicación CV_CFL_JAVA es Java.

Idioma de la aplicación CV_CFL_JSCRIPT es Jscript.

Idioma de aplicación CV_CFL_MSIL es un desconocido Microsoft Intermediate Language (MSIL), posiblemente un resultado del uso de la [/LTCG (generación de código de tiempo de vínculo)](/cpp/build/reference/ltcg-link-time-code-generation) cambie.

CV_CFL_HLSL lenguaje es el lenguaje de sombreado de alto nivel.

## <a name="remarks"></a>Comentarios
Los valores de esta enumeración se devuelven mediante una llamada a la [Get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst.h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
