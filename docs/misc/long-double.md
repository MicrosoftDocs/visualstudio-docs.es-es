---
title: "Long double | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.types"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "long double de 10 bytes"
  - "Windows de 16 bits"
  - "Windows de 32 bits"
  - "long double de 8 bytes"
  - "precisión de 80 bits"
  - "precisión de 80 bits"
  - "long double de 8 bytes"
  - "long double"
ms.assetid: bb581e20-b5c2-4079-8ee8-ac6739a37852
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Long double
Las versiones de 16 bits anteriores de Microsoft C\/C\+\+ y Microsoft Visual C\+\+ admitidos `long double`, tipo de datos de la precisión de 80 bits.  En Win32 que programa, sin embargo, se asigna a `double`, tipo de datos de 64 bits del tipo de datos de `long double` de precisión.  La biblioteca en tiempo de ejecución de Microsoft proporciona versiones de `long double` de las funciones matemáticas solo por compatibilidad con versiones anteriores.  Los prototipos de función de `long double` son idénticos a los prototipos para sus homólogos de `double` , salvo que el tipo de datos de `long``double` reemplaza el tipo de datos de `double` .  Las versiones de `long double` de estas funciones no deben usarse en código nuevo.  
  
### Double funciona y sus homólogos de doble de Su Long  
  
|Función|Doble largo<br /><br /> equivalente|Función|Doble largo<br /><br /> equivalente|  
|-------------|---------------------------------|-------------|---------------------------------|  
|[acos](/visual-cpp/c-runtime-library/reference/acos-acosf-acosl)|`acosl`|[frexp](/visual-cpp/c-runtime-library/reference/frexp)|`frexpl`|  
|[asin](/visual-cpp/c-runtime-library/reference/asin-asinf-asinl)|`asinl`|[\_hypot](/visual-cpp/c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl)|`_hypotl`|  
|[atan](/visual-cpp/c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l)|`atanl`|[ldexp](/visual-cpp/c-runtime-library/reference/ldexp)|`ldexpl`|  
|[atan2](/visual-cpp/c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l)|`atan2l`|[log](/visual-cpp/c-runtime-library/reference/log-logf-log10-log10f)|`logl`|  
|[atof](/visual-cpp/c-runtime-library/reference/atof-atof-l-wtof-wtof-l)|`_atold`|[log10](/visual-cpp/c-runtime-library/reference/log-logf-log10-log10f)|`log10l`|  
|[Funciones Bessel s, j1, jn](../misc/bessel-functions-j0-j1-jn.md)|`j0l, j1l, jnl`|[\_matherr](/visual-cpp/c-runtime-library/reference/matherr)|`_matherrl`|  
|[Funciones Bessel y0, y1, yn](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|`y0l, y1l, ynl`|[modf](/visual-cpp/c-runtime-library/reference/modf-modff-modfl)|`modfl`|  
|[\_cabs](/visual-cpp/c-runtime-library/reference/cabs)|`_cabsl`|[pow](/visual-cpp/c-runtime-library/reference/pow-powf-powl)|`powl`|  
|[ceil](/visual-cpp/c-runtime-library/reference/ceil-ceilf-ceill)|`ceill`|[sin](/visual-cpp/c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl)|`sinl`|  
|[cos](/visual-cpp/c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl)|`cosl`|[sinh](/visual-cpp/c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl)|`sinhl`|  
|[cosh](/visual-cpp/c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl)|`coshl`|[sqrt](/visual-cpp/c-runtime-library/reference/sqrt-sqrtf-sqrtl)|`sqrtl`|  
|[exp](/visual-cpp/c-runtime-library/reference/exp-expf)|`expl`|[strtod](/visual-cpp/c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l)|`_strtold`|  
|[fabs](/visual-cpp/c-runtime-library/reference/fabs-fabsf-fabsl)|`fabsl`|[tan](/visual-cpp/c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl)|`tanl`|  
|[floor](/visual-cpp/c-runtime-library/reference/floor-floorf-floorl)|`floorl`|[tanh](/visual-cpp/c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl)|`tanhl`|  
|[fmod](/visual-cpp/c-runtime-library/reference/fmod-fmodf)|`fmodl`|||  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](/visual-cpp/c-runtime-library/run-time-routines-by-category)