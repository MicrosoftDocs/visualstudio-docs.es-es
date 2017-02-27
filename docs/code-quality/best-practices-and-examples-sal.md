---
title: "Procedimientos recomendados y ejemplos (SAL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Procedimientos recomendados y ejemplos (SAL)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aquí se muestran algunas maneras de conseguir lo mejor del lenguaje de anotación de código fuente \(SAL\) y de evitar algunos problemas comunes.  
  
## \_In\_  
 Si se supone que la función tiene que escribir en el elemento, utilice `_Inout_` en lugar de `_In_`.  Esto es especialmente pertinente en casos de conversión automatizada de anteriores macros a SAL.  Antes de SAL, muchos programadores utilizaban macros como comentarios \-macros que se llamaban `IN`, `OUT`, `IN_OUT`, o variaciones de estos nombres.  Aunque recomendamos que se conviertan estas macros a SAL, le animamos a tener cuidado cuando lo convierta porque el código podría haber cambiado desde que el prototipo original fue escrito y la antigua macro puede ya no reflejar lo que hace el código.  Tenga especial cuidado con la macro de comentario `OPTIONAL` porque a menudo se coloca incorrectamente \-por ejemplo, en el lado equivocado de una coma.  
  
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
  
## \_opt\_  
 Si no se permite al llamador pasar un puntero NULL, use `_In_` o `_Out_` en lugar de `_In_opt_` o de `_Out_opt_`.  Esto se aplica incluso a una función que comprueba sus parámetros y devuelve un error si es NULL cuando no debe ser.  Aunque es una buena práctica de codificación defensiva tener un control de función comprueba el parámetro por si hay NULL inesperados y retornos correctos, no significa que la anotación del parámetro pueda ser de un tipo opcional \(\_*Xxx*\_opt\_\).  
  
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
  
## \_Pre\_defensive\_ y \_Post\_defensive\_  
 Si una función aparece en un límite de confianza, se recomienda usar la anotación de `_Pre_defensive_` .  El modificador “defensivo” modifica determinadas anotaciones para indicar que, en un punto de la llamada, la interfaz se debe comprobar estrictamente, pero en el cuerpo de la implementación debe suponer que los parámetros incorrectos pueden pasarse.  En ese caso, `_In_ _Pre_defensive_` está preferido en un límite de confianza para indicar que aunque un llamador produzca un error si intenta pasar NULL, el cuerpo de la función se analiza como si el parámetro puede ser NULL, y cualquier de\- referencia de los intentos el puntero sin primero comprobar NULL se marca\/marcada.  Una anotación de `_Post_defensive_` también está disponible, para su uso en las devoluciones de llamada donde se supone el entidad de confianza para ser el llamador y el código que no es de confianza es el código denominado.  
  
## \_Out\_writes\_  
 El ejemplo siguiente demuestra un uso incorrecto común de `_Out_writes_`.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 La anotación `_Out_writes_` significa que tiene un búfer.  Tiene bytes `cb` asignados, con el primer byte inicializado en la salida.  Esta anotación no es estrictamente incorrecta y es útil expresar el tamaño asignado.  Sin embargo, no indica cuántos elementos son inicializados por la función.  
  
 El siguiente de ejemplo muestra tres maneras correctas de especificar el tamaño exacto de la parte inicializada del búfer.  
  
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
  
## \_Out\_ PSTR  
 El uso de `_Out_ PSTR` casi siempre es incorrecto.  Se interpreta esto como tener un parámetro de salida que señala un carácter almacenado en búfer y se termina en null.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 Una anotación como `_In_ PCSTR` es común y útil.  Apunta a una cadena de entrada que tiene una terminación NULL porque la condición previa de `_In_` permite el reconocimiento de una cadena terminada en NULL.  
  
## \_In\_ WCHAR\* p  
 `_In_ WCHAR* p` indica que hay un puntero `p` de entrada que señala a un carácter.  Sin embargo, en la mayoría de los casos, es probable que no sea la especificación esperada.  En su lugar, lo que se espera probablemente es la especificación de una matriz terminada en NULL; para ello, use `_In_ PWSTR`.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 Es común la falta de la especificación de terminación NULL adecuada.  Utilice la versión adecuada de `STR` para reemplazar el tipo, como se muestra en el ejemplo siguiente.  
  
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
  
## \_Out\_range\_  
 Si el parámetro es un puntero y se desea expresar el intervalo de valores de elemento comunicado por el puntero, utilice `_Deref_out_range_` en lugar de `_Out_range_`.  En el ejemplo siguiente, el intervalo de \*pcbFilled se expresa, no pcbFilled.  
  
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
  
 `_Deref_out_range_(0, cbSize)` no es estrictamente necesaria para algunas herramientas porque se puede deducir de `_Out_writes_to_(cbSize,*pcbFilled)`, pero se muestra aquí para mayor precisión.  
  
## Contexto incorrecto en \_When\_  
 Otro error común es utilizar la evaluación del estado posterior para las condiciones previas.  En el ejemplo siguiente, `_Requires_lock_held_` es una condición previa.  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 La expresión `result` hace referencia a un valor de estado posterior que no está disponible en un estado previo.  
  
## TRUE en \_Success\_  
 Si la función tiene éxito cuando el valor devuelto es distinto de cero, utilice `return != 0` como condición correcta en lugar de `return == TRUE`.  No cero no significa necesariamente una equivalencia al valor real que el compilador proporciona para `TRUE`.  El parámetro a `_Success_` es una expresión, y las siguientes expresiones se evalúan como equivalentes: `return != 0`, `return != false`, `return != FALSE`, y `return` sin parámetros o comparaciones.  
  
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
  
## Variable de referencia  
 Para una variable de referencia, la versión anterior SAL utilizó el puntero implícitamente como destino de anotaciones y requería la adición de `__deref` a las anotaciones que adjuntaron a una variable de referencia.  Esta versión usa el propio objeto y no requiere el `_Deref_`adicional.  
  
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
  
## Anotaciones en valores devueltos  
 El ejemplo siguiente muestra un problema común al devolver valores de anotaciones.  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 En este ejemplo, `_Out_opt_` indica que el puntero podría ser NULL como parte de la condición previa.  Sin embargo, las condiciones previas no se pueden aplicar al valor devuelto.  En este caso, la anotación correcta es `_Ret_maybenull_`.  
  
## Vea también  
 [Utilizar anotaciones SAL para reducir defectos de código de C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Introducción a SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)   
 [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)   
 [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funciones intrínsecas](../code-quality/intrinsic-functions.md)