---
title: Reglas de documentación
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- rules, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f4ec6a0dd154dae89145add26c60a8b1322a444
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808657"
---
# <a name="documentation-rules"></a>Reglas de documentación

Las reglas de documentación permiten escribir bibliotecas bien documentadas mediante el uso correcto de [comentarios de documentación XML](/dotnet/csharp/codedoc) para API visibles externamente.

## <a name="in-this-section"></a>En esta sección

| Regla | Descripción |
| - | - |
| [CA1200: Evitar el uso de etiquetas cref con un prefijo](../code-quality/ca1200.md) | El atributo [CREF](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) de una etiqueta de documentación XML significa "referencia de código". Especifica que el texto interno de la etiqueta es un elemento de código, como un tipo, un método o una propiedad. Evite el uso de `cref` etiquetas con prefijos, ya que impide que el compilador Compruebe las referencias. También impide que el entorno de desarrollo integrado (IDE) de Visual Studio busque y actualice estas referencias de símbolos durante las refactorizaciones. |

## <a name="see-also"></a>Consulte también

- [Reglas de análisis de código](../code-quality/code-analysis-for-managed-code-warnings.md)
