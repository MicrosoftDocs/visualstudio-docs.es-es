---
title: Introducción a SAL
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 56d416ce154f071804beb9b47d2623f2acee15af
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889925"
---
# <a name="understanding-sal"></a>Introducción a SAL

El lenguaje de anotación de código fuente (SAL) de Microsoft proporciona un conjunto de anotaciones que puede usar para describir cómo una función usa sus parámetros, las suposiciones que hace sobre ellos y las garantías de que lo hace al terminar. Las anotaciones se definen en el archivo de encabezado `<sal.h>`. Análisis de código de Visual Studio para C++ usa anotaciones SAL para modificar el análisis de funciones. Para obtener más información acerca de SAL 2.0 para el desarrollo de controladores de Windows, consulte [anotaciones de SAL 2.0 para Windows controladores](http://go.microsoft.com/fwlink/?LinkId=250979).

De forma nativa, C y C++ proporcionan solo maneras limitadas para los programadores a expresar de forma coherente intención e invarianza. Mediante el uso de anotaciones SAL, puede describir las funciones con más detalle para que los desarrolladores que los consumen puedan comprender mejor cómo usarlas.

## <a name="what-is-sal-and-why-should-you-use-it"></a>¿What ' s SAL y por qué debería usarlo?

En pocas palabras, SAL es una manera económica para permitir que el compilador compruebe el código para usted.

### <a name="sal-makes-code-more-valuable"></a>SAL hace que el código más valioso

SAL puede ayudar a que el diseño de código sea más comprensible tanto para los seres humanos para herramientas de análisis de código. Considere este ejemplo que muestra la función de tiempo de ejecución de C `memcpy`:

```cpp

void * memcpy(
   void *dest,
   const void *src,
   size_t count
);
```

¿Se puede saber lo que hace esta función? Cuando se implementa o se llama a una función, se deben mantener ciertas propiedades para garantizar la corrección del programa. Si se examina una declaración como la mostrada en el ejemplo, no sabe qué son. Sin anotaciones de SAL, tendría que depender de documentación o los comentarios de código. Aquí es lo que la documentación de MSDN para `memcpy` dice:

> "Bytes de src en el destino del recuento de copias. Si el origen y destino se superponen, el comportamiento de memcpy es indefinido. Use memmove para controlar las áreas superpuestas.
> **Nota sobre la seguridad:** Asegúrese de que el búfer de destino sea del mismo tamaño o mayor que el búfer de origen. Para obtener más información, consulte evitar saturaciones del búfer."

La documentación contiene un par de bits de información que sugieren que el código tiene que mantener ciertas propiedades para garantizar la exactitud del programa:

- `memcpy` copia el `count` de bytes del búfer de origen al búfer de destino.

- El búfer de destino debe ser al menos tan grande como el búfer de origen.

Sin embargo, el compilador no puede leer la documentación o comentarios informales. No sabe que hay una relación entre dos búferes y `count`, y también no eficazmente adivine sobre una relación. SAL podría proporcionar más claridad con respecto a las propiedades y la implementación de la función, como se muestra aquí:

```cpp

void * memcpy(
   _Out_writes_bytes_all_(count) void *dest,
   _In_reads_bytes_(count) const void *src,
   size_t count
);
```

Tenga en cuenta que estas anotaciones son similares a la información de la documentación de MSDN, pero son más concisas y siguen un modelo semántico. Al leer este código, puede comprender rápidamente las propiedades de esta función y a evitar problemas de seguridad de saturación del búfer. Mejor aún, los modelos semánticos que SAL proporciona pueden mejorar la eficiencia y eficacia de las herramientas de análisis de código automatizado de la detección temprana de posibles errores. Imagine que alguien escribe esta implementación con errores de `wmemcpy`:

```cpp

wchar_t * wmemcpy(
   _Out_writes_all_(count) wchar_t *dest,
   _In_reads_(count) const wchar_t *src,
   size_t count)
{
   size_t i;
   for (i = 0; i <= count; i++) { // BUG: off-by-one error
      dest[i] = src[i];
   }
   return dest;
}
```

Esta implementación contiene un error común de off a uno. Afortunadamente, el autor del código incluye la anotación de tamaño de búfer SAL: una herramienta de análisis de código podría interceptar el error mediante el análisis de esta función por sí solo.

### <a name="sal-basics"></a>Conceptos básicos SAL
 SAL define cuatro tipos básicos de parámetros, que se clasifican según el patrón de uso.

|Categoría|Anotación de parámetro|Descripción|
|--------------|--------------------------|-----------------|
|**Al llamar la función de entrada**|`_In_`|Datos se pasan a la función llamada y es tratados como de solo lectura.|
|**Entrada a llama a la función y de salida al autor de llamada**|`_Inout_`|Puede usar datos se pasan a la función y potencialmente se modifican.|
|**Salida al autor de llamada**|`_Out_`|El llamador solo proporciona espacio para la función llamada escribir en. La función llamada escribe datos en ese espacio.|
|**Salida del puntero al autor de llamada**|`_Outptr_`|Al igual que **de salida al autor de llamada**. El valor devuelto por la función llamada es un puntero.|

 Estas cuatro anotaciones básicas se pueden hacer más explícitas de varias maneras. De forma predeterminada, se supone que los parámetros de puntero anotado requerirse: deben ser distintos de NULL para la función se realice correctamente. La variación más frecuente de las anotaciones básicas indica que un parámetro de puntero es opcional, si es NULL, la función se puede autenticar correctamente al hacer su trabajo.

 Esta tabla muestra cómo distinguir entre los parámetros obligatorios y opcionales:

||Se requieren los parámetros|Los parámetros son opcionales|
|-|-----------------------------|-----------------------------|
|**Al llamar la función de entrada**|`_In_`|`_In_opt_`|
|**Entrada a llama a la función y de salida al autor de llamada**|`_Inout_`|`_Inout_opt_`|
|**Salida al autor de llamada**|`_Out_`|`_Out_opt_`|
|**Salida del puntero al autor de llamada**|`_Outptr_`|`_Outptr_opt_`|

 Estas anotaciones ayudar a identificar los posibles valores sin inicializar y usa el puntero null no válido de una manera formal y precisa. Pasar NULL a un parámetro necesario podría provocar un bloqueo, o puede provocar un código de error "error" va a devolver. En cualquier caso, la función no se puede ejecutar correctamente en hacer su trabajo.

## <a name="sal-examples"></a>Ejemplos SAL
 En esta sección se muestra ejemplos de código para las anotaciones de SAL básicos.

### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Uso de la herramienta de análisis de código de Visual Studio para encontrar defectos
 En los ejemplos, se usa la herramienta de análisis de código de Visual Studio junto con las anotaciones SAL para encontrar defectos de código. Aquí le mostramos cómo hacerlo.

#### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Usar herramientas de análisis de código de Visual Studio y SAL

1.  En Visual Studio, abra un proyecto de C++ que contiene las anotaciones de SAL.

2.  En la barra de menús, elija **compilar**, **ejecutar análisis de código en la solución**.

     Tenga en cuenta la \_en\_ ejemplo de esta sección. Si ejecuta el análisis de código en él, se muestra esta advertencia:

    > **Valor de parámetro no válido de C6387** 'pinta' puede ser '0': no cumple con las especificaciones de la función 'InCallee'.

### <a name="example-the-in-annotation"></a>Ejemplo: El \_en\_ anotación

El `_In_` anotación indica que:

-   El parámetro debe ser válido y no se modificará.

-   La función sólo se leerá desde el búfer único elemento.

-   El llamador debe proporcionar el búfer e inicialícelo.

-   `_In_` especifica "solo lectura". Un error común es aplicar `_In_` a un parámetro que debe tener el `_Inout_` anotación en su lugar.

-   `_In_` está permitido pero se omitirá el analizador de valores escalares que no son de puntero.

```cpp
void InCallee(_In_ int *pInt)
{
   int i = *pInt;
}

void GoodInCaller()
{
   int *pInt = new int;
   *pInt = 5;

   InCallee(pInt);
   delete pInt;
}

void BadInCaller()
{
   int *pInt = NULL;
   InCallee(pInt); // pInt should not be NULL
}
```

Si usa Visual Studio Code Analysis en este ejemplo, valida que los llamadores pasan un puntero no nulo a un búfer inicializado para `pInt`. En este caso, `pInt` puntero no puede ser NULL.

### <a name="example-the-inopt-annotation"></a>Ejemplo: El \_en\_opt\_ anotación

`_In_opt_` es el mismo que `_In_`, salvo que el parámetro de entrada puede ser NULL y, por lo tanto, debe comprobar la función de este.

```cpp

void GoodInOptCallee(_In_opt_ int *pInt)
{
   if(pInt != NULL) {
      int i = *pInt;
   }
}

void BadInOptCallee(_In_opt_ int *pInt)
{
   int i = *pInt; // Dereferencing NULL pointer 'pInt'
}

void InOptCaller()
{
   int *pInt = NULL;
   GoodInOptCallee(pInt);
   BadInOptCallee(pInt);
}
```

Análisis de código de Visual Studio valida que la función comprueba si es NULL antes de tener acceso el búfer.

### <a name="example-the-out-annotation"></a>Ejemplo: El \_Out\_ anotación

`_Out_` admite un escenario común en el que se pasa un puntero no NULL que apunta a un búfer de elemento y la función inicializa el elemento. El llamador no tiene que inicializar el búfer antes de la llamada; la función llamada promete inicializarlo antes de devolver.

```cpp
void GoodOutCallee(_Out_ int *pInt)
{
   *pInt = 5;
}

void BadOutCallee(_Out_ int *pInt)
{
   // Did not initialize pInt buffer before returning!
}

void OutCaller()
{
   int *pInt = new int;
   GoodOutCallee(pInt);
   BadOutCallee(pInt);
   delete pInt;
}
```

Herramienta de análisis de código de Visual Studio valida que el llamador pasa un puntero no nulo a un búfer para `pInt` y que se inicializa el búfer de la función antes de devolver.

### <a name="example-the-outopt-annotation"></a>Ejemplo: El \_Out\_opt\_ anotación

`_Out_opt_` es el mismo que `_Out_`, salvo que el parámetro puede ser NULL y, por lo tanto, debe comprobar la función de este.

```cpp
void GoodOutOptCallee(_Out_opt_ int *pInt)
{
   if (pInt != NULL) {
      *pInt = 5;
   }
}

void BadOutOptCallee(_Out_opt_ int *pInt)
{
   *pInt = 5; // Dereferencing NULL pointer 'pInt'
}

void OutOptCaller()
{
   int *pInt = NULL;
   GoodOutOptCallee(pInt);
   BadOutOptCallee(pInt);
}
```

Análisis de código de Visual Studio valida que esta función comprueba si es NULL antes de `pInt` se desreferencia y si `pInt` no es NULL, que se inicializa el búfer de la función antes de devolver.

### <a name="example-the-inout-annotation"></a>Ejemplo: El \_Inout\_ anotación

`_Inout_` se usa para anotar un parámetro de puntero que se puede cambiar la función. El puntero debe señalar a los datos inicializados válidos antes de la llamada y, aunque cambie, todavía debe tener un valor válido en la devolución. La anotación se especifica que la función puede leer y escribir en el búfer de un elemento libremente. El llamador debe proporcionar el búfer e inicialícelo.

> [!NOTE]
> Al igual que `_Out_`, `_Inout_` debe aplicar a un valor modificable.

```cpp
void InOutCallee(_Inout_ int *pInt)
{
   int i = *pInt;
   *pInt = 6;
}

void InOutCaller()
{
   int *pInt = new int;
   *pInt = 5;
   InOutCallee(pInt);
   delete pInt;
}

void BadInOutCaller()
{
   int *pInt = NULL;
   InOutCallee(pInt); // 'pInt' should not be NULL
}
```

Análisis de código de Visual Studio valida que los llamadores pasar un puntero no nulo a un búfer inicializado para `pInt`y que, antes de la devolución, `pInt` todavía no es NULL y se inicializa el búfer.

### <a name="example-the-inoutopt-annotation"></a>Ejemplo: El \_Inout\_opt\_ anotación

`_Inout_opt_` es el mismo que `_Inout_`, salvo que el parámetro de entrada puede ser NULL y, por lo tanto, debe comprobar la función de este.

```cpp
void GoodInOutOptCallee(_Inout_opt_ int *pInt)
{
   if(pInt != NULL) {
      int i = *pInt;
      *pInt = 6;
   }
}

void BadInOutOptCallee(_Inout_opt_ int *pInt)
{
   int i = *pInt; // Dereferencing NULL pointer 'pInt'
   *pInt = 6;
}

void InOutOptCaller()
{
   int *pInt = NULL;
   GoodInOutOptCallee(pInt);
   BadInOutOptCallee(pInt);
}
```

Análisis de código de Visual Studio valida que esta función comprueba si es NULL antes de tener acceso el búfer y si `pInt` no es NULL, que se inicializa el búfer de la función antes de devolver.

### <a name="example-the-outptr-annotation"></a>Ejemplo: El \_Outptr\_ anotación

`_Outptr_` se usa para anotar un parámetro que se va a devolver un puntero.  El propio parámetro no debe ser NULL y la función llamada devuelve un puntero no NULL y ese puntero apunta a los datos inicializados.

```cpp
void GoodOutPtrCallee(_Outptr_ int **pInt)
{
   int *pInt2 = new int;
   *pInt2 = 5;

   *pInt = pInt2;
}

void BadOutPtrCallee(_Outptr_ int **pInt)
{
   int *pInt2 = new int;
   // Did not initialize pInt buffer before returning!
   *pInt = pInt2;
}

void OutPtrCaller()
{
   int *pInt = NULL;
   GoodOutPtrCallee(&pInt);
   BadOutPtrCallee(&pInt);
}
```

Análisis de código de Visual Studio valida que el llamador pasa un puntero no nulo `*pInt`, y que se inicializa el búfer de la función antes de devolver.

### <a name="example-the-outptropt-annotation"></a>Ejemplo: El \_Outptr\_opt\_ anotación

`_Outptr_opt_` es el mismo que `_Outptr_`, salvo que el parámetro es opcional, el llamador puede pasar un puntero NULL para el parámetro.

```cpp
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)
{
   int *pInt2 = new int;
   *pInt2 = 6;

   if(pInt != NULL) {
      *pInt = pInt2;
   }
}

void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)
{
   int *pInt2 = new int;
   *pInt2 = 6;
   *pInt = pInt2; // Dereferencing NULL pointer 'pInt'
}

void OutPtrOptCaller()
{
   int **ppInt = NULL;
   GoodOutPtrOptCallee(ppInt);
   BadOutPtrOptCallee(ppInt);
}
```

Análisis de código de Visual Studio valida que esta función comprueba si es NULL antes de `*pInt` se desreferencia, y que se inicializa el búfer de la función antes de devolver.

### <a name="example-the-success-annotation-in-combination-with-out"></a>Ejemplo: El \_éxito\_ anotación en combinación con \_Out\_

Las anotaciones se pueden aplicar a la mayoría de los objetos.  En concreto, puede anotar una función completa.  Una de las características de una función más evidentes es que puede se realice correctamente o producirá un error. Pero, al igual que la asociación entre un búfer y su tamaño, no puede expresar C o C++ función éxito o error. Mediante el uso de la `_Success_` anotación, puede decir qué se realizó correctamente para una función es similar a.  El parámetro para el `_Success_` anotación es simplemente una expresión que cuando es true indica que la función se ha realizado correctamente. La expresión puede ser cualquier cosa que puede controlar el analizador de anotación. Los efectos de las anotaciones después de la función devuelve solo son aplicables cuando la función se realiza correctamente. Este ejemplo se muestra cómo `_Success_` interactúa con `_Out_` hacer lo correcto. Puede usar la palabra clave `return` para representar el valor devuelto.

```cpp
_Success_(return != false) // Can also be stated as _Success_(return)
bool GetValue(_Out_ int *pInt, bool flag)
{
   if(flag) {
      *pInt = 5;
      return true;
   } else {
      return false;
   }
}
```

El `_Out_` anotación hace que el análisis de código de Visual Studio para validar que el llamador pasa un puntero no nulo a un búfer para `pInt`, y que se inicializa el búfer de la función antes de devolver.

## <a name="sal-best-practice"></a>Práctica recomendada de SAL

### <a name="adding-annotations-to-existing-code"></a>Agregar anotaciones en el código existente

SAL es una tecnología eficaz y puede ayudarle a mejorar la seguridad y confiabilidad del código. Después de obtener SAL, puede aplicar la nueva habilidad para el trabajo diario. En el nuevo código, puede utilizar especificaciones de SAL por cuestiones de diseño a lo largo de; en el código anterior, puede agregar anotaciones de forma incremental y, por tanto, aumentar las ventajas de cada vez que actualice.

Ya se anotan encabezados públicos de Microsoft. Por lo tanto, se recomienda que en los proyectos primero anota las funciones del nodo de hoja y funciones que llaman a las API de Win32 para obtener el máximo provecho.

### <a name="when-do-i-annotate"></a>¿Cuándo anotar?

Estas son algunas directrices:

- Anotar todos los parámetros de puntero.

- Anotar las anotaciones del intervalo de valores para que el análisis de código puede garantizar la seguridad de búfer y el puntero.

- Anotar las reglas de bloqueos y bloqueos efectos secundarios. Para obtener más información, consulte [anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md).

- Anotar las propiedades del controlador y otras propiedades específicas de dominio.

O bien, puede anotar todos los parámetros para que su intención clara a lo largo de y para que sea fácil comprobar que se hayan realizado las anotaciones.

## <a name="related-resources"></a>Recursos relacionados

[Blog del equipo de análisis de código](http://go.microsoft.com/fwlink/p/?LinkId=251197)

## <a name="see-also"></a>Vea también

- [Uso de anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)
- [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)
- [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)
- [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)