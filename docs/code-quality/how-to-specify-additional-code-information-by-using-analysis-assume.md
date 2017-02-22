---
title: "C&#243;mo: Especificar informaci&#243;n de c&#243;digo adicional mediante __analysis_assume | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__analysis_assume"
helpviewer_keywords: 
  - "__analysis_assume"
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C&#243;mo: Especificar informaci&#243;n de c&#243;digo adicional mediante __analysis_assume
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede proporcionar sugerencias a la herramienta de análisis de código para código en C\/C\+\+ que servirán de ayuda en el proceso de análisis y reducirán las advertencias.  Para proporcionar información adicional, utilice la función siguiente:  
  
 `__analysis_assume(`   `expr`   `)`  
  
 `expr`: expresión de la que se supone que se evalúa como true.  
  
 La herramienta de análisis de código supone que la condición representada por la expresión se aplica en el punto donde aparece la función y seguirá aplicándose hasta que se modifique la expresión, por ejemplo, si se asigna a una variable.  
  
> [!NOTE]
>  `__analysis_assume` no afecta a la optimización del código.  Fuera de la herramienta de análisis de código, `__analysis_assume` se define como una ausencia de operación.  
  
## Ejemplo  
 El código siguiente utiliza `__analysis_assume` para corregir la advertencia de análisis de código [C6388](../code-quality/c6388.md):  
  
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
  
## Vea también  
 [\_\_assume](/visual-cpp/intrinsics/assume)