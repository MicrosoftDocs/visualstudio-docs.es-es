---
title: 'Cómo: especificar información de código adicional mediante _Analysis_assume'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: ce8102bbc790019490c4dc2a2ccbfab7d8c33981
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031532"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Cómo: especificar información de código adicional mediante _Analysis_assume
Puede proporcionar sugerencias a la herramienta de análisis de código para el código de C o C++ que le ayudarán el proceso de análisis y reducir las advertencias. Para proporcionar información adicional, utilice la siguiente función:

 `_Analysis_assume(`  `expr`  `)`

 `expr` -cualquier expresión que se supone que se evalúe como true.

 La herramienta de análisis de código se supone que la condición representada por la expresión es verdadera en el punto donde aparece la función y siga siendo verdadera hasta que la expresión se modifica, por ejemplo, mediante la asignación a una variable.

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