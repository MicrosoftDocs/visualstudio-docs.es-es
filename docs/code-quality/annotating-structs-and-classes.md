---
title: Anotar structs y clases
ms.date: 06/28/2019
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 35be465064c9524eb0e1339794b6a19b7a595da1
ms.sourcegitcommit: d2b234e0a4a875c3cba09321cdf246842670d872
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2019
ms.locfileid: "67493638"
---
# <a name="annotating-structs-and-classes"></a>Anotar structs y clases

Miembros de clase y struct se pueden anotar utilizando las anotaciones que actúan como invariables, que se supone que cumplirse en cualquier llamada de función o de entrada/salida de la función que implica la estructura envolvente como un parámetro o un valor de resultado.

## <a name="struct-and-class-annotations"></a>Anotaciones de clase y struct

- `_Field_range_(low, high)`

     El campo está en el intervalo (inclusivo) desde `low` a `high`.  Equivalente a `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` aplicado al objeto anotado utilizando las condiciones pre o post adecuadas.

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Un campo que tiene un tamaño de lectura de elementos (o bytes) como especificado por `size`.

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     Un campo que tiene un tamaño de lectura de elementos (o bytes) como especificado por `size`y el `count` de los elementos (bytes) que son legibles.

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Un campo que tiene el tamaño de lectura y escritura en elementos (o bytes) como especificado por `size`.

- `_Field_z_`

     Un campo que tiene una cadena terminada en null.

- `_Struct_size_bytes_(size)`

     Se aplica a la declaración de clase o estructura.  Indica que un objeto válido de ese tipo puede ser mayor que el tipo declarado, con el número de bytes especificado por `size`.  Por ejemplo:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     El tamaño del búfer en bytes de un parámetro `pM` de tipo `MyStruct *` , a continuación, se convierte en:

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="example"></a>Ejemplo

```cpp
#include <sal.h>
// For FIELD_OFFSET macro
#include <windows.h>

// This _Struct_size_bytes_ is equivalent to what below _Field_size_ means.
_Struct_size_bytes_(FIELD_OFFSET(MyBuffer, buffer) + bufferSize * sizeof(int))
struct MyBuffer
{
    static int MaxBufferSize;
    
    _Field_z_
    const char* name;
    
    int firstField;

    // ... other fields

    _Field_range_(1, MaxBufferSize)
    int bufferSize;
    _Field_size_(bufferSize)        // Prefered way - easier to read and maintain.
    int buffer[0];
};
```

Notas para este ejemplo:

- `_Field_z_` es equivalente a `_Null_terminated_`.  `_Field_z_` para el nombre de campo especifica que el campo nombre es una cadena terminada en null.
- `_Field_range_` para `bufferSize` especifica que el valor de `bufferSize` debe estar comprendido entre 1 y `MaxBufferSize` (ambos inclusive).
- Los resultados finales de la `_Struct_size_bytes_` y `_Field_size_` las anotaciones son equivalentes. Para estructuras o clases que tienen un diseño similar, `_Field_size_` es más fácil de leer y mantener, ya que tiene menos referencias y cálculos que el equivalente `_Struct_size_bytes_` anotación. `_Field_size_` no requiere conversión para el tamaño en bytes. Si el tamaño en bytes es la única opción, por ejemplo, para un campo de puntero void, `_Field_size_bytes_` se puede usar. Si ambos `_Struct_size_bytes_` y `_Field_size_` existe, ambos estarán disponibles para las herramientas. Es responsabilidad de la herramienta de qué hacer si las dos anotaciones están en desacuerdo.

## <a name="see-also"></a>Vea también

- [Uso de anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Introducción a SAL](../code-quality/understanding-sal.md)
- [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)
- [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)
- [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funciones intrínsecas](../code-quality/intrinsic-functions.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)