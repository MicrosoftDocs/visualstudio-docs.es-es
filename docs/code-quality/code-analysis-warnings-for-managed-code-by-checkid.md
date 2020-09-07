---
title: Información general sobre las reglas de calidad del código
ms.date: 08/27/2020
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1005
- CA1008
- CA1010
- CA1012
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1021
- CA1024
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1036
- CA1040
- CA1041
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1058
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1066
- CA1067
- CA1068
- CA1069
- CA1070
- CA1200
- CA1303
- CA1304
- CA1305
- CA1307
- CA1308
- CA1309
- CA1310
- CA1401
- CA1417
- CA1501
- CA1502
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1700
- CA1707
- CA1708
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- CA1716
- CA1717
- CA1720
- CA1721
- CA1724
- CA1725
- CA1801
- CA1802
- CA1805
- CA1806
- CA1810
- CA1812
- CA1813
- CA1814
- CA1815
- CA1816
- CA1819
- CA1820
- CA1821
- CA1822
- CA1823
- CA1824
- CA1825
- CA1826
- CA1827
- CA1828
- CA1829
- CA1830
- CA1831
- CA1832
- CA1833
- CA1834
- CA1835
- CA1836
- CA1837
- CA1838
- CA2000
- CA2002
- CA2007
- CA2008
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
- CA2016
- CA2100
- CA2101
- CA2109
- CA2119
- CA2153
- CA2200
- CA2201
- CA2207
- CA2208
- CA2211
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2219
- CA2225
- CA2226
- CA2227
- CA2229
- CA2231
- CA2234
- CA2235
- CA2237
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA2247
- CA2248
- CA2249
- CA2300
- CA2301
- CA2302
- CA2305
- CA2310
- CA2311
- CA2312
- CA2315
- CA2321
- CA2322
- CA2326
- CA2327
- CA2328
- CA2329
- CA2330
- CA2350
- CA2351
- CA2352
- CA2353
- CA2354
- CA2355
- CA2356
- CA2361
- CA2362
- CA3001
- CA3002
- CA3003
- CA3004
- CA3005
- CA3006
- CA3007
- CA3008
- CA3009
- CA3010
- CA3011
- CA3012
- CA3061
- CA3075
- CA3076
- CA3077
- CA5347
- CA5350
- CA5351
- CA5359
- CA5360
- CA5361
- CA5362
- CA5363
- CA5364
- CA5365
- CA5366
- CA5367
- CA5368
- CA5369
- CA5370
- CA5371
- CA5372
- CA5373
- CA5374
- CA5375
- CA5376
- CA5377
- CA5378
- CA5379
- CA5380
- CA5381
- CA5382
- CA5383
- CA5384
- CA5385
- CA5386
- CA5387
- CA5388
- CA5389
- CA5390
- CA5391
- CA5392
- CA5393
- CA5394
- CA5395
- CA5397
- CA5398
- CA5399
- CA5400
- CA5401
- CA5402
- CA5403
- IL3000
- IL3001
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8e4b728fab6eb47501bb0d1bb752d22c0c29a8b4
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509450"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Advertencias de análisis de código para código administrado por CheckId

En la tabla siguiente se enumeran las advertencias de análisis de código para código administrado ordenadas por el identificador CheckId de la advertencia.

| Identificador de comprobación | Advertencia | Descripción |
|---------| - | - |
| CA1000 | [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000.md) | Cuando se llama a un miembro estático de un tipo genérico, se debe especificar el argumento de tipo correspondiente a ese tipo. Cuando se llama a un miembro de instancia genérico que no admite la interferencia, se debe especificar el argumento de tipo para el miembro. En estos dos casos, la sintaxis para especificar el argumento de tipo es diferente y resulta fácil confundirse. |
| CA1001 | [CA1001: Los tipos que poseen campos descartables deben ser descartables](../code-quality/ca1001.md) | Una clase declara e implementa un campo de instancia que es de tipo System.IDisposable y la clase no implementa IDisposable. Una clase que declara un campo IDisposable posee indirectamente un recurso no administrado y debería implementar la interfaz IDisposable. |
| CA1002 | [CA1002: No exponer listas genéricas](../code-quality/ca1002.md) | System. Collections. Generic. List< (of \<(T> ) >) es una colección genérica diseñada para el rendimiento, no para la herencia. Por consiguiente, List no contiene ningún miembro virtual. En su lugar, se debe exponer las colecciones genéricas diseñadas para herencia. |
| CA1003 | [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003.md) |Un tipo contiene un delegado que devuelve void cuya firma contiene dos parámetros (el primero un objeto y el segundo un tipo asignable a EventArgs), y el ensamblado que lo contiene está dirigido a Microsoft .NET Framework 2.0. |
| CA1005 | [CA1005: Evitar los parámetros excesivos en tipos genéricos](../code-quality/ca1005.md) | Cuantos más parámetros type contenga un tipo genérico, más difícil resulta saber y recordar qué representa cada uno de ellos. Normalmente, es obvio con un parámetro de tipo, como en la lista \<T> , y en determinados casos que tienen dos parámetros de tipo, como en el diccionario \<TKey, TValue> . Sin embargo, si hay más de dos parámetros de tipo, la dificultad se vuelve demasiado grande para la mayoría de los usuarios. |
| CA1008 | [CA1008: Las enumeraciones deben tener un valor igual a cero](../code-quality/ca1008.md) | El valor predeterminado de una enumeración no inicializada, igual que otros tipos de valor, es cero. Una enumeración con atributo y sin marcadores debería definir un miembro con el valor de cero de modo que el valor predeterminado sea un valor válido de la enumeración. Si una enumeración a la que se le haya aplicado el atributo FlagsAttribute define un miembro con valor cero, su nombre debe ser "None" para indicar que no se han establecido valores en la enumeración. |
| CA1010 | [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010.md) | Para ampliar la utilidad de una colección, implemente una de las interfaces de colección genéricas. Entonces podrá utilizar la colección para rellenar tipos de colecciones genéricas. |
| CA1012 | [CA1012: Los tipos abstractos no deberían tener constructores](../code-quality/ca1012.md) | Los tipos derivados pueden llamar solo a los constructores de tipos abstractos. Puesto que los constructores públicos crean instancias de un tipo y no se pueden crear instancias de un tipo abstracto, no es correcto diseñar un tipo abstracto con un constructor público. |
| CA1014 | [CA1014: Marcar los ensamblados con CLSCompliantAttribute](../code-quality/ca1014.md) | La Common Language Specification (CLS) define las restricciones de nomenclatura, los tipos de datos y las reglas a las que los ensamblados deben ajustarse si se van a utilizar los lenguajes de programación. Los procedimientos de diseño establecen que todos los ensamblados deben indicar explícitamente la conformidad a CLS mediante el atributo <xref:System.CLSCompliantAttribute>. Si este atributo no está presente en un ensamblado, el ensamblado no es conforme. |
| CA1016 | [CA1016: Marcar los ensamblados con AssemblyVersionAttribute](../code-quality/ca1016.md) | .NET usa el número de versión para identificar de forma única un ensamblado y enlazar a los tipos de ensamblados con nombre seguro. El número de versión se utiliza junto con la versión y la directiva del fabricante. De forma predeterminada, las aplicaciones sólo se ejecutan con la versión de ensamblado con la que se compilaron. |
| CA1017 | [CA1017: Marcar los ensamblados con ComVisibleAttribute](../code-quality/ca1017.md) |ComVisibleAttribute determina cómo obtienen acceso los clientes COM al código administrado. Los procedimientos de diseño recomendados dictan que los ensamblados indican explícitamente la visibilidad COM. La visibilidad COM se puede establecer para un ensamblado completo y, a continuación, se puede invalidar para los tipos individuales y los miembros de tipo. Si este atributo no está presente, el contenido del ensamblado es visible para los clientes COM. |
| CA1018 | [CA1018: Marcar atributos con AttributeUsageAttribute](../code-quality/ca1018.md) | Cuando defina un atributo personalizado, márquelo utilizando AttributeUsageAttribute para indicar dónde se puede aplicar en el código fuente. El significado de un atributo y el uso que se le va a dar determinará sus ubicaciones válidas en código. |
| CA1019 | [CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019.md) | Los atributos pueden definir argumentos obligatorios que deben especificarse al aplicar el atributo a un destino. Éstos también se denominan argumentos posicionales porque se proporcionan para atribuir constructores como parámetros posicionales. Para cada argumento obligatorio, el atributo debe proporcionar también una propiedad de sólo lectura correspondiente de modo que el valor del argumento se pueda recuperar en tiempo de ejecución. Los atributos también pueden definir argumentos opcionales, que también se denominan argumentos con nombre. Estos argumentos se proporcionan para atribuir constructores por nombre y deben tener una propiedad de lectura/escritura correspondiente. |
| CA1021 | [CA1021: Evitar los parámetros out](../code-quality/ca1021.md) | Para pasar tipos por referencia (utilizando los parámetros out o ref) es necesario tener experiencia con punteros, saber la diferencia entre los tipos de referencia y los tipos de valor, y controlar métodos con varios valores devueltos. Además, no se suele saber qué diferencia hay entre los parámetros out y ref. |
| CA1024 | [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024.md) | Un método público o protegido tiene un nombre que comienza por "Get", no toma ningún parámetro y devuelve un valor que no es una matriz. El método podría ser un buen candidato para convertirse en propiedad. |
| CA1027 |[CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027.md) | Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. Aplique FlagsAttribute a una enumeración cuando se pueda combinar con sentido sus constantes con nombre. |
| CA1028 | [CA1028: El almacenamiento de la enumeración debe ser de tipo Int32](../code-quality/ca1028.md) | Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. De manera predeterminada, el tipo de datos System.Int32 se utiliza para almacenar el valor constante. Aunque puede cambiar este tipo subyacente, no es necesario ni se recomienda en la mayoría de los escenarios. |
| CA1030 | [CA1030: Utilizar eventos cuando sea apropiado](../code-quality/ca1030.md) |Esta regla detecta métodos que tienen nombres que normalmente se utilizarían para eventos. Si se llama a un método en respuesta a un cambio de estado claramente definido, un controlador de eventos debe invocar al método. Los objetos que llaman al método deben provocar eventos en lugar de llamar directamente al método. |
| CA1031 | [CA1031: No capturar los tipos de excepción general](../code-quality/ca1031.md) | No se deben capturar excepciones generales. Detecte una excepción más específica o vuelva a producir una excepción general como la última instrucción del bloque Catch. |
| CA1032 |[CA1032: Implementar constructores de excepción estándar](../code-quality/ca1032.md) | El error al proporcionar el conjunto completo de constructores puede dificultar el control correcto de las excepciones. |
| CA1033 | [CA1033: Los tipos secundarios deben poder llamar a los métodos de interfaz](../code-quality/ca1033.md) | Un tipo no sellado visible externamente proporciona un método explícito de implementación de una interfaz pública pero no proporciona un método visible externamente alternativo con el mismo nombre. |
| CA1034 | [CA1034: Los tipos anidados no deben ser visibles](../code-quality/ca1034.md) | Los tipos anidados son tipos declarados en el ámbito de otro tipo. Los tipos anidados son útiles para encapsular los detalles de la implementación privada del tipo contenido. Los tipos anidados, utilizados para este propósito, no deben ser visibles externamente. |
| CA1036 | [CA1036: Invalidar métodos en tipos comparables](../code-quality/ca1036.md) |Un tipo público o protegido implementa la interfaz System.IComparable. No invalida Object.Equals ni sobrecarga al operador específico del lenguaje para la igualdad, desigualdad, menor que o mayor que. |
| CA1040 |[CA1040: Evitar las interfaces vacías](../code-quality/ca1040.md) | Las interfaces definen miembros que proporcionan un comportamiento o acuerdo de uso. Cualquier tipo puede adoptar la funcionalidad descrita por la interfaz sin tener en cuenta dónde aparece el tipo en la jerarquía de herencia. Un tipo implementa una interfaz proporcionando las implementaciones para los miembros de la interfaz. Una interfaz vacía no define ningún miembro; por consiguiente, no define ningún contrato que se pueda implementar. |
| CA1041 | [CA1041: Proporcionar un mensaje ObsoleteAttribute](../code-quality/ca1041.md) | Un tipo o miembro se marca con un atributo System.ObsoleteAttribute para el que no se ha especificado su propiedad ObsoleteAttribute.Message. Cuando se compila un tipo o miembro marcado con ObsoleteAttribute, se muestra la propiedad Message del atributo. Esto proporciona información al usuario sobre el miembro o tipo obsoleto. |
| CA1043 | [CA1043: Utilizar un argumento integral o de cadena en indizadores](../code-quality/ca1043.md) | Los indizadores (es decir, las propiedades indizadas) deben utilizar tipos enteros o de cadena para el índice. Estos tipos se utilizan normalmente para indizar las estructuras de datos y aumentan la utilidad de la biblioteca. El uso del tipo Object debería limitarse a los casos en los que el tipo entero o de cadena no se puede especificar en tiempo de diseño. |
| CA1044 | [CA1044: Las propiedades no deben ser de solo escritura](../code-quality/ca1044.md) | Aunque es aceptable y a menudo necesario tener una propiedad de solo lectura, las directrices de diseño prohíben el uso de propiedades de solo escritura. Esto es porque si se deja que un usuario configure un valor, y a continuación se impide que el usuario vea ese valor, no proporciona ninguna seguridad. Además, sin acceso de lectura, no se puede ver el estado de los objetos compartidos, lo que limita su utilidad. |
| CA1045 |[CA1045: No pasar tipos por referencia](../code-quality/ca1045.md) | Para pasar tipos por referencia (utilizando los parámetros out o ref) es necesario tener experiencia con punteros, saber la diferencia entre los tipos de referencia y los tipos de valor, y controlar métodos con varios valores devueltos. Los arquitectos de biblioteca que diseñan para un público general no deben esperar que los usuarios dominen el trabajo con `out` `ref` los parámetros o. |
| CA1046 | [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046.md) | Para los tipos de referencia, la implementación predeterminada del operador de igualdad casi siempre es correcta. De manera predeterminada, dos referencias son iguales sólo si señalan al mismo objeto. |
| CA1047 |[CA1047: No declarar miembros protegidos en tipos sellados](../code-quality/ca1047.md) | Los tipos declaran miembros protegidos para que los tipos heredados puedan obtener acceso o reemplazar el miembro. Por definición, no se puede heredar de tipos sealed, lo que significa que no se puede llamar a los métodos protegidos en tipos sealed. |
| CA1050 | [CA1050: Declarar tipos en espacios de nombres](../code-quality/ca1050.md) | Los tipos se declaran dentro de los espacios de nombres para evitar conflictos de nombre y como una forma de organizar los tipos relacionados en una jerarquía de objetos. |
| CA1051 | [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051.md) | El uso principal de un campo debe ser como un detalle de implementación. Los campos deben ser privados o internos y deben exponerse utilizando propiedades. |
| CA1052 | [CA1052: Los tipos titulares estáticos deben estar sellados](../code-quality/ca1052.md) | Un tipo público o protegido solamente contiene miembros estáticos y no se declara con el modificador sealed (NotInheritable) (Referencia de C#). Un tipo que no está diseñado para heredarse debería marcarse con el modificador sealed para impedir su uso como tipo base. |
| CA1053 |[CA1053: Los tipos titulares estáticos no deben tener constructores](../code-quality/ca1053.md) | Un tipo público o público anidado declara sólo miembros estáticos y tiene un constructor predeterminado público o protegido. El constructor no es necesario puesto que al llamar a los miembros estáticos no se requiere una instancia del tipo. La sobrecarga de la cadena debería llamar a la sobrecarga del identificador URI utilizando el argumento string por motivos de seguridad y protección. |
| CA1054 | [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054.md) | Si un método toma una representación de cadena de un identificador URI, debe proporcionarse la sobrecarga correspondiente que toma una instancia de la clase URI, que proporciona estos servicios de forma segura. |
| CA1055 | [CA1055: Los valores devueltos URI no deben ser cadenas](../code-quality/ca1055.md) | Esta regla supone que el método devuelve un URI. Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La clase System.Uri proporciona estos servicios de una manera segura. |
| CA1056 | [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056.md) | La regla supone que la propiedad representa un Identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La clase System.Uri proporciona estos servicios de una manera segura. |
| CA1058 | [CA1058: Los tipos no deben ampliar ciertos tipos base](../code-quality/ca1058.md) | Un tipo visible externamente extiende algunos tipos base. Utilice una de las alternativas. |
| CA1060 | [CA1060: mueve P/Invoke a la clase NativeMethods](../code-quality/ca1060.md) | Los métodos de invocación de plataforma, como aquellos marcados con el atributo System.Runtime.InteropServices.DllImportAttribute o los métodos definidos utilizando la palabra clave Declare en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], tienen acceso al código no administrado. Estos métodos deben ser de la clase NativeMethods, UnsafeNativeMethods o SafeNativeMethods. |
| CA1061 |[CA1061: No ocultar métodos de clase base](../code-quality/ca1061.md) | Un método de un tipo base está oculto por un método del mismo nombre en un tipo derivado cuando la firma del parámetro del método derivado solo se diferencia por tipos derivados de manera más débil que los tipos correspondientes de la firma del parámetro del método base. |
| CA1062 | [CA1062: Validar argumentos de métodos públicos](../code-quality/ca1062.md) | Todos los argumentos de referencia pasados a métodos visibles externamente se deben comprobar para ver si son null. |
| CA1063 | [CA1063: Implementar IDisposable correctamente](../code-quality/ca1063.md) | Todos los tipos IDisposable deben implementar el modelo de Dispose correctamente. |
| CA1064 | [CA1064: Las excepciones deben ser públicas](../code-quality/ca1064.md) | Una excepción interna solo se ve dentro de su propio ámbito interno. Cuando la excepción esté fuera del ámbito interno, sólo se podrá usar la excepción base para detectarla. Si la excepción interna se hereda de <xref:System.Exception> , <xref:System.SystemException> o <xref:System.ApplicationException> , el código externo no tendrá información suficiente para saber qué hacer con la excepción. |
| CA1065 | [CA1065: No producir excepciones en ubicaciones inesperadas](../code-quality/ca1065.md) | Un método que no se espera que produzca excepciones inicia una excepción. |
| CA1066 | [CA1066: Implementar IEquatable al invalidar Equals](../code-quality/ca1066.md) | Un tipo de valor invalida el <xref:System.Object.Equals%2A> método, pero no implementa <xref:System.IEquatable%601> . |
| CA1067 | [CA1067: Invalidar Equals al implementar IEquatable](../code-quality/ca1067.md) | Un tipo implementa <xref:System.IEquatable%601> , pero no invalida el <xref:System.Object.Equals%2A> método. |
| CA1068 | [CA1068: Los parámetros CancellationToken deben aparecer en último lugar](../code-quality/ca1068.md) | Un método tiene un parámetro CancellationToken que no es el último parámetro. |
| CA1069 | [CA1069: Los enumeradores no deben tener valores duplicados](../code-quality/ca1069.md) | Una enumeración tiene varios miembros a los que se les asigna explícitamente el mismo valor constante. |
| CA1070 | [CA1070: No declarar los campos de eventos como virtuales](../code-quality/ca1070.md) | Un [evento similar](/dotnet/csharp/language-reference/language-specification/classes#field-like-events) a un campo se declaró como virtual. |
| CA1200 | [CA1200: Evitar el uso de etiquetas cref con un prefijo](../code-quality/ca1200.md) | El atributo [CREF](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) de una etiqueta de documentación XML significa "referencia de código". Especifica que el texto interno de la etiqueta es un elemento de código, como un tipo, un método o una propiedad. Evite el uso de `cref` etiquetas con prefijos, ya que impide que el compilador Compruebe las referencias. También impide que el entorno de desarrollo integrado (IDE) de Visual Studio busque y actualice estas referencias de símbolos durante las refactorizaciones. |
| CA1303 | [CA1303: No pasar literales como parámetros localizados](../code-quality/ca1303.md) | Un método visible externamente pasa un literal de cadena como un parámetro a un constructor o método .NET, y esa cadena debe ser localizable. |
| CA1304 | [CA1304: Especificar CultureInfo](../code-quality/ca1304.md) | Un método o constructor llama a un miembro que tiene una sobrecarga que acepta un parámetro System.Globalization.CultureInfo, y el método o constructor no llama a la sobrecarga que toma el parámetro CultureInfo. Si no se proporciona un objeto CultureInfo o System.IFormatProvider, el valor predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las configuraciones regionales. |
| CA1305 | [CA1305: Especificar IFormatProvider](../code-quality/ca1305.md) | Un método o constructor llama a uno o más miembros que tienen sobrecargas que aceptan un parámetro System.IFormatProvider, y el método o constructor no llama a la sobrecarga que toma el parámetro IFormatProvider. Si no se proporciona un objeto System.Globalization.CultureInfo o IFormatProvider, el valor predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las configuraciones regionales. |
| CA1307 | [CA1307: Especificar StringComparison para mayor claridad](../code-quality/ca1307.md) | Una operación de comparación de cadenas utiliza una sobrecarga de método que no establece un parámetro StringComparison. |
| CA1308 |[CA1308: Normalizar cadenas en mayúsculas](../code-quality/ca1308.md) | Las cadenas se deberían normalizar para que se escriban en letras mayúsculas. Hay un grupo pequeño de caracteres que no pueden realizar un viaje de ida y vuelta cuando se pasan a minúsculas. |
| CA1309 | [CA1309: Utilizar StringComparison ordinal](../code-quality/ca1309.md) | Una operación no lingüística de comparación de cadenas no establece el parámetro StringComparison en Ordinal ni en OrdinalIgnoreCase. Si se establece explícitamente el parámetro en StringComparison.Ordinal o StringComparison.OrdinalIgnoreCase, el código será más rápido y ganará en precisión y confiabilidad. |
| CA1310 | [CA1310: Especificar StringComparison para mayor corrección](../code-quality/ca1310.md) | Una operación de comparación de cadenas utiliza una sobrecarga de método que no establece un parámetro StringComparison y utiliza de forma predeterminada la comparación de cadenas específica de la referencia cultural. |
| CA1401 | [CA1401: P/Invoke no debe estar visible](../code-quality/ca1401.md) | Un método público o protegido en un tipo público tiene el atributo System.Runtime.InteropServices.DllImportAttribute (también se implementa por la palabra clave Declare en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. No se deberían exponer estos métodos. |
| CA1417 | [CA1417: no se usa `OutAttribute` en parámetros de cadena para P/Invoke](../code-quality/ca1417.md) | Los parámetros de cadena pasados por valor con el `OutAttribute` pueden desestabilizar el tiempo de ejecución si la cadena es una cadena interna. |
| CA1501 | [CA1501: Evitar una herencia excesiva](../code-quality/ca1501.md) | Un tipo tiene más de cuatro niveles de profundidad en su jerarquía de herencia. Las jerarquías de tipos con demasiados niveles de anidación pueden resultar difíciles de seguir, comprender y mantener. |
| CA1502 | [CA1502: Evitar una complejidad excesiva](../code-quality/ca1502.md) | Esta regla mide el número de rutas de acceso independientes de forma lineal a través del método, que es determinado por el número y la complejidad de bifurcaciones condicionales. |
| CA1505 | [CA1505: Evitar código que no se puede mantener](../code-quality/ca1505.md) | Un tipo o método tiene un valor del índice de mantenimiento bajo. Un índice de mantenimiento bajo indica que un tipo o método resulta probablemente difícil de mantener y se debería volver a diseñar. |
| CA1506 | [CA1506: Evitar el acoplamiento excesivo de clases](../code-quality/ca1506.md) | Esta regla mide el acoplamiento de clase contando el número de referencias de tipo únicas que contiene un tipo o método. |
| CA1507 | [CA1507: Usar nameof en lugar de la cadena](../code-quality/ca1507.md) | Un literal de cadena se usa como argumento en el que se `nameof` podría utilizar una expresión. |
| CA1508 | [CA1508: Evitar código de condición no alcanzado](../code-quality/ca1508.md) | Un método tiene código condicional que siempre se evalúa como `true` o `false` en tiempo de ejecución. Esto conduce a código muerto en la `false` rama de la condición. |
| CA1509 | [CA1509: Entrada no válida en el archivo de configuración de métricas de código](../code-quality/ca1509.md) | Las reglas de métricas de código, como [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) y [CA1506](ca1506.md), proporcionan un archivo de configuración denominado `CodeMetricsConfig.txt` que tiene una entrada no válida. |
| CA1700 | [CA1700: No nombrar valores de enumeración como 'Reserved'](../code-quality/ca1700.md) | Esta regla supone que un miembro de la enumeración con un nombre que contiene la palabra "reserved" no se utiliza actualmente pero hace de marcador de posición para que se pueda quitar o cambiar el nombre en una versión posterior. Quitar o cambiar el nombre de un miembro es un cambio importante. |
| CA1707 | [CA1707: Los identificadores no deben contener caracteres de subrayado](../code-quality/ca1707.md) | Por convención, los nombres del identificador no contienen el carácter de subrayado (_). Esta regla comprueba espacios de nombres, tipos, miembros y parámetros. |
| CA1708 | [CA1708: Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708.md) | Los identificadores de los espacios de nombres, miembros y parámetros no puede distinguirse sólo por mayúsculas o minúsculas porque los lenguajes que tienen como destino el Common Language Runtime no necesitan distinguir entre mayúsculas y minúsculas. |
| CA1710 | [CA1710: Los identificadores deben tener un sufijo correcto](../code-quality/ca1710.md) |Por convención, los nombres de tipos que extienden determinados tipos base o que implementan algunas interfaces, o tipos derivados de estos tipos, tienen un sufijo asociado al tipo base o a la interfaz. |
| CA1711 | [CA1711: Los identificadores no deben tener un sufijo incorrecto](../code-quality/ca1711.md) | Por convención, los nombres de tipos que extienden determinados tipos base o que implementan algunas interfaces, o tipos derivados de estos tipos, deben terminar con unos sufijos reservados específicos. Otros nombres de tipo no deben utilizar estos sufijos reservados. |
| CA1712 | [CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo](../code-quality/ca1712.md) | Los nombres de los miembros de la enumeración no llevan el nombre de tipo como prefijo porque se espera que las herramientas de desarrollo proporcionen la información de tipo. |
| CA1713 | [CA1713: Los eventos no deben tener prefijos antes ni después](../code-quality/ca1713.md) | El nombre de un evento empieza por "Before" o "After". Para nombrar los eventos relacionados que se provocan en una secuencia específica, utilice el tiempo presente o pasado para indicar la posición relativa en la secuencia de acciones. |
| CA1714 | [CA1714: Las enumeraciones Flags deben tener nombres en plural](../code-quality/ca1714.md) | Una enumeración pública tiene el atributo System.FlagsAttribute y su nombre no termina en "s". Los tipos marcados con FlagsAttribute tienen nombres en plural porque el atributo indica que se puede especificar más de un valor. |
| CA1715 | [CA1715: Los identificadores deben tener el prefijo correcto](../code-quality/ca1715.md) | El nombre de una interfaz visible externamente no empieza por "I" mayúscula. El nombre de un parámetro de tipo genérico en un tipo o método visibles externamente no empieza por "T" mayúscula. |
| CA1716 | [CA1716: Los identificadores no deben coincidir con palabras clave](../code-quality/ca1716.md) | Un nombre de espacio de nombres o un nombre de tipo coinciden con una palabra clave reservada en un lenguaje de programación. Los identificadores para los espacios de nombres y tipos no deberían coincidir con palabras clave definidas por los lenguajes que tienen como destino el Common Language Runtime. |
| CA1717 | [CA1717: Solo las enumeraciones FlagsAttribute deben tener nombres en plural](../code-quality/ca1717.md) | Las convenciones de nomenclatura establecen que un nombre en plural para una enumeración indica que se pueden especificar varios valores de enumeración al mismo tiempo. |
| CA1720 |[CA1720: Los identificadores no deben contener nombres de tipo](../code-quality/ca1720.md) | El nombre de un parámetro en un miembro visible externamente contiene un nombre de tipo de datos o el nombre de un miembro visible externamente contiene un nombre de tipo de datos específico del lenguaje. |
| CA1721 | [CA1721: Los nombres de propiedades no deben coincidir con los métodos get](../code-quality/ca1721.md) |El nombre de un miembro público o protegido empieza por "Get" y en cualquier otro caso coincide con el nombre de una propiedad pública o protegida. Las propiedades y métodos "Get" deberían tener nombres que distingan claramente su función. |
| CA1724 | [CA1724: Los nombres de tipo no deben coincidir con los espacios de nombres](../code-quality/ca1724.md) | Los nombres de tipo no deben coincidir con los nombres de los espacios de nombres de .NET. Infringir esta regla puede reducir la utilidad de la biblioteca. |
| CA1725 | [CA1725: Los nombres de parámetro deben coincidir con la declaración base](../code-quality/ca1725.md) | El uso del mismo nombre para un parámetro en una jerarquía de reemplazo aumenta la utilidad de los reemplazos de método. Cuando el nombre de un parámetro en un método derivado es distinto del nombre de la declaración base, puede resultar difícil determinar si el método es un reemplazo del método base o una nueva sobrecarga del método. |
| CA1801 | [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801.md) | Una firma de método incluye un parámetro que no se utiliza en el cuerpo del método. |
| CA1802 |[CA1802: Utilizar literales cuando sea apropiado](../code-quality/ca1802.md) |Un campo se declara como static y de solo lectura (Shared y ReadOnly en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) y se inicializa con un valor que se puede calcular durante la compilación. Dado que el valor asignado al campo de destino es calculable en tiempo de compilación, cambie la declaración a un campo const (const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) para que el valor se calcule en tiempo de compilación en lugar de en tiempo de ejecución. |
| CA1805 | [CA1805: No inicializar innecesariamente](../code-quality/ca1805.md) | El tiempo de ejecución de .NET inicializa todos los campos de los tipos de referencia a sus valores predeterminados antes de ejecutar el constructor. En la mayoría de los casos, la inicialización explícita de un campo a su valor predeterminado es redundante, lo que aumenta los costos de mantenimiento y puede degradar el rendimiento (por ejemplo, con un mayor tamaño de ensamblado). |
| CA1806 | [CA1806: No omitir resultados del método](../code-quality/ca1806.md) | Se crea un nuevo objeto pero nunca se utiliza, o se llama a un método que crea y devuelve una nueva cadena y esta nunca se utiliza, o un método COM o P/Invoke devuelve un código de error o HRESULT que nunca se utiliza. |
| CA1810 | [CA1810: Inicializar campos estáticos de tipo de referencia insertados](../code-quality/ca1810.md) | Cuando un tipo declara un constructor estático explícito, el compilador Just-In-Time (JIT) agrega una comprobación a cada constructor de instancia y a cada método estático del tipo para asegurarse de que se ha llamado anteriormente al constructor estático. Las comprobaciones del constructor estático pueden reducir el rendimiento. |
| CA1812 | [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812.md) | El código del ensamblado no crea una instancia del tipo del nivel de ensamblado. |
| CA1813 | [CA1813: Evitar los atributos no sellados](../code-quality/ca1813.md) | .NET proporciona métodos para recuperar atributos personalizados. De forma predeterminada, estos métodos buscan la jerarquía de herencia de atributo. La acción de sellar el atributo elimina la búsqueda en la jerarquía de herencia y puede mejorarse el rendimiento. |
| CA1814 | [CA1814: Preferir matrices escalonadas antes que multidimensionales](../code-quality/ca1814.md) | Una matriz escalonada es una matriz cuyos elementos son matrices. Las matrices que constituyen los elementos pueden ser de tamaños diferentes, reduciendo el espacio desaprovechado para algunos conjuntos de datos. |
| CA1815 | [CA1815: Invalidar Equals y el operador Equals en los tipos de valores](../code-quality/ca1815.md) | Para los tipos de valor, la implementación heredada de Equals utiliza la biblioteca de reflexión y compara el contenido de todos los campos. Mediante el cálculo, la reflexión es cara y no es necesario comparar cada campo para comprobar si hay igualdad. Si espera que los usuarios comparen u ordenen instancias, o utilicen instancias como claves de tabla hash, el tipo de valor debe implementar Equals. |
| CA1816 | [CA1816: Llamar a GC.SuppressFinalize correctamente](../code-quality/ca1816.md) | Un método que es una implementación de Dispose no llama a GC.SuppressFinalize, o un método que no es una implementación de Dispose llama a GC.SuppressFinalize, o un método llama a GC.SuppressFinalize y pasa algo distinto de "this" (Me en Visual Basic). |
| CA1819 | [CA1819: Las propiedades no deben devolver matrices](../code-quality/ca1819.md) | Las matrices devueltas por las propiedades no están protegidas contra escritura, aun cuando la propiedad es de solo lectura. Para mantener la matriz inviolable, la propiedad debe devolver una copia de la matriz. Por lo general, los usuarios no entienden las implicaciones de rendimiento adversas que se originan al llamar a este tipo de propiedad. |
| CA1820 | [CA1820: Comprobar si las cadenas están vacías mediante la longitud de cadena](../code-quality/ca1820.md) | El uso de la propiedad String.Length o del método String.IsNullOrEmpty para comparar cadenas es mucho más rápido que el uso de Equals. |
| CA1821 | [CA1821: Quitar finalizadores vacíos](../code-quality/ca1821.md) | Siempre que pueda, evite los finalizadores debido a la sobrecarga de rendimiento adicional necesaria para el seguimiento de la duración del objeto. Un finalizador vacío produce una sobrecarga adicional sin ningún beneficio. |
| CA1822 |[CA1822: Marcar miembros como estáticos](../code-quality/ca1822.md) | Los miembros que no tienen acceso a datos de instancia o que llaman a métodos de instancia se pueden marcar como static (Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Después de marcar los métodos como static, el compilador emite los sitios de llamada no virtuales para estos miembros. Esto puede proporcionar una mejora apreciable del rendimiento del código en el que el rendimiento es fundamental. |
| CA1823 | [CA1823: Evitar los campos privados sin utilizar](../code-quality/ca1823.md) | Se detectaron campos privados a los que no parece que se tenga acceso en el ensamblado. |
| CA1824 |[CA1824: Marcar los ensamblados con NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | El atributo NeutralResourcesLanguage informa al administrador de recursos del idioma que se usó para mostrar los recursos de una referencia cultural neutra para un ensamblado. Esto mejora el rendimiento de la búsqueda del primer recurso que se carga y puede reducir el espacio de trabajo. |
| CA1825 |[CA1825: Evitar asignaciones de matrices de longitud cero](../code-quality/ca1825.md) | Al inicializar una matriz de longitud cero, se produce una asignación de memoria innecesaria. En su lugar, use la instancia de matriz vacía asignada estáticamente mediante una llamada a <xref:System.Array.Empty%2A?displayProperty=nameWithType> . La asignación de memoria se comparte entre todas las invocaciones de este método. |
| CA1826 |[CA1826: Usar la propiedad en lugar del método Linq Enumerable](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable> El método LINQ se usó en un tipo que admite una propiedad equivalente y más eficaz. |
| CA1827 |[CA1827: No usar Count/LongCount si se puede usar Any](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A><xref:System.Linq.Enumerable.LongCount%2A>se usó el método o, donde el <xref:System.Linq.Enumerable.Any%2A> método sería más eficaz. |
| CA1828 |[CA1828: No usar CountAsync/LongCountAsync si se puede usar AnyAsync](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A><xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A>se usó el método o, donde el <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> método sería más eficaz. |
| CA1829 |[CA1829: Usar la propiedad Length/Count en lugar del método Enumerable.Count](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> El método LINQ se usó en un tipo que admite una propiedad equivalente, más eficaz `Length` o `Count` . |
| CA1830 |[CA1830: Preferir las sobrecargas de método Append e Insert fuertemente tipadas en StringBuilder](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> y <xref:System.Text.StringBuilder.Insert%2A> proporcionan sobrecargas para varios tipos más allá de <xref:System.String> .  Siempre que sea posible, prefiera las sobrecargas fuertemente tipadas sobre el uso de ToString () y la sobrecarga basada en cadena. |
| CA1831 |[CA1831: Usar AsSpan en lugar de indizadores basados en intervalos para una cadena cuando proceda](../code-quality/ca1831.md) | Cuando se usa un indexador de intervalo en una cadena y se asigna implícitamente el valor al &lt; tipo char de ReadOnlySpan &gt; , se <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> utilizará el método en lugar de <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , que genera una copia de la parte solicitada de la cadena. |
| CA1832 |[CA1832: Usar AsSpan o AsMemory en lugar de indizadores basados en intervalos para obtener la parte ReadOnlySpan o ReadOnlyMemory de una matriz](../code-quality/ca1832.md) | Cuando se usa un indexador de intervalo en una matriz y se asigna implícitamente el valor a un <xref:System.ReadOnlySpan%601> <xref:System.ReadOnlyMemory%601> tipo o, se utilizará el método en <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> lugar de <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , que genera una copia de la parte solicitada de la matriz. |
| CA1833 |[CA1833: Usar AsSpan o AsMemory en lugar de indizadores basados en intervalos para obtener la parte Span o Memory de una matriz](../code-quality/ca1833.md) | Cuando se usa un indexador de intervalo en una matriz y se asigna implícitamente el valor a un <xref:System.Span%601> <xref:System.Memory%601> tipo o, se utilizará el método en <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> lugar de <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , que genera una copia de la parte solicitada de la matriz. |
| CA1834 |[CA1834: Usar StringBuilder.Append(char) para cadenas de un solo carácter](../code-quality/ca1834.md) | <xref:System.Text.StringBuilder> tiene una `Append` sobrecarga que toma `char` como argumento. Prefiera llamar a la `char` sobrecarga por motivos de rendimiento. |
| CA1835 |[CA1835: preferir las sobrecargas basadas en Memory' para ' ReadAsync ' y ' WriteAsync '](../code-quality/ca1835.md) | ' Stream ' tiene una sobrecarga ' ReadAsync ' que toma un ' byte de memoria &lt; &gt; ' como primer argumento y una sobrecarga ' WriteAsync ' que toma un ' ReadOnlyMemory &lt; byte &gt; ' como primer argumento. Prefiera llamar a las sobrecargas basadas en memoria, que son más eficaces. |
| CA1836 |[CA1836: preferir `IsEmpty` `Count` cuando esté disponible](../code-quality/ca1836.md) | Propiedad preferida `IsEmpty` que es más eficaz `Count` que `Length` , <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> o <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> para determinar si el objeto contiene o no elementos. |
| CA1837 | [CA1837: use `Environment.ProcessId` en lugar de `Process.GetCurrentProcess().Id`](../code-quality/ca1837.md) | `Environment.ProcessId` es más sencillo y más rápido que `Process.GetCurrentProcess().Id` . |
| CA1838 | [CA1838: evitar `StringBuilder` parámetros para P/Invoke](../code-quality/ca1838.md) | La serialización de ' StringBuilder ' siempre crea una copia de búfer nativo, lo que da lugar a varias asignaciones para una operación de serialización. |
| CA2000 | [CA2000: Desechar objetos antes de perder el ámbito](../code-quality/ca2000.md) | Dado que podría producirse un evento excepcional que evitaría que el finalizador de un objeto se ejecutase, el objeto debe estar disponible en su lugar antes de que todas las referencias a él estén fuera del ámbito. |
| CA2002 |[CA2002: No bloquear objetos con identidad débil](../code-quality/ca2002.md) |Se dice que un objeto tiene una identidad débil cuando se puede tener acceso directamente a través de los límites del dominio de aplicación. Un subproceso que intenta obtener un bloqueo en un objeto que tiene identidad débil se puede bloquear con un segundo subproceso en un dominio de aplicación diferente que tenga bloqueado el mismo objeto. |
| CA2007 | [CA2007: No esperar una tarea directamente](ca2007.md) | Un método asincrónico [espera](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> directamente. Cuando un método asincrónico espera <xref:System.Threading.Tasks.Task> directamente, la continuación se produce en el mismo subproceso que creó la tarea. Este comportamiento puede ser costoso en términos de rendimiento y puede dar lugar a un interbloqueo en el subproceso de la interfaz de usuario. Considere <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> la posibilidad de llamar a para señalar su intención de continuación. |
| CA2008 | [CA2008: No crear tareas sin pasar un elemento TaskScheduler](ca2008.md) | Una operación de creación o continuación de tareas utiliza una sobrecarga de método que no especifica un <xref:System.Threading.Tasks.TaskScheduler> parámetro. |
| CA2009 | [CA2009: No llame a ToImmutableCollection en un valor ImmutableCollection](ca2009.md) | `ToImmutable` se llamó innecesariamente al método en una colección inmutable desde el <xref:System.Collections.Immutable> espacio de nombres. |
| CA2011 | [CA2011: No asignar la propiedad dentro de su establecedor](ca2011.md) | Se asignó accidentalmente un valor a una propiedad dentro de su propio [descriptor de acceso set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
| CA2012 | [CA2012: Usar ValueTasks correctamente](ca2012.md) | Los ValueTasks devueltos de las invocaciones de miembro están diseñados para esperarse directamente.  Los intentos de consumir un ValueTask varias veces o de tener acceso directamente a uno de los resultados antes de que se sepa que se han completado pueden producir una excepción o daños.  Omitir tal ValueTask es probable que se trate de un error funcional y puede degradar el rendimiento. |
| CA2013 | [CA2013: No usar ReferenceEquals con tipos de valor](ca2013.md) | Al comparar valores mediante <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , si objA y objB son tipos de valor, se les aplica la conversión boxing antes de que se pasen al <xref:System.Object.ReferenceEquals%2A> método. Esto significa que, aunque objA y objB representen la misma instancia de un tipo de valor, el <xref:System.Object.ReferenceEquals%2A> método devuelve false. |
| CA2014 | [CA2014: no use stackalloc en los bucles.](ca2014.md) | El espacio de pila asignado por stackalloc solo se libera al final de la invocación del método actual.  Su uso en un bucle puede dar lugar a un crecimiento de pila sin enlazar y a condiciones de desbordamiento de pila eventuales. |
| CA2015 | [CA2015: no definir finalizadores para los tipos derivados de MemoryManager &lt; T&gt;](ca2015.md) | Agregar un finalizador a un tipo derivado de <xref:System.Buffers.MemoryManager%601> puede permitir que la memoria se libere mientras esté siendo utilizada por <xref:System.Span%601> . |
| CA2016 | [CA2016: Reenviar el parámetro CancellationToken a los métodos que lo usan](ca2016.md) | Reenvíe el `CancellationToken` parámetro a los métodos que toman uno para asegurarse de que las notificaciones de cancelación de la operación se propagan correctamente, o que `CancellationToken.None` se pasan explícitamente para indicar que no se propague el token de forma intencionada. |
| CA2100 | [CA2100: Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad](../code-quality/ca2100.md) | Un método establece la propiedad System.Data.IDbCommand.CommandText utilizando una cadena que se construye partiendo de un argumento de cadena para el método. Esta regla supone que el argumento de cadena contiene datos proporcionados por el usuario. Una cadena de comandos de SQL compilada a partir de datos proporcionados por el usuario es vulnerable a ataques de inserción de SQL. |
| CA2101 |[CA2101: especificar el cálculo de referencias para argumentos de cadena P/Invoke](../code-quality/ca2101.md) | Un miembro de invocación de plataforma permite llamadores que no son de plena confianza y no serializa explícitamente la cadena. Esto puede producir una vulnerabilidad de seguridad. |
| CA2109 | [CA2109: Revisar los controladores de eventos visibles](../code-quality/ca2109.md) | Se detectó un método de control de eventos público o protegido. No se deberían exponer los métodos de control de eventos a menos que sea absolutamente necesario. |
| CA2119 | [CA2119: Sellar los métodos que satisfacen las interfaces privadas](../code-quality/ca2119.md) | Un tipo público heredable proporciona una implementación de método reemplazable de una interfaz interna (de tipo "Friend" en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Para corregir una infracción de esta regla, impida que el método se invalide fuera del ensamblado. |
| CA2153 |[CA2153: evitar el control de excepciones de estado dañadas](../code-quality/ca2153.md) | Las excepciones de estado dañadas (CSE) indican que hay daños en la memoria en el proceso. Detectar estos problemas y evitar el bloqueo del proceso puede provocar vulnerabilidades de seguridad si un atacante puede colocar una vulnerabilidad de seguridad en la región de memoria dañada. |
| CA2200 | [CA2200: Reiniciar para mantener los detalles de la pila](../code-quality/ca2200.md) | Se vuelve a producir una excepción y se especifica explícitamente en la instrucción throw. Si se vuelve a producir una excepción especificándola en la instrucción throw, se pierde la lista de llamadas al método entre el método original que produjo la excepción y el método actual. |
| CA2201 | [CA2201: No provocar tipos de excepción reservados](../code-quality/ca2201.md) | Esto hace que el error original sea difícil de detectar y depurar. |
| CA2207 | [CA2207: Inicializar campos estáticos de tipo de valor insertados](../code-quality/ca2207.md) | Un tipo de valor declara un constructor estático explícito. Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declara y quite el constructor estático. |
| CA2208 |[CA2208: Crear instancias de las excepciones del argumento correctamente](../code-quality/ca2208.md) | Se realiza una llamada al constructor predeterminado (sin parámetros) de un tipo de excepción que es o deriva de ArgumentException, o se pasa un argumento de cadena incorrecto a un constructor con parámetros de un tipo de excepción que es o deriva de ArgumentException. |
| CA2211 |[CA2211: Los campos no constantes no deben ser visibles](../code-quality/ca2211.md) | Los campos estáticos que no son constantes ni de sólo lectura no son seguros para subprocesos. Obtener acceso a este tipo de campo se debe controlar cuidadosamente y requiere técnicas de programación avanzadas para sincronizar el acceso al objeto de clase. |
| CA2213 | [CA2213: Los campos descartables deben ser descartables](../code-quality/ca2213.md) | Un tipo que implementa System.IDisposable declara campos que son de tipos que también implementan IDisposable. El método Dispose del tipo declarativo no llama al método Dispose del campo. |
| CA2214 | [CA2214: No llamar a métodos reemplazables en constructores](../code-quality/ca2214.md) | Cuando un constructor llama a un método virtual, es posible que no se haya ejecutado el constructor para la instancia que invoca el método. |
| CA2215 | [CA2215: Los métodos Dispose deben llamar al método Dispose de la clase base](../code-quality/ca2215.md) | Si un tipo hereda de un tipo descartable, debe llamar al método Dispose del tipo base desde su propio método Dispose. |
| CA2216 |[CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216.md) | Un tipo que implementa System.IDisposable y tiene campos que sugieren el uso de recursos no administrados, no implementa un finalizador descrito por Object.Finalize. |
| CA2217 | [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217.md) |Una enumeración visible externamente está marcada con FlagsAttribute y tiene uno o varios valores que no son potencias de dos o una combinación de los otros valores definidos en la enumeración. |
| CA2219 | [CA2219: No producir excepciones en cláusulas de excepción](../code-quality/ca2219.md) | Cuando se genera una excepción en una cláusula finally o fault, la nueva excepción oculta la excepción activa. Cuando se genera una excepción en una cláusula filter, el runtime la detecta automáticamente. Esto hace que el error original sea difícil de detectar y depurar. |
| CA2225 | [CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225.md) |Se detectó una sobrecarga del operador y no se encontró el método alternativo con el nombre esperado. El miembro alternativo con nombre proporciona acceso a la misma funcionalidad que el operador; esto se hace para los desarrolladores que programan en lenguajes que no admiten operadores sobrecargados. |
| CA2226 | [CA2226: Los operadores deben tener sobrecargas simétricas](../code-quality/ca2226.md) | Un tipo implementa el operador de igualdad o de desigualdad y no implementa el operador opuesto. |
| CA2227 |[CA2227: Las propiedades de la colección deben ser de solo lectura](../code-quality/ca2227.md) |Una propiedad de colección grabable permite al usuario reemplazar la colección por otra diferente. Una propiedad de sólo lectura impide que la colección se reemplace, pero sí permite establecer miembros individuales. |
| CA2229 | [CA2229: Implementar constructores de serialización](../code-quality/ca2229.md) | Para corregir una infracción de esta regla, implemente el constructor de serialización. Para una clase sellada, marque el constructor como privado; de lo contrario, márquelo como protegido. |
| CA2231 | [CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231.md) | Un tipo de valor invalida Object.Equals pero no implementa el operador de igualdad. |
| CA2234 | [CA2234: Pasar objetos System.Uri en lugar de cadenas](../code-quality/ca2234.md) | Se realiza una llamada a un método que tiene un parámetro de cadena cuyo nombre contiene "uri", "URI", "urn", "URN", "url" o "URL". El tipo declarativo del método contiene una sobrecarga de método correspondiente que tiene un parámetro System.Uri. |
| CA2235 | [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235.md) | Un campo de instancia de un tipo que no es serializable se declara en un tipo que es serializable. |
| CA2237 | [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237.md) | Para que los tipos sean reconocidos como serializables por Common Language Runtime, deben estar marcados con el atributo SerializableAttribute incluso si el tipo utiliza una rutina de serialización personalizada a través de la implementación de la interfaz ISerializable. |
| CA2241 | [CA2241: Proporcionar argumentos correctos a los métodos de formato](../code-quality/ca2241.md) | El argumento format pasado a System.String.Format no contiene un elemento de formato que corresponda a cada argumento de objeto o viceversa. |
| CA2242 |[CA2242: Comprobar NaN correctamente](../code-quality/ca2242.md) | Esta expresión prueba un valor respecto a Single.Nan o Double.Nan. Utilice IsNan(Single) o Double.IsNan(Double) para probar el valor. |
| CA2243 |[CA2243: Los literales de cadena de atributo se deben analizar correctamente](../code-quality/ca2243.md) | El parámetro de literal de cadena de un atributo no se analiza correctamente para una dirección URL, un GUID o una versión. |
| CA2244 | [CA2244: No duplicar inicializaciones de elementos indexados](../code-quality/ca2244.md) | Un inicializador de objeto tiene más de un inicializador de elemento indizado con el mismo índice de constante. Todo menos el último inicializador son redundantes. |
| CA2245 | [CA2245: No asignar una propiedad a sí misma](../code-quality/ca2245.md) | Una propiedad se asignó accidentalmente a sí misma. |
| CA2246 | [CA2246: No asignar un símbolo y su miembro en la misma instrucción](../code-quality/ca2246.md) | No se recomienda asignar un símbolo y su miembro, es decir, un campo o una propiedad, en la misma instrucción. No está claro si el acceso a miembros debía usar el valor anterior del símbolo antes de la asignación o el nuevo valor de la asignación en esta instrucción. |
| CA2247 | [CA2247: el argumento pasado al constructor TaskCompletionSource debe ser una enumeración TaskCreationOptions en lugar de TaskContinuationOptions enum.](../code-quality/ca2247.md) | TaskCompletionSource tiene constructores que toman un TaskCreationOptions que controla la tarea subyacente y constructores que toman el estado del objeto almacenado en la tarea.  Pasar accidentalmente un TaskContinuationOptions en lugar de un TaskCreationOptions dará lugar a que la llamada trate las opciones como estado. |
| CA2248 | [CA2248: Proporcionar el argumento enum correcto para Enum.HasFlag](../code-quality/ca2248.md) | El tipo de enumeración que se pasa como argumento a la `HasFlag` llamada al método es diferente del tipo de enumeración que realiza la llamada. |
| CA2249 | [CA2249: Valorar la posibilidad de usar String.Contains en lugar de String.IndexOf](../code-quality/ca2249.md) | Las llamadas a `string.IndexOf` donde se utiliza el resultado para comprobar la presencia o ausencia de una subcadena se pueden reemplazar por `string.Contains` . |
| CA2300 | [CA2300: No usar el deserializador no seguro BinaryFormatter](../code-quality/ca2300.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2301 | [CA2301: No llamar a BinaryFormatter.Deserialize sin establecer primero BinaryFormatter.Binder](../code-quality/ca2301.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2302 | [CA2302: Asegurarse de que BinaryFormatter.Binder está establecido antes de llamar a BinaryFormatter.Deserialize](../code-quality/ca2302.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2305 | [CA2305: No usar el deserializador no seguro LosFormatter](../code-quality/ca2305.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2310 | [CA2310: No usar el deserializador no seguro NetDataContractSerializer](../code-quality/ca2310.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2311 | [CA2311: No deserializar sin establecer primero NetDataContractSerializer.Binder](../code-quality/ca2311.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2312 | [CA2312: Asegúrese de que se establece NetDataContractSerializer.Binder antes de deserializar](../code-quality/ca2312.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2315 | [CA2315: No usar el deserializador no seguro ObjectStateFormatter](../code-quality/ca2315.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2321 | [CA2321: No deserializar con JavaScriptSerializer mediante SimpleTypeResolver](../code-quality/ca2321.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2322 | [CA2322: Asegúrese de que JavaScriptSerializer no se ha inicializado con SimpleTypeResolver antes de deserializar](../code-quality/ca2322.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2326 | [CA2326: No usar valores TypeNameHandling que no sean None](../code-quality/ca2326.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2327 | [CA2327: No usar valores JsonSerializerSettings no seguros](../code-quality/ca2327.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2328 | [CA2328: Asegurarse de que los valores JsonSerializerSettings sean seguros](../code-quality/ca2328.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2329 | [CA2329: No deserializar con JsonSerializer y una configuración no segura](../code-quality/ca2329.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2330 | [CA2330: Asegurarse de que la configuración de JsonSerializer es segura al deserializar](../code-quality/ca2330.md) | Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. |
| CA2350 | [CA2350: Asegurarse de que la entrada de DataTable.ReadXml() sea de confianza](ca2350.md) | Al deserializar un <xref:System.Data.DataTable> con una entrada que no es de confianza, un atacante puede crear una entrada malintencionada para realizar un ataque de denegación de servicio. Puede haber vulnerabilidades de ejecución de código remoto desconocidas. |
| CA2351 | [CA2351: Asegúrese de que la entrada de DataSet.ReadXml() sea de confianza](ca2351.md) | Al deserializar un <xref:System.Data.DataSet> con una entrada que no es de confianza, un atacante puede crear una entrada malintencionada para realizar un ataque de denegación de servicio. Puede haber vulnerabilidades de ejecución de código remoto desconocidas. |
| CA2352 | [CA2352: Un objeto DataSet o DataTable no seguro en un tipo serializable puede ser vulnerable a ataques de ejecución de código remoto](ca2352.md) | Una clase o estructura marcada con <xref:System.SerializableAttribute> contiene un <xref:System.Data.DataSet> campo o una <xref:System.Data.DataTable> propiedad, y no tiene un <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> . |
| CA2353 | [CA2353: Objeto DataSet o DataTable no seguro en un tipo serializable](ca2353.md) | Una clase o estructura marcada con un atributo de serialización XML o un atributo de contrato de datos contiene una <xref:System.Data.DataSet> propiedad o un <xref:System.Data.DataTable> campo o. |
| CA2354 | [CA2354: Un objeto DataSet o DataTable no seguro en un gráfico de objetos deserializado puede ser vulnerable a ataques de ejecución de código remoto](ca2354.md) | La deserialización con un <xref:System.Runtime.Serialization.IFormatter?displayProperty=nameWithType> serializado y el gráfico de objetos del tipo convertido pueden incluir <xref:System.Data.DataSet> o <xref:System.Data.DataTable> . |
| CA2355 | [CA2355: Objeto DataSet o DataTable no seguro en un gráfico de objetos deserializado](ca2355.md) | Deserializar cuando el gráfico de objetos del tipo especificado o convertido puede incluir <xref:System.Data.DataSet> o <xref:System.Data.DataTable> . |
| CA2356 | [CA2356: DataSet no seguro o DataTable en el gráfico de objetos deserializados Web](ca2356.md) | Un método con <xref:System.Web.Services.WebMethodAttribute?displayProperty=nameWithType> o <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> tiene un parámetro que puede hacer referencia a un <xref:System.Data.DataSet> o <xref:System.Data.DataTable> . |
| CA2361 | [CA2361: Asegurarse de que la clase autogenerada que contiene DataSet.ReadXml() no se utilice con datos que no son de confianza](ca2361.md) | Al deserializar un <xref:System.Data.DataSet> con una entrada que no es de confianza, un atacante puede crear una entrada malintencionada para realizar un ataque de denegación de servicio. Puede haber vulnerabilidades de ejecución de código remoto desconocidas. |
| CA2362 | [CA2362: Un elemento DataSet o DataTable no seguro en un tipo serializable autogenerado puede ser vulnerable a ataques de ejecución remota de código](ca2362.md) | Al deserializar la entrada que no es de confianza con <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> y el gráfico de objetos deserializados contiene <xref:System.Data.DataSet> o <xref:System.Data.DataTable> , un atacante puede crear una carga malintencionada para realizar un ataque de ejecución de código remoto. |
| CA3001 | [CA3001: Revisión de código en busca de vulnerabilidades de inyección de SQL](../code-quality/ca3001.md) | Al trabajar con comandos SQL y de entrada que no son de confianza, tenga en cuentan los ataques por inyección de SQL. Un ataque por inyección de SQL puede ejecutar comandos SQL malintencionados, poniendo en peligro la seguridad y la integridad de la aplicación. |
| CA3002 | [CA3002: Revisión de código en busca de vulnerabilidades de XSS](../code-quality/ca3002.md) | Al trabajar con una entrada que no es de confianza de las solicitudes Web, tenga en cuentan los ataques de scripting entre sitios (XSS). Un ataque XSS inyecta entradas que no son de confianza en salidas HTML sin procesar, lo que permite al atacante ejecutar scripts malintencionados o modificar contenido de forma malintencionada en la Página Web. |
| CA3003 | [CA3003: Revisión de código en busca de vulnerabilidades de inyección de rutas de acceso a archivos](../code-quality/ca3003.md) | Al trabajar con una entrada que no es de confianza de las solicitudes Web, tenga en cuentan el uso de entradas controladas por el usuario al especificar las rutas de acceso a los archivos. |
| CA3004 | [CA3004: Revisión de código en busca de vulnerabilidades de divulgación de información](../code-quality/ca3004.md) | Al revelar la información de la excepción, se ofrece a los atacantes información sobre el funcionamiento interno de la aplicación, lo que puede ayudar a los atacantes a encontrar otras vulnerabilidades que se puedan aprovechar. |
| CA3006 | [CA3006: Revisión de código en busca de vulnerabilidades de inyección de comandos de procesos](../code-quality/ca3006.md) | Al trabajar con una entrada que no es de confianza, tenga en cuentan los ataques por inyección de comandos. Un ataque por inyección de comandos puede ejecutar comandos malintencionados en el sistema operativo subyacente, poniendo en peligro la seguridad y la integridad del servidor. |
| CA3007 | [CA3007: Revisión de código en busca de vulnerabilidades de redireccionamiento abierto](../code-quality/ca3007.md) | Al trabajar con una entrada que no es de confianza, tenga en cuentan las vulnerabilidades de redireccionamiento abierto. Un atacante puede aprovechar una vulnerabilidad de redirección abierta para usar el sitio web con el fin de dar la apariencia de una dirección URL legítima, pero redirigir a un visitante que no sospecha a un phishing u otra página web malintencionada. |
| CA3008 | [CA3008: Revisión de código en busca de vulnerabilidades de inyección de XPath](../code-quality/ca3008.md) | Al trabajar con una entrada que no es de confianza, tenga en cuentan los ataques por inyección de XPath. La construcción de consultas XPath mediante la entrada que no es de confianza puede permitir a un atacante manipular de forma malintencionada la consulta para devolver un resultado no deseado y, posiblemente, divulgar el contenido del XML consultado. |
| CA3009 | [CA3009: Revisión de código en busca de vulnerabilidades de inyección de XML](../code-quality/ca3009.md) | Al trabajar con una entrada que no es de confianza, tenga en cuentan los ataques por inyección de XML. |
| CA3010 | [CA3010: Revisión de código en busca de vulnerabilidades de inyección de XAML](../code-quality/ca3010.md) | Al trabajar con una entrada que no es de confianza, tenga en cuentan los ataques por inyección de XAML. XAML es un lenguaje de marcado que representa directamente la creación de instancias y la ejecución de objetos. Esto significa que los elementos creados en XAML pueden interactuar con los recursos del sistema (por ejemplo, el acceso a la red y la e/s del sistema de archivos). |
| CA3011 | [CA3011: Revisión de código en busca de vulnerabilidades de inyección de DLL](../code-quality/ca3011.md) | Al trabajar con una entrada que no es de confianza, tenga en cuentan la carga de código que no es de confianza. Si la aplicación web carga código que no es de confianza, es posible que un atacante pueda insertar archivos dll malintencionados en el proceso y ejecutar código malintencionado. |
| CA3012 | [CA3012: Revisión de código en busca de vulnerabilidades de inyección de expresiones regulares](../code-quality/ca3012.md) | Al trabajar con una entrada que no es de confianza, tenga en cuentan los ataques por inyección de Regex. Un atacante puede usar la inyección de Regex para modificar de forma malintencionada una expresión regular, para hacer que el regex coincida con los resultados imprevistos o para hacer que la expresión regular consuma una CPU excesiva, lo que produce un ataque de denegación de servicio. |
| CA3061 | [CA3061: No agregar esquema por dirección URL](../code-quality/ca3061.md) | No use la sobrecarga no segura del método Add porque puede provocar referencias externas peligrosas. |
| CA3075 | [CA3075: Procesamiento no seguro de DTD](../code-quality/ca3075.md) | Si usa instancias de DTDProcessing inseguras o hace referencia a orígenes de entidades externas, el analizador podría aceptar entradas que no sean de confianza y revelar información confidencial a atacantes. |
| CA3076 | [CA3076: Ejecución del script XSLT no segura](../code-quality/ca3076.md) | Si ejecuta transformaciones del lenguaje de hojas de estilo extensible (XSLT) en aplicaciones .NET de forma no segura, el procesador puede resolver referencias de URI que no son de confianza y que podrían revelar información confidencial a atacantes, lo que provoca ataques de denegación de servicio y entre sitios. |
| CA3077 | [CA3077: Procesamiento no seguro en el diseño de una API, documento XML y lector de texto XML](../code-quality/ca3077.md) | Al diseñar una API derivada de XMLDocument y XMLTextReader, tenga en cuenta la propiedad DtdProcessing. El uso de instancias de DTDProcessing inseguras al hacer referencia a orígenes de entidades externas o resolverlos, o la definición de valores inseguros en el lenguaje XML puede provocar la divulgación de información. |
| CA3147 | [CA3147: Marcar los controladores de verbo con ValidateAntiForgeryToken](../code-quality/ca3147.md) | Al diseñar un controlador ASP.NET MVC, tenga en cuentan los ataques de falsificación de solicitudes entre sitios. Un ataque de falsificación de solicitudes entre sitios puede enviar solicitudes malintencionadas de un usuario autenticado a su controlador ASP.NET MVC. |
| CA5350 | [CA5350: No usar algoritmos criptográficos no seguros](../code-quality/ca5350.md) | Las funciones hash y los algoritmos de cifrado débiles se usan hoy en día para numerosos propósitos, pero no se recomiendan para garantizar la confidencialidad o la integridad de los datos que se protegen. Esta regla se desencadena cuando se encuentran los algoritmos TripleDES, SHA1 o RIPEMD160 en el código.|
| CA5351 | [CA5351 No use algoritmos criptográficos rotos](../code-quality/ca5351.md) | Los algoritmos criptográficos rotos no se consideran seguros y debe desalentarse su uso. Esta regla se desencadena cuando encuentra el algoritmo hash MD5 o los algoritmos de cifrado DES o RC2 en el código. |
| CA5358 | [CA5358: No usar modos de cifrado inseguro](../code-quality/ca5358.md) | No usar modos de cifrado inseguro |
| CA5359 | [CA5359 no deshabilitar la validación de certificados](../code-quality/ca5359.md) | Un certificado puede ayudar a autenticar la identidad del servidor. Los clientes deben validar el certificado de servidor para asegurarse de que las solicitudes se envían al servidor previsto. Si ServerCertificateValidationCallback (siempre devuelve `true` , cualquier certificado pasará la validación. |
| CA5360 | [CA5360 no llama a métodos peligrosos en la deserialización](../code-quality/ca5360.md) | La deserialización no segura es una vulnerabilidad que se produce cuando los datos que no son de confianza se usan para abusar la lógica de una aplicación, provocar un ataque de denegación de servicio (DoS) o incluso ejecutar código arbitrario cuando se deserializa. A menudo, es posible que los usuarios malintencionados abusan estas características de deserialización cuando la aplicación está deserializando datos que no son de confianza y están bajo su control. En concreto, invoque métodos peligrosos en el proceso de deserialización. Los ataques de deserialización inseguros que se han realizado correctamente podrían permitir que un atacante lleve a cabo ataques como ataques de DoS, omisiones de autenticación y ejecución remota de código. |
| CA5361 | [CA5361: No deshabilitar el uso de cifrado seguro de SChannel](../code-quality/ca5361.md) | Establecer `Switch.System.Net.DontEnableSchUseStrongCrypto` para `true` debilita la criptografía usada en las conexiones de seguridad de la capa de transporte (TLS) salientes. La criptografía más débil puede poner en peligro la confidencialidad de la comunicación entre la aplicación y el servidor, lo que facilita a los atacantes la interceptación de información confidencial. |
| CA5362 | [Ciclo de referencia potencial de CA5362 en el gráfico de objetos deserializados](../code-quality/ca5362.md) | Si se deserializan los datos que no son de confianza, el procesamiento de código del gráfico de objetos deserializados debe controlar los ciclos de referencia sin entrar en bucles infinitos. Esto incluye el código que forma parte de una devolución de llamada de deserialización y el código que procesa el gráfico de objetos una vez completada la deserialización. De lo contrario, un atacante podría realizar un ataque por denegación de servicio con datos malintencionados que contuvieran un ciclo de referencia. |
| CA5363 | [CA5363: No deshabilitar la validación de solicitudes](../code-quality/ca5363.md) | La validación de solicitudes es una característica de ASP.NET que examina las solicitudes HTTP y determina si contienen contenido potencialmente peligroso que puede conducir a ataques de inyección, incluido el scripting entre sitios. |
| CA5364 | [CA5364: No usar protocolos de seguridad en desuso](../code-quality/ca5364.md) | La seguridad de la capa de transporte (TLS) protege la comunicación entre equipos, normalmente con el protocolo seguro de transferencia de hipertexto (HTTPS). Las versiones de protocolo anteriores de TLS son menos seguras que las de TLS 1,2 y TLS 1,3 y es más probable que tengan nuevas vulnerabilidades. Evite las versiones anteriores del protocolo para minimizar el riesgo. |
| CA5365 | [CA5365 no deshabilitar la comprobación de encabezados HTTP](../code-quality/ca5365.md) | La comprobación de encabezados HTTP permite codificar el retorno de carro y los caracteres de nueva línea, \r y \n, que se encuentran en los encabezados de respuesta. Esta codificación puede ayudar a evitar ataques de inyección que aprovechan una aplicación que repite datos que no son de confianza contenidos en el encabezado. |
| CA5366 | [CA5366 usar XmlReader para leer XML de DataSet](../code-quality/ca5366.md) | El uso de <xref:System.Data.DataSet> para leer XML con datos que no son de confianza puede cargar referencias externas peligrosas, que se deben restringir mediante un <xref:System.Xml.XmlReader> con un solucionador seguro o con el procesamiento de DTD deshabilitado. |
| CA5367 | [CA5367 no serializan tipos con campos de puntero](../code-quality/ca5367.md) | Esta regla comprueba si hay una clase serializable con una propiedad o un campo de puntero. Los miembros que no se pueden serializar pueden ser un puntero, como los miembros estáticos o los campos marcados con <xref:System.NonSerializedAttribute> . |
| CA5368 | [CA5368 Set ViewStateUserKey para las clases derivadas de Page](../code-quality/ca5368.md) | El establecimiento de la <xref:System.Web.UI.Page.ViewStateUserKey> propiedad puede ayudarle a evitar ataques en la aplicación al permitirle asignar un identificador a la variable de estado de vista de usuarios individuales para que los atacantes no puedan usar la variable para generar un ataque. De lo contrario, habrá vulnerabilidades en la falsificación de solicitudes entre sitios. |
| CA5369 | [CA5369: Usar XmlReader para deserializar](../code-quality/ca5369.md) | El procesamiento de DTD y esquemas XML que no son de confianza puede habilitar la carga de referencias externas peligrosas, que se deben restringir mediante un XmlReader con un solucionador seguro o con el procesamiento de esquemas en línea XML y DTD deshabilitado. |
| CA5370 | [CA5370: Usar XmlReader para validar el lector](../code-quality/ca5370.md) | El procesamiento de DTD y esquemas XML que no son de confianza puede habilitar la carga de referencias externas peligrosas. Esta carga peligrosa se puede restringir mediante el uso de un XmlReader con un solucionador seguro o con el procesamiento de esquemas en línea de DTD y XML deshabilitado. |
| CA5371 | [CA5371: Usar XmlReader para leer el esquema](../code-quality/ca5371.md) | El procesamiento de DTD y esquemas XML que no son de confianza puede habilitar la carga de referencias externas peligrosas. El uso de un XmlReader con un solucionador seguro o con DTD y el procesamiento de esquemas en línea XML deshabilitado restringe esto. |
| CA5372 | [CA5372: Usar XmlReader para XPathDocument](../code-quality/ca5372.md) | El procesamiento de XML a partir de datos que no son de confianza puede cargar referencias externas peligrosas, que se pueden restringir mediante un XmlReader con un solucionador seguro o con el procesamiento de DTD deshabilitado. |
| CA5373 | [CA5373: No usar la función de derivación de clave obsoleta](../code-quality/ca5373.md) | Esta regla detecta la invocación de métodos de derivación de claves débiles <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> y `Rfc2898DeriveBytes.CryptDeriveKey` . <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> usó un algoritmo débil del PBKDF1. |
| CA5374 | [CA5374 no usar XslTransform](../code-quality/ca5374.md) | Esta regla comprueba si <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> se crean instancias en el código. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> está ahora obsoleto y no debe usarse. |
| CA5375 | [CA5375 no usar firma de acceso compartido de cuenta](../code-quality/ca5375.md) | Una SAS de cuenta puede delegar el acceso a operaciones de lectura, escritura y eliminación en contenedores de blobs, tablas, colas y recursos compartidos de archivos que no se permiten con una SAS de servicio. Sin embargo, no es compatible con las directivas de nivel de contenedor y tiene menos flexibilidad y control sobre los permisos que se conceden. Una vez que los usuarios malintencionados la obtienen, la cuenta de almacenamiento se verá comprometida fácilmente. |
| CA5376 | [CA5376 uso de SharedAccessProtocol HttpsOnly](../code-quality/ca5376.md) | SAS es información confidencial que no se puede transportar en texto sin formato en HTTP. |
| CA5377 | [CA5377 usar la Directiva de acceso de nivel de contenedor](../code-quality/ca5377.md) | Una directiva de acceso de nivel de contenedor se puede modificar o revocar en cualquier momento. Proporciona mayor flexibilidad y control sobre los permisos que se conceden. |
| CA5378 | [CA5378: No deshabilitar ServicePointManagerSecurityProtocols](../code-quality/ca5378.md) | Establecer `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` en `true` limita las conexiones de seguridad de la capa de transporte (TLS) de Windows Communication Framework (WCF) al uso de TLS 1,0. Esa versión de TLS quedará en desuso. |
| CA5379 | [CA5379 no usar el algoritmo de función de derivación de clave débil](../code-quality/ca5379.md) | De <xref:System.Security.Cryptography.Rfc2898DeriveBytes> forma predeterminada, la clase usa el <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> algoritmo. Debe especificar el algoritmo hash que se utilizará en algunas sobrecargas del constructor con <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> o superior. Tenga en cuenta <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> que la propiedad solo tiene un `get` descriptor de acceso y no tiene un `overriden` modificador. |
| CA5380 | [CA5380: No agregar certificados al almacén raíz](../code-quality/ca5380.md) | Esta regla detecta código que agrega un certificado al almacén de certificados de entidades de certificación raíz de confianza. De forma predeterminada, el almacén de certificados de entidades de certificación raíz de confianza se configura con un conjunto de entidades de certificación públicas que cumplen los requisitos del programa de certificados raíz de Microsoft. |
| CA5381 | [CA5381: Asegurar que no se agregan certificados al almacén raíz](../code-quality/ca5381.md) | Esta regla detecta código que puede Agregar un certificado al almacén de certificados de entidades de certificación raíz de confianza. De forma predeterminada, el almacén de certificados de entidades de certificación raíz de confianza se configura con un conjunto de entidades de certificación (CA) públicas que cumplen los requisitos del programa de certificados raíz de Microsoft. |
| CA5382 | [CA5382 usar cookies seguras en ASP.NET Core](../code-quality/ca5382.md) | Las aplicaciones disponibles a través de HTTPS deben usar cookies seguras, que indican al explorador que la cookie solo se debe transmitir mediante Capa de sockets seguros (SSL). |
| CA5383 | [CA5383 Asegúrese de usar cookies seguras en ASP.NET Core](../code-quality/ca5383.md) | Las aplicaciones disponibles a través de HTTPS deben usar cookies seguras, que indican al explorador que la cookie solo se debe transmitir mediante Capa de sockets seguros (SSL). |
| CA5384 | [CA5384 no usar el algoritmo de firma digital (DSA)](../code-quality/ca5384.md) | DSA es un algoritmo de cifrado asimétrico débil. |
| CA5385 | [CA5385 usar el algoritmo Rivest – Shamir – Adleman (RSA) con el tamaño de clave suficiente](../code-quality/ca5385.md) | Una clave RSA de menos de 2048 bits es más vulnerable a los ataques por fuerza bruta. |
| CA5386 | [CA5386: Evitar codificar el valor SecurityProtocolType de forma rígida](../code-quality/ca5386.md) | La seguridad de la capa de transporte (TLS) protege la comunicación entre equipos, normalmente con el protocolo seguro de transferencia de hipertexto (HTTPS). Las versiones de protocolo TLS 1,0 y TLS 1,1 están desusadas, mientras que TLS 1,2 y TLS 1,3 están actualizados. En el futuro, TLS 1,2 y TLS 1,3 pueden estar en desuso. Para asegurarse de que la aplicación sigue siendo segura, evite codificar una versión del protocolo y tenga como destino al menos .NET Framework v 4.7.1. |
| CA5387 | [CA5387 no usar la función de derivación de clave débil con el recuento de iteraciones insuficiente](../code-quality/ca5387.md) | Esta regla comprueba si se generó una clave criptográfica <xref:System.Security.Cryptography.Rfc2898DeriveBytes> con un recuento de iteraciones inferior a 100.000. Un recuento de iteraciones mayor puede ayudar a mitigar los ataques de diccionario que intentan adivinar la clave criptográfica generada. |
| CA5388 | [CA5388 garantizar el número de iteraciones suficientes al usar la función de derivación de clave débil](../code-quality/ca5388.md) | Esta regla comprueba si se generó una clave criptográfica <xref:System.Security.Cryptography.Rfc2898DeriveBytes> con un recuento de iteraciones que puede ser inferior a 100.000. Un recuento de iteraciones mayor puede ayudar a mitigar los ataques de diccionario que intentan adivinar la clave criptográfica generada. |
| CA5389 | [CA5389: No agregar la ruta de acceso del elemento de archivo a la ruta de acceso del sistema de archivos de destino](../code-quality/ca5389.md) | La ruta de acceso de archivo puede ser relativa y puede dar lugar a un acceso al sistema de archivos fuera de la ruta de destino del sistema de archivos esperada, lo que provoca cambios de configuración malintencionados y la ejecución remota de código mediante la técnica de establecer y esperar. |
| CA5390 | [CA5390 no codificar clave de cifrado](../code-quality/ca5390.md) | Para que un algoritmo simétrico se realice correctamente, solo el remitente y el receptor deben conocer la clave secreta. Cuando una clave está codificada de forma rígida, se detecta fácilmente. Incluso con los archivos binarios compilados, es fácil que los usuarios malintencionados lo extraigan. Una vez que la clave privada se ve comprometida, el texto cifrado se puede descifrar directamente y ya no está protegido. |
| CA5391 | [CA5391 usar tokens antifalsificación en controladores MVC de ASP.NET Core](../code-quality/ca5391.md) | Controlar una `POST` `PUT` solicitud,, `PATCH` o `DELETE` sin validar un token antifalsificación puede ser vulnerable a los ataques de falsificación de solicitudes entre sitios. Un ataque de falsificación de solicitudes entre sitios puede enviar solicitudes malintencionadas de un usuario autenticado a un controlador de MVC de ASP.NET Core. |
| CA5392 | [CA5392 usar el atributo DefaultDllImportSearchPaths para P/Invoke](../code-quality/ca5392.md) | De forma predeterminada, las funciones P/Invoke <xref:System.Runtime.InteropServices.DllImportAttribute> que usan sondeos incluyen un número de directorios, incluido el directorio de trabajo actual de la biblioteca que se va a cargar. Puede tratarse de un problema de seguridad para ciertas aplicaciones, lo que conduce a la secuestro de DLL. |
| CA5393 | [CA5393 no usar un valor DllImportSearchPath no seguro](../code-quality/ca5393.md) | Podría haber un archivo DLL malintencionado en los directorios de búsqueda DLL predeterminados y los directorios de ensamblado. O, en función de dónde se ejecute la aplicación, podría haber un archivo DLL malintencionado en el directorio de la aplicación. |
| CA5394 | [CA5394 no usar aleatoriedad no segura](../code-quality/ca5394.md) | El uso de un generador de números pseudoaleatorios no seguros criptográficamente puede permitir que un atacante prediga qué valor de seguridad se generará. |
| CA5395 | [CA5395 perdió HttpVerb atributo para métodos de acción](../code-quality/ca5395.md) | Todos los métodos de acción que crean, modifican, eliminan o modifican de algún otro modo los datos deben protegerse con el atributo antifalsificación de los ataques de falsificación de solicitudes entre sitios. Realizar una operación GET debe ser una operación segura que no tenga efectos secundarios y no modifique los datos persistentes. |
| CA5396 | [CA5396 establecer HttpOnly en true para HttpCookie](../code-quality/ca5396.md) | Como medida de defensa en profundidad, asegúrese de que las cookies HTTP confidenciales de seguridad estén marcadas como HttpOnly. Esto indica que los exploradores Web deben impedir que los scripts tengan acceso a las cookies. Los scripts malintencionados insertados son una forma habitual de robar cookies. |
| CA5397 | [CA5397: No usar valores SslProtocols en desuso](../code-quality/ca5397.md) | La seguridad de la capa de transporte (TLS) protege la comunicación entre equipos, normalmente con el protocolo seguro de transferencia de hipertexto (HTTPS). Las versiones de protocolo anteriores de TLS son menos seguras que las de TLS 1,2 y TLS 1,3 y es más probable que tengan nuevas vulnerabilidades. Evite las versiones anteriores del protocolo para minimizar el riesgo. |
| CA5398 | [CA5398: Evitar valores SslProtocols codificados de forma rígida](../code-quality/ca5398.md) | La seguridad de la capa de transporte (TLS) protege la comunicación entre equipos, normalmente con el protocolo seguro de transferencia de hipertexto (HTTPS). Las versiones de protocolo TLS 1,0 y TLS 1,1 están desusadas, mientras que TLS 1,2 y TLS 1,3 están actualizados. En el futuro, TLS 1,2 y TLS 1,3 pueden estar en desuso. Para asegurarse de que la aplicación sigue siendo segura, evite codificar una versión del protocolo. |
| CA5399 | [CA5399 deshabilitar definitivamente la comprobación de la lista de revocación de certificados HttpClient](../code-quality/ca5399.md) | Un certificado revocado ya no es de confianza. Podría ser utilizado por los atacantes para pasar algunos datos malintencionados o robar datos confidenciales en la comunicación HTTPS. |
| CA5400 | [CA5400 asegurarse de que la lista de revocación de certificados HttpClient no está deshabilitada](../code-quality/ca5400.md) | Un certificado revocado ya no es de confianza. Podría ser utilizado por los atacantes para pasar algunos datos malintencionados o robar datos confidenciales en la comunicación HTTPS. |
| CA5401 | [CA5401 no usar CreateEncryptor con un IV no predeterminado](../code-quality/ca5401.md) | El cifrado simétrico siempre debe usar un vector de inicialización no repetible para evitar ataques de diccionario. |
| CA5402 | [CA5402 usar CreateEncryptor con el valor de IV predeterminado](../code-quality/ca5402.md) | El cifrado simétrico siempre debe usar un vector de inicialización no repetible para evitar ataques de diccionario. |
| CA5403 | [CA5403: No codificar el certificado de forma rígida](../code-quality/ca5403.md) | El `data` `rawData` parámetro o de un <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> constructor o está codificado de forma rígida. |
| IL3000 | [IL3000 evitar el acceso a la ruta de acceso del archivo de ensamblado al publicar como un solo archivo](../code-quality/il3000.md) | Evite el uso de la ruta de acceso del archivo de ensamblado al publicar como un solo archivo |
| IL3001 | [IL3001 evitar el acceso a la ruta de acceso del archivo de ensamblado al publicar como un solo archivo](../code-quality/il3001.md) | Evitar el acceso a la ruta de acceso del archivo de ensamblado al publicar como un solo archivo |
