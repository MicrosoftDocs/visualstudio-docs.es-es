---
title: Procedimientos recomendados y ejemplos (SAL)
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: d26f5329f530af2d6547f44b73ded82c5db53f4f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="best-practices-and-examples-sal"></a>Procedimientos recomendados y ejemplos (SAL)
Aquí se muestran algunas maneras de sacar el máximo partido fuera del lenguaje de anotación de código fuente (SAL) y evitar algunos problemas comunes.

## <a name="in"></a>\_In\_

Si la función se debe para escribir en el elemento, utilice `_Inout_` en lugar de `_In_`. Esto es especialmente importante en los casos de conversión automatizada de macros anteriores a SAL. Antes de SAL, muchos programadores utilizan macros como comentarios, las macros que se denominaron `IN`, `OUT`, `IN_OUT`, o las variantes de estos nombres. Aunque se recomienda que convierten estas macros a SAL, también le recomendamos que tenga cuidado al convertirlos porque el código podría haber cambiado desde que se escribió el prototipo original y la macro anterior ya no es posible que refleje lo que hace el código. Tenga especial cuidado al `OPTIONAL` comentario macro porque se coloca incorrectamente con frecuencia, por ejemplo, en el lado incorrecto de una coma.

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="opt"></a>\_participación\_

Si el llamador no tiene permiso para pasar de un puntero nulo, use `_In_` o `_Out_` en lugar de `_In_opt_` o `_Out_opt_`. Esto se aplica incluso a una función que comprueba sus parámetros y devuelve un error si es NULL cuando no debería estar. Aunque tener una función comprobar su parámetro un valor nulo inesperado y devolver correctamente es una buena práctica de codificación defensiva, eso no significa que la anotación del parámetro puede ser de tipo opcional (`_*Xxx*_opt_`).

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}

```

## <a name="predefensive-and-postdefensive"></a>\_Pre\_estable\_ y \_Post\_estable\_

Si una función aparece en un límite de confianza, se recomienda que realice la `_Pre_defensive_` anotación.  El modificador "estable" modifica determinadas anotaciones para indicar, en el momento de la llamada, la interfaz debe comprobarse estrictamente, pero en el cuerpo de la implementación, debe asumir que pueden pasarse parámetros incorrectos. En ese caso, `_In_ _Pre_defensive_` es preferible en un límite de confianza para indicar que aunque un llamador obtendrán un error si intenta pasar NULL, el cuerpo de la función se analizará como si el parámetro puede ser NULL y cualquier intento de hacer referencia a anular el puntero sin primero se marcará la comprobación de NULL.  Un `_Post_defensive_` anotación también está disponible para su uso en las devoluciones de llamada que el usuario de confianza se supone que el autor de llamada y el código no confiable es el código llamado.

## <a name="outwrites"></a>\_Out\_escribe\_

En el ejemplo siguiente se muestra un uso indebido comunes de `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);

```

La anotación `_Out_writes_` significa que tienen un búfer. Tiene `cb` bytes asignados por el primer byte que se inicializa al salir. Esta anotación no es estrictamente incorrecta y resulta útil expresar el tamaño asignado. Sin embargo, saber cuántos elementos se inicializan por la función.

En el ejemplo siguiente se muestra tres formas correctas para especificar el tamaño exacto de la parte inicializado del búfer.

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);

```

## <a name="out-pstr"></a>\_Out\_ PSTR

El uso de `_Out_ PSTR` casi siempre es incorrecto. Esto se interpreta como si tuviera un parámetro de salida que apunta a un búfer de caracteres y está terminada en NULL.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);

```

Al igual que una anotación `_In_ PCSTR` es habitual y útil. Apunta a una cadena de entrada con terminación NULL porque la condición previa de `_In_` permite que el reconocimiento de una cadena terminada en NULL.

## <a name="in-wchar-p"></a>\_En\_ WCHAR * p

`_In_ WCHAR* p` indica que hay un puntero de entrada `p` que apunta a un carácter. Sin embargo, en la mayoría de los casos, esto probablemente no es la especificación que se ha previsto. En su lugar, lo que probablemente se esperaba es la especificación de una matriz terminada en NULL; Para ello, utilice `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);

```

Falta la especificación de finalización en NULL adecuada es habitual. Utilice la sintaxis de `STR` versión para reemplazar el tipo, como se muestra en el ejemplo siguiente.

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}

```

## <a name="outrange"></a>\_Out_range\_

Si el parámetro es un puntero y desea expresar el intervalo del valor del elemento al que apunta el puntero, usar `_Deref_out_range_` en lugar de `_Out_range_`. En el ejemplo siguiente, el intervalo de * se expresa pcbFilled, no pcbFilled.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);

```

 `_Deref_out_range_(0, cbSize)` no es estrictamente necesaria para algunas herramientas porque se puede inferir a partir `_Out_writes_to_(cbSize,*pcbFilled)`, pero se muestra aquí por integridad.

## <a name="wrong-context-in-when"></a>Contexto equivocado en \_cuando\_

Otro error común es usar la evaluación posterior al estado de las condiciones previas. En el ejemplo siguiente, `_Requires_lock_held_` es una condición previa.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);

```

 La expresión `result` hace referencia a un valor de estado posterior a la que no está disponible en estado previo.

## <a name="true-in-success"></a>TRUE en \_correcto\_

Si la función se realiza correctamente cuando el valor devuelto es distinto de cero, use `return != 0` como la condición correcta en lugar de `return == TRUE`. NonZero no significa necesariamente equivalencia con el valor real que el compilador proporciona para `TRUE`. El parámetro `_Success_` es una expresión y se evalúan las expresiones siguientes son equivalentes: `return != 0`, `return != false`, `return != FALSE`, y `return` sin parámetros ni comparaciones.

```cpp

// Incorrect
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

```

## <a name="reference-variable"></a>Variable de referencia

Para una variable de referencia, la versión anterior de SAL utiliza el puntero implícito como el destino de la anotación y requiere la adición de un `__deref` a las anotaciones que se adjunta a una variable de referencia. Esta versión usa el objeto propiamente dicho y no requiere la adición `_Deref_`.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);

```

## <a name="annotations-on-return-values"></a>Anotaciones en los valores devueltos

En el ejemplo siguiente se muestra un problema común en las anotaciones de valor devuelto.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();

```

En este ejemplo, `_Out_opt_` indica que el puntero puede ser NULL como parte de la condición previa. Sin embargo, las condiciones previas no se puede aplicar al valor devuelto. En este caso, la anotación correcta es `_Ret_maybenull_`.

## <a name="see-also"></a>Vea también

[Utilizar anotaciones SAL para reducir defectos de código de C o C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
[descripción SAL](../code-quality/understanding-sal.md)
[anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md) 
 [Anotar el comportamiento de la función](../code-quality/annotating-function-behavior.md)
[anotar Structs y clases](../code-quality/annotating-structs-and-classes.md)
[anotar el comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md) 
 [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)
[funciones intrínsecas](../code-quality/intrinsic-functions.md)