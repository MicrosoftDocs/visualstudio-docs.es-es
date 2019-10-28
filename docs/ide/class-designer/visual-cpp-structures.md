---
title: Estructuras de C++ en el Diseñador de clases
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 65fb4738b3124daf48b501c6db416d3803da32ec
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748918"
---
# <a name="c-structures-in-class-designer"></a>Estructuras de C++ en el Diseñador de clases

El **Diseñador de clases** admite estructuras de C++, que se declaran con la palabra clave `struct`. A continuación se muestra un ejemplo:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Para más información sobre cómo usar el tipo `struct`, vea [struct](/cpp/cpp/struct-cpp).

Una forma de estructura de C++ en un diagrama de clases se parece a una forma de clase y funciona como esta, salvo que en la etiqueta se muestra **Struct** y tiene las esquinas cuadradas en lugar de redondeadas.

|Elemento de código|Vista Diseñador de clases|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Struct|

## <a name="see-also"></a>Vea también

- [Trabajo con código de C++](working-with-visual-cpp-code.md)
- [Clases y structs](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)