---
title: Anotar parámetros de función y valores devueltos
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: d60691836b38720cadeddfdf254d3646f9fa5479
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2018
ms.locfileid: "53805112"
---
# <a name="annotating-function-parameters-and-return-values"></a>Anotar parámetros de función y valores devueltos
En este artículo se describe los usos típicos de las anotaciones de parámetros de función simple, escalares y punteros a estructuras y clases y casi todos los tipos de búferes.  En este artículo también muestra los patrones de uso común para las anotaciones. Para obtener información sobre las anotaciones adicionales que están relacionados con las funciones, vea [anotar comportamiento de la función](../code-quality/annotating-function-behavior.md)

## <a name="pointer-parameters"></a>Parámetros de puntero
 Para las anotaciones en la tabla siguiente, cuando se anota un parámetro de puntero, el analizador notifica un error si el puntero es null.  Esto se aplica a los punteros y a cualquier elemento de datos que señala.

 **Las anotaciones y descripciones**

-   `_In_`

     Anota los parámetros de entrada que son valores escalares, estructuras, punteros a estructuras y similares.  Explícitamente se pueden utilizar en valores escalares simples.  El parámetro debe ser válido en estado preliminar y no se modificará.

-   `_Out_`

     Anota los parámetros de salida que son valores escalares, estructuras, punteros a estructuras y similares.  No aplicar esto a un objeto que no se puede devolver un valor, por ejemplo, un valor escalar que se pasa por valor.  El parámetro no tiene que ser válido en un estado anterior, pero debe ser válido en el estado posterior a la.

-   `_Inout_`

     Anota un parámetro que se cambiará por la función.  Debe ser válido en el estado previo y posterior a la de estado, pero se supone que tiene valores diferentes antes y después de la llamada. Debe aplicar a un valor modificable.

-   `_In_z_`

     Un puntero a una cadena terminada en null que se usa como entrada.  La cadena debe ser válida en un estado anterior.  Las variantes de `PSTR`, que ya tiene las anotaciones correctas, se prefieren.

-   `_Inout_z_`

     Un puntero a una matriz de caracteres terminada en null que se va a modificar.  Debe ser válido antes y después de la llamada, pero se supone que el valor ha cambiado.  Se puede mover el terminador nulo, pero pueden tener acceso a solo los elementos hasta el terminador nulo original.

-   `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Un puntero a una matriz, que se lee por la función.  La matriz es de tamaño `s` elementos, todos ellos deben ser válidos.

     El `_bytes_` variante proporciona el tamaño en bytes en lugar de elementos. Úselo solo cuando el tamaño no puede expresarse como elementos.  Por ejemplo, `char` cadenas utilizaría el `_bytes_` variante solo si la función una similar que utiliza `wchar_t` sería.

-   `_In_reads_z_(s)`

     Un puntero a una matriz terminada en null y que tiene un tamaño conocido. Los elementos hasta el terminador nulo, o `s` si no hay ningún terminador nulo, debe ser válido en un estado anterior.  Si se conoce el tamaño en bytes, escalar `s` por el tamaño del elemento.

-   `_In_reads_or_z_(s)`

     Un puntero a una matriz terminada en null o tiene un tamaño conocido, o ambas. Los elementos hasta el terminador nulo, o `s` si no hay ningún terminador nulo, debe ser válido en un estado anterior.  Si se conoce el tamaño en bytes, escalar `s` por el tamaño del elemento.  (Utilizado para la `strn` familia.)

-   `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Un puntero a una matriz de `s` elementos (bytes resp) que se escribirá la función.  Los elementos de matriz no debe ser válido en un estado anterior y se ha especificado el número de elementos que son válidas en el estado posterior a la.  Si no hay anotaciones en el tipo de parámetro, se aplican en el estado posterior a la. Por ejemplo, considere el fragmento de código siguiente:

     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`

     En este ejemplo, el autor de la llamada proporciona un búfer de `size` elementos para `p1`.  `MyStringCopy` hace algunos de esos elementos válidos. Más importante aún, la `_Null_terminated_` anotación en `PWSTR` significa que `p1` está terminada en null en estado posterior a la.  De este modo, el número de elementos válidos es todavía bien definido, pero no se requiere un recuento de elemento específico.

     El `_bytes_` variante proporciona el tamaño en bytes en lugar de elementos. Úselo solo cuando el tamaño no puede expresarse como elementos.  Por ejemplo, `char` cadenas utilizaría el `_bytes_` variante solo si la función una similar que utiliza `wchar_t` sería.

-   `_Out_writes_z_(s)`

     Un puntero a una matriz de `s` elementos.  Los elementos tienen no sea válido en un estado anterior.  En posteriores al estado, los elementos de copia mediante el terminador nulo, que debe estar presente, debe ser válido.  Si se conoce el tamaño en bytes, escalar `s` por el tamaño del elemento.

-   `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Un puntero a una matriz, que es de lectura y escritura en la función.  Es de tamaño `s` elementos y es válido en estado previo y posterior a la de estado.

     El `_bytes_` variante proporciona el tamaño en bytes en lugar de elementos. Úselo solo cuando el tamaño no puede expresarse como elementos.  Por ejemplo, `char` cadenas utilizaría el `_bytes_` variante solo si la función una similar que utiliza `wchar_t` sería.

-   `_Inout_updates_z_(s)`

     Un puntero a una matriz terminada en null y que tiene un tamaño conocido. Los elementos de copia mediante el terminador nulo, que debe estar presente, debe ser válido en el estado previo y posterior a la de estado.  El valor en el estado posterior a la se supone que es diferente del valor en el estado previo; Esto incluye la ubicación del terminador nulo. Si se conoce el tamaño en bytes, escalar `s` por el tamaño del elemento.

-   `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Un puntero a una matriz de `s` elementos.  Los elementos tienen no sea válido en un estado anterior.  En posteriores al estado, los elementos existentes hasta el `c`- ésimo elemento debe ser válido.  Si se conoce el tamaño en bytes, escalar `s` y `c` por el tamaño del elemento o use el `_bytes_` variante, que se define como:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     En otras palabras, todos los elementos que existe en el búfer hasta `s` en el estado previo es válido en el estado posterior a la.  Por ejemplo:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

-   `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Un puntero a una matriz, que es leer y escribir por la función.  Es de tamaño `s` elementos, todos los cuales deben ser válidos en estado preliminar, y `c` elementos deben ser válidos en el estado posterior a la.

     El `_bytes_` variante proporciona el tamaño en bytes en lugar de elementos. Úselo solo cuando el tamaño no puede expresarse como elementos.  Por ejemplo, `char` cadenas utilizaría el `_bytes_` variante solo si la función una similar que utiliza `wchar_t` sería.

-   `_Inout_updates_z_(s)`

     Un puntero a una matriz terminada en null y que tiene un tamaño conocido. Los elementos de copia mediante el terminador nulo, que debe estar presente, debe ser válido en el estado previo y posterior a la de estado.  El valor en el estado posterior a la se supone que es diferente del valor en el estado previo; Esto incluye la ubicación del terminador nulo. Si se conoce el tamaño en bytes, escalar `s` por el tamaño del elemento.

-   `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Un puntero a una matriz de `s` elementos.  Los elementos tienen no sea válido en un estado anterior.  En posteriores al estado, los elementos existentes hasta el `c`- ésimo elemento debe ser válido.  Si se conoce el tamaño en bytes, escalar `s` y `c` por el tamaño del elemento o use el `_bytes_` variante, que se define como:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     En otras palabras, todos los elementos que existe en el búfer hasta `s` en el estado previo es válido en el estado posterior a la.  Por ejemplo:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

-   `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Un puntero a una matriz, que es leer y escribir por la función.  Es de tamaño `s` elementos, todos los cuales deben ser válidos en estado preliminar, y `c` elementos deben ser válidos en el estado posterior a la.

     El `_bytes_` variante proporciona el tamaño en bytes en lugar de elementos. Úselo solo cuando el tamaño no puede expresarse como elementos.  Por ejemplo, `char` cadenas utilizaría el `_bytes_` variante solo si la función una similar que utiliza `wchar_t` sería.

-   `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Un puntero a una matriz, que es leer y escribir por la función del tamaño `s` elementos. Se definen como equivalentes para:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     En otras palabras, todos los elementos que existe en el búfer hasta `s` en el estado previo es válido en el estado previo y posterior a la de estado.

     El `_bytes_` variante proporciona el tamaño en bytes en lugar de elementos. Úselo solo cuando el tamaño no puede expresarse como elementos.  Por ejemplo, `char` cadenas utilizaría el `_bytes_` variante solo si la función una similar que utiliza `wchar_t` sería.

-   `_In_reads_to_ptr_(p)`

     Un puntero a una matriz para que la expresión `p`  -  `_Curr_` (es decir, `p` menos `_Curr_`) se define mediante el estándar del lenguaje adecuado.  Los elementos anteriores a `p` debe ser válido en un estado anterior.

-   `_In_reads_to_ptr_z_(p)`

     Un puntero a una matriz terminada en null para el que la expresión `p`  -  `_Curr_` (es decir, `p` menos `_Curr_`) se define mediante el estándar del lenguaje adecuado.  Los elementos anteriores a `p` debe ser válido en un estado anterior.

-   `_Out_writes_to_ptr_(p)`

     Un puntero a una matriz para que la expresión `p`  -  `_Curr_` (es decir, `p` menos `_Curr_`) se define mediante el estándar del lenguaje adecuado.  Los elementos anteriores a `p` no tiene que ser válido en estado preliminar y debe ser válido en el estado posterior a la.

-   `_Out_writes_to_ptr_z_(p)`

     Un puntero a una matriz terminada en null para el que la expresión `p`  -  `_Curr_` (es decir, `p` menos `_Curr_`) se define mediante el estándar del lenguaje adecuado.  Los elementos anteriores a `p` no tiene que ser válido en estado preliminar y debe ser válido en el estado posterior a la.

## <a name="optional-pointer-parameters"></a>Parámetros de puntero opcional
 Cuando se incluye una anotación del parámetro de puntero `_opt_`, indica que el parámetro puede ser null. En caso contrario, la anotación realiza la misma que la versión que no incluya `_opt_`. Esta es una lista de los `_opt_` variantes de las anotaciones de parámetro de puntero:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>Parámetros de puntero de salida
 Los parámetros de puntero de salida requieren una notación especial al nulidad en el parámetro y la ubicación señalada para eliminar la ambigüedad.

 **Las anotaciones y descripciones**

- `_Outptr_`

   Parámetro no puede ser null, y en el estado posterior a la la ubicación al que apunta no puede ser null y debe ser válida.

- `_Outptr_opt_`

   El parámetro puede ser null, pero en el estado posterior a la la ubicación al que apunta no puede ser null y debe ser válida.

- `_Outptr_result_maybenull_`

   Parámetro no puede ser null, y en el estado posterior a la la señala a la ubicación puede ser null.

- `_Outptr_opt_result_maybenull_`

   El parámetro puede ser null, y en el estado posterior a la la señala a la ubicación puede ser null.

  En la siguiente tabla, subcadenas adicionales se insertan en el nombre de anotación y seguir calificando el significado de la anotación.  Son varias las subcadenas `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`, y `_to_`.

> [!IMPORTANT]
>  Si la interfaz que está anotando es COM, utilice el formulario de COM de estas anotaciones. No utilice las anotaciones de COM con cualquier otra interfaz de tipo.

 **Las anotaciones y descripciones**

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Ouptr_opt_result_maybenull_z_`

   El puntero devuelto tiene el `_Null_terminated_` anotación.

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   El puntero devuelto tiene semántica de COM y, por lo tanto, lleva un `_On_failure_` posteriores a la condición de que el puntero devuelto es null.

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   El puntero devuelto señala a un búfer de tamaño válido `s` elementos o bytes.

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   El puntero devuelto señala a un búfer de tamaño `s` elementos o bytes, de los cuales el primero `c` son válidos.

  Ciertas convenciones de la interfaz suponen que los parámetros de salida se compensan los riesgos en caso de error.  Salvo explícitamente código COM, se prefieren los formularios en la tabla siguiente.  Para código COM, utilice los formatos correspondientes de COM que se enumeran en la sección anterior.

  **Las anotaciones y descripciones**

- `_Result_nullonfailure_`

   Modifica otras anotaciones. El resultado se establece en null si se produce un error en la función.

- `_Result_zeroonfailure_`

   Modifica otras anotaciones. El resultado se establece en cero si se produce un error en la función.

- `_Outptr_result_nullonfailure_`

   El puntero devuelto señala a un búfer válido si la función se realiza correctamente, o null si se produce un error en la función. Esta anotación es para un parámetro que no es opcional.

- `_Outptr_opt_result_nullonfailure_`

   El puntero devuelto señala a un búfer válido si la función se realiza correctamente, o null si se produce un error en la función. Esta anotación es para un parámetro opcional.

- `_Outref_result_nullonfailure_`

   El puntero devuelto señala a un búfer válido si la función se realiza correctamente, o null si se produce un error en la función. Esta anotación es para un parámetro de referencia.

## <a name="output-reference-parameters"></a>Parámetros de referencia de salida
 Un uso común del parámetro de referencia es para los parámetros de salida.  Para los parámetros de referencia de salida simples, por ejemplo, `int&`:`_Out_` proporciona la semántica correcta.  Sin embargo, cuando el valor de salida es un puntero, por ejemplo `int *&`, como las anotaciones de puntero equivalente `_Outptr_ int **` no proporcionan la semántica correcta.  Para expresar de forma concisa la semántica de referencia de parámetros de salida para los tipos de puntero, utilice estas anotaciones compuestas:

 **Las anotaciones y descripciones**

-   `_Outref_`

     Resultado debe ser válido en el estado posterior a la y no puede ser null.

-   `_Outref_result_maybenull_`

     Resultado debe ser válido en estado posterior, pero puede ser null en el estado posterior a la.

-   `_Outref_result_buffer_(s)`

     Resultado debe ser válido en el estado posterior a la y no puede ser null. Apunta a un búfer válido de tamaño `s` elementos.

-   `_Outref_result_bytebuffer_(s)`

     Resultado debe ser válido en el estado posterior a la y no puede ser null. Apunta a un búfer válido de tamaño `s` bytes.

-   `_Outref_result_buffer_to_(s, c)`

     Resultado debe ser válido en el estado posterior a la y no puede ser null. Apunta al búfer de `s` elementos de los cuales el primero `c` son válidos.

-   `_Outref_result_bytebuffer_to_(s, c)`

     Resultado debe ser válido en el estado posterior a la y no puede ser null. Apunta al búfer de `s` bytes de los cuales el primero `c` son válidos.

-   `_Outref_result_buffer_all_(s)`

     Resultado debe ser válido en el estado posterior a la y no puede ser null. Apunta a un búfer válido de tamaño `s` elementos válidos.

-   `_Outref_result_bytebuffer_all_(s)`

     Resultado debe ser válido en el estado posterior a la y no puede ser null. Apunta a un búfer válido de `s` bytes de los elementos válidos.

-   `_Outref_result_buffer_maybenull_(s)`

     Resultado debe ser válido en estado posterior, pero puede ser null en el estado posterior a la. Apunta a un búfer válido de tamaño `s` elementos.

-   `_Outref_result_bytebuffer_maybenull_(s)`

     Resultado debe ser válido en estado posterior, pero puede ser null en el estado posterior a la. Apunta a un búfer válido de tamaño `s` bytes.

-   `_Outref_result_buffer_to_maybenull_(s, c)`

     Resultado debe ser válido en estado posterior, pero puede ser null en el estado posterior a la. Apunta al búfer de `s` elementos de los cuales el primero `c` son válidos.

-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Resultado debe ser válido en el estado posterior a la, pero puede ser null en el estado de publicación. Apunta al búfer de `s` bytes de los cuales el primero `c` son válidos.

-   `_Outref_result_buffer_all_maybenull_(s)`

     Resultado debe ser válido en el estado posterior a la, pero puede ser null en el estado de publicación. Apunta a un búfer válido de tamaño `s` elementos válidos.

-   `_Outref_result_bytebuffer_all_maybenull_(s)`

     Resultado debe ser válido en el estado posterior a la, pero puede ser null en el estado de publicación. Apunta a un búfer válido de `s` bytes de los elementos válidos.

## <a name="return-values"></a>Valores devueltos
 El valor devuelto de una función es similar a un `_Out_` parámetro, pero está en un nivel diferente de de-reference y no tiene que tener en cuenta el concepto del puntero al resultado.  Para las siguientes anotaciones, el valor devuelto es el objeto anotado, un valor escalar, un puntero a una estructura o un puntero a un búfer. Estas anotaciones tienen la misma semántica que el correspondiente `_Out_` anotación.

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="other-common-annotations"></a>Otras anotaciones comunes
 **Las anotaciones y descripciones**

-   `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     El parámetro, el campo o el resultado está en el intervalo (inclusivo) desde `low` a `hi`.  Equivalente a `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` que se aplica al objeto anotado junto con las condiciones de estado previo o posterior al estado adecuados.

    > [!IMPORTANT]
    >  Aunque los nombres contienen "en" y "out", la semántica de `_In_` y `_Out_` hacer **no** se aplican a estas anotaciones.

-   `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     El valor anotado es exactamente `expr`.  Equivalente a `_Satisfies_(_Curr_ == expr)` que se aplica al objeto anotado junto con las condiciones de estado previo o posterior al estado adecuados.

-   `_Struct_size_bytes_(size)`

     Se aplica a una declaración de clase o estructura.  Indica que un objeto válido de ese tipo puede ser mayor que el tipo declarado, con el número de bytes que se ha proporcionado por `size`.  Por ejemplo:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     El tamaño del búfer en bytes de un parámetro `pM` de tipo `MyStruct *` , a continuación, se convierte en:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>Recursos relacionados
 [Blog del equipo de análisis de código](http://go.microsoft.com/fwlink/?LinkId=251197)

## <a name="see-also"></a>Vea también

- [Uso de anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Introducción a SAL](../code-quality/understanding-sal.md)
- [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)
- [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)
- [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)
- [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funciones intrínsecas](../code-quality/intrinsic-functions.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)