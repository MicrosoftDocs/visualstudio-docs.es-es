---
title: Procedimiento Especificar información de código adicional mediante _Analysis_assume
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 17e25ace1da6cad9fcdc129b6c6f517c39c9c103
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845086"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Procedimiento Especificar información de código adicional mediante _Analysis_assume
Puede proporcionar sugerencias a la herramienta de análisis de código para código de C o C++ que ayudan al proceso de análisis y reducir las advertencias. Para proporcionar información adicional, utilice la siguiente función:

 `_Analysis_assume(`  `expr`  `)`

 `expr` -cualquier expresión que se supone que se evalúe como true.

 La herramienta de análisis de código se da por supuesto que la condición representada por la expresión es verdadera en el punto donde aparece la función y siga siendo verdadera hasta que la expresión se modifica, por ejemplo, mediante la asignación a una variable.

> [!NOTE]
>  `_Analysis_assume` no afecta a la optimización de código. Fuera de la herramienta de análisis de código, `_Analysis_assume` se define como una operación inefectiva.

## <a name="example"></a>Ejemplo
 El siguiente código utiliza `_Analysis_assume` para corregir la advertencia de análisis de código [C6388](../code-quality/c6388.md):

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
  _Analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>Vea también
 [__assume](/cpp/intrinsics/assume)