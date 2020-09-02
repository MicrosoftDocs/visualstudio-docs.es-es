---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c1fabdb202d51b85eb2983360bdfd02757f7649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699359"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica el idioma del código fuente de la aplicación o del módulo vinculado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 El idioma de la aplicación es C.  
  
 CV_CFL_CXX  
 El lenguaje de la aplicación es C++.  
  
 CV_CFL_FORTRAN  
 El lenguaje de aplicación es FORTRAN.  
  
 CV_CFL_MASM  
 El idioma de la aplicación es Microsoft macro Assembler.  
  
 CV_CFL_PASCAL  
 El idioma de la aplicación es Pascal.  
  
 CV_CFL_BASIC  
 El idioma de la aplicación es básico.  
  
 CV_CFL_COBOL  
 El idioma de la aplicación es COBOL.  
  
 CV_CFL_LINK  
 La aplicación es un módulo generado por el enlazador.  
  
 CV_CFL_CVTRES  
 La aplicación es un módulo de recursos convertido con la herramienta CVTRES.  
  
 CV_CFL_CVTPGD  
 La aplicación es un módulo con optimización POGO generado con la herramienta CVTPGD.  
  
 CV_CFL_CSHARP  
 El lenguaje de la aplicación es C#.  
  
 CV_CFL_VB  
 El idioma de la aplicación es Visual Basic.  
  
 CV_CFL_ILASM  
 El lenguaje de aplicación es un ensamblado de lenguaje intermedio (es decir, un ensamblado de Common Language Runtime (CLR)).  
  
 CV_CFL_JAVA  
 El lenguaje de la aplicación es Java.  
  
 CV_CFL_JSCRIPT  
 El lenguaje de la aplicación es JScript.  
  
 CV_CFL_MSIL  
 El lenguaje de aplicación es un lenguaje intermedio de Microsoft (MSIL) desconocido, posiblemente como resultado del uso del modificador [/LTCG (generación de código en tiempo de vínculo)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) .  
  
 CV_CFL_HLSL  
 El idioma de la aplicación es el idioma del sombreador de alto nivel.  
  
## <a name="remarks"></a>Observaciones  
 Los valores de esta enumeración son devueltos por una llamada al método [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst. h  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
