---
title: Procedimiento Especificar información de código adicional mediante __analysis_assume | Microsoft Docs
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
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: e130f2248ae6715b3248226c780bc162e1ff01ef
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426638"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Procedimiento Especificar información de código adicional mediante _analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede proporcionar sugerencias a la herramienta de análisis de código para código de C o C++ que ayudan al proceso de análisis y reducir las advertencias. Para proporcionar información adicional, utilice la siguiente función:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -cualquier expresión que se supone que se evalúe como true.  
  
 La herramienta de análisis de código se da por supuesto que la condición representada por la expresión es verdadera en el punto donde aparece la función y siga siendo verdadera hasta que la expresión se modifica, por ejemplo, mediante la asignación a una variable.  
  
> [!NOTE]
> `__analysis_assume` no afecta a la optimización de código. Fuera de la herramienta de análisis de código, `__analysis_assume` se define como una operación inefectiva.  
  
## <a name="example"></a>Ejemplo  
 El siguiente código utiliza `__analysis_assume` para corregir la advertencia de análisis de código [C6388](../code-quality/c6388.md):  
  
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
  
## <a name="see-also"></a>Vea también  
 [__assume](http://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
