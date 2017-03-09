---
title: "Anotar structs y clases | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Field_size_bytes_part_"
  - "_Field_size_bytes_full_opt_"
  - "_Field_size_bytes_"
  - "_Field_size_opt_"
  - "_Field_size_part_"
  - "_Field_size_bytes_part_opt_"
  - "_Field_range_"
  - "_Field_size_part_opt_"
  - "_Field_size_"
  - "_Field_size_bytes_opt_"
  - "_Struct_size_bytes_"
  - "_Field_size_bytes_full_"
  - "_Field_size_full_"
  - "_Field_size_full_opt_"
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Anotar structs y clases
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede anotar los miembros de clase y struct mediante anotaciones que actúan como las invariantes, supuestamente deberían ser true en cualquier llamada de función o entrada/salida de la función que implica la estructura contenedora como un parámetro o un valor de resultado.  
  
## <a name="struct-and-class-annotations"></a>Anotaciones de clase y struct  
  
-   `_Field_range_(low, high)`  
  
     El campo está en el intervalo (inclusivo) desde `low` a `high`.  Equivalente a `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` aplicado al objeto anotado utilizando las condiciones pre o post adecuadas.  
  
-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Un campo que tiene un tamaño de escritura en elementos (o bytes) como especificado por `size`.  
  
-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Un campo que tiene un tamaño de escritura en elementos (o bytes) como especificado por `size`, y el `count` de dichos elementos (bytes) que son legibles.  
  
-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Un campo que tiene un tamaño puede leer y escribir en elementos (o bytes) como especificado por `size`.  
  
-   `_Struct_size_bytes_(size)`  
  
     Un campo que tiene un tamaño puede leer y escribir en elementos (o bytes) como especificado por `size`.  
  
     Se aplica a la declaración de clase o estructura.  Indica que un objeto válido de ese tipo puede ser mayor que el tipo declarado, con el número de bytes especificado por `size`.  Por ejemplo:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     El tamaño del búfer en bytes de un parámetro `pM` de tipo `MyStruct *` a continuación, se convierte en:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Utilizar anotaciones SAL para reducir defectos de código de C o C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Introducción a SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar el comportamiento de la función](../code-quality/annotating-function-behavior.md)   
 [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funciones intrínsecas](../code-quality/intrinsic-functions.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)