---
title: Editar código de Python
description: Para Python, Visual Studio proporciona IntelliSense enriquecido, fragmentos de código y características de navegación, además de formato, detección de errores y refactorización.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b111d3b0fe2f4af9098186aff3ef661045215473
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59366281"
---
# <a name="edit-python-code"></a>Editar código de Python

Dado que invierte mucho tiempo de desarrollo en el editor de código, la [compatibilidad de Python en Visual Studio](installing-python-support-in-visual-studio.md) proporciona funciones para ayudarle a ser más productivo. Las características incluyen resalte de sintaxis de IntelliSense, finalización automática, ayuda para la firma, invalidaciones de método, búsqueda y navegación.

El editor también está integrado en la ventana **interactiva** de Visual Studio, lo que hace que sea sencillo intercambiar código entre los dos. Vea [Paso 3 del tutorial: Uso de la ventana interactiva de REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) y [Uso de la ventana interactiva - Comando Enviar código a Interactive](python-interactive-repl-in-visual-studio.md#send-to-interactive-command) para obtener información detallada.

Para obtener documentación general sobre la edición de código en Visual Studio, vea [Características del editor de código](../ide/writing-code-in-the-code-and-text-editor.md). Vea también [Esquematización](../ide/outlining.md), que le ayudará a mantenerse centrado en determinadas secciones del código.

También puede usar el **Examinador de objetos** de Visual Studio (**Ver** > **Otras ventanas** > **Examinador de objetos** o **Ctrl**+**W** > **J**) para inspeccionar las clases de Python definidas en cada módulo y las funciones definidas en esas clases.

## <a name="intellisense"></a>IntelliSense

IntelliSense ofrece [finalizaciones](#completions), [ayuda para la firma](#signature-help), [información rápida](#quick-info) y [coloración de código](#code-coloring). Visual Studio 2017 versión 15.7 y posteriores también admite [sugerencias de tipo](#type-hints).

Para mejorar el rendimiento, IntelliSense en Visual Studio 2017, versión 15.5 y versiones anteriores, depende de la base de datos de finalizaciones que se genera para cada entorno de Python en el proyecto. Si agrega, quita o actualiza paquetes las bases de datos puede que necesiten actualizarse. El estado de la base de datos se muestra en la ventana **Entornos de Python** (un elemento relacionado del **Explorador de soluciones**) en la pestaña **IntelliSense** (vea [Referencia de pestañas de la ventana Entorno de Python](python-environments-window-tab-reference.md#intellisense-tab)).

Visual Studio 2017, versión 15.6 y posteriores, se utiliza un medio diferente para proporcionar finalizaciones de IntelliSense que no dependen de la base de datos.

### <a name="completions"></a>Finalizaciones

Las finalizaciones aparecen como instrucciones, identificadores y otras palabras que pueden especificarse adecuadamente en la ubicación actual en el editor. Lo que se muestra en la lista se basa en contexto y se filtra para omitir las opciones incorrectas o molestas. Las finalizaciones a menudo se desencadenan escribiendo instrucciones diferentes (como `import`) y operadores (incluido el punto), pero puede hacer que aparezcan en cualquier momento si presiona **Ctrl**+**J** > **Espacio**.

![Finalización de miembros en el editor de Visual Studio](media/code-editing-completions-simple.png)

Cuando se abre una lista de finalizaciones, puede buscar la finalización que desee con las teclas de dirección, el mouse o bien escribiendo algo más. A medida que escriba más letras, la lista se seguirá filtrando para mostrar las finalizaciones probables. También puede usar accesos directos como:

- Escribir letras que no están al principio del nombre, como "parse" para buscar "argparse"
- Escribir solo las letras que se encuentran al principio de palabras, como "abc" para buscar 'AbstractBaseClass' o "air" para buscar "as_integer_ratio"
- Omitir letras, como "b64" para buscar "base64"

Algunos ejemplos:

![Finalización de miembros con filtrado en el editor de Visual Studio](media/code-editing-completion-filtering.png)

Las finalizaciones de miembros aparecen automáticamente al escribir un punto después de una variable o un valor, junto con los métodos y atributos de los tipos posibles. Si una variable puede ser de más de un tipo, la lista incluye todas las posibilidades de todos los tipos, con información adicional para indicar qué tipos admite cada finalización. Cuando una finalización es compatible con todos los tipos posibles, se muestra sin la anotación.

![Finalización de miembros en varios tipos en el editor de Visual Studio](media/code-editing-completion-types.png)

De manera predeterminada, no se muestran los miembros "dunder" (miembros que comienzan y terminan con un doble carácter de subrayado). En general, no se debe acceder a dichos miembros directamente. En cambio, si necesita uno, al escribir el doble carácter de subrayado inicial se agregan estas finalizaciones a la lista:

![Finalización de miembros privados en el editor de Visual Studio](media/code-editing-completion-dunder.png)

Las instrucciones `import` y `from ... import` muestran una lista de módulos que pueden importarse. Con `from ... import`, la lista incluye miembros que pueden importarse desde el módulo especificado.

![Finalización de importaciones en el editor de Visual Studio](media/code-editing-completion-import.png)

Las instrucciones `raise` y `except` muestran listas de clases que probablemente sean tipos de error. La lista puede no incluir todas las excepciones definidas por el usuario, pero le ayudan a encontrar rápidamente las excepciones integradas adecuadas:

![Finalización de excepciones en el editor de Visual Studio](media/code-editing-completion-exception.png)

Al escribir @ se inicia un decorador y se muestran todos los posibles decoradores. Muchos de estos elementos no se pueden usar como decoradores; consulte la documentación de la biblioteca para determinar cuál se va a usar.

![Finalización de decoradores en el editor de Visual Studio](media/code-editing-completion-decorator.png)

> [!Tip]
> Puede configurar el comportamiento de estas finalizaciones en **Herramientas** > **Opciones** > **Editor de texto** > **Python** > **Opciones avanzadas**. De estas opciones, **Filter list based on search string** (Filtrar lista en función de la cadena de búsqueda) aplica el filtrado de sugerencias de finalización mientras se escribe (activo de manera predeterminada) y **Member completion displays intersection of members** (La finalización de miembros muestra la intersección de miembros) muestra solo las finalizaciones que son compatibles con todos los posibles tipos (desactivado de manera predeterminada). Vea [Opciones: resultados de finalización](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Sugerencias de escritura

*Visual Studio 2017 versión 15.7 y posteriores.*

"Sugerencias de escritura" en Python 3.5 + ([PEP 484](https://www.python.org/dev/peps/pep-0484/) (python.org) es una sintaxis de anotación de funciones y clases que indica los tipos de argumentos, valores devueltos y atributos de clase. IntelliSense muestra sugerencias de tipo cuando mantiene el mouse sobre las llamadas a funciones, argumentos y variables que tengan dichas anotaciones.

En el ejemplo siguiente, la clase `Vector` se declara como `List[float]`, y la función `scale` contiene sugerencias de tipo para sus argumentos y el valor devuelto. Al mantener el mouse sobre una llamada a esa función se muestran las sugerencias de tipo:

![Mantener el mouse sobre una llamada de función para mostrar sugerencias de tipo](media/code-editing-type-hints1.png)

En el ejemplo siguiente puede ver cómo los atributos anotados de la clase `Employee` aparecen en la ventana emergente de finalización de IntelliSense para un atributo:

![Finalización de IntelliSense que muestra sugerencias de tipo](media/code-editing-type-hints2.png)

También es útil validar las sugerencias de tipo en todo el proyecto, porque los errores normalmente no aparecerán hasta el tiempo de ejecución. Para ello, Visual Studio integra la herramienta estándar del sector MyPy mediante el comando de menú contextual **Python** > **Ejecutar MyPy** en el **Explorador de soluciones**:

![Ejecute el comando de menú contextual de MyPy en el Explorador de soluciones](media/code-editing-type-hints-run-mypy.png)

Al ejecutar el comando se le solicita que instale el paquete MyPy, si es necesario. Después, Visual Studio ejecuta MyPy para validar las sugerencias de tipo de cada archivo de Python en el proyecto. Los errores se muestran en la ventana **Lista de errores** de Visual Studio. Al seleccionar un elemento en la ventana se desplaza a la línea adecuada del código.

Como ejemplo sencillo, la siguiente definición de función contiene una sugerencia de tipo para indicar que el argumento `input` es de tipo `str`, mientras que la llamada a esa función intenta pasar un entero:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Al usar el comando **Ejecutar MyPy** en este código se genera el siguiente error:

![Resultado de ejemplo donde MyPy valida las sugerencias de tipo](media/code-editing-type-hints-validation-error.png)

::: moniker range="vs-2017"
> [!Tip]
> Para las versiones de Python anteriores a la 3.5, Visual Studio también muestra las sugerencias de tipo que proporcione a través de *archivos de código auxiliar* de Typeshed (*.pyi*). Puede usar archivos de código auxiliar siempre que no quiera incluir sugerencias de tipo directamente en el código o cuando quiera crear sugerencias de tipo para una biblioteca que no los usa directamente. Para obtener más información, vea [Create Stubs for Python Modules](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) (Creación de códigos auxiliares para los módulos de Python) en la wiki de proyecto de MyPy.
>
> Actualmente Visual Studio no admite sugerencias de tipo en los comentarios.
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> Para las versiones de Python anteriores a la 3.5, Visual Studio también muestra las sugerencias de tipo que proporcione a través de *archivos de código auxiliar* de Typeshed (*.pyi*). Puede usar archivos de código auxiliar siempre que no quiera incluir sugerencias de tipo directamente en el código o cuando quiera crear sugerencias de tipo para una biblioteca que no los usa directamente. Para obtener más información, vea [Create Stubs for Python Modules](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) (Creación de códigos auxiliares para los módulos de Python) en la wiki de proyecto de MyPy.
>
> Visual Studio incluye un conjunto de agrupaciones de archivos Typeshed para Python 2 y 3, por lo que no se necesitan otras descargas. Sin embargo, si quiere usar un conjunto de archivos distinto, puede especificar la ruta en las opciones **Herramientas** > **Opciones** > **Python** > **Servidor de lenguaje**. Consulte [Opciones: servidor de lenguaje](python-support-options-and-settings-in-visual-studio.md#language-server-options).
>
> Actualmente Visual Studio no admite sugerencias de tipo en los comentarios.
::: moniker-end

### <a name="signature-help"></a>Ayuda para la firma

Al escribir código que llama a una función, la ayuda para la firma aparece cuando se escribe el `(` de apertura y muestra la información de documentación y parámetros disponible. También puede hacer que aparezca con **Ctrl**+**Mayús**+**Espacio** dentro de una llamada de función. La información que se muestra depende de las cadenas de documentación del código fuente de la función, pero incluye los valores predeterminados.

![Ayuda para la firma en el editor de Visual Studio](media/code-editing-signature-help.png)

> [!Tip]
> Para deshabilitar la ayuda para la firma, vaya a **Herramientas** > **Opciones** > **Editor de texto** > **Python** > **General** y desactive **Finalización de instrucciones** > **Información de parámetros**.

### <a name="quick-info"></a>Información rápida

Al pasar el puntero del mouse sobre un identificador aparece una sugerencia de información rápida. Según el identificador, la información rápida puede mostrar los valores o tipos posibles, cualquier documentación disponible, los tipos de devolución y las ubicaciones de definición:

![Información rápida en el editor de Visual Studio](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Coloración de código

La coloración de código utiliza información desde análisis de código a variables de colores, instrucciones y otras partes del código. Por ejemplo, las variables que hacen referencia a clases o módulos pueden mostrarse en un color diferente que las funciones u otros valores, y los nombres de los parámetros aparecen en un color diferente que las variables locales o globales. (De manera predeterminada, las funciones no se muestran en negrita):

![Colores de código y sintaxis en el editor de Visual Studio](media/code-editing-code-coloring.png)

Para personalizar los colores, vaya a **Herramientas** > **Opciones** > **Entorno** > **Fuentes y colores** y modifique las entradas de **Python** en la lista **Mostrar elementos**:

![Opciones de fuentes y colores en Visual Studio](media/code-editing-customize-colors.png)

> [!Tip]
> Para deshabilitar la coloración de código, vaya a **Herramientas** > **Opciones** > **Editor de texto** > **Python** > **Opciones avanzadas** y desactive **Otras opciones** > **Color names based on type** (Nombres de colores basados en tipo). Vea [Opciones: Otras opciones](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Fragmentos de código

Los fragmentos de código son pedazos de código que se pueden insertar en los archivos mediante un método abreviado de teclado y la tecla **Tab** o bien con los comandos **Editar** > **IntelliSense** > **Insertar fragmento de código** y **Delimitar con**, seleccionando **Python** y luego el fragmento deseado.

Por ejemplo, `class` es un acceso directo para un fragmento de código que inserta una definición de clase. El fragmento de código aparece en la lista de finalización automática cuando se escribe `class`:

![Acceso directo del fragmento de código para la clase](media/code-editing-code-snippet-class.png)

Al presionar **Tab**, se genera el resto de la clase. Puede escribir sobre el nombre y la lista de bases, moviéndose entre los campos resaltados con **Tab**, y luego presionar **Entrar** para empezar a escribir el cuerpo.

![Resaltado en las áreas de un fragmento de código para completar](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Comandos de menú

Cuando use el comando de menú **Editar** > **IntelliSense** > **Insertar fragmento de código**, seleccione **Python** primero y luego un fragmento de código:

![Selección de un fragmento de código mediante el comando Insertar fragmento de código](media/code-editing-code-snippet-insert.png)

Del mismo modo, el comando **Editar** > **IntelliSense** > **Delimitar con**, coloca la selección actual en el editor de texto dentro de un elemento estructural elegido. Por ejemplo, suponga que tiene un poco de código similar al siguiente:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Al seleccionar este código y elegir el comando **Delimitar con** aparece una lista de fragmentos de código disponibles. Al elegir **def** en la lista se coloca el código seleccionado dentro de una definición de función, y puede utilizar la tecla **Tab** para desplazarse entre los argumentos y el nombre de la función resaltados:

![Uso del comando Delimitar con para fragmentos de código](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Examen de los fragmentos de código disponibles

Puede ver los fragmentos de código disponibles en el **Administrador de fragmentos de código**, que se abre con el comando de menú **Herramientas** > **Administrador de fragmentos de código**, y seleccionando **Python** como lenguaje:

![Administrador de fragmentos de código en Visual Studio](media/code-editing-code-snippets-manager.png)

Para crear fragmentos de código propios, vea [Tutorial: Creación de un fragmento de código](../ide/walkthrough-creating-a-code-snippet.md).

Si escribe un fragmento de código excelente que le gustaría compartir, no dude en publicarlo de manera resumida y [hacérnoslo saber](https://github.com/Microsoft/PTVS/issues). Es posible que podamos incluirlo en una futura versión de Visual Studio.

## <a name="navigate-your-code"></a>Navegar por el código

La compatibilidad con Python en Visual Studio proporciona varios medios para desplazarse rápidamente dentro del código, incluidas las bibliotecas para las que hay código fuente disponible: la [barra de navegación](#navigation-bar), [**Ir a definición**](#go-to-definition), [**Navegar a**](#navigate-to) y [**Buscar todas las referencias**](#find-all-references). También se puede usar el [**Examinador de objetos**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser) de Visual Studio.

### <a name="navigation-bar"></a>Barra de navegación

La barra de navegación se muestra en la parte superior de cada ventana del editor e incluye una lista de dos niveles de definiciones. La lista desplegable de la izquierda contiene la clase de nivel superior y las definiciones de funciones en el archivo actual; la lista desplegable de la derecha muestra una lista de definiciones dentro del ámbito que se muestra en la izquierda. A medida que recorra el editor, las listas se actualizan para mostrar el contexto actual y, además, puede seleccionar una entrada de estas listas para ir directamente a ella.

![Barra de navegación en el editor de Visual Studio](media/code-editing-navigation-bar.png)

> [!Tip]
> Para ocultar la barra de navegación, vaya a **Herramientas** > **Opciones** > **Editor de texto** > **Python** > **General** y desactive **Configuración** > **Barra de navegación**.

### <a name="go-to-definition"></a>Ir a definición

**Ir a definición** rápidamente salta del uso de un identificador (por ejemplo, un nombre de función, clase o variable) al código fuente donde se define. Se invoca haciendo clic con el botón derecho en un identificador y seleccionando **Ir a definición**, o colocando el símbolo de intercalación en el identificador y presionando **F12**. Funciona en todo su código y las bibliotecas externas siempre que el código fuente esté disponible. Si el código fuente de la biblioteca no está disponible, **Ir a definición** salta a la correspondiente instrucción `import` para una referencia de módulo, o mostrará un error.

![Comando Ir a definición en Visual Studio](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Navegar a

El comando **Editar** > **Navegar a** (**Ctrl**+**,**) muestra un cuadro de búsqueda en el editor donde puede escribir cualquier cadena y consultar las posibles coincidencias en el código que define una función, una clase o una variable que contiene la cadena. Esta característica proporciona una función similar a **Ir a definición**, pero sin tener que buscar un uso de un identificador.

Haga doble clic en cualquier nombre, o seleccione con las teclas de dirección y **Entrar**, para navegar a la definición de ese identificador.

![Comando Navegar a en Visual Studio](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Buscar todas las referencias

**Buscar todas las referencias** es una forma útil de detectar aquellas instancias en las que un identificador determinado se define y utiliza, incluidas las importaciones y las asignaciones. Se invoca haciendo clic con el botón derecho en un identificador y seleccionando **Buscar todas las referencias**, o colocando el símbolo de intercalación en el identificador y presionando **Mayús**+**F12**. Al hacer doble clic en un elemento de la lista se navega hasta su ubicación.

![Resultados de Buscar todas las referencias](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Vea también

- [Formato](formatting-python-code.md)
- [Refactorización](refactoring-python-code.md)
- [Utilizar un linter](linting-python-code.md)
