---
title: Enumeraciones de Visual C++ en el Diseñador de clases
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d5f02d899c9d81c8dd19aac879bed7ac9c1acdb8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946833"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Enumeraciones de Visual C++ en el Diseñador de clases

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

- [Trabajar con código de Visual C++](working-with-visual-cpp-code.md)
- [Enumeraciones](/cpp/cpp/enumerations-cpp)