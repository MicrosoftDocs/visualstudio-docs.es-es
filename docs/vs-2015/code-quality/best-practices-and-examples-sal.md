---
title: Procedimientos recomendados y ejemplos (SAL) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 5a03d2f64e3facba434de03bb18dbb2ac5bd809b
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275240"
---
# <a name="best-practices-and-examples-sal"></a>Procedimientos recomendados y ejemplos (SAL)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Estas son algunas formas de sacar el máximo partido del lenguaje de anotación de código fuente (SAL) y evitar algunos problemas comunes.  
  
## <a name="_in_"></a>\_In\_
 Si se supone que la función escribe en el elemento, use `_Inout_` en lugar de `_In_`. Esto es especialmente importante en los casos de conversión automatizada de macros anteriores a SAL. Antes de SAL, muchos programadores usaban macros como comentarios: macros que se denominaban `IN`, `OUT`, `IN_OUT`o variantes de estos nombres. Aunque se recomienda convertir estas macros en SAL, también le recomendamos que tenga cuidado al convertirlas porque el código podría haber cambiado desde que se escribió el prototipo original y la macro antigua podría no reflejar lo que hace el código. Tenga especial cuidado con la macro `OPTIONAL` comment porque se coloca incorrectamente, por ejemplo, en el lado equivocado de una coma.  
  
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
  
## <a name="_opt_"></a>\_opt\_  
 Si el autor de la llamada no puede pasar un puntero nulo, use `_In_` o `_Out_` en lugar de `_In_opt_` o `_Out_opt_`. Esto se aplica incluso a una función que comprueba sus parámetros y devuelve un error si es NULL cuando no debe ser. Aunque tener una función comprueba su parámetro para comprobar si es NULL inesperada y volver correctamente es una buena práctica de codificación defensiva, no significa que la anotación de parámetro puede ser de un tipo opcional (\_*Xxx*_opt\_).  
  
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
  
## <a name="_pre_defensive_-and-_post_defensive_"></a>\_Pre_defensive\_ y \_Post_defensive\_  
 Si una función aparece en un límite de confianza, se recomienda utilizar la anotación `_Pre_defensive_`.  El modificador "defensivo" modifica determinadas anotaciones para indicar que, en el momento de la llamada, la interfaz debe comprobarse estrictamente, pero en el cuerpo de la implementación debe asumir que se pueden pasar parámetros incorrectos. En ese caso, se prefiere el `_In_ _Pre_defensive_` en un límite de confianza para indicar que, aunque un llamador obtendrá un error si intenta pasar NULL, el cuerpo de la función se analizará como si el parámetro pudiera ser NULL y se marcará cualquier intento de desreferenciar el puntero sin comprobarlo antes de que sea NULL.  También está disponible una anotación `_Post_defensive_`, para su uso en devoluciones de llamada en las que se supone que la entidad de confianza es el llamador y el código que no es de confianza es el código llamado.  
  
## <a name="_out_writes_"></a>\_Out_writes\_  
 En el ejemplo siguiente se muestra un uso de `_Out_writes_`común.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 La anotación `_Out_writes_` significa que tiene un búfer. Tiene `cb` bytes asignados, con el primer byte inicializado al salir. Esta anotación no es estrictamente incorrecta y resulta útil expresar el tamaño asignado. Sin embargo, no indica el número de elementos que la función inicializa.  
  
 En el ejemplo siguiente se muestran tres maneras correctas de especificar completamente el tamaño exacto de la parte inicializada del búfer.  
  
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
  
## <a name="_out_-pstr"></a>\_\_ PSTR  
 El uso de `_Out_ PSTR` casi siempre es incorrecto. Esto se interpreta como tener un parámetro de salida que apunta a un búfer de caracteres y termina en NULL.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 Una anotación como `_In_ PCSTR` es común y útil. Apunta a una cadena de entrada que tiene terminación nula porque la condición previa de `_In_` permite el reconocimiento de una cadena terminada en NULL.  
  
## <a name="_in_-wchar-p"></a>\_en\_ WCHAR * p  
 `_In_ WCHAR* p` indica que hay un puntero de entrada `p` que apunta a un carácter. Sin embargo, en la mayoría de los casos, es probable que no sea la especificación prevista. En su lugar, lo que probablemente se pretende es la especificación de una matriz terminada en NULL; para ello, use `_In_ PWSTR`.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 Falta la especificación adecuada de terminación NULL. Use la versión de `STR` adecuada para reemplazar el tipo, como se muestra en el ejemplo siguiente.  
  
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
  
## <a name="_out_range_"></a>\_Out_range\_  
 Si el parámetro es un puntero y desea expresar el intervalo del valor del elemento al que apunta el puntero, use `_Deref_out_range_` en lugar de `_Out_range_`. En el ejemplo siguiente, se expresa el intervalo de * pcbFilled, no pcbFilled.  
  
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
  
 `_Deref_out_range_(0, cbSize)` no es estrictamente necesario para algunas herramientas porque se puede inferir de `_Out_writes_to_(cbSize,*pcbFilled)`, pero aquí se muestra por integridad.  
  
## <a name="wrong-context-in-_when_"></a>Contexto incorrecto en \_cuando\_  
 Otro error común es usar la evaluación posterior al estado de las condiciones previas. En el ejemplo siguiente, `_Requires_lock_held_` es una condición previa.  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 La expresión `result` hace referencia a un valor posterior al estado que no está disponible en el estado anterior.  
  
## <a name="true-in-_success_"></a>TRUE en \_correcto\_  
 Si la función se ejecuta correctamente cuando el valor devuelto es distinto de cero, use `return != 0` como condición de éxito en lugar de `return == TRUE`. Distinto de cero no implica necesariamente la equivalencia con el valor real que proporciona el compilador para `TRUE`. El parámetro para `_Success_` es una expresión y las siguientes expresiones se evalúan como equivalentes: `return != 0`, `return != false`, `return != FALSE`y `return` sin parámetros o comparaciones.  
  
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
 En el caso de una variable de referencia, la versión anterior de SAL usaba el puntero implícito como el destino de la anotación y requería la adición de una `__deref` a las anotaciones que se adjuntan a una variable de referencia. Esta versión usa el propio objeto y no requiere el `_Deref_`adicional.  
  
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
  
## <a name="annotations-on-return-values"></a>Anotaciones en valores devueltos  
 En el ejemplo siguiente se muestra un problema común en las anotaciones de valores devueltos.  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 En este ejemplo, `_Out_opt_` indica que el puntero puede ser NULL como parte de la condición previa. Sin embargo, las condiciones previas no se pueden aplicar al valor devuelto. En este caso, la anotación correcta es `_Ret_maybenull_`.  
  
## <a name="see-also"></a>Consulte también  
 [Uso de anotaciones sal para reducir defectos deC++ C/Code](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Descripción de SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores Devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar el comportamiento](../code-quality/annotating-function-behavior.md) de la función   
 [Anotar Structs y clases](../code-quality/annotating-structs-and-classes.md)   
 [Anotar el comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Especificar Cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funciones intrínsecas](../code-quality/intrinsic-functions.md)
