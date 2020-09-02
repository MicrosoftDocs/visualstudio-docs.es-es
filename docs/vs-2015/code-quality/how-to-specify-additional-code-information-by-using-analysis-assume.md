---
title: 'Cómo: especificar información de código adicional mediante __analysis_assume | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: f2f18c9284ec96de7a7b8663aff485962d194282
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277977"
---
# <a name="how-to-specify-additional-code-information-by-using-__analysis_assume"></a>Cómo: Especificar información de código adicional mediante __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede proporcionar sugerencias a la herramienta de análisis de código para código de C/C++ que le ayudará en el proceso de análisis y reducirá las advertencias. Para proporcionar información adicional, utilice la siguiente función:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` : cualquier expresión que se supone que se evalúa como true.  
  
 La herramienta de análisis de código supone que la condición representada por la expresión es true en el punto en el que aparece la función y sigue siendo true hasta que se modifica la expresión, por ejemplo, mediante asignación a una variable.  
  
> [!NOTE]
> `__analysis_assume` no afecta a la optimización del código. Fuera de la herramienta de análisis de código, `__analysis_assume` se define como una operación no operativa.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente usa `__analysis_assume` para corregir la advertencia de análisis de código [C6388](../code-quality/c6388.md):  
  
```  
#include<windows.h>  
#include<codeanalysis\sourceannotations.h>  
  
using namespace vc_attributes;  
  
// calls free and sets ch to null  
void FreeAndNull(char* ch);  
  
//requires pc to be null  
void f([Pre(Null=Yes)] char* pc);  
  
void test( )  
{  
  char *pc = (char*)malloc(5);  
  FreeAndNull(pc);  
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## <a name="see-also"></a>Consulte también  
 [__assume](https://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
