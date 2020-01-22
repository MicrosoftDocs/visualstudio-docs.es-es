---
title: Enumeraciones de C++ en el Diseñador de clases
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: ee56850c05e4b06ea4325ec238e56e99b38978d0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114189"
---
# <a name="c-enumerations-in-class-designer"></a>Enumeraciones de C++ en el Diseñador de clases

El **Diseñador de clases** admite tipos `enum` y `enum class` de ámbito de C++. A continuación se muestra un ejemplo:

```cpp
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};
```

Una forma de enumeración de C++ en un diagrama de clases se parece y funciona como una forma de estructura, salvo que en la etiqueta se muestra **Enum** o **Enum class**, es de color fucsia en lugar de azul y el borde de los márgenes superior e izquierdo está coloreado. Tanto las formas de enumeración como las formas de estructura tienen las esquinas cuadradas.

Para obtener más información sobre cómo usar el tipo `enum`, vea [Enumerations (Enumeraciones)](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Vea también

- [Trabajo con código de C++](working-with-visual-cpp-code.md)
- [Enumeraciones](/cpp/cpp/enumerations-cpp)
