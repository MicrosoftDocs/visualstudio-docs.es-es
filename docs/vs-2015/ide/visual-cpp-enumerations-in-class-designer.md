---
title: Enumeraciones de Visual C++ en el Diseñador de clases | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f967420e37d6337ce6d86cc56524f2751218f56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651665"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Enumeraciones de Visual C++ en el Diseñador de clases
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Diseñador de clases admite tipos `enum` y `enum class` de ámbito de C++. El siguiente es un ejemplo:

```
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

 Para obtener más información sobre cómo usar el tipo `enum`, vea [Enumerations (Enumeraciones)](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3).

## <a name="see-also"></a>Consulte también
 Trabajar con [enumeraciones](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3) [de código de Visual C++ (diseñador de clases)](../ide/working-with-visual-cpp-code-class-designer.md)
