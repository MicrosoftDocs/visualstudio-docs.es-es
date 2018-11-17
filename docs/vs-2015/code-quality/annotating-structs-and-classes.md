---
title: Anotar Structs y clases | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 965a823c658516edf247f6a99d23d189097b31f0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801490"
---
# <a name="annotating-structs-and-classes"></a>Anotar structs y clases
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Miembros de clase y struct se pueden anotar utilizando las anotaciones que actúan como invariables, que se supone que cumplirse en cualquier llamada de función o de entrada/salida de la función que implica la estructura envolvente como un parámetro o un valor de resultado.  
  
## <a name="struct-and-class-annotations"></a>Anotaciones de clase y struct  
  
-   `_Field_range_(low, high)`  
  
     El campo está en el intervalo (inclusivo) desde `low` a `high`.  Equivalente a `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` aplicado al objeto anotado utilizando las condiciones pre o post adecuadas.  
  
-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Un campo que tiene un tamaño de lectura de elementos (o bytes) como especificado por `size`.  
  
-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Un campo que tiene un tamaño de lectura de elementos (o bytes) como especificado por `size`y el `count` de los elementos (bytes) que son legibles.  
  
-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Un campo que tiene el tamaño de lectura y escritura en elementos (o bytes) como especificado por `size`.  
  
-   `_Struct_size_bytes_(size)`  
  
     Un campo que tiene el tamaño de lectura y escritura en elementos (o bytes) como especificado por `size`.  
  
     Se aplica a la declaración de clase o estructura.  Indica que un objeto válido de ese tipo puede ser mayor que el tipo declarado, con el número de bytes especificado por `size`.  Por ejemplo:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     El tamaño del búfer en bytes de un parámetro `pM` de tipo `MyStruct *` , a continuación, se convierte en:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Utilizar anotaciones SAL para reducir defectos de código de c/c ++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Introducción a SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar comportamiento de la función](../code-quality/annotating-function-behavior.md)   
 [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funciones intrínsecas](../code-quality/intrinsic-functions.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)



