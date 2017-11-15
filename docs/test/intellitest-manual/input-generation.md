---
title: "Ejecución simbólica dinámica | Herramientas de prueba para desarrolladores de Microsoft IntelliTest | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Dynamic symbolic execution
ms.assetid: B938E2D2-7B7C-4D76-B26C-2616F5B4A9F5
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 7739a7fd1d802150ecf6cdc3e364423598ff090c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="input-generatation-using-dynamic-symbolic-execution"></a>Generación de entradas con la ejecución simbólica dinámica

IntelliTest genera entradas para las [pruebas unitarias parametrizadas](test-generation.md#parameterized-unit-testing) analizando las condiciones de rama en el programa. Las entradas de prueba se eligen basándose en si pueden desencadenar nuevos comportamientos de rama del programa. El análisis es un proceso incremental. Afina un predicado **q: I -> {true, false}** en los parámetros de entrada de pruebas formales **I**. **q** representa el conjunto de comportamientos que IntelliTest ya ha observado. Inicialmente, **q := false**, ya que no se ha observado nada todavía.

Los pasos del bucle son:

1. IntelliTest determina entradas **i** como **q(i)=false** con un [solucionador de restricciones](#constraint-solver). 
   Mediante la construcción, la entrada **i** tomará una ruta de ejecución no vista anteriormente. Inicialmente, esto significa que **i** puede ser cualquier entrada, porque todavía no se ha detectado ninguna ruta de ejecución.

1. IntelliTest ejecuta la prueba con la entrada **i** elegida, y supervisa la ejecución de la prueba y el programa sometido a prueba.

1. Durante la ejecución, el programa toma una ruta concreta que se determina mediante todas las ramas condicionales del programa. El conjunto de todas las condiciones que determina la ejecución se denomina *condición de ruta de acceso*, que se escribe como el predicado **p: I -> {true, false}** en los parámetros de entrada formales. IntelliTest calcula una representación de este predicado.

1. IntelliTest establece **q := (q o p)**. En otras palabras, registra el hecho de que ha visto la ruta representada mediante **p**.

1. Vaya al paso 1.

El [solucionador de restricciones](#constraint-solver) de IntelliTest puede tratar con valores de todos los tipos que pueden aparecer en programas .NET:

* Números [enteros](#integers-and-floats) y [flotantes](#integers-and-floats)
* [Objects](#objects)
* [Estructuras](#structs)
* [Matrices](#arrays-and-strings) y [cadenas](#arrays-and-strings)

IntelliTest filtra las entradas que infringen las hipótesis indicadas.

Además de las entradas inmediatas (argumentos para las [pruebas unitarias parametrizadas](test-generation.md#parameterized-unit-testing)), una prueba puede extraer valores de entrada de la clase estática [PexChoose](static-helper-classes.md#pexchoose). Las elecciones también determinan el comportamiento de [objetos ficticios parametrizados](#parameterized-mocks).

<a name="constraint-solver"></a>
## <a name="constraint-solver"></a>Solucionador de restricciones

IntelliTest usa un solucionador de restricciones para determinar los valores de entrada relevantes de una prueba y del programa sometido a prueba.

IntelliTest usa el solucionador de restricciones [Z3](https://github.com/Z3Prover/z3/wiki).

<a name="dynamic-code-coverage"></a>
## <a name="dynamic-code-coverage"></a>Cobertura de código dinámica

Como un efecto secundario de la supervisión del runtime, IntelliTest recopila datos de cobertura de código dinámica. Se denomina *dinámica* porque IntelliTest solo conoce el código que se ha ejecutado y, por lo tanto, no puede proporcionar valores absolutos para la cobertura de la misma manera que lo realiza normalmente otra herramienta de cobertura. 

Por ejemplo, cuando IntelliTest notifica la cobertura dinámica como bloques básicos 5/10, esto significa que cinco bloques de diez están cubiertos, donde el número total de bloques en todos los métodos que se han alcanzado hasta el momento mediante el análisis (en lugar de todos los métodos que existen en el ensamblado sometido a prueba) es diez.
Posteriormente en el análisis, como se detectan más métodos accesibles, tanto el numerador (5 en este ejemplo) como el denominador (10) pueden aumentar.

<a name="integers-and-floats"></a>
## <a name="integers-and-floats"></a>Números enteros y flotantes

El [solucionador de restricciones](#constraint-solver) de IntelliTest determina los valores de entrada de prueba de tipos primitivos como **byte**, **int** y **float**, entre otros, para desencadenar diferentes rutas de ejecución para la prueba y el programa sometido a prueba.

<a name="objects"></a>
## <a name="objects"></a>de la empresa

IntelliTest puede [crear instancias de clases .NET existentes](#existing-classes) o puede usar IntelliTest para [crear objetos ficticios](#parameterized-mocks) automáticamente que implementen una interfaz específica y se comporten de diferentes maneras dependiendo del uso.

<a name="existing-classes"></a>
## <a name="instantiating-existing-classes"></a>Creación de instancias de las clases existentes

**¿Cuál es el problema?**

IntelliTest supervisa las instrucciones ejecutadas cuando ejecuta una prueba y el programa sometido a prueba. En concreto, supervisa todo el acceso a los campos. Después, usa un [solucionador de restricciones](#constraint-solver) para determinar nuevas entradas de prueba, incluidos objetos y sus valores de campo, de manera que la prueba y el programa sometido a prueba se comportarán de otras maneras interesantes.

Esto significa que IntelliTest debe crear objetos de determinados tipos y establecer sus valores de campo. Si la clase es [visible](#visibility) y tiene un constructor predeterminado [visible](#visibility), IntelliTest puede crear una instancia de la clase.
Si todos los campos de la clase son [visibles](#visibility), IntelliTest puede establecer los campos automáticamente.

Si el tipo no es visible o los campos no son [visibles](#visibility), IntelliTest necesita ayuda para crear objetos y proporcionarles estados interesantes para obtener la máxima cobertura de código. IntelliTest podría usar la reflexión para crear e inicializar instancias de maneras arbitrarias, pero normalmente  
no se recomienda porque puede proporcionar un estado al objeto que nunca pueda producirse durante una ejecución normal del programa. En su lugar, IntelliTest se basa en las sugerencias del usuario.

<a name="visibility"></a>
## <a name="visibility"></a>Visibility

.NET Framework tiene un modelo de visibilidad elaborado: tipos, métodos, campos y otros miembros pueden ser **privados**, **públicos** e **internos**, entre otros.

Cuando IntelliTest genera pruebas, intentará realizar solo acciones (como llamar a los constructores, métodos y campos de configuración) que sean legales respecto a las reglas de visibilidad de .NET desde el contexto de las pruebas generadas.

Las reglas son las siguientes:

* **Visibilidad de miembros internos**
  * IntelliTest presupone que las pruebas generadas tendrán acceso a los miembros internos que eran visibles para el atributo [PexClass](attribute-glossary.md#pexclass) envolvente.
  .NET tiene **InternalsVisibleToAttribute** para ampliar la visibilidad de los miembros internos en otros ensamblados.<p />

* **Visibilidad de miembros de la familia y privados (protegidos en C#) de [PexClass](attribute-glossary.md#pexclass)**
  * IntelliTest siempre coloca las pruebas generadas directamente en [PexClass](attribute-glossary.md#pexclass) o en una subclase. Por lo tanto, IntelliTest presupone que puede usar todos los miembros de la familia visibles (**protegidos** en C#).
  * Si las pruebas generadas se colocan directamente en [PexClass](attribute-glossary.md#pexclass) (normalmente mediante clases parciales), IntelliTest presupone que también puede usar todos los miembros privados de [PexClass](attribute-glossary.md#pexclass).<p />

* **Visibilidad de miembros públicos**
  * IntelliTest presupone que puede usar todos los miembros exportados visibles en el contexto de [PexClass](attribute-glossary.md#pexclass).

<a name="parameterized-mocks"></a>
## <a name="parameterized-mocks"></a>Objetos ficticios parametrizados

¿Cómo se puede probar un método que tiene un parámetro de un tipo de interfaz? ¿O de una clase no sealed? IntelliTest no sabe que implementaciones se usarán más tarde cuando se llame a este método. Y, quizás, ni siquiera existe una implementación real disponible en el tiempo de la prueba.

La respuesta convencional es usar *objetos ficticios* con un comportamiento explícito. 

Un objeto ficticio implementa una interfaz (o amplía una clase no sealed). No representa una implementación real, sino solo un acceso directo que permite la ejecución de pruebas con el objeto ficticio. Su comportamiento se define manualmente como parte de cada caso de prueba donde se usa. Existen muchas herramientas que facilitan la definición de objetos ficticios y su comportamiento esperado, pero este comportamiento todavía debe definirse manualmente.

En lugar de valores codificados de forma rígida en objetos ficticios, IntelliTest puede generar los valores. Igual que permite las [pruebas unitarias parametrizadas](test-generation.md#parameterized-unit-testing), IntelliTest también permite los objetos ficticios parametrizados.

Los objetos ficticios parametrizados tienen dos modos de ejecución diferentes:

* **choosing**: al explorar código, los objetos ficticios parametrizados son un origen de entradas de prueba adicionales, e IntelliTest intentará elegir valores interesantes
* **replay**: al ejecutar una prueba generada anteriormente, los objetos ficticios parametrizados se comportan como códigos auxiliares con comportamiento (en otras palabras, un comportamiento predefinido).

Use [PexChoose](static-helper-classes.md#pexchoose) para obtener valores para los objetos ficticios parametrizados.

<a name="structs"></a>
## <a name="structs"></a>Estructuras

El razonamiento de IntelliTest sobre los valores **struct** es similar a la manera en que trata a los [objetos](#objects).

<a name="arrays-and-strings"></a>
## <a name="arrays-and-strings"></a>Matrices y cadenas

IntelliTest supervisa las instrucciones ejecutadas cuando ejecuta una prueba y el programa sometido a prueba. En concreto, observa cuándo el programa depende de la longitud de una cadena o una matriz (y las longitudes y límites inferiores de una matriz multidimensional). También observa cómo el programa usa los diferentes elementos de una cadena o matriz. Después, usa un [solucionador de restricciones](#constraint-solver) para determinar qué longitudes y valores de elemento pueden provocar que la prueba y el programa sometido a prueba se comporten de maneras interesantes.

IntelliTest intenta minimizar el tamaño de las matrices y las cadenas necesarias para desencadenar comportamientos de programa interesantes.

<a name="additional-inputs"></a>
## <a name="obtaining-additional-inputs"></a>Obtención de entradas adicionales

La clase estática [PexChoose](static-helper-classes.md#pexchoose) puede usarse para obtener entradas adicionales para una prueba, y puede usarse para implementar [objetos ficticios parametrizados](#parameterized-mocks).

<a name="further-reading"></a>
## <a name="further-reading"></a>Información adicional

* [¿Cómo funciona?](https://blogs.msdn.microsoft.com/visualstudioalm/2014/12/11/smart-unit-tests-a-mental-model/)

## <a name="got-feedback"></a>¿Tiene comentarios?

Publique sus ideas y solicitudes de características en **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
