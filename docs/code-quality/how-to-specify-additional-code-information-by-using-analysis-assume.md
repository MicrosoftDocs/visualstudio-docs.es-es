---
title: Usar _Analysis_assume para sugerencias de análisis de código
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 9933a013ed4f2df0978fb66e3aff87b4cdc024f9
ms.sourcegitcommit: c6af923c1f485959d751b23ab3f03541013fc4a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73925960"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Cómo: especificar información de código adicional mediante el uso de _Analysis_assume

Puede proporcionar sugerencias a la herramienta de análisis de código para C/C++ Code que le ayudará en el proceso de análisis y reducirá las advertencias. Para proporcionar información adicional, utilice la siguiente función:

`_Analysis_assume(`  `expr`  `)`

`expr`: cualquier expresión que se supone que se evalúa como true.

La herramienta de análisis de código supone que la condición representada por la expresión es true en el punto en el que aparece la función y sigue siendo true hasta que se modifica la expresión, por ejemplo, mediante asignación a una variable.

> [!NOTE]
> `_Analysis_assume` no afecta a la optimización del código. Fuera de la herramienta de análisis de código, `_Analysis_assume` se define como una operación no operativa.

## <a name="example"></a>Ejemplo

En el código siguiente se usa `_Analysis_assume` para corregir la advertencia de análisis de código [C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    _Analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Vea también

- [__assume](/cpp/intrinsics/assume)
