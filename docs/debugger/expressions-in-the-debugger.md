---
title: Expresiones en el depurador | Microsoft Docs
ms.date: 02/07/2017
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 596f36457627e8da435c2a8c4223487aa35c60f4
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227399"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Expresiones en el depurador de Visual Studio
El depurador de Visual Studio incluye evaluadores de expresión que funcionan cuando escribe una expresión en el cuadro de diálogo **Inspección rápida** , la ventana **Inspección** o la ventana **Inmediato** . Los evaluadores de expresión también se utilizan en la ventana **Puntos de interrupción** y en muchos otros lugares en el depurador.

Las secciones siguientes se describen las limitaciones de la evaluación de expresiones de idiomas compatibles con Visual Studio.

## <a name="f-expressions-are-not-supported"></a>No se admiten las expresiones de F#
No se reconocen las expresiones de F#. Si va a depurar código F#, es necesario traducir las expresiones a la sintaxis de C# antes de escribirlas en una ventana o un cuadro de diálogo de depurador. Al traducir expresiones de F# a C#, recuerde que C# usa el operador `==` para comprobar la igualdad, mientras que F# usa `=`.

## <a name="c-expressions"></a>Expresiones de C++
Para obtener información sobre el uso de operadores de contexto con las expresiones de C++, vea [Context Operator (C++)](../debugger/context-operator-cpp.md).

### <a name="unsupported-expressions-in-c"></a>Expresiones no admitidas en C++

#### <a name="constructors-destructors-and-conversions"></a>Constructores, destructores y conversiones
No puede llamar a un constructor o destructor de un objeto, ya sea de manera explícita como implícita. Por ejemplo, la siguiente expresión llama explícitamente a un constructor y se produce un mensaje de error:

```C++
my_date( 2, 3, 1985 )
```

No se puede llamar a una función de conversión si el destino de la conversión es una clase. Dicha conversión implica la construcción de un objeto. Por ejemplo, si `myFraction` es una instancia de `CFraction`, que define el operador de la función de conversión `FixedPoint`, la siguiente expresión genera un error:

```C++
(FixedPoint)myFraction
```

No se puede llamar a nuevos operadores ni eliminarlos. Por ejemplo, no se admiten expresiones como la siguiente:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Macros de preprocesador
El depurador no admite las macros de preprocesador. Por ejemplo, si una constante `VALUE` se declara como: `#define VALUE 3`, no puede usar `VALUE` en la ventana **Inspección** . Para evitar esta limitación, debe reemplazar `#define`con enumeraciones y funciones siempre que sea posible.

### <a name="using-namespace-declarations"></a>uso de declaraciones de espacios de nombres
No se pueden usar las declaraciones `using namespace` .  Para obtener acceso a un nombre de tipo o variable fuera del espacio de nombres actual, debe usar el nombre completo.

### <a name="anonymous-namespaces"></a>Espacios de nombres anónimos
No se admiten los espacios de nombres anónimos. Si tiene el siguiente código, no se puede agregar `test` a la ventana Inspección:

```C++
namespace mars
{
    namespace
    {
        int test = 0;
    }
}
int main()
{
    // Adding a watch on test does not work.
    mars::test++;
    return 0;
}

```

### <a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Usar funciones intrínsecas del depurador para mantener el estado
Las funciones intrínsecas del depurador proporcionan una manera de llamar a determinadas funciones de C/C++ en expresiones sin cambiar el estado de la aplicación.

Funciones intrínsecas del depurador:

- Se garantiza que son seguras: ejecutar una función intrínseca del depurador no dañará el proceso que se está depurando.

- Se permiten en todas las expresiones, incluso en escenarios en los que no se permiten efectos secundarios ni evaluación de funciones.

- Funcionan en escenarios en los que no son posibles llamadas de función estándar, por ejemplo la depuración de un minivolcado.

  Las funciones intrínsecas del depurador también pueden crear expresiones de evaluación más adecuadas. Por ejemplo, `strncmp(str, "asd")` es mucho más fácil de escribir en una condición de punto de interrupción que `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`. )

|Área|Funciones intrínsecas|
|----------|-------------------------|
|**Longitud de la cadena**|strlen, wcslen, strnlen, wcsnlen|
|**Comparación de cadena**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsicmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|
|**Búsqueda de cadena**|strchr, wcschr, strstr, wcsstr|
|**Win32**|GetLastError(), TlsGetValue()|
|**Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Estas funciones requieren el proceso que se depura para ejecutarse en Windows 8. La depuración de archivos de volcado de memoria generados por un dispositivo con Windows 8 también requiere que el equipo de Visual Studio ejecute Windows 8. Sin embargo, si depura un dispositivo con Windows 8 de forma remota, el equipo de Visual Studio puede ejecutar Windows 7.|
|**Varios**|__log2<br /><br /> Devuelve el logaritmo en base dos de un entero especificado, redondeado al entero más bajo más próximo.|

## <a name="ccli---unsupported-expressions"></a>C++/CLI: Expresiones no admitidas

- No se admiten las conversiones que afectan a punteros o las conversiones definidas por el usuario.

- No se admiten las comparaciones y asignaciones de objetos

- No se admiten los operadores y las funciones sobrecargadas.

- No se admiten las conversiones boxing y unboxing.

- No se admite el operador`Sizeof` .

## <a name="c---unsupported-expressions"></a>C#: Expresiones no admitidas

### <a name="dynamic-objects"></a>Objetos dinámicos
Puede usar variables en expresiones del depurador que tengan tipos estáticos como dinámicos. Cuando los objetos que implementan <xref:System.Dynamic.IDynamicMetaObjectProvider> se evalúan en la ventana Inspección, se agrega el nodo Vista dinámica. El nodo Vista dinámica muestra los miembros de objetos, pero no permite editar los valores de los miembros.

No se admiten las características siguientes de los objetos dinámicos:

- Los operadores compuestos `+=`, `-=`, `%=`, `/=`y `*=`

- Muchas conversiones, incluidas las conversiones numéricas y las conversiones de argumentos de tipos

- Llamadas a métodos con más de dos argumentos

- Captadores de propiedades con más de dos argumentos

- Establecedores de propiedades con argumentos

- Asignación a un indizador

- Operadores booleanos `&&` y `||`

### <a name="anonymous-methods"></a>Métodos anónimos
No se admite la creación de nuevos métodos anónimos.

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic: Expresiones no admitidas

### <a name="dynamic-objects"></a>Objetos dinámicos
Puede usar variables en expresiones del depurador que tengan tipos estáticos como dinámicos. Cuando los objetos que implementan la interfaz <xref:System.Dynamic.IDynamicMetaObjectProvider> se evalúan en la ventana Inspección, se agrega el nodo Vista dinámica. El nodo Vista dinámica muestra los miembros de objetos, pero no permite editar los valores de los miembros.

No se admiten las características siguientes de los objetos dinámicos:

- Los operadores compuestos `+=`, `-=`, `%=`, `/=`y `*=`

- Muchas conversiones, incluidas las conversiones numéricas y las conversiones de argumentos de tipos

- Llamadas a métodos con más de dos argumentos

- Captadores de propiedades con más de dos argumentos

- Establecedores de propiedades con argumentos

- Asignación a un indizador

- Operadores booleanos `&&` y `||`

### <a name="local-constants"></a>Constantes locales
No se admiten constantes locales.

### <a name="import-aliases"></a>Alias de importación
No se admiten los alias de importación.

### <a name="variable-declarations"></a>Declaraciones de variables
No se pueden declarar nuevas variables explícitas en las ventanas del depurador. Sin embargo, puede asignar nuevas variables implícitas en la ventana **Inmediato** . Estas variables implícitas se encuentran en el ámbito de la sesión del depurador y no están accesibles fuera del depurador. Por ejemplo, la instrucción `o = 5` crea implícitamente una nueva variable `o` y le asigna el valor 5. Estas variables implícitas son de tipo **Object** , a menos que el depurador pueda deducir el tipo.

### <a name="unsupported-keywords"></a>Palabras clave no admitidas

- `AddressOf`

- `End`

- `Error`

- `Exit`

- `Goto`

- `On Error`

- `Resume`

- `Return`

- `Select/Case`

- `Stop`

- `SyncLock`

- `Throw`

- `Try/Catch/Finally`

- `With`

- Palabras clave de espacio de nombres o de módulo como, por ejemplo, `End Sub` o `Module`.

## <a name="see-also"></a>Vea también
[Especificadores de formato en C++](../debugger/format-specifiers-in-cpp.md)  
[Operador de contexto (C++)](../debugger/context-operator-cpp.md)  
[Especificadores de formato en C#](../debugger/format-specifiers-in-csharp.md)  
[Pseudovariables](../debugger/pseudovariables.md)
