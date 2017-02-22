---
title: "CV_CFL_LANG | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CV_CFL_LANG (enumeración)"
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CV_CFL_LANG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica el lenguaje del código fuente de la aplicación o el módulo vinculado.  
  
## Sintaxis  
  
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
  
## Elementos \(Elements\)  
 CV\_CFL\_C  
 El lenguaje de la aplicación es C.  
  
 CV\_CFL\_CXX  
 El lenguaje de la aplicación es C\+\+.  
  
 CV\_CFL\_FORTRAN  
 El lenguaje de la aplicación es FORTRAN.  
  
 CV\_CFL\_MASM  
 El lenguaje de la aplicación es macro assembler de Microsoft.  
  
 CV\_CFL\_PASCAL  
 El lenguaje de la aplicación es Pascal.  
  
 CV\_CFL\_BASIC  
 El lenguaje de la aplicación es BÁSICO.  
  
 CV\_CFL\_COBOL  
 El lenguaje de la aplicación es COBOL.  
  
 CV\_CFL\_LINK  
 La aplicación es un módulo vinculador\-generado.  
  
 CV\_CFL\_CVTRES  
 La aplicación es un módulo de recursos convierte con la herramienta de CVTRES.  
  
 CV\_CFL\_CVTPGD  
 La aplicación es un módulo optimizado POGO generado con la herramienta de CVTPGD.  
  
 CV\_CFL\_CSHARP  
 El lenguaje de la aplicación es C\#.  
  
 CV\_CFL\_VB  
 El lenguaje de la aplicación es Visual Basic.  
  
 CV\_CFL\_ILASM  
 El lenguaje de la aplicación es ensamblado de lenguaje intermedio \(es decir, un ensamblado de \(CLR\) de Common Language Runtime\).  
  
 CV\_CFL\_JAVA  
 El lenguaje de la aplicación es Java.  
  
 CV\_CFL\_JSCRIPT  
 El lenguaje de la aplicación es Jscript.  
  
 CV\_CFL\_MSIL  
 El lenguaje de la aplicación es un Lenguaje intermedio de Microsoft desconocido \(MSIL\), posiblemente un resultado de utilizar el modificador [\/LTCG \(Generación de código en tiempo de enlace\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) .  
  
 CV\_CFL\_HLSL  
 El lenguaje de la aplicación es lenguaje de Sombreador de Alto\- nivel.  
  
## Comentarios  
 Los valores de esta enumeración son devueltos por una llamada al método de [IDiaSymbol::get\_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .  
  
## Requisitos  
 Encabezado: cvconst.h  
  
## Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)