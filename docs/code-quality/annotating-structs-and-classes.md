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
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 1cff36760a84821a33dcdb1ee4cc6842cd40aee0
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "72015969"
---
# <a name="annotating-structs-and-classes"></a>Anotar structs y clases

Puede anotar los miembros de struct y de clase mediante anotaciones que actúan como invariantes; se supone que son verdaderos en cualquier llamada de función o entrada y salida de función que implique la estructura de inclusión como un parámetro o un valor de resultado.

## <a name="struct-and-class-annotations"></a>Anotaciones de estructuras y clases

- `_Field_range_(low, high)`

     El campo está en el intervalo (inclusivo) de `low` a `high`.  Equivalente a `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` aplicada al objeto anotado utilizando las condiciones previas o posteriores adecuadas.

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Campo que tiene un tamaño de escritura en elementos (o bytes) según especifica `size`.

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     Campo que tiene un tamaño de escritura en los elementos (o bytes) especificados por `size` y el `count` de esos elementos (bytes) que se pueden leer.

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Campo que tiene un tamaño de lectura y escritura en los elementos (o bytes) especificados por `size`.

- `_Field_z_`

     Campo que tiene una cadena terminada en NULL.

- `_Struct_size_bytes_(size)`

     Se aplica a la declaración de clase o struct.  Indica que un objeto válido de ese tipo puede ser mayor que el tipo declarado, con el número de bytes especificado por `size`.  Por ejemplo:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     A continuación, el tamaño de búfer en bytes de un parámetro `pM` de tipo `MyStruct *` se considera:

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

- `_Field_z_` es equivalente a `_Null_terminated_`.  `_Field_z_` para el campo nombre especifica que el campo nombre es una cadena terminada en NULL.
- `_Field_range_` para `bufferSize` especifica que el valor de `bufferSize` debe estar comprendido entre 1 y `MaxBufferSize` (ambos inclusivos).
- Los resultados finales de las anotaciones `_Struct_size_bytes_` y `_Field_size_` son equivalentes. En el caso de estructuras o clases que tienen un diseño similar, `_Field_size_` es más fácil de leer y mantener, ya que tiene menos referencias y cálculos que la anotación `_Struct_size_bytes_` equivalente. `_Field_size_` no requiere conversión al tamaño de bytes. Si el tamaño de byte es la única opción, por ejemplo, para un campo de puntero void, se puede usar `_Field_size_bytes_`. Si existen `_Struct_size_bytes_` y `_Field_size_`, ambos estarán disponibles para las herramientas. Depende de la herramienta qué hacer si las dos anotaciones están en desacuerdo.

## <a name="see-also"></a>Vea también

- [Uso de anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Introducción a SAL](../code-quality/understanding-sal.md)
- [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)
- [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)
- [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funciones intrínsecas](../code-quality/intrinsic-functions.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)