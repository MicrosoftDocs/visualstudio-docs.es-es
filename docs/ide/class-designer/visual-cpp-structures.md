---
title: Estructuras de Visual C++ en el Diseñador de clases
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 79b4adcfbcacc8cf342b5fc4183ae4fe27431b09
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864776"
---
# <a name="visual-c-structures-in-class-designer"></a>Estructuras de Visual C++ en el Diseñador de clases

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

- [Trabajar con código de Visual C++](working-with-visual-cpp-code.md)
- [Clases y structs](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)