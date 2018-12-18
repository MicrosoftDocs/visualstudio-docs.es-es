---
title: CV_CFL_LANG | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63426af550894df0e9796babaec91ff5758bbf1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909921"
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
 CV_CFL_C  
 Es de lenguaje C.  
  
 CV_CFL_CXX  
 Idioma de la aplicación es C++.  
  
 CV_CFL_FORTRAN  
 Idioma de la aplicación es FORTRAN.  
  
 CV_CFL_MASM  
 Idioma de la aplicación es Microsoft Macro Assembler.  
  
 CV_CFL_PASCAL  
 Idioma de la aplicación es Pascal.  
  
 CV_CFL_BASIC  
 Lenguaje de la aplicación es BASIC.  
  
 CV_CFL_COBOL  
 Idioma de la aplicación es COBOL.  
  
 CV_CFL_LINK  
 Aplicación es un módulo generada por el vinculador.  
  
 CV_CFL_CVTRES  
 Aplicación es un módulo de recursos con la herramienta CVTRES puede convertido.  
  
 CV_CFL_CVTPGD  
 Aplicación es un módulo POGO optimizado generado con la herramienta CVTPGD.  
  
 CV_CFL_CSHARP  
 Lenguaje es C#.  
  
 CV_CFL_VB  
 Idioma de la aplicación es Visual Basic.  
  
 CV_CFL_ILASM  
 Idioma de la aplicación es el ensamblado de lenguaje intermedio (es decir, el ensamblado de Common Language Runtime (CLR)).  
  
 CV_CFL_JAVA  
 Idioma de la aplicación es Java.  
  
 CV_CFL_JSCRIPT  
 Idioma de la aplicación es Jscript.  
  
 CV_CFL_MSIL  
 Idioma de la aplicación es un desconocido Microsoft Intermediate Language (MSIL), posiblemente un resultado del uso de la [/LTCG (generación de código de tiempo de vínculo)](/cpp/build/reference/ltcg-link-time-code-generation) cambie.  
  
 CV_CFL_HLSL  
 Idioma de la aplicación es el lenguaje de sombreado de alto nivel.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración se devuelven mediante una llamada a la [Get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)