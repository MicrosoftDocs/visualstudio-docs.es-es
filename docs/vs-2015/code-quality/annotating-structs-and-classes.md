---
title: Anotar Structs y clases | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 6db2202971facb0419db68c04835c8d5c848f528
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271580"
---
# <a name="annotating-structs-and-classes"></a>Anotar structs y clases
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede anotar los miembros de struct y de clase mediante anotaciones que actúan como invariantes; se supone que son verdaderos en cualquier llamada de función o entrada y salida de función que implique la estructura de inclusión como un parámetro o un valor de resultado.  
  
## <a name="struct-and-class-annotations"></a>Anotaciones de estructuras y clases  
  
- `_Field_range_(low, high)`  
  
     El campo está en el intervalo (inclusivo) de `low` a `high`.  Equivalente a `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` aplicado al objeto anotado utilizando las condiciones previas o posteriores adecuadas.  
  
- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Campo que tiene un tamaño de escritura en elementos (o bytes) tal y como lo especifica `size`.  
  
- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`, `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Campo que tiene un tamaño de escritura en elementos (o bytes) tal y como se especifica en `size`, y el `count` de esos elementos (bytes) que se pueden leer.  
  
- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Campo que tiene un tamaño de lectura y escritura en los elementos (o bytes) especificados por `size`.  
  
- `_Struct_size_bytes_(size)`  
  
     Campo que tiene un tamaño de lectura y escritura en los elementos (o bytes) especificados por `size`.  
  
     Se aplica a la declaración de clase o struct.  Indica que un objeto válido de ese tipo puede ser mayor que el tipo declarado, con el número de bytes especificado por `size`.  Por ejemplo:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     El tamaño de búfer en bytes de un parámetro `pM` de tipo `MyStruct *` se toma entonces como:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Consulte también  
 [Uso de anotaciones sal para reducir defectos deC++ C/Code](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Descripción de SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores Devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar el comportamiento](../code-quality/annotating-function-behavior.md) de la función   
 [Anotar el comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Especificar Cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funciones intrínsecas](../code-quality/intrinsic-functions.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)
