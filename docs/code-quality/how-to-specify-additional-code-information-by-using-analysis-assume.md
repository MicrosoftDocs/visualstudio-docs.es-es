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
ms.openlocfilehash: 186ea6ac58736098720d60c644c30801073b7453
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018720"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Procedimiento Especificar información de código adicional mediante _Analysis_assume

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
    __analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Vea también

- [__assume](/cpp/intrinsics/assume)
