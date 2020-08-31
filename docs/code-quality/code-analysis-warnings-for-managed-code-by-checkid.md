---
title: Información general sobre las reglas de calidad del código
ms.date: 08/27/2020
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1004
- CA1005
- CA1006
- CA1007
- CA1008
- CA1009
- CA1010
- CA1011
- CA1012
- CS1013
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1020
- CA1021
- CA1022
- CA1023
- CA1024
- CS1025
- CA1026
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1035
- CA1036
- CA1037
- CA1038
- CA1039
- CA1040
- CA1041
- CA1042
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1048
- CA1049
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1057
- CA1058
- CA1059
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
- CA1300
- CA1301
- CA1302
- CA1303
- CA1304
- CA1305
- CA1306
- CA1307
- CA1308
- CA1309
- CA1400
- CA1401
- CA1402
- CA1403
- CA1404
- CA1405
- CA1406
- CA1407
- CA1408
- CA1409
- CA1410
- CA1411
- CA1412
- CA1413
- CA1414
- CA1415
- CA1417
- CA1500
- CA1501
- CA1502
- CA1503
- CA1504
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1600
- CA1601
- CA1700
- CA1701
- CA1702
- CA1703
- CA1704
- CA1707
- CA1708
- CA1709
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- VA1716
- CA1717
- CA1719
- CA1720
- CA1721
- CA1722
- CA1723
- CA1724
- CA1725
- CA1726
- CA1727
- CA1728
- CA1729
- CA1730
- CA1800
- CA1801
- CA1802
- CA1803
- CA1804
- CA1805
- CA1806
- CA1809
- CA1810
- CA1811
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
- CA1835
- CA1836
- CA1838
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
- CA2007
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
- CA2016
- CA2100
- CA2101
- CA2102
- CA2103
- CA2104
- CA2105
- CA2106
- CA2107
- CA2108
- CA2109
- CA2110
- CA2111
- CA2112
- CA2114
- CA2115
- CA2116
- CA2117
- CA2118
- CA2119
- CA2120
- CA2121
- CA2122
- CA2123
- CA2124
- CA2126
- CA2127
- CA2128
- CA2129
- CA2130
- CA2131
- CA2132
- CA2133
- CA2134
- CA2135
- CA2136
- CA2137
- CA2138
- CA2139
- CA2140
- CA2141
- CA2142
- CA2143
- CA2144
- CA2145
- CA2146
- CA2147
- CA2148
- CA2149
- CA2150
- CA2151
- CA2200
- CA2201
- CA2202
- CA2204
- CA2205
- CA2207
- CA2208
- CA2210
- CA2211
- CA2212
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2218
- CA2219
- CA2220
- CA2221
- CA2222
- CA2223
- CA2224
- CA2225
- CA2226
- CA2228
- CA2229
- CA2227
- CA2230
- CA2231
- CA2232
- CA2233
- CA2234
- CA2235
- CA2236
- CA2237
- CA2238
- CA2239
- CA2240
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA2247
- CA5122
- CA5374
- IL3000
- IL3001
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 61c15689e92132d4e3e089823bc94fc90852d4ed
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176070"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Advertencias de análisis de código para código administrado por CheckId

En la tabla siguiente se enumeran las advertencias de análisis de código para código administrado ordenadas por el identificador CheckId de la advertencia.

| Identificador de comprobación | Advertencia | Descripción |
|---------| - | - |
| CA1000 | [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000.md) | Cuando se llama a un miembro estático de un tipo genérico, se debe especificar el argumento de tipo correspondiente a ese tipo. Cuando se llama a un miembro de instancia genérico que no admite la interferencia, se debe especificar el argumento de tipo para el miembro. En estos dos casos, la sintaxis para especificar el argumento de tipo es diferente y resulta fácil confundirse. |
| CA1001 | [CA1001: Los tipos que poseen campos descartables deben ser descartables](../code-quality/ca1001.md) | Una clase declara e implementa un campo de instancia que es de tipo System.IDisposable y la clase no implementa IDisposable. Una clase que declara un campo IDisposable posee indirectamente un recurso no administrado y debería implementar la interfaz IDisposable. |
| CA1002 | [CA1002: No exponer listas genéricas](../code-quality/ca1002.md) | System. Collections. Generic. List< (of \<(T> ) >) es una colección genérica diseñada para el rendimiento, no para la herencia. Por consiguiente, List no contiene ningún miembro virtual. En su lugar, se debe exponer las colecciones genéricas diseñadas para herencia. |
| CA1003 | [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003.md) |Un tipo contiene un delegado que devuelve void cuya firma contiene dos parámetros (el primero un objeto y el segundo un tipo asignable a EventArgs), y el ensamblado que lo contiene está dirigido a Microsoft .NET Framework 2.0. |
| CA1004 | [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004.md) | La inferencia es el modo en que se determina el argumento de tipo de un método genérico partiendo del tipo de argumento pasado al método, en lugar de especificar directamente el argumento de tipo. Para habilitar la inferencia, la firma de parámetro de un método genérico debe incluir un parámetro del mismo tipo que el parámetro type del método. En este caso, no es necesario especificar el argumento de tipo. Cuando se utiliza la inferencia para todos los parámetros de tipo, la sintaxis para llamar a los métodos de instancia genéricos y no genéricos es la misma; esto simplifica la capacidad de uso de los métodos genéricos. |
| CA1005 | [CA1005: Evitar los parámetros excesivos en tipos genéricos](../code-quality/ca1005.md) | Cuantos más parámetros type contenga un tipo genérico, más difícil resulta saber y recordar qué representa cada uno de ellos. Normalmente, es obvio con un parámetro de tipo, como en la lista \<T> , y en determinados casos que tienen dos parámetros de tipo, como en el diccionario \<TKey, TValue> . Sin embargo, si hay más de dos parámetros de tipo, la dificultad se vuelve demasiado grande para la mayoría de los usuarios. |
| CA1006 | [CA1006: No anidar tipos genéricos en signaturas de miembro](../code-quality/ca1006.md) | Un argumento de tipo anidado es un argumento de tipo que también es un tipo genérico. Para llamar a un miembro cuya firma contenga un argumento de tipo anidado, el usuario debe crear instancias de un tipo genérico y pasar este tipo al constructor de un segundo tipo genérico. El procedimiento y la sintaxis necesarios para ello son complejos, por lo que es preferible evitarlo. |
| CA1007 |[CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007.md) | Un método visible externamente contiene un parámetro de referencia de tipo System.Object. El uso de un método genérico permite pasar al método todos los tipos, sujeto a las restricciones que puedan ser de aplicación, sin convertirlos antes al tipo del parámetro de referencia. |
| CA1008 | [CA1008: Las enumeraciones deben tener un valor igual a cero](../code-quality/ca1008.md) | El valor predeterminado de una enumeración no inicializada, igual que otros tipos de valor, es cero. Una enumeración con atributo y sin marcadores debería definir un miembro con el valor de cero de modo que el valor predeterminado sea un valor válido de la enumeración. Si una enumeración a la que se le haya aplicado el atributo FlagsAttribute define un miembro con valor cero, su nombre debe ser "None" para indicar que no se han establecido valores en la enumeración. |
| CA1009 | [CA1009: Declarar los controladores de evento correctamente](../code-quality/ca1009.md) | Los métodos de control de eventos toman dos parámetros. El primero es de tipo System.Object y se denomina "sender". Éste es el objeto que provocó el evento. El segundo parámetro es de tipo System.EventArgs y se denomina "e". Estos son los datos están asociados a este evento. Los métodos de control de eventos no deben devolver un valor; en el lenguaje de programación C#, esto se indica mediante el tipo de valor devuelto void. |
| CA1010 | [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010.md) | Para ampliar la utilidad de una colección, implemente una de las interfaces de colección genéricas. Entonces podrá utilizar la colección para rellenar tipos de colecciones genéricas. |
| CA1011 |[CA1011: Considerar pasar los tipos base como parámetros](../code-quality/ca1011.md) | Cuando en una declaración de método se especifica un tipo base como parámetro, cualquier tipo derivado del tipo base puede pasarse al método como el argumento correspondiente. Si la funcionalidad adicional proporcionada por el tipo de parámetro derivado no resulta necesaria, el uso del tipo base permite que el método se utilice más ampliamente. |
| CA1012 | [CA1012: Los tipos abstractos no deberían tener constructores](../code-quality/ca1012.md) | Los tipos derivados pueden llamar solo a los constructores de tipos abstractos. Puesto que los constructores públicos crean instancias de un tipo y no se pueden crear instancias de un tipo abstracto, no es correcto diseñar un tipo abstracto con un constructor público. |
| CA1013 | [CA1013: El operador de sobrecarga es igual que la suma y resta de sobrecarga](../code-quality/ca1013.md) | Un tipo público o protegido implementa los operadores de suma o resta sin implementar el operador de igualdad. |
| CA1014 | [CA1014: Marcar los ensamblados con CLSCompliantAttribute](../code-quality/ca1014.md) | La Common Language Specification (CLS) define las restricciones de nomenclatura, los tipos de datos y las reglas a las que los ensamblados deben ajustarse si se van a utilizar los lenguajes de programación. Los procedimientos de diseño establecen que todos los ensamblados deben indicar explícitamente la conformidad a CLS mediante el atributo <xref:System.CLSCompliantAttribute>. Si este atributo no está presente en un ensamblado, el ensamblado no es conforme. |
| CA1016 | [CA1016: Marcar los ensamblados con AssemblyVersionAttribute](../code-quality/ca1016.md) | .NET usa el número de versión para identificar de forma única un ensamblado y enlazar a los tipos de ensamblados con nombre seguro. El número de versión se utiliza junto con la versión y la directiva del fabricante. De forma predeterminada, las aplicaciones sólo se ejecutan con la versión de ensamblado con la que se compilaron. |
| CA1017 | [CA1017: Marcar los ensamblados con ComVisibleAttribute](../code-quality/ca1017.md) |ComVisibleAttribute determina cómo obtienen acceso los clientes COM al código administrado. Los procedimientos de diseño recomendados dictan que los ensamblados indican explícitamente la visibilidad COM. La visibilidad COM se puede establecer para un ensamblado completo y, a continuación, se puede invalidar para los tipos individuales y los miembros de tipo. Si este atributo no está presente, el contenido del ensamblado es visible para los clientes COM. |
| CA1018 | [CA1018: Marcar atributos con AttributeUsageAttribute](../code-quality/ca1018.md) | Cuando defina un atributo personalizado, márquelo utilizando AttributeUsageAttribute para indicar dónde se puede aplicar en el código fuente. El significado de un atributo y el uso que se le va a dar determinará sus ubicaciones válidas en código. |
| CA1019 | [CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019.md) | Los atributos pueden definir argumentos obligatorios que deben especificarse al aplicar el atributo a un destino. Éstos también se denominan argumentos posicionales porque se proporcionan para atribuir constructores como parámetros posicionales. Para cada argumento obligatorio, el atributo debe proporcionar también una propiedad de sólo lectura correspondiente de modo que el valor del argumento se pueda recuperar en tiempo de ejecución. Los atributos también pueden definir argumentos opcionales, que también se denominan argumentos con nombre. Estos argumentos se proporcionan para atribuir constructores por nombre y deben tener una propiedad de lectura/escritura correspondiente. |
| CA1020 | [CA1020: Evitar los espacios de nombres con pocos tipos](../code-quality/ca1020.md) | Asegúrese de que hay una organización lógica para cada espacio de nombres y que existe una razón para colocar los tipos en un espacio de nombres apenas lleno. |
| CA1021 | [CA1021: Evitar los parámetros out](../code-quality/ca1021.md) | Para pasar tipos por referencia (utilizando los parámetros out o ref) es necesario tener experiencia con punteros, saber la diferencia entre los tipos de referencia y los tipos de valor, y controlar métodos con varios valores devueltos. Además, no se suele saber qué diferencia hay entre los parámetros out y ref. |
| CA1023 | [CA1023: Los indizadores no deben ser multidimensionales](../code-quality/ca1023.md) | Los indizadores (es decir, las propiedades indizadas) deben utilizar un índice único. Los indizadores multidimensionales pueden reducir de forma significativa la utilidad de la biblioteca. |
| CA1024 | [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024.md) | Un método público o protegido tiene un nombre que comienza por "Get", no toma ningún parámetro y devuelve un valor que no es una matriz. El método podría ser un buen candidato para convertirse en propiedad. |
| CA1025 | [CA1025: Reemplazar argumentos repetitivos por una matriz de parámetros](../code-quality/ca1025.md) | Utilice una matriz de parámetros en lugar de argumentos repetidos si no conoce el número exacto de argumentos y si los argumentos de variable son del mismo tipo o pueden pasarse como si fueran del mismo tipo. |
| CA1026 | [CA1026: No deben usarse parámetros predeterminados](../code-quality/ca1026.md) | Los métodos que utilizan parámetros predeterminados están permitidos en CLS; sin embargo, CLS permite que los compiladores omitan los valores asignados a estos parámetros. Para seguir utilizando el comportamiento que desea en los lenguajes de programación, los métodos que utilizan parámetros predeterminados deberían reemplazarse con sobrecargas de métodos que proporcionen los parámetros predeterminados. |
| CA1027 |[CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027.md) | Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. Aplique FlagsAttribute a una enumeración cuando se pueda combinar con sentido sus constantes con nombre. |
| CA1028 | [CA1028: El almacenamiento de la enumeración debe ser de tipo Int32](../code-quality/ca1028.md) | Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. De manera predeterminada, el tipo de datos System.Int32 se utiliza para almacenar el valor constante. Aunque puede cambiar este tipo subyacente, no es necesario ni se recomienda en la mayoría de los escenarios. |
| CA1030 | [CA1030: Utilizar eventos cuando sea apropiado](../code-quality/ca1030.md) |Esta regla detecta métodos que tienen nombres que normalmente se utilizarían para eventos. Si se llama a un método en respuesta a un cambio de estado claramente definido, un controlador de eventos debe invocar al método. Los objetos que llaman al método deben provocar eventos en lugar de llamar directamente al método. |
| CA1031 | [CA1031: No capturar los tipos de excepción general](../code-quality/ca1031.md) | No se deben capturar excepciones generales. Detecte una excepción más específica o vuelva a producir una excepción general como la última instrucción del bloque Catch. |
| CA1032 |[CA1032: Implementar constructores de excepción estándar](../code-quality/ca1032.md) | El error al proporcionar el conjunto completo de constructores puede dificultar el control correcto de las excepciones. |
| CA1033 | [CA1033: Los tipos secundarios deben poder llamar a los métodos de interfaz](../code-quality/ca1033.md) | Un tipo no sellado visible externamente proporciona un método explícito de implementación de una interfaz pública pero no proporciona un método visible externamente alternativo con el mismo nombre. |
| CA1034 | [CA1034: Los tipos anidados no deben ser visibles](../code-quality/ca1034.md) | Los tipos anidados son tipos declarados en el ámbito de otro tipo. Los tipos anidados son útiles para encapsular los detalles de la implementación privada del tipo contenido. Los tipos anidados, utilizados para este propósito, no deben ser visibles externamente. |
| CA1035 | [CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados](../code-quality/ca1035.md) | Esta regla requiere que las implementaciones de ICollection proporcionen miembros fuertemente tipados para que los usuarios no necesiten convertir los argumentos en el tipo Object cuando utilicen la funcionalidad proporcionada por la interfaz. Esta regla supone que el tipo que implementa ICollection lo hace para administrar una colección de instancias de un tipo que es más fuerte que Object. |
| CA1036 | [CA1036: Invalidar métodos en tipos comparables](../code-quality/ca1036.md) |Un tipo público o protegido implementa la interfaz System.IComparable. No invalida Object.Equals ni sobrecarga al operador específico del lenguaje para la igualdad, desigualdad, menor que o mayor que. |
| CA1038 | [CA1038: Los enumeradores deben estar fuertemente tipados](../code-quality/ca1038.md) | Esta regla requiere que las implementaciones de IEnumerator también proporcionen una versión fuertemente tipada de la propiedad Current para que los usuarios no tengan que convertir el valor devuelto en un tipo inflexible cuando utilicen la funcionalidad proporcionada por la interfaz. |
| CA1039 | [CA1039: Las listas están fuertemente tipadas](../code-quality/ca1039.md) | Esta regla requiere que las implementaciones de IList proporcionen miembros fuertemente tipados para que los usuarios no necesiten convertir los argumentos en el tipo System.Object cuando utilicen la funcionalidad proporcionada por la interfaz. |
| CA1040 |[CA1040: Evitar las interfaces vacías](../code-quality/ca1040.md) | Las interfaces definen miembros que proporcionan un comportamiento o acuerdo de uso. Cualquier tipo puede adoptar la funcionalidad descrita por la interfaz sin tener en cuenta dónde aparece el tipo en la jerarquía de herencia. Un tipo implementa una interfaz proporcionando las implementaciones para los miembros de la interfaz. Una interfaz vacía no define ningún miembro; por consiguiente, no define ningún contrato que se pueda implementar. |
| CA1041 | [CA1041: Proporcionar un mensaje ObsoleteAttribute](../code-quality/ca1041.md) | Un tipo o miembro se marca con un atributo System.ObsoleteAttribute para el que no se ha especificado su propiedad ObsoleteAttribute.Message. Cuando se compila un tipo o miembro marcado con ObsoleteAttribute, se muestra la propiedad Message del atributo. Esto proporciona información al usuario sobre el miembro o tipo obsoleto. |
| CA1043 | [CA1043: Utilizar un argumento integral o de cadena en indizadores](../code-quality/ca1043.md) | Los indizadores (es decir, las propiedades indizadas) deben utilizar tipos enteros o de cadena para el índice. Estos tipos se utilizan normalmente para indizar las estructuras de datos y aumentan la utilidad de la biblioteca. El uso del tipo Object debería limitarse a los casos en los que el tipo entero o de cadena no se puede especificar en tiempo de diseño. |
| CA1044 | [CA1044: Las propiedades no deben ser de solo escritura](../code-quality/ca1044.md) | Aunque es aceptable y a menudo necesario tener una propiedad de solo lectura, las directrices de diseño prohíben el uso de propiedades de solo escritura. Esto es porque si se deja que un usuario configure un valor, y a continuación se impide que el usuario vea ese valor, no proporciona ninguna seguridad. Además, sin acceso de lectura, no se puede ver el estado de los objetos compartidos, lo que limita su utilidad. |
| CA1045 |[CA1045: No pasar tipos por referencia](../code-quality/ca1045.md) | Para pasar tipos por referencia (utilizando los parámetros out o ref) es necesario tener experiencia con punteros, saber la diferencia entre los tipos de referencia y los tipos de valor, y controlar métodos con varios valores devueltos. Los arquitectos de biblioteca que diseñan para un público general no deben esperar que los usuarios dominen el trabajo con `out` `ref` los parámetros o. |
| CA1046 | [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046.md) | Para los tipos de referencia, la implementación predeterminada del operador de igualdad casi siempre es correcta. De manera predeterminada, dos referencias son iguales sólo si señalan al mismo objeto. |
| CA1047 |[CA1047: No declarar miembros protegidos en tipos sellados](../code-quality/ca1047.md) | Los tipos declaran miembros protegidos para que los tipos heredados puedan obtener acceso o reemplazar el miembro. Por definición, no se puede heredar de tipos sealed, lo que significa que no se puede llamar a los métodos protegidos en tipos sealed. |
| CA1048 | [CA1048: No declarar miembros virtuales en tipos sellados](../code-quality/ca1048.md) | Los tipos declaran los métodos como virtuales para que los tipos heredados puedan reemplazar la implementación del método virtual. Por definición, no se puede heredar de un tipo sealed. Esto hace que un método virtual en un tipo sealed no tenga sentido. |
| CA1049 | [CA1049: Los tipos que poseen recursos nativos deben ser descartables](../code-quality/ca1049.md) | Los tipos que se asignan a recursos no administrados deberían implementar IDisposable para permitir que los llamadores liberen estos recursos a petición y reduzcan el período de duración de los objetos que contienen los recursos. |
| CA1050 | [CA1050: Declarar tipos en espacios de nombres](../code-quality/ca1050.md) | Los tipos se declaran dentro de los espacios de nombres para evitar conflictos de nombre y como una forma de organizar los tipos relacionados en una jerarquía de objetos. |
| CA1051 | [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051.md) | El uso principal de un campo debe ser como un detalle de implementación. Los campos deben ser privados o internos y deben exponerse utilizando propiedades. |
| CA1052 | [CA1052: Los tipos titulares estáticos deben estar sellados](../code-quality/ca1052.md) | Un tipo público o protegido solamente contiene miembros estáticos y no se declara con el modificador sealed (NotInheritable) (Referencia de C#). Un tipo que no está diseñado para heredarse debería marcarse con el modificador sealed para impedir su uso como tipo base. |
| CA1053 |[CA1053: Los tipos titulares estáticos no deben tener constructores](../code-quality/ca1053.md) | Un tipo público o público anidado declara sólo miembros estáticos y tiene un constructor predeterminado público o protegido. El constructor no es necesario puesto que al llamar a los miembros estáticos no se requiere una instancia del tipo. La sobrecarga de la cadena debería llamar a la sobrecarga del identificador URI utilizando el argumento string por motivos de seguridad y protección. |
| CA1054 | [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054.md) | Si un método toma una representación de cadena de un identificador URI, debe proporcionarse la sobrecarga correspondiente que toma una instancia de la clase URI, que proporciona estos servicios de forma segura. |
| CA1055 | [CA1055: Los valores devueltos URI no deben ser cadenas](../code-quality/ca1055.md) | Esta regla supone que el método devuelve un URI. Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La clase System.Uri proporciona estos servicios de una manera segura. |
| CA1056 | [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056.md) | La regla supone que la propiedad representa un Identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La clase System.Uri proporciona estos servicios de una manera segura. |
| CA1057 | [CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri](../code-quality/ca1057.md) | Un tipo declara sobrecargas de método que solamente se distinguen por la sustitución de un parámetro de cadena por un parámetro System.Uri. La sobrecarga que toma el parámetro de cadena no llama a la sobrecarga que toma el parámetro URI. |
| CA1058 | [CA1058: Los tipos no deben ampliar ciertos tipos base](../code-quality/ca1058.md) | Un tipo visible externamente extiende algunos tipos base. Utilice una de las alternativas. |
| CA1059 |[CA1059: Los miembros no deben exponer algunos tipos concretos](../code-quality/ca1059.md) | Un tipo concreto es un tipo que tiene una implementación completa y, por consiguiente, se pueden crear instancias de él. Para permitir un uso extendido del miembro, reemplace el tipo concreto por la interfaz sugerida. |
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
| CA1300 | [CA1300: Especificar MessageBoxOptions](../code-quality/ca1300.md) | Para mostrar correctamente un cuadro de mensaje para las referencias culturales con escritura de derecha a izquierda, se deben pasar al método Show los miembros RightAlign y RtlReading de la enumeración MessageBoxOptions. |
| CA1301 | [CA1301: Evitar los aceleradores duplicados](../code-quality/ca1301.md) | Una tecla de acceso, también denominada acelerador, permite el acceso mediante teclado a un control utilizando la tecla ALT. Cuando varios controles tienen las teclas de acceso duplicadas, no se define correctamente el comportamiento de la tecla de acceso. |
| CA1302 | [CA1302: No codificar las cadenas específicas de configuración regional](../code-quality/ca1302.md) | La enumeración System.Environment.SpecialFolder contiene miembros que hacen referencia a carpetas del sistema especiales. La ubicación de estas carpetas puede tener diferentes valores en sistemas operativos distintos, el usuario puede cambiar alguna de estas ubicaciones y además, están adaptadas. El método Environment.GetFolderPath devuelve las ubicaciones asociadas a la enumeración Environment.SpecialFolder, adaptadas y adecuadas al equipo actualmente en ejecución. |
| CA1303 | [CA1303: No pasar literales como parámetros localizados](../code-quality/ca1303.md) | Un método visible externamente pasa un literal de cadena como un parámetro a un constructor o método .NET, y esa cadena debe ser localizable. |
| CA1304 | [CA1304: Especificar CultureInfo](../code-quality/ca1304.md) | Un método o constructor llama a un miembro que tiene una sobrecarga que acepta un parámetro System.Globalization.CultureInfo, y el método o constructor no llama a la sobrecarga que toma el parámetro CultureInfo. Si no se proporciona un objeto CultureInfo o System.IFormatProvider, el valor predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las configuraciones regionales. |
| CA1305 | [CA1305: Especificar IFormatProvider](../code-quality/ca1305.md) | Un método o constructor llama a uno o más miembros que tienen sobrecargas que aceptan un parámetro System.IFormatProvider, y el método o constructor no llama a la sobrecarga que toma el parámetro IFormatProvider. Si no se proporciona un objeto System.Globalization.CultureInfo o IFormatProvider, el valor predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las configuraciones regionales. |
| CA1306 | [CA1306: Establecer configuración regional de tipos de datos](../code-quality/ca1306.md) | La configuración regional determina los elementos de presentación específicos de la referencia cultural para los datos, como el formato para los valores numéricos, símbolos de divisa y criterio de ordenación. Cuando se crea un objeto DataTable o DataSet, debe establecerse explícitamente la configuración regional. |
| CA1307 | [CA1307: Especificar StringComparison](../code-quality/ca1307.md) | Una operación de comparación de cadenas utiliza una sobrecarga de método que no establece un parámetro StringComparison. |
| CA1308 |[CA1308: Normalizar cadenas en mayúsculas](../code-quality/ca1308.md) | Las cadenas se deberían normalizar para que se escriban en letras mayúsculas. Hay un grupo pequeño de caracteres que no pueden realizar un viaje de ida y vuelta cuando se pasan a minúsculas. |
| CA1309 | [CA1309: Utilizar StringComparison ordinal](../code-quality/ca1309.md) | Una operación no lingüística de comparación de cadenas no establece el parámetro StringComparison en Ordinal ni en OrdinalIgnoreCase. Si se establece explícitamente el parámetro en StringComparison.Ordinal o StringComparison.OrdinalIgnoreCase, el código será más rápido y ganará en precisión y confiabilidad. |
| CA1400 | [CA1400: deben existir puntos de entrada P/Invoke](../code-quality/ca1400.md) |Un método público o protegido se marca con el atributo System.Runtime.InteropServices.DllImportAttribute. No se pudo encontrar la biblioteca no administrada o el método no coincide con una función de la biblioteca. |
| CA1401 | [CA1401: P/Invoke no debe estar visible](../code-quality/ca1401.md) | Un método público o protegido en un tipo público tiene el atributo System.Runtime.InteropServices.DllImportAttribute (también se implementa por la palabra clave Declare en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. No se deberían exponer estos métodos. |
| CA1402 |[CA1402: Evitar las sobrecargas en interfaces visibles a través de COM](../code-quality/ca1402.md) | Cuando se exponen métodos sobrecargados a los clientes COM, sólo la primera sobrecarga de método conserva su nombre. Las sobrecargas subsiguientes reciben un nombre único resultante de anexar al nombre un carácter de subrayado (_) y un entero correspondiente al orden de declaración de la sobrecarga. |
| CA1403 | [CA1403: Los tipos de diseño automático no deben ser visibles a través de COM](../code-quality/ca1403.md) | Un tipo de valor visible para COM se marca con el atributo System. Runtime. InteropServices. StructLayoutAttribute establecido en LayoutKind. auto. El diseño de estos tipos puede cambiar entre versiones de .NET, lo que interrumpirá a los clientes COM que esperan un diseño específico. |
| CA1404 | [CA1404: llamar a GetLastError inmediatamente después de P/Invoke](../code-quality/ca1404.md) | Se realiza una llamada al método Marshal. GetLastWin32Error o a la [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] función GetLastError equivalente, y la llamada anterior inmediatamente no es a un método de invocación del sistema operativo. |
| CA1405 | [CA1405: Los tipos base de tipos visibles a través de COM deben ser visibles a través de COM](../code-quality/ca1405.md) | Un tipo visible a través de COM se deriva de un tipo no visible a través de COM. |
| CA1406 |[CA1406: Evitar los argumentos Int64 en clientes Visual Basic 6](../code-quality/ca1406.md) | Los clientes COM de Visual Basic 6 no pueden tener acceso a los enteros de 64 bits. |
| CA1407 |[CA1407: Evitar los miembros estáticos en tipos visibles a través de COM](../code-quality/ca1407.md) | COM no es compatible con métodos estáticos. |
| CA1408 | [CA1408: No utilizar AutoDual ClassInterfaceType](../code-quality/ca1408.md) | Los tipos que utilizan una interfaz dual permiten a los clientes enlazarse a un diseño de interfaz concreto. Cualquier cambio que se introduzca en una versión futura en el diseño del tipo o en cualquier tipo base provocará un error en los clientes COM que están enlazados a la interfaz. De forma predeterminada, si no se especifica el atributo ClassInterfaceAttribute, se utiliza una interfaz solo de envío. |
| CA1409 | [CA1409: Los tipos visibles a través de COM se deben poder crear](../code-quality/ca1409.md) |Un tipo de referencia marcado específicamente como visible para COM contiene un constructor parametrizado público pero no contiene un constructor (sin parámetros) predeterminado público. Un tipo sin un constructor predeterminado público no se puede crear mediante clientes COM. |
| CA1410 | [CA1410: Los métodos de registro COM deben coincidir](../code-quality/ca1410.md) | Un tipo declara un método marcado con el atributo System.Runtime.InteropServices.ComRegisterFunctionAttribute pero no declara ningún método marcado con el atributo System.Runtime.InteropServices.ComUnregisterFunctionAttribute o viceversa. |
| CA1411 | [CA1411: Los métodos de registro COM no deben ser visibles](../code-quality/ca1411.md) | Un método marcado con el atributo System.Runtime.InteropServices.ComRegisterFunctionAttribute o el atributo System.Runtime.InteropServices.ComUnregisterFunctionAttribute es visible externamente. |
| CA1412 | [CA1412: Marcar las interfaces ComSource como IDispatch](../code-quality/ca1412.md) | Un tipo se marca con el atributo System.Runtime.InteropServices.ComSourceInterfacesAttribute y por lo menos una de las interfaces especificadas no se marca con el atributo System.Runtime.InteropServices.InterfaceTypeAttribute establecido en ComInterfaceType.InterfaceIsIDispatch. |
| CA1413 | [CA1413: Evitar los campos no públicos en tipos de valor visibles a través de COM](../code-quality/ca1413.md) | Los campos de instancia no públicos de tipos de valor visibles para COM están visibles para los clientes COM. Revise el contenido de los campos para obtener información que no deba exponerse o que tendrá un impacto no deseado sobre la seguridad o el diseño. |
| CA1414 | [CA1414: Marque los argumentos P/Invoke booleanos con MarshalAs](../code-quality/ca1414.md) | El tipo de datos Boolean tiene varias representaciones en el código no administrado. |
| CA1415 | [CA1415: declarar P/Invoke correctamente](../code-quality/ca1415.md) | Esta regla busca declaraciones de método de invocación de sistema operativo dirigidas a funciones de [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] que tengan un puntero a un parámetro de estructura OVERLAPPED y el parámetro administrado correspondiente no es un puntero para una estructura System.Threading.NativeOverlapped. |
| CA1417 | [CA1417: no se usa `OutAttribute` en parámetros de cadena para P/Invoke](../code-quality/ca1417.md) | Los parámetros de cadena pasados por valor con el `OutAttribute` pueden desestabilizar el tiempo de ejecución si la cadena es una cadena interna. |
| CA1500 | [CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos](../code-quality/ca1500.md) | Un método de instancia declara un parámetro o una variable local cuyo nombre coincide con un campo de instancia del tipo declarativo, lo que da lugar a errores. |
| CA1501 | [CA1501: Evitar una herencia excesiva](../code-quality/ca1501.md) | Un tipo tiene más de cuatro niveles de profundidad en su jerarquía de herencia. Las jerarquías de tipos con demasiados niveles de anidación pueden resultar difíciles de seguir, comprender y mantener. |
| CA1502 | [CA1502: Evitar una complejidad excesiva](../code-quality/ca1502.md) | Esta regla mide el número de rutas de acceso independientes de forma lineal a través del método, que es determinado por el número y la complejidad de bifurcaciones condicionales. |
| CA1504 | [CA1504: Revisar los nombres de campos erróneos](../code-quality/ca1504.md) | El nombre de un campo de instancia empieza por "s_" o el nombre de un campo estático (Shared en Visual Basic) empieza por "m_". |
| CA1505 | [CA1505: Evitar código que no se puede mantener](../code-quality/ca1505.md) | Un tipo o método tiene un valor del índice de mantenimiento bajo. Un índice de mantenimiento bajo indica que un tipo o método resulta probablemente difícil de mantener y se debería volver a diseñar. |
| CA1506 | [CA1506: Evitar el acoplamiento excesivo de clases](../code-quality/ca1506.md) | Esta regla mide el acoplamiento de clase contando el número de referencias de tipo únicas que contiene un tipo o método. |
| CA1507 | [CA1507: Usar nameof en lugar de la cadena](../code-quality/ca1507.md) | Un literal de cadena se usa como argumento en el que se `nameof` podría utilizar una expresión. |
| CA1508 | [CA1508: Evitar código de condición no alcanzado](../code-quality/ca1508.md) | Un método tiene código condicional que siempre se evalúa como `true` o `false` en tiempo de ejecución. Esto conduce a código muerto en la `false` rama de la condición. |
| CA1509 | [CA1509: Entrada no válida en el archivo de configuración de métricas de código](../code-quality/ca1509.md) | Las reglas de métricas de código, como [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) y [CA1506](ca1506.md), proporcionan un archivo de configuración denominado `CodeMetricsConfig.txt` que tiene una entrada no válida. |
| CA1600 | [CA1600: No utilizar la prioridad del proceso inactiva](../code-quality/ca1600.md) | No establezca la prioridad de proceso en Idle. Los procesos que tienen System.Diagnostics.ProcessPriorityClass.Idle ocupan la CPU cuando, de otro modo, estaría inactiva y, por consiguiente, bloquean el estado de espera. |
| CA1601 | [CA1601: No utilizar temporizadores que impidan los cambios de estado de energía](../code-quality/ca1601.md) | Una actividad periódica más frecuente hará que la CPU no esté disponible, e interferirá con los temporizadores de inactividad para ahorro de energía, que apagan el monitor y el disco duro. |
| CA1700 | [CA1700: No nombrar valores de enumeración como 'Reserved'](../code-quality/ca1700.md) | Esta regla supone que un miembro de la enumeración con un nombre que contiene la palabra "reserved" no se utiliza actualmente pero hace de marcador de posición para que se pueda quitar o cambiar el nombre en una versión posterior. Quitar o cambiar el nombre de un miembro es un cambio importante. |
| CA1701 | [CA1701: En las palabras compuestas de la cadena de recursos se deben utilizar mayúsculas y minúsculas correctamente](../code-quality/ca1701.md) | Cada palabra en la cadena de recursos se divide en tokens basándose en el uso de mayúsculas y minúsculas. La biblioteca de correctores ortográficos de Microsoft comprueba cada combinación de dos tokens contiguos. Si la reconoce, la palabra genera una infracción de la regla. |
| CA1702 | [CA1702: En las palabras compuestas se deben utilizar mayúsculas y minúsculas correctamente](../code-quality/ca1702.md) | El nombre de un identificador contiene varias palabras y al menos una de ellas parece ser una palabra compuesta en la que no se utilizan correctamente las mayúsculas y minúsculas. |
| CA1703 | [CA1703: La ortografía de las cadenas de recursos debe ser correcta](../code-quality/ca1703.md) | Una cadena de recurso contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce. |
| CA1704 | [CA1704: La ortografía de los identificadores debe ser correcta](../code-quality/ca1704.md) | El nombre de un identificador visible externamente contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce. |
| CA1707 | [CA1707: Los identificadores no deben contener caracteres de subrayado](../code-quality/ca1707.md) | Por convención, los nombres del identificador no contienen el carácter de subrayado (_). Esta regla comprueba espacios de nombres, tipos, miembros y parámetros. |
| CA1708 | [CA1708: Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708.md) | Los identificadores de los espacios de nombres, miembros y parámetros no puede distinguirse sólo por mayúsculas o minúsculas porque los lenguajes que tienen como destino el Common Language Runtime no necesitan distinguir entre mayúsculas y minúsculas. |
| CA1709 | [CA1709: Los identificadores deben utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709.md) | Por convención, los nombres de parámetro utilizan la convención Camel de uso de mayúsculas, mientras que los nombres de espacio de nombres, tipo y miembro utilizan la convención Pascal. |
| CA1710 | [CA1710: Los identificadores deben tener un sufijo correcto](../code-quality/ca1710.md) |Por convención, los nombres de tipos que extienden determinados tipos base o que implementan algunas interfaces, o tipos derivados de estos tipos, tienen un sufijo asociado al tipo base o a la interfaz. |
| CA1711 | [CA1711: Los identificadores no deben tener un sufijo incorrecto](../code-quality/ca1711.md) | Por convención, los nombres de tipos que extienden determinados tipos base o que implementan algunas interfaces, o tipos derivados de estos tipos, deben terminar con unos sufijos reservados específicos. Otros nombres de tipo no deben utilizar estos sufijos reservados. |
| CA1712 | [CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo](../code-quality/ca1712.md) | Los nombres de los miembros de la enumeración no llevan el nombre de tipo como prefijo porque se espera que las herramientas de desarrollo proporcionen la información de tipo. |
| CA1713 | [CA1713: Los eventos no deben tener prefijos antes ni después](../code-quality/ca1713.md) | El nombre de un evento empieza por "Before" o "After". Para nombrar los eventos relacionados que se provocan en una secuencia específica, utilice el tiempo presente o pasado para indicar la posición relativa en la secuencia de acciones. |
| CA1714 | [CA1714: Las enumeraciones Flags deben tener nombres en plural](../code-quality/ca1714.md) | Una enumeración pública tiene el atributo System.FlagsAttribute y su nombre no termina en "s". Los tipos marcados con FlagsAttribute tienen nombres en plural porque el atributo indica que se puede especificar más de un valor. |
| CA1715 | [CA1715: Los identificadores deben tener el prefijo correcto](../code-quality/ca1715.md) | El nombre de una interfaz visible externamente no empieza por "I" mayúscula. El nombre de un parámetro de tipo genérico en un tipo o método visibles externamente no empieza por "T" mayúscula. |
| CA1716 | [CA1716: Los identificadores no deben coincidir con palabras clave](../code-quality/ca1716.md) | Un nombre de espacio de nombres o un nombre de tipo coinciden con una palabra clave reservada en un lenguaje de programación. Los identificadores para los espacios de nombres y tipos no deberían coincidir con palabras clave definidas por los lenguajes que tienen como destino el Common Language Runtime. |
| CA1717 | [CA1717: Solo las enumeraciones FlagsAttribute deben tener nombres en plural](../code-quality/ca1717.md) | Las convenciones de nomenclatura establecen que un nombre en plural para una enumeración indica que se pueden especificar varios valores de enumeración al mismo tiempo. |
| CA1719 | [CA1719: Los nombres de parámetro no deben coincidir con los nombres de miembro](../code-quality/ca1719.md) | Un nombre de parámetro debe comunicar el significado del parámetro y un nombre de miembro debe comunicar el significado del miembro. Sería un diseño extraño si éstos fueran los mismos. Denominar un parámetro igual que el nombre del miembro no es intuitivo y dificulta el uso de la biblioteca. |
| CA1720 |[CA1720: Los identificadores no deben contener nombres de tipo](../code-quality/ca1720.md) | El nombre de un parámetro en un miembro visible externamente contiene un nombre de tipo de datos o el nombre de un miembro visible externamente contiene un nombre de tipo de datos específico del lenguaje. |
| CA1721 | [CA1721: Los nombres de propiedades no deben coincidir con los métodos get](../code-quality/ca1721.md) |El nombre de un miembro público o protegido empieza por "Get" y en cualquier otro caso coincide con el nombre de una propiedad pública o protegida. Las propiedades y métodos "Get" deberían tener nombres que distingan claramente su función. |
| CA1722 | [CA1722: Los identificadores no deben tener un prefijo incorrecto](../code-quality/ca1722.md) | Por convención, sólo ciertos elementos de programación tienen nombres que comienzan con un prefijo concreto. |
| CA1724 | [CA1724: Los nombres de tipo no deben coincidir con los espacios de nombres](../code-quality/ca1724.md) | Los nombres de tipo no deben coincidir con los nombres de los espacios de nombres de .NET. Infringir esta regla puede reducir la utilidad de la biblioteca. |
| CA1725 | [CA1725: Los nombres de parámetro deben coincidir con la declaración base](../code-quality/ca1725.md) | El uso del mismo nombre para un parámetro en una jerarquía de reemplazo aumenta la utilidad de los reemplazos de método. Cuando el nombre de un parámetro en un método derivado es distinto del nombre de la declaración base, puede resultar difícil determinar si el método es un reemplazo del método base o una nueva sobrecarga del método. |
| CA1726 | [CA1726: Utilizar términos preferidos](../code-quality/ca1726.md) | El nombre de un identificador visible externamente incluye un término para el que existe un término alternativo más apropiado. Alternativamente, el nombre incluye el término "Flag" o "Flags". |
| CA1800 | [CA1800: No convertir innecesariamente](../code-quality/ca1800.md) | Las conversiones duplicadas reducen el rendimiento, sobre todo cuando se realizan en instrucciones de iteración compactas. |
| CA1801 | [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801.md) | Una firma de método incluye un parámetro que no se utiliza en el cuerpo del método. |
| CA1802 |[CA1802: Utilizar literales cuando sea apropiado](../code-quality/ca1802.md) |Un campo se declara como static y de solo lectura (Shared y ReadOnly en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) y se inicializa con un valor que se puede calcular durante la compilación. Dado que el valor asignado al campo de destino es calculable en tiempo de compilación, cambie la declaración a un campo const (const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) para que el valor se calcule en tiempo de compilación en lugar de en tiempo de ejecución. |
| CA1804 | [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804.md) | Las variables locales no usadas y las asignaciones innecesarias aumentan el tamaño de un ensamblado y reducen el rendimiento. |
| CA1805 | [CA1805: No inicializar innecesariamente](../code-quality/ca1805.md) | El tiempo de ejecución de .NET inicializa todos los campos de los tipos de referencia a sus valores predeterminados antes de ejecutar el constructor. En la mayoría de los casos, la inicialización explícita de un campo a su valor predeterminado es redundante, lo que aumenta los costos de mantenimiento y puede degradar el rendimiento (por ejemplo, con un mayor tamaño de ensamblado). |
| CA1806 | [CA1806: No omitir resultados del método](../code-quality/ca1806.md) | Se crea un nuevo objeto pero nunca se utiliza, o se llama a un método que crea y devuelve una nueva cadena y esta nunca se utiliza, o un método COM o P/Invoke devuelve un código de error o HRESULT que nunca se utiliza. |
| CA1809 |[CA1809: Evitar las variables locales excesivas](../code-quality/ca1809.md) | Una optimización de rendimiento común es almacenar un valor en un registro del procesador en lugar de en la memoria, lo que se denomina "registrar el valor". Para aumentar la posibilidad de que todas las variables locales se registren, limite el número de variables locales a 64. |
| CA1810 | [CA1810: Inicializar campos estáticos de tipo de referencia insertados](../code-quality/ca1810.md) | Cuando un tipo declara un constructor estático explícito, el compilador Just-In-Time (JIT) agrega una comprobación a cada constructor de instancia y a cada método estático del tipo para asegurarse de que se ha llamado anteriormente al constructor estático. Las comprobaciones del constructor estático pueden reducir el rendimiento. |
| CA1811 | [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811.md) | Un miembro interno o privado (nivel de ensamblado) no tiene llamadores en el ensamblado, no es invocado por Common Language Runtime ni tampoco por un delegado. |
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
| CA1835 |[CA1835: preferir las sobrecargas basadas en Memory' para ' ReadAsync ' y ' WriteAsync '](../code-quality/ca1835.md) | ' Stream ' tiene una sobrecarga ' ReadAsync ' que toma un ' byte de memoria &lt; &gt; ' como primer argumento y una sobrecarga ' WriteAsync ' que toma un ' ReadOnlyMemory &lt; byte &gt; ' como primer argumento. Prefiera llamar a las sobrecargas basadas en memoria, que son más eficaces. |
| CA1836 |[CA1836: preferir `IsEmpty` `Count` cuando esté disponible](../code-quality/ca1836.md) | Propiedad preferida `IsEmpty` que es más eficaz `Count` que `Length` , <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> o <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> para determinar si el objeto contiene o no elementos. |
| CA1838 | [CA1838: evitar `StringBuilder` parámetros para P/Invoke](../code-quality/ca1838.md) | La serialización de ' StringBuilder ' siempre crea una copia de búfer nativo, lo que da lugar a varias asignaciones para una operación de serialización. |
| CA1900 | [CA1900: Los campos de tipo de valor deben ser portátiles](../code-quality/ca1900.md) | Esta regla comprueba que las estructuras declaradas mediante un atributo de diseño explícito se alinearán correctamente cuando se calculen las referencias al código no administrado en sistemas operativos de 64 bits. |
| CA1901 | [CA1901: las declaraciones P/Invoke deben ser portátiles](../code-quality/ca1901.md) | Esta regla evalúa el tamaño de cada parámetro y el valor devuelto de P/Invoke, y comprueba que el tamaño del parámetro sea correcto al serializar para su conversión en código no administrado en sistemas operativos de 32 y 64 bits. |
| CA1903 | [CA1903: Usar solo API de la versión de .NET Framework de destino](../code-quality/ca1903.md) | Un miembro o tipo utiliza un miembro o tipo que se introdujo en un Service Pack no incluido junto con la versión de .NET Framework de destino del proyecto. |
| CA2000 | [CA2000: Desechar objetos antes de perder el ámbito](../code-quality/ca2000.md) | Dado que podría producirse un evento excepcional que evitaría que el finalizador de un objeto se ejecutase, el objeto debe estar disponible en su lugar antes de que todas las referencias a él estén fuera del ámbito. |
| CA2001 | [CA2001: Evitar llamar a métodos problemáticos](../code-quality/ca2001.md) | Un miembro llama a un método potencialmente peligroso o problemático. |
| CA2002 |[CA2002: No bloquear objetos con identidad débil](../code-quality/ca2002.md) |Se dice que un objeto tiene una identidad débil cuando se puede tener acceso directamente a través de los límites del dominio de aplicación. Un subproceso que intenta obtener un bloqueo en un objeto que tiene identidad débil se puede bloquear con un segundo subproceso en un dominio de aplicación diferente que tenga bloqueado el mismo objeto. |
| CA2003 |[CA2003: No tratar fibras como subprocesos](../code-quality/ca2003.md) | Un subproceso administrado se trata como un subproceso de [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)]. |
| CA2004 | [CA2004: Quitar las llamadas a GC.KeepAlive](../code-quality/ca2004.md) | Al efectuar la conversión para utilizar SafeHandle, quite todas las llamadas a GC.KeepAlive (objeto). En este caso, las clases no deberían tener que llamar a GC.KeepAlive. Esto supone que no tienen un finalizador sino que depende de SafeHandle para finalizar el identificador de sistema operativo. |
| CA2006 | [CA2006: Utilizar SafeHandle para encapsular recursos nativos](../code-quality/ca2006.md) | El uso de IntPtr en código administrado podría indicar un posible problema para la seguridad y la confiabilidad. Todos los usos de IntPtr se deben revisar para determinar si se necesita utilizar en su lugar SafeHandle o una tecnología similar. |
| CA2007 | [CA2007: No esperar una tarea directamente](ca2007.md) | Un método asincrónico [espera](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> directamente. Cuando un método asincrónico espera <xref:System.Threading.Tasks.Task> directamente, la continuación se produce en el mismo subproceso que creó la tarea. Este comportamiento puede ser costoso en términos de rendimiento y puede dar lugar a un interbloqueo en el subproceso de la interfaz de usuario. Considere <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> la posibilidad de llamar a para señalar su intención de continuación. |
| CA2009 | [CA2009: No llame a ToImmutableCollection en un valor ImmutableCollection](ca2009.md) | `ToImmutable` se llamó innecesariamente al método en una colección inmutable desde el <xref:System.Collections.Immutable> espacio de nombres. |
| CA2011 | [CA2011: No asignar la propiedad dentro de su establecedor](ca2011.md) | Se asignó accidentalmente un valor a una propiedad dentro de su propio [descriptor de acceso set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
| CA2012 | [CA2012: Usar ValueTasks correctamente](ca2012.md) | Los ValueTasks devueltos de las invocaciones de miembro están diseñados para esperarse directamente.  Los intentos de consumir un ValueTask varias veces o de tener acceso directamente a uno de los resultados antes de que se sepa que se han completado pueden producir una excepción o daños.  Omitir tal ValueTask es probable que se trate de un error funcional y puede degradar el rendimiento. |
| CA2013 | [CA2013: No usar ReferenceEquals con tipos de valor](ca2013.md) | Al comparar valores mediante <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , si objA y objB son tipos de valor, se les aplica la conversión boxing antes de que se pasen al <xref:System.Object.ReferenceEquals%2A> método. Esto significa que, aunque objA y objB representen la misma instancia de un tipo de valor, el <xref:System.Object.ReferenceEquals%2A> método devuelve false. |
| CA2014 | [CA2014: no use stackalloc en los bucles.](ca2014.md) | El espacio de pila asignado por stackalloc solo se libera al final de la invocación del método actual.  Su uso en un bucle puede dar lugar a un crecimiento de pila sin enlazar y a condiciones de desbordamiento de pila eventuales. |
| CA2015 | [CA2015: no definir finalizadores para los tipos derivados de MemoryManager &lt; T&gt;](ca2015.md) | Agregar un finalizador a un tipo derivado de <xref:System.Buffers.MemoryManager%601> puede permitir que la memoria se libere mientras esté siendo utilizada por <xref:System.Span%601> . |
| CA2016 | [CA2016: Reenviar el parámetro CancellationToken a los métodos que lo usan](ca2016.md) | Reenvíe el `CancellationToken` parámetro a los métodos que toman uno para asegurarse de que las notificaciones de cancelación de la operación se propagan correctamente, o que `CancellationToken.None` se pasan explícitamente para indicar que no se propague el token de forma intencionada. |
| CA2100 | [CA2100: Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad](../code-quality/ca2100.md) | Un método establece la propiedad System.Data.IDbCommand.CommandText utilizando una cadena que se construye partiendo de un argumento de cadena para el método. Esta regla supone que el argumento de cadena contiene datos proporcionados por el usuario. Una cadena de comandos de SQL compilada a partir de datos proporcionados por el usuario es vulnerable a ataques de inserción de SQL. |
| CA2101 |[CA2101: especificar el cálculo de referencias para argumentos de cadena P/Invoke](../code-quality/ca2101.md) | Un miembro de invocación de plataforma permite llamadores que no son de plena confianza y no serializa explícitamente la cadena. Esto puede producir una vulnerabilidad de seguridad. |
| CA2102 | [CA2102: Detectar las excepciones que no son CLSCompliant en los controladores generales](../code-quality/ca2102.md) | Un miembro de un ensamblado que no está marcado con el atributo RuntimeCompatibilityAttribute o está marcado con RuntimeCompatibility(WrapNonExceptionThrows = false) contiene un bloque catch que controla el objeto System.Exception y no contiene un bloque catch general inmediatamente después. |
| CA2103 | [CA2103: Revisar la seguridad imperativa](../code-quality/ca2103.md) |Un método utiliza la seguridad imperativa y podría estar creando el permiso utilizando la información de estado y los valores devueltos que pueden cambiar mientras la solicitud está activa. Utilice la seguridad declarativa siempre que sea posible. |
| CA2104 |[CA2104: No declarar tipos de referencias mutables de solo lectura](../code-quality/ca2104.md) | Un tipo visible externamente contiene un campo de sólo lectura visible externamente que es un tipo de referencia que se puede cambiar. Un tipo que mutable es un tipo cuyos datos de instancia se pueden modificar. |
| CA2105 | [CA2105: Los campos de matrices no deben ser de solo lectura](../code-quality/ca2105.md) |Cuando se aplica el modificador de solo lectura (ReadOnly en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) a un campo que contiene una matriz, el campo no se puede modificar para hacer referencia a una matriz distinta. Sin embargo, se pueden cambiar los elementos de la matriz almacenados en un campo de solo lectura. |
| CA2106 | [CA2106: Proteger las aserciones](../code-quality/ca2106.md) | Un método valida un permiso y no se realiza ninguna comprobación de seguridad en el llamador. Validar un permiso de seguridad sin realizar ninguna comprobación de seguridad puede dejar una debilidad de seguridad explotable en el código. |
| CA2107 | [CA2107: Revisar el uso de Deny y PermitOnly](../code-quality/ca2107.md) |Las acciones de seguridad método PermitOnly y CodeAccessPermission. deny solo las deben usar los usuarios con conocimientos avanzados de seguridad de .NET. Debería realizarse una revisión de la seguridad del código que utiliza estas acciones de seguridad. |
| CA2108 | [CA2108: Revisar la seguridad declarativa en los tipos de valores](../code-quality/ca2108.md) | Un tipo de valor público o protegido está protegido por acceso a datos o peticiones de vínculos. |
| CA2109 | [CA2109: Revisar los controladores de eventos visibles](../code-quality/ca2109.md) | Se detectó un método de control de eventos público o protegido. No se deberían exponer los métodos de control de eventos a menos que sea absolutamente necesario. |
| CA2111 |[CA2111: Los punteros no deben estar visibles](../code-quality/ca2111.md) | Un puntero no es privado, interno ni de solo lectura. El código malintencionado puede cambiar el valor del puntero, permitiendo potencialmente el acceso a ubicaciones arbitrarias en memoria o provocando errores del sistema o de aplicación. |
| CA2112 | [CA2112: Los tipos seguros no deben exponer campos](../code-quality/ca2112.md) | Un tipo público o protegido contiene campos públicos y está protegido por peticiones de vínculos. Si el código tiene acceso a una instancia de tipo que está protegida por una solicitud de vínculo, el código no cumplirá la solicitud para obtener acceso a los campos del tipo. |
| CA2114 | [CA2114: La seguridad del método debe ser un supraconjunto del tipo](../code-quality/ca2114.md) | Un método no debe tener seguridad declarativa en el nivel de método y de tipo para la misma acción. |
| CA2115 | [CA2115: Llamar a Call GC.KeepAlive cuando se utilicen recursos nativos](../code-quality/ca2115.md) | Esta regla detecta errores que pueden haberse producido porque se finaliza un recurso no administrado mientras todavía se utiliza en código no administrado. |
| CA2116 | [CA2116: Los métodos APTCA deben llamar solo a métodos APTCA](../code-quality/ca2116.md) |Si está presente el atributo APTCA (AllowPartiallyTrustedCallersAttribute) en un ensamblado de plena confianza y el ensamblado ejecuta código en otro ensamblado que permite llamadores parcialmente confiables, se puede producir un ataque en el sistema de seguridad. |
| CA2117 | [CA2117: Los tipos APTCA solo amplían tipos base APTCA](../code-quality/ca2117.md) | Si está presente el atributo APTCA en un ensamblado de plena confianza y un tipo del ensamblado se hereda de otro que permite llamadores parcialmente confiables, se puede producir un ataque de seguridad. |
| CA2118 | [CA2118: Revisar el uso de SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118.md) |SuppressUnmanagedCodeSecurityAttribute cambia el comportamiento del sistema de seguridad predeterminado por miembros que ejecutan código no administrado que utiliza la interoperabilidad COM o la invocación de sistema operativo. Este atributo se utiliza principalmente para aumentar el rendimiento; sin embargo, las mejoras de rendimiento suponen riesgos de seguridad importantes. |
| CA2119 | [CA2119: Sellar los métodos que satisfacen las interfaces privadas](../code-quality/ca2119.md) | Un tipo público heredable proporciona una implementación de método reemplazable de una interfaz interna (de tipo "Friend" en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Para corregir una infracción de esta regla, impida que el método se invalide fuera del ensamblado. |
| CA2120 | [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120.md) | Este tipo tiene un constructor que toma un objeto System.Runtime.Serialization.SerializationInfo y un objeto System.Runtime.Serialization.StreamingContext (la firma del constructor de serialización). Una comprobación de seguridad no protege este constructor, pero protege uno o más constructores regulares del tipo. |
| CA2121 | [CA2121: Los constructores estáticos deben ser privados](../code-quality/ca2121.md) | El sistema llama al constructor estático antes de crear la primera instancia del tipo o antes de hacer referencia a cualquier miembro estático. Si un constructor estático no es privado, se puede llamar a través de un código distinto del sistema. En función de las operaciones que se realizan en el constructor, esto puede producir un comportamiento inesperado. |
| CA2122 | [CA2122: No exponer indirectamente métodos con peticiones de vínculos](../code-quality/ca2122.md) | Un miembro público o protegido tiene peticiones de vínculos y lo llama un miembro que no realiza ninguna comprobación de seguridad. Una solicitud de vínculo sólo comprueba los permisos del llamador inmediato. |
| CA2123 | [CA2123: Las peticiones de vínculos de invalidaciones deben ser idénticas a la base](../code-quality/ca2123.md) | Esta regla compara un método con su método base, que es una interfaz o un método virtual de otro tipo y, a continuación, compara las solicitudes de vínculos en cada uno. Si se infringe esta regla, un llamador malintencionado puede omitir la petición de vínculo tan solo con llamar al método no seguro. |
| CA2124 | [CA2124: Incluir cláusulas finally vulnerables en un bloque try externo](../code-quality/ca2124.md) | Un método público o protegido contiene un bloque try/finally. El bloque finally aparece para restablecer el estado de seguridad y no se incluye a sí mismo en un bloque finally. |
| CA2126 | [CA2126: Las peticiones de vínculos de tipos requieren peticiones de herencias](../code-quality/ca2126.md) | Un tipo público no sellado está protegido con una petición de vínculo y tiene un método reemplazable. Ni el tipo ni el método están protegidos con una petición de herencia. |
| CA2130 | [CA2130: Las constantes críticas para la seguridad deben ser transparentes](../code-quality/ca2130.md) | El cumplimiento de la transparencia no se exige para los valores constantes porque los compiladores alinean los valores constantes para que no se requiera ninguna búsqueda en tiempo de ejecución. Los campos constantes deberían ser transparentes en seguridad de modo que los revisores del código no supongan que el código transparente no puede tener acceso a la constante. |
| CA2131 | [CA2131: Los tipos críticos para la seguridad no pueden participar en la equivalencia de tipos](../code-quality/ca2131.md) | Un tipo participa en la equivalencia de tipos y el propio tipo, o un miembro o campo del tipo, se marca mediante el atributo SecurityCriticalAttribute. Esta regla se produce en todos los tipos críticos o en los tipos que contienen métodos o campos críticos que participan en la equivalencia de tipos. Cuando CLR detecta esta clase de tipo, no lo carga con TypeLoadException en tiempo de ejecución. Normalmente, esta regla solo se genera cuando los usuarios implementan la equivalencia de tipos de forma manual, en vez de basarse en tlbimp y en los compiladores para realizar la equivalencia de tipos. |
| CA2132 | [CA2132: Los constructores predeterminados deben ser al menos tan críticos para la seguridad como los constructores predeterminados de tipo base](../code-quality/ca2132.md) |El código de la aplicación Silverlight no puede usar los tipos y miembros con SecurityCriticalAttribute. El código de confianza puede utilizar solo tipos y miembros críticos para la seguridad en .NET Framework para la biblioteca de clases de Silverlight. Dado que una construcción pública o protegida en una clase derivada debe tener la misma transparencia, o mayor, que su clase base, una clase de una aplicación no puede derivar de una clase marcada como SecurityCritical. |
| CA2133 | [CA2133: Los delegados deben enlazarse a métodos con una transparencia coherente](../code-quality/ca2133.md) | Esta advertencia se genera en un método que enlaza un delegado marcado mediante SecurityCriticalAttribute a un método que es transparente o está marcado con SecuritySafeCriticalAttribute. La advertencia también desencadena un método que enlaza un delegado transparente o crítico para la seguridad a un método crítico. |
| CA2134 | [CA2134: Los métodos deben mantener una transparencia coherente al invalidar métodos base](../code-quality/ca2134.md) |Esta regla se genera cuando un método marcado mediante SecurityCriticalAttribute invalida un método que es transparente o está marcado con SecuritySafeCriticalAttribute. Esta regla también se genera cuando un método marcado mediante SecurityCriticalAttribute invalida un método que es transparente o está marcado con SecuritySafeCriticalAttribute. Se aplica la regla al invalidar un método virtual o implementar una interfaz. |
| CA2135 | [CA2135: Los ensamblados de nivel 2 no deben contener LinkDemands](../code-quality/ca2135.md) | LinkDemands está desusado en el conjunto de reglas de seguridad de nivel 2. En lugar de utilizar LinkDemands para exigir la seguridad en el momento de la compilación Just-In-Time (JIT), marque los métodos, tipos y campos con el atributo SecurityCriticalAttribute. |
| CA2127 | [CA2136: Los miembros no deben tener anotaciones de transparencia en conflicto](../code-quality/ca2136.md) | No se puede producir código crítico en un ensamblado de 100 por ciento transparente. Esta regla analiza los ensamblados del 100 por ciento transparentes para las anotaciones de SecurityCritical en los niveles de tipo, campo y método. |
| CA2136 | [CA2136: Los miembros no deben tener anotaciones de transparencia en conflicto](../code-quality/ca2136.md) | Los atributos de transparencia se aplican de los elementos de código de ámbito mayor a los elementos de ámbito menor. Los atributos de transparencia de los elementos de código con mayor ámbito tienen prioridad sobre los atributos de transparencia de los elementos de código incluidos en el primer elemento. Por ejemplo, una clase marcada con el atributo SecurityCriticalAttribute no puede contener un método marcado con el atributo SecuritySafeCriticalAttribute. |
| CA2137 | [CA2137: Los métodos transparentes deben contener solo IL que se pueda comprobar](../code-quality/ca2137.md) | Un método contiene código que no se puede comprobar o devuelve un tipo por referencia. Esta regla se desencadena en los intentos del código transparente en seguridad de ejecutar MISL no comprobable (Lenguaje intermedio de Microsoft). Sin embargo, la regla no contiene un comprobador de IL completo y, en su lugar, utiliza la heurística para detectar la mayoría de las infracciones de comprobación MSIL. |
| CA2138 | [CA2138: Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity](../code-quality/ca2138.md) | Un método transparente en seguridad llama a un método marcado mediante el atributo SuppressUnmanagedCodeSecurityAttribute. |
| CA2139 | [CA2139: Los métodos transparentes no pueden usar el atributo HandleProcessCorruptingExceptions](../code-quality/ca2139.md) | Esta regla la desencadena cualquier método que sea transparente e intente controlar una excepción de daño de proceso utilizando el atributo HandleProcessCorruptedStateExceptionsAttribute. Una excepción de daño de proceso en la versión 4.0 de CLR es una clasificación de excepciones como AccessViolationException. El atributo HandleProcessCorruptedStateExceptionsAttribute solo lo pueden utilizar los métodos críticos para la seguridad, y se omitirá si se aplica a un método transparente. |
| CA2129 | [CA2140: El código transparente no debe hacer referencia a elementos críticos para la seguridad](../code-quality/ca2140.md) | Los métodos que se marcan con el atributo SecurityTransparentAttribute llaman a miembros no públicos marcados como SecurityCritical. Esta regla analiza todos los métodos y tipos de un ensamblado que tiene una mezcla de transparente y crítico, y marca las llamadas desde código transparente a código crítico no público que no están marcadas como SecurityTreatAsSafe. |
| CA2140 | [CA2140: El código transparente no debe hacer referencia a elementos críticos para la seguridad](../code-quality/ca2140.md) | Un elemento de código que se marca con el atributo SecurityCriticalAttribute es crítico para la seguridad. Un método transparente no puede utilizar un elemento crítico para la seguridad. Si un tipo transparente intenta usar un tipo crítico para la seguridad, se produce una excepción TypeAccessException, MethodAccessException o FieldAccessException. |
| CA2141 |[CA2141: Los métodos transparentes no deben satisfacer LinkDemands](../code-quality/ca2141.md) | Un método transparente en seguridad llama a un método de un ensamblado no marcado mediante APTCA o bien satisface un LinkDemand para un tipo o método. |
| CA2142 | [CA2142: El código transparente no debe protegerse con LinkDemands](../code-quality/ca2142.md) | Esta regla se desencadena en métodos transparentes que exigen que LinkDemands tenga acceso a ellos. El código transparente en seguridad no debería ser responsable de comprobar la seguridad de una operación y, por consiguiente, no debería exigir permisos. |
| CA2143 | [CA2143: Los métodos transparentes no deben usar peticiones de seguridad](../code-quality/ca2143.md) | El código transparente en seguridad no debería ser responsable de comprobar la seguridad de una operación y, por consiguiente, no debería exigir permisos. El código transparente en seguridad debería utilizar peticiones completas para tomar decisiones de seguridad y el código crítico para la seguridad no debió confiar en el código transparente al realizar la petición completa. |
| CA2144 | [CA2144: El código transparente no debe cargar ensamblados desde matrices de bytes](../code-quality/ca2144.md) | La revisión de seguridad del código transparente no es tan exhaustiva como la revisión de seguridad del código crítico, porque el código transparente no puede realizar acciones que afectan a la seguridad. Los ensamblados cargados desde una matriz de bytes podrían no distinguirse en el código transparente, y esa matriz de bytes podría contener código importante crítico para la seguridad, que no hace falta auditar. |
| CA2145 | [CA2145: Los métodos transparentes no deben ser representativos con el atributo SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2145.md) | Los métodos decorados con el atributo SuppressUnmanagedCodeSecurityAttribute tienen una LinkDemand implícita colocada en cualquier método que la llame. Esta LinkDemand requiere que el código de llamada sea crítico para la seguridad. Marcar el método que utiliza SuppressUnmanagedCodeSecurity con el atributo SecurityCriticalAttribute hace este requisito más obvio para los llamadores del método. |
| CA2146 | [CA2146: Los tipos deben ser al menos tan críticos para la seguridad como sus interfaces y tipos base](../code-quality/ca2146.md) | Esta regla se desencadena cuando un tipo derivado tiene un atributo de transparencia de seguridad que no es tan crítico como su tipo base o interfaz implementada. Solo los tipos críticos pueden derivar de los tipos base críticos o implementar interfaces críticas, y solo los tipos críticos o críticos para la seguridad pueden derivar de tipos base críticos para la seguridad o implementar interfaces críticas para la seguridad. |
| CA2128 |[CA2147: Los métodos transparentes no pueden usar aserciones de seguridad](../code-quality/ca2147.md) | Esta regla analiza todos los métodos y tipos de un ensamblado que es 100 por ciento transparente o mixto y crítico, y marca cualquier uso declarativo o imperativo de Assert. |
| CA2147 |[CA2147: Los métodos transparentes no pueden usar aserciones de seguridad](../code-quality/ca2147.md) | El código marcado como SecurityTransparentAttribute no tiene permisos suficientes para imponerse. |
| CA2149 | [CA2149: Los métodos transparentes no deben llamar a código nativo](../code-quality/ca2149.md) | Esta regla se genera en cualquier método transparente que llame directamente al código nativo (por ejemplo, a través de P/Invoke). Las infracciones de esta regla tienen como resultado una excepción MethodAccessException en el modelo de transparencia de nivel 2 y una demanda completa de UnmanagedCode en el modelo de transparencia de nivel 1. |
| CA2151 |[CA2151: Los campos con tipos críticos deben ser críticos para la seguridad](../code-quality/ca2151.md) | Para utilizar tipos críticos para la seguridad, el código que hace referencia al tipo debe ser crítico para la seguridad o crítico para la seguridad y disponible desde código transparente. Esto es así incluso si la referencia es indirecta. Por consiguiente, tener un campo transparente para la seguridad o crítico para la seguridad y disponible desde código transparente puede llevar a confusión, porque el código transparente todavía no podrá tener acceso al campo. |
| CA2200 | [CA2200: Reiniciar para mantener los detalles de la pila](../code-quality/ca2200.md) | Se vuelve a producir una excepción y se especifica explícitamente en la instrucción throw. Si se vuelve a producir una excepción especificándola en la instrucción throw, se pierde la lista de llamadas al método entre el método original que produjo la excepción y el método actual. |
| CA2201 | [CA2201: No provocar tipos de excepción reservados](../code-quality/ca2201.md) | Esto hace que el error original sea difícil de detectar y depurar. |
| CA2202 | [CA2202: No usar Dispose varias veces en objetos](../code-quality/ca2202.md) |La implementación de un método contiene rutas de acceso del código que podrían provocar varias llamadas a System.IDisposable.Dispose o a un equivalente de Dispose (como un método Close() en algunos tipos) en el mismo objeto. |
| CA2204 | [CA2204: Los literales deben estar escritos correctamente](../code-quality/ca2204.md) | Una cadena literal en el cuerpo de un método contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce. |
| CA2205 | [CA2205: Utilizar equivalentes administrados de la API Win32](../code-quality/ca2205.md) | Se define un método de invocación del sistema operativo y hay disponible un método .NET que tiene la funcionalidad equivalente. |
| CA2207 | [CA2207: Inicializar campos estáticos de tipo de valor insertados](../code-quality/ca2207.md) | Un tipo de valor declara un constructor estático explícito. Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declara y quite el constructor estático. |
| CA2208 |[CA2208: Crear instancias de las excepciones del argumento correctamente](../code-quality/ca2208.md) | Se realiza una llamada al constructor predeterminado (sin parámetros) de un tipo de excepción que es o deriva de ArgumentException, o se pasa un argumento de cadena incorrecto a un constructor con parámetros de un tipo de excepción que es o deriva de ArgumentException. |
| CA2210 |[CA2210: Los ensamblados deben tener nombres seguros válidos](../code-quality/ca2210.md) | El nombre seguro protege los clientes de cargar inconscientemente un ensamblado con el que se ha alterado. Los ensamblados sin nombres seguros sólo deben implementarse en escenarios muy limitados. Si se comparten o se distribuyen ensamblados que no están correctamente firmados, el ensamblado puede manipularse, el Common Language Runtime podría no cargar el ensamblado o el usuario podría deshabilitar la comprobación del equipo. |
| CA2211 |[CA2211: Los campos no constantes no deben ser visibles](../code-quality/ca2211.md) | Los campos estáticos que no son constantes ni de sólo lectura no son seguros para subprocesos. Obtener acceso a este tipo de campo se debe controlar cuidadosamente y requiere técnicas de programación avanzadas para sincronizar el acceso al objeto de clase. |
| CA2212 | [CA2212: No marcar los componentes con servicio como WebMethod](../code-quality/ca2212.md) |Un método en un tipo que hereda de System.EnterpriseServices.ServicedComponent está marcado con System.Web.Services.WebMethodAttribute. Dado que un método ServicedComponent y WebMethodAttribute tienen comportamientos y requisitos conflictivos para el flujo de transacción y el contexto, el comportamiento del método es incorrecto en algunas situaciones. |
| CA2213 | [CA2213: Los campos descartables deben ser descartables](../code-quality/ca2213.md) | Un tipo que implementa System.IDisposable declara campos que son de tipos que también implementan IDisposable. El método Dispose del tipo declarativo no llama al método Dispose del campo. |
| CA2214 | [CA2214: No llamar a métodos reemplazables en constructores](../code-quality/ca2214.md) | Cuando un constructor llama a un método virtual, es posible que no se haya ejecutado el constructor para la instancia que invoca el método. |
| CA2215 | [CA2215: Los métodos Dispose deben llamar al método Dispose de la clase base](../code-quality/ca2215.md) | Si un tipo hereda de un tipo descartable, debe llamar al método Dispose del tipo base desde su propio método Dispose. |
| CA2216 |[CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216.md) | Un tipo que implementa System.IDisposable y tiene campos que sugieren el uso de recursos no administrados, no implementa un finalizador descrito por Object.Finalize. |
| CA2217 | [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217.md) |Una enumeración visible externamente está marcada con FlagsAttribute y tiene uno o varios valores que no son potencias de dos o una combinación de los otros valores definidos en la enumeración. |
| CA2218 |[CA2218: Invalidar el método GetHashCode al invalidar el método Equals](../code-quality/ca2218.md) | GetHashCode devuelve un valor basado en la instancia actual que es adecuado para los algoritmos hash y las estructuras de datos como una tabla hash. Dos objetos que son del mismo tipo y son iguales deben devolver el mismo código hash. |
| CA2219 | [CA2219: No producir excepciones en cláusulas de excepción](../code-quality/ca2219.md) | Cuando se genera una excepción en una cláusula finally o fault, la nueva excepción oculta la excepción activa. Cuando se genera una excepción en una cláusula filter, el runtime la detecta automáticamente. Esto hace que el error original sea difícil de detectar y depurar. |
| CA2220 | [CA2220: Los finalizadores deben llamar al finalizador de la clase base](../code-quality/ca2220.md) | La finalización se debe difundir a través de la jerarquía de herencia. Para garantizar esto, los tipos deben llamar a su método Finalize de clase base en su propio método Finalize. |
| CA2221 |[CA2221: Los finalizadores deben estar protegidos](../code-quality/ca2221.md) | Los finalizadores deben utilizar el modificador de acceso de familia. |
| CA2222 | [CA2222: No disminuir la visibilidad del miembro heredado](../code-quality/ca2222.md) |No debería cambiar el modificador de acceso para los miembros heredados. Cambiando un miembro heredado a privado no evita que los llamadores tengan acceso a la implementación de la clase base del método. |
| CA2223 | [CA2223: Los miembros deben diferenciarse por algo más que por un tipo de valor devuelto](../code-quality/ca2223.md) | Aunque Common Language Runtime permite utilizar tipos de valor devuelto para diferenciar miembros idénticos, esta característica no se encuentra en Common Language Specification ni es una característica común de los lenguajes de programación de .NET. |
| CA2224 | [CA2224: Invalidar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224.md) | Un tipo público implementa el operador de igualdad, pero no reemplaza Object.Equals. |
| CA2225 | [CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225.md) |Se detectó una sobrecarga del operador y no se encontró el método alternativo con el nombre esperado. El miembro alternativo con nombre proporciona acceso a la misma funcionalidad que el operador; esto se hace para los desarrolladores que programan en lenguajes que no admiten operadores sobrecargados. |
| CA2226 | [CA2226: Los operadores deben tener sobrecargas simétricas](../code-quality/ca2226.md) | Un tipo implementa el operador de igualdad o de desigualdad y no implementa el operador opuesto. |
| CA2227 |[CA2227: Las propiedades de la colección deben ser de solo lectura](../code-quality/ca2227.md) |Una propiedad de colección grabable permite al usuario reemplazar la colección por otra diferente. Una propiedad de sólo lectura impide que la colección se reemplace, pero sí permite establecer miembros individuales. |
| CA2228 | [CA2228: No enviar formatos de recursos no lanzados](../code-quality/ca2228.md) | Los archivos de recursos que se compilaron con versiones preliminares de .NET podrían no ser utilizados por las versiones compatibles de .NET. |
| CA2229 | [CA2229: Implementar constructores de serialización](../code-quality/ca2229.md) | Para corregir una infracción de esta regla, implemente el constructor de serialización. Para una clase sellada, marque el constructor como privado; de lo contrario, márquelo como protegido. |
| CA2230 | [CA2230: Usar parámetros en argumentos de variable](../code-quality/ca2230.md) | Un tipo público o protegido contiene un método público o protegido que utiliza la convención de llamada VarArgs en lugar de la palabra clave params. |
| CA2231 | [CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231.md) | Un tipo de valor invalida Object.Equals pero no implementa el operador de igualdad. |
| CA2232 | [CA2232: Marcar puntos de entrada de Windows Forms con STAThread](../code-quality/ca2232.md) | STAThreadAttribute indica que el modelo de subprocesos de COM para la aplicación es un contenedor uniproceso. Este atributo debe estar presente en el punto de entrada de cualquier aplicación que utilice Formularios Windows Forms; si se omite, los componentes de Windows podrían no funcionar correctamente. |
| CA2233 |[CA2233: Las operaciones no deben desbordarse](../code-quality/ca2233.md) | No debería realizar operaciones aritméticas sin validar primero los operandos. Esto asegura que el resultado de la operación no está fuera del intervalo de valores posibles para los tipos de datos que están implicados. |
| CA2234 | [CA2234: Pasar objetos System.Uri en lugar de cadenas](../code-quality/ca2234.md) | Se realiza una llamada a un método que tiene un parámetro de cadena cuyo nombre contiene "uri", "URI", "urn", "URN", "url" o "URL". El tipo declarativo del método contiene una sobrecarga de método correspondiente que tiene un parámetro System.Uri. |
| CA2235 | [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235.md) | Un campo de instancia de un tipo que no es serializable se declara en un tipo que es serializable. |
| CA2236 | [CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236.md) | Para corregir una infracción de esta regla, llame al método de tipo base GetObjectData o al constructor de serialización desde el constructor o el método de tipo derivado correspondiente. |
| CA2237 | [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237.md) | Para que los tipos sean reconocidos como serializables por Common Language Runtime, deben estar marcados con el atributo SerializableAttribute incluso si el tipo utiliza una rutina de serialización personalizada a través de la implementación de la interfaz ISerializable. |
| CA2238 |[CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238.md) | Un método que controla un evento de serialización no especifica la firma correcta, el tipo de valor devuelto ni la visibilidad. |
| CA2239 | [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239.md) | Un tipo tiene un campo que está marcado con el atributo System.Runtime.Serialization.OptionalFieldAttribute y el tipo no proporciona métodos de control de eventos de deserialización. |
| CA2240 | [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240.md) | Para corregir una infracción de esta regla, haga que el método GetObjectData sea visible y reemplazable, y asegúrese de que todos los campos de instancia se incluyan en el proceso de serialización o se marquen explícitamente con el atributo NonSerializedAttribute. |
| CA2241 | [CA2241: Proporcionar argumentos correctos a los métodos de formato](../code-quality/ca2241.md) | El argumento format pasado a System.String.Format no contiene un elemento de formato que corresponda a cada argumento de objeto o viceversa. |
| CA2242 |[CA2242: Comprobar NaN correctamente](../code-quality/ca2242.md) | Esta expresión prueba un valor respecto a Single.Nan o Double.Nan. Utilice IsNan(Single) o Double.IsNan(Double) para probar el valor. |
| CA2243 |[CA2243: Los literales de cadena de atributo se deben analizar correctamente](../code-quality/ca2243.md) | El parámetro de literal de cadena de un atributo no se analiza correctamente para una dirección URL, un GUID o una versión. |
| CA2244 | [CA2244: No duplicar inicializaciones de elementos indexados](../code-quality/ca2244.md) | Un inicializador de objeto tiene más de un inicializador de elemento indizado con el mismo índice de constante. Todo menos el último inicializador son redundantes. |
| CA2245 | [CA2245: No asignar una propiedad a sí misma](../code-quality/ca2245.md) | Una propiedad se asignó accidentalmente a sí misma. |
| CA2246 | [CA2246: No asignar un símbolo y su miembro en la misma instrucción](../code-quality/ca2246.md) | No se recomienda asignar un símbolo y su miembro, es decir, un campo o una propiedad, en la misma instrucción. No está claro si el acceso a miembros debía usar el valor anterior del símbolo antes de la asignación o el nuevo valor de la asignación en esta instrucción. |
| CA2247 | [CA2247: el argumento pasado al constructor TaskCompletionSource debe ser una enumeración TaskCreationOptions en lugar de TaskContinuationOptions enum.](../code-quality/ca2247.md) | TaskCompletionSource tiene constructores que toman un TaskCreationOptions que controla la tarea subyacente y constructores que toman el estado del objeto almacenado en la tarea.  Pasar accidentalmente un TaskContinuationOptions en lugar de un TaskCreationOptions dará lugar a que la llamada trate las opciones como estado. |
| CA2249 | [CA2249: CA2249: considere la posibilidad de usar String. Contains en lugar de String. IndexOf](../code-quality/ca2249.md) | Las llamadas a `string.IndexOf` donde se utiliza el resultado para comprobar la presencia o ausencia de una subcadena se pueden reemplazar por `string.Contains` . |
| CA5122 | [Las declaraciones de CA5122: P/Invoke no deben ser críticas para la seguridad](../code-quality/ca5122.md) | Los métodos se marcan como SecuritySafeCritical cuando realizan una operación que afecta a la seguridad pero también son seguros para su uso en código transparente. El código transparente nunca puede llamar a código nativo a través de P/Invoke. Por consiguiente, aunque se marque P/Invoke como crítico para la seguridad y disponible desde código transparente no permitirá que se llame desde código transparente llamarlo, y es erróneo para los análisis de seguridad. |
| CA5359 | [CA5359 no deshabilitar la validación de certificados](../code-quality/ca5359.md) | Un certificado puede ayudar a autenticar la identidad del servidor. Los clientes deben validar el certificado de servidor para asegurarse de que las solicitudes se envían al servidor previsto. Si ServerCertificateValidationCallback (siempre devuelve `true` , cualquier certificado pasará la validación. |
| CA5360 | [CA5360 no llama a métodos peligrosos en la deserialización](../code-quality/ca5360.md) | La deserialización no segura es una vulnerabilidad que se produce cuando los datos que no son de confianza se usan para abusar la lógica de una aplicación, provocar un ataque de denegación de servicio (DoS) o incluso ejecutar código arbitrario cuando se deserializa. A menudo, es posible que los usuarios malintencionados abusan estas características de deserialización cuando la aplicación está deserializando datos que no son de confianza y están bajo su control. En concreto, invoque métodos peligrosos en el proceso de deserialización. Los ataques de deserialización inseguros que se han realizado correctamente podrían permitir que un atacante lleve a cabo ataques como ataques de DoS, omisiones de autenticación y ejecución remota de código. |
| CA5362 | [Ciclo de referencia potencial de CA5362 en el gráfico de objetos deserializados](../code-quality/ca5362.md) | Si se deserializan los datos que no son de confianza, el procesamiento de código del gráfico de objetos deserializados debe controlar los ciclos de referencia sin entrar en bucles infinitos. Esto incluye el código que forma parte de una devolución de llamada de deserialización y el código que procesa el gráfico de objetos una vez completada la deserialización. De lo contrario, un atacante podría realizar un ataque por denegación de servicio con datos malintencionados que contuvieran un ciclo de referencia. |
| CA5365 | [CA5365 no deshabilitar la comprobación de encabezados HTTP](../code-quality/ca5365.md) | La comprobación de encabezados HTTP permite codificar el retorno de carro y los caracteres de nueva línea, \r y \n, que se encuentran en los encabezados de respuesta. Esta codificación puede ayudar a evitar ataques de inyección que aprovechan una aplicación que repite datos que no son de confianza contenidos en el encabezado. |
| CA5366 | [CA5366 usar XmlReader para leer XML de DataSet](../code-quality/ca5366.md) | El uso de <xref:System.Data.DataSet> para leer XML con datos que no son de confianza puede cargar referencias externas peligrosas, que se deben restringir mediante un <xref:System.Xml.XmlReader> con un solucionador seguro o con el procesamiento de DTD deshabilitado. |
| CA5367 | [CA5367 no serializan tipos con campos de puntero](../code-quality/ca5367.md) | Esta regla comprueba si hay una clase serializable con una propiedad o un campo de puntero. Los miembros que no se pueden serializar pueden ser un puntero, como los miembros estáticos o los campos marcados con <xref:System.NonSerializedAttribute> . |
| CA5368 | [CA5368 Set ViewStateUserKey para las clases derivadas de Page](../code-quality/ca5368.md) | El establecimiento de la <xref:System.Web.UI.Page.ViewStateUserKey> propiedad puede ayudarle a evitar ataques en la aplicación al permitirle asignar un identificador a la variable de estado de vista de usuarios individuales para que los atacantes no puedan usar la variable para generar un ataque. De lo contrario, habrá vulnerabilidades en la falsificación de solicitudes entre sitios. |
| CA5374 | [CA5374 no usar XslTransform](../code-quality/ca5374.md) | Esta regla comprueba si <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> se crean instancias en el código. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> está ahora obsoleto y no debe usarse. |
| CA5375 | [CA5375 no usar firma de acceso compartido de cuenta](../code-quality/ca5375.md) | Una SAS de cuenta puede delegar el acceso a operaciones de lectura, escritura y eliminación en contenedores de blobs, tablas, colas y recursos compartidos de archivos que no se permiten con una SAS de servicio. Sin embargo, no es compatible con las directivas de nivel de contenedor y tiene menos flexibilidad y control sobre los permisos que se conceden. Una vez que los usuarios malintencionados la obtienen, la cuenta de almacenamiento se verá comprometida fácilmente. |
| CA5376 | [CA5376 uso de SharedAccessProtocol HttpsOnly](../code-quality/ca5376.md) | SAS es información confidencial que no se puede transportar en texto sin formato en HTTP. |
| CA5377 | [CA5377 usar la Directiva de acceso de nivel de contenedor](../code-quality/ca5377.md) | Una directiva de acceso de nivel de contenedor se puede modificar o revocar en cualquier momento. Proporciona mayor flexibilidad y control sobre los permisos que se conceden. |
| CA5379 | [CA5379 no usar el algoritmo de función de derivación de clave débil](../code-quality/ca5379.md) | De <xref:System.Security.Cryptography.Rfc2898DeriveBytes> forma predeterminada, la clase usa el <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> algoritmo. Debe especificar el algoritmo hash que se utilizará en algunas sobrecargas del constructor con <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> o superior. Tenga en cuenta <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> que la propiedad solo tiene un `get` descriptor de acceso y no tiene un `overriden` modificador. |
| CA5382 | [CA5382 usar cookies seguras en ASP.NET Core](../code-quality/ca5382.md) | Las aplicaciones disponibles a través de HTTPS deben usar cookies seguras, que indican al explorador que la cookie solo se debe transmitir mediante Capa de sockets seguros (SSL). |
| CA5383 | [CA5383 Asegúrese de usar cookies seguras en ASP.NET Core](../code-quality/ca5383.md) | Las aplicaciones disponibles a través de HTTPS deben usar cookies seguras, que indican al explorador que la cookie solo se debe transmitir mediante Capa de sockets seguros (SSL). |
| CA5384 | [CA5384 no usar el algoritmo de firma digital (DSA)](../code-quality/ca5384.md) | DSA es un algoritmo de cifrado asimétrico débil. |
| CA5385 | [CA5385 usar el algoritmo Rivest – Shamir – Adleman (RSA) con el tamaño de clave suficiente](../code-quality/ca5385.md) | Una clave RSA de menos de 2048 bits es más vulnerable a los ataques por fuerza bruta. |
| CA5387 | [CA5387 no usar la función de derivación de clave débil con el recuento de iteraciones insuficiente](../code-quality/ca5387.md) | Esta regla comprueba si se generó una clave criptográfica <xref:System.Security.Cryptography.Rfc2898DeriveBytes> con un recuento de iteraciones inferior a 100.000. Un recuento de iteraciones mayor puede ayudar a mitigar los ataques de diccionario que intentan adivinar la clave criptográfica generada. |
| CA5388 | [CA5388 garantizar el número de iteraciones suficientes al usar la función de derivación de clave débil](../code-quality/ca5388.md) | Esta regla comprueba si se generó una clave criptográfica <xref:System.Security.Cryptography.Rfc2898DeriveBytes> con un recuento de iteraciones que puede ser inferior a 100.000. Un recuento de iteraciones mayor puede ayudar a mitigar los ataques de diccionario que intentan adivinar la clave criptográfica generada. |
| CA5390 | [CA5390 no codificar clave de cifrado](../code-quality/ca5390.md) | Para que un algoritmo simétrico se realice correctamente, solo el remitente y el receptor deben conocer la clave secreta. Cuando una clave está codificada de forma rígida, se detecta fácilmente. Incluso con los archivos binarios compilados, es fácil que los usuarios malintencionados lo extraigan. Una vez que la clave privada se ve comprometida, el texto cifrado se puede descifrar directamente y ya no está protegido. |
| CA5391 | [CA5391 usar tokens antifalsificación en controladores MVC de ASP.NET Core](../code-quality/ca5391.md) | Controlar una `POST` `PUT` solicitud,, `PATCH` o `DELETE` sin validar un token antifalsificación puede ser vulnerable a los ataques de falsificación de solicitudes entre sitios. Un ataque de falsificación de solicitudes entre sitios puede enviar solicitudes malintencionadas de un usuario autenticado a un controlador de MVC de ASP.NET Core. |
| CA5392 | [CA5392 usar el atributo DefaultDllImportSearchPaths para P/Invoke](../code-quality/ca5392.md) | De forma predeterminada, las funciones P/Invoke <xref:System.Runtime.InteropServices.DllImportAttribute> que usan sondeos incluyen un número de directorios, incluido el directorio de trabajo actual de la biblioteca que se va a cargar. Puede tratarse de un problema de seguridad para ciertas aplicaciones, lo que conduce a la secuestro de DLL. |
| CA5393 | [CA5393 no usar un valor DllImportSearchPath no seguro](../code-quality/ca5393.md) | Podría haber un archivo DLL malintencionado en los directorios de búsqueda DLL predeterminados y los directorios de ensamblado. O, en función de dónde se ejecute la aplicación, podría haber un archivo DLL malintencionado en el directorio de la aplicación. |
| CA5394 | [CA5394 no usar aleatoriedad no segura](../code-quality/ca5394.md) | El uso de un generador de números pseudoaleatorios no seguros criptográficamente puede permitir que un atacante prediga qué valor de seguridad se generará. |
| CA5395 | [CA5395 perdió HttpVerb atributo para métodos de acción](../code-quality/ca5395.md) | Todos los métodos de acción que crean, modifican, eliminan o modifican de algún otro modo los datos deben protegerse con el atributo antifalsificación de los ataques de falsificación de solicitudes entre sitios. Realizar una operación GET debe ser una operación segura que no tenga efectos secundarios y no modifique los datos persistentes. |
| CA5396 | [CA5396 establecer HttpOnly en true para HttpCookie](../code-quality/ca5396.md) | Como medida de defensa en profundidad, asegúrese de que las cookies HTTP confidenciales de seguridad estén marcadas como HttpOnly. Esto indica que los exploradores Web deben impedir que los scripts tengan acceso a las cookies. Los scripts malintencionados insertados son una forma habitual de robar cookies. |
| CA5399 | [CA5399 deshabilitar definitivamente la comprobación de la lista de revocación de certificados HttpClient](../code-quality/ca5399.md) | Un certificado revocado ya no es de confianza. Podría ser utilizado por los atacantes para pasar algunos datos malintencionados o robar datos confidenciales en la comunicación HTTPS. |
| CA5400 | [CA5400 asegurarse de que la lista de revocación de certificados HttpClient no está deshabilitada](../code-quality/ca5400.md) | Un certificado revocado ya no es de confianza. Podría ser utilizado por los atacantes para pasar algunos datos malintencionados o robar datos confidenciales en la comunicación HTTPS. |
| CA5401 | [CA5401 no usar CreateEncryptor con un IV no predeterminado](../code-quality/ca5401.md) | El cifrado simétrico siempre debe usar un vector de inicialización no repetible para evitar ataques de diccionario. |
| CA5402 | [CA5402 usar CreateEncryptor con el valor de IV predeterminado](../code-quality/ca5402.md) | El cifrado simétrico siempre debe usar un vector de inicialización no repetible para evitar ataques de diccionario. |
| IL3000 | [IL3000 evitar el acceso a la ruta de acceso del archivo de ensamblado al publicar como un solo archivo](../code-quality/il3000.md) | Evite el uso de la ruta de acceso del archivo de ensamblado al publicar como un solo archivo |
| IL3001 | [IL3001 evitar el acceso a la ruta de acceso del archivo de ensamblado al publicar como un solo archivo](../code-quality/il3001.md) | Evitar el acceso a la ruta de acceso del archivo de ensamblado al publicar como un solo archivo |
