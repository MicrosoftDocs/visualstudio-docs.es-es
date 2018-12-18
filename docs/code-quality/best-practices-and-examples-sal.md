---
title: Procedimientos recomendados y ejemplos (SAL)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 7922d381d61d40c20fa69859dd091849684723b2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899973"
---
# <a name="best-practices-and-examples-sal"></a>Procedimientos recomendados y ejemplos (SAL)
Estas son algunas formas de sacar el máximo fuera del lenguaje de anotación de código (SAL) de origen y evitar algunos problemas comunes.

## <a name="in"></a>\_In\_

Si se supone que la función para escribir en el elemento, utilice `_Inout_` en lugar de `_In_`. Esto es especialmente importante en los casos de conversión automatizada de macros anteriores a la SAL. Antes de SAL, muchos programadores usaban macros como comentarios, las macros que se denominaron `IN`, `OUT`, `IN_OUT`, o las variantes de estos nombres. Aunque se recomienda que convierta estas macros en SAL, también le recomendamos que tenga cuidado al convertir porque el código podría haber cambiado desde que se escribió el prototipo original y la macro anterior ya no es posible que refleje lo que hace el código. Tenga especial cuidado la `OPTIONAL` comentar macro porque se encuentra incorrectamente con frecuencia, por ejemplo, en el lado equivocado de una coma.

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

## <a name="opt"></a>\_opt\_

Si el llamador no tiene permiso para pasar un puntero nulo, utilice `_In_` o `_Out_` en lugar de `_In_opt_` o `_Out_opt_`. Esto se aplica incluso a una función que comprueba sus parámetros y devuelve un error si es NULL cuando no debería estar. Aunque tener una función comprobar su parámetro nulo inesperado y devolver correctamente es una buena práctica de programación defensiva, no significa que la anotación del parámetro puede ser de tipo opcional (`_*Xxx*_opt_`).

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

## <a name="predefensive-and-postdefensive"></a>\_Pre\_defensivas\_ y \_Post\_defensivas\_

Si aparece una función en un límite de confianza, se recomienda usar el `_Pre_defensive_` anotación.  El modificador "defensivo" modifica determinadas anotaciones para indicar que, en el punto de llamada, la interfaz debe comprobarse estrictamente, pero en el cuerpo de la implementación, debe asumir que pueden haber pasado parámetros incorrectos. En ese caso, `_In_ _Pre_defensive_` se prefiere en un límite de confianza para indicar que aunque un autor de llamada producirá un error si se intenta pasar NULL, el cuerpo de la función se analizará como si el parámetro puede ser NULL y cualquier intento de hacer referencia a anular el puntero sin primero se marcará la comprobación de NULL.  Un `_Post_defensive_` anotación también está disponible para su uso en las devoluciones de llamada que la entidad de confianza se supone que el llamador y el código no confiable es el código llamado.

## <a name="outwrites"></a>\_Out\_escribe\_

En el ejemplo siguiente se muestra de forma incorrecta comunes `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

La anotación `_Out_writes_` significa que tiene un búfer. Tiene `cb` bytes asignados por el primer byte que se inicializa en la salida. Esta anotación no es estrictamente incorrecta y resulta útil expresar el tamaño asignado. Sin embargo, saber cuántos elementos se inicializan por la función.

En el ejemplo siguiente se muestra tres formas correctas para especificar el tamaño exacto de la parte del búfer inicializado.

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

El uso de `_Out_ PSTR` casi siempre es incorrecto. Esto se interpreta como si tuviera un parámetro de salida que apunta a un búfer de caracteres y es terminada en NULL.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

Al igual que una anotación `_In_ PCSTR` es habitual y útil. Apunta a una cadena de entrada con terminación NULL porque la condición previa de `_In_` permite que el reconocimiento de una cadena terminada en NULL.

## <a name="in-wchar-p"></a>\_En\_ WCHAR * p

`_In_ WCHAR* p` indica que hay un puntero de entrada `p` que apunta a un carácter. Sin embargo, en la mayoría de los casos, esto probablemente no es la especificación que sirve. En su lugar, lo que probablemente se pretende es la especificación de una matriz terminada en NULL; Para ello, utilice `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

Falta la especificación apropiada de terminación NULL es habitual. Utilice la sintaxis de `STR` versión para reemplazar el tipo, como se muestra en el ejemplo siguiente.

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

## <a name="outrange"></a>\_Out\_intervalo\_

Si el parámetro es un puntero y desea expresar el intervalo del valor del elemento al que apunta el puntero, usar `_Deref_out_range_` en lugar de `_Out_range_`. En el ejemplo siguiente, el intervalo de * pcbFilled se expresa, no pcbFilled.

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

 `_Deref_out_range_(0, cbSize)` no es estrictamente necesaria para algunas herramientas ya que se puede inferir de `_Out_writes_to_(cbSize,*pcbFilled)`, pero se muestra aquí por integridad.

## <a name="wrong-context-in-when"></a>En un contexto incorrecto \_cuando\_

Otro error común es usar el estado posterior a la evaluación para las condiciones previas. En el ejemplo siguiente, `_Requires_lock_held_` es una condición previa.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

 La expresión `result` hace referencia a un valor de estado posterior a la que no está disponible en un estado anterior.

## <a name="true-in-success"></a>TRUE en \_correcto\_

Si la función se realiza correctamente cuando el valor devuelto es distinto de cero, use `return != 0` como la condición correcta en lugar de `return == TRUE`. Distinto de cero no significa necesariamente equivalencia con el valor real que proporciona el compilador para `TRUE`. El parámetro `_Success_` es una expresión y se evalúan las expresiones siguientes como equivalentes: `return != 0`, `return != false`, `return != FALSE`, y `return` sin parámetros o comparaciones.

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

Para una variable de referencia, la versión anterior de SAL utiliza el puntero implícito como el destino de la anotación y requiere la adición de un `__deref` a las anotaciones que se adjunta a una variable de referencia. Esta versión usa el objeto en Sí y no requiere la adición `_Deref_`.

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

El ejemplo siguiente muestra un problema común en las anotaciones de valor devuelto.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

En este ejemplo, `_Out_opt_` indica que el puntero puede ser NULL como parte de la condición previa. Sin embargo, las condiciones previas no se puede aplicar al valor devuelto. En este caso, la anotación correcta es `_Ret_maybenull_`.

## <a name="see-also"></a>Vea también

[Utilizar anotaciones SAL para reducir defectos de código de c/c ++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
[comprender SAL](../code-quality/understanding-sal.md)
[anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md) 
 [Anotar el comportamiento de la función](../code-quality/annotating-function-behavior.md)
[anotar Structs y clases](../code-quality/annotating-structs-and-classes.md)
[anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md) 
 [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)
[funciones intrínsecas](../code-quality/intrinsic-functions.md)