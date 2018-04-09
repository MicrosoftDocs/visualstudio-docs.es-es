---
title: Edición del código de Python | Microsoft Docs
description: La edición de Python en Visual Studio proporciona IntelliSense, fragmentos de código y características de navegación, además de formato, linting y refactorización.
ms.custom: ''
ms.date: 03/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 8e9d5a3b18e7193786ea2b6d0bf2dfb038828e78
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2018
---
# <a name="editing-python-code"></a>Edición de código de Python

Los desarrolladores invierten mucho tiempo en el editor de código, por lo que la [compatibilidad de Python en Visual Studio](installing-python-support-in-visual-studio.md) proporciona funciones para ayudarle a ser más productivo. Las características incluyen resalte de sintaxis de IntelliSense, finalización automática, ayuda para la firma, invalidaciones de método, búsqueda y navegación.

El editor también está integrado en la ventana interactiva de Visual Studio, lo que hace que sea sencillo intercambiar código entre los dos. Vea [Tutorial Step 3: Using the interactive REPL window](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) (Paso 3 del tutorial: Usar la ventana interactiva de REPL) y [Uso de la ventana interactiva - Comando Enviar código a Interactive](python-interactive-repl-in-visual-studio.md#send-code-to-interactive-command) para obtener información detallada.

|   |   |
|---|---|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | [Eche un vistazo a un vídeo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Editing-Python-Code-r2iQH5LWE_4605918567) para ver una demostración de la edición de código Python (2 minutos 30 segundos).|

Para obtener documentación general sobre la edición de código en Visual Studio, consulte [Escribir código en el editor de código y texto](../ide/writing-code-in-the-code-and-text-editor.md). Consulte también [Esquematización](../ide/outlining.md), que le ayudará a mantenerse centrado en determinadas secciones del código.

También puede usar el Examinador de objetos de Visual Studio (**Ver > Otras ventanas > Examinador de objetos** o Ctrl+W,J) para inspeccionar las clases de Python definidas en cada módulo y las funciones definidas en esas clases.

## <a name="intellisense"></a>IntelliSense

IntelliSense ofrece [finalizaciones](#completions), [ayuda para la firma](#signature-help), [información rápida](#quick-info) y [coloración de código](#code-coloring).

Para mejorar el rendimiento, IntelliSense en **Visual Studio 2017, versión 15.5** y anteriores, depende de la base de datos de finalizaciones que se genera para cada entorno de Python en el proyecto. Si agrega, quita o actualiza paquetes las bases de datos puede que necesiten actualizarse. El estado de la base de datos se muestra en la ventana **Entornos de Python** (un elemento relacionado del Explorador de soluciones) en la pestaña **IntelliSense** (consulte [Referencia de pestañas de la ventana Entorno de Python](python-environments-window-tab-reference.md#intellisense-tab)).

**Visual Studio 2017, versión 15.6** y posteriores utiliza un medio diferente para proporcionar finalizaciones de IntelliSense que no dependen de la base de datos.

### <a name="completions"></a>Finalizaciones

Las finalizaciones aparecen como instrucciones, identificadores y otras palabras que pueden especificarse adecuadamente en la ubicación actual en el editor. Lo que se muestra en la lista se basa en contexto y se filtra para omitir las opciones incorrectas o molestas. Las finalizaciones a menudo se desencadenan escribiendo instrucciones diferentes (como `import`) y operadores (incluido el punto), pero puede hacer que aparezcan en cualquier momento escribiendo Ctrl-J, Espacio.

![Finalizaciones de miembros](media/code-editing-completions-simple.png)

Cuando se abre una lista de finalizaciones, puede buscar la finalización que desee con las teclas de dirección, el mouse o bien escribiendo algo más. A medida que escriba más letras, la lista se seguirá filtrando para mostrar las finalizaciones probables. También puede usar accesos directos como:

- Escribir letras que no están al principio del nombre, como "parse" para buscar "argparse"
- Escribir solo las letras que se encuentran al principio de palabras, como "abc" para buscar 'AbstractBaseClass' o "air" para buscar "as_integer_ratio"
- Omitir letras, como "b64" para buscar "base64"

Algunos ejemplos:

![Finalizaciones de miembros con filtrado](media/code-editing-completion-filtering.png)

Las finalizaciones de miembros aparecen automáticamente al escribir un punto después de una variable o un valor, junto con los métodos y atributos de los tipos posibles. Si una variable puede ser de más de un tipo, la lista incluye todas las posibilidades de todos los tipos, con información adicional para indicar qué tipos admite cada finalización. Cuando una finalización es compatible con todos los tipos posibles, se muestra sin la anotación.

![Finalización de miembros en varios tipos](media/code-editing-completion-types.png)

De manera predeterminada, no se muestran los miembros "dunder" (miembros que comienzan y terminan con un doble carácter de subrayado). En general, no se debe acceder a dichos miembros directamente. En cambio, si necesita uno, al escribir el doble carácter de subrayado inicial se agregan estas finalizaciones a la lista:

![Finalización de miembros privados](media/code-editing-completion-dunder.png)

Las instrucciones `import` y `from ... import` muestran una lista de módulos que pueden importarse. Con `from ... import`, la lista incluye miembros que pueden importarse desde el módulo especificado.

![Finalización de importaciones](media/code-editing-completion-import.png)

Las instrucciones `raise` y `except` muestran listas de clases que probablemente sean tipos de error. La lista puede no incluir todas las excepciones definidas por el usuario, pero le ayudan a encontrar rápidamente las excepciones integradas adecuadas:

![Finalización de excepciones](media/code-editing-completion-exception.png)

Al escribir @ se inicia un decorador y se muestran todos los posibles decoradores. Muchos de estos elementos no se pueden usar como decoradores; consulte la documentación de la biblioteca para determinar cuál se va a usar.

![Finalización de decoradores](media/code-editing-completion-decorator.png)

> [!Tip]
> Puede configurar el comportamiento de estas finalizaciones en **Herramientas > Opciones > Editor de texto > Python > Opciones avanzadas**. De estas opciones, **Filter list based on search string** (Filtrar lista en función de la cadena de búsqueda) aplica el filtrado de sugerencias de finalización mientras se escribe (activo de manera predeterminada) y **Member completion displays intersection of members** (La finalización de miembros muestra la intersección de miembros) muestra solo las finalizaciones que son compatibles con todos los posibles tipos (desactivado de manera predeterminada). Vea [Opciones: resultados de finalización](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="signature-help"></a>Ayuda para la firma

Al escribir código que llama a una función, la ayuda para la firma aparece cuando se escribe el `(` de apertura y muestra la información de documentación y parámetros disponible. También puede hacer que aparezca con Ctrl+Mayús+Espacio dentro de una llamada de función. La información que se muestra depende de las cadenas de documentación del código fuente de la función, pero incluye los valores predeterminados.

![Ayuda para la firma](media/code-editing-signature-help.png)

> [!Tip]
> Para deshabilitar la ayuda para la firma, vaya a **Herramientas > Opciones > Editor de texto> General** y desactive **Finalización de instrucciones > Información de parámetros**.

### <a name="quick-info"></a>Información rápida

Al pasar el puntero del mouse sobre un identificador aparece una sugerencia de información rápida. Según el identificador, la información rápida puede mostrar los valores o tipos posibles, cualquier documentación disponible, los tipos de devolución y las ubicaciones de definición:

![Información rápida](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Coloración de código

La coloración de código utiliza información desde análisis de código a variables de colores, instrucciones y otras partes del código. Por ejemplo, las variables que hacen referencia a clases o módulos pueden mostrarse en un color diferente que las funciones u otros valores, y los nombres de los parámetros aparecen en un color diferente que las variables locales o globales. (De manera predeterminada, las funciones no se muestran en negrita):

![Coloración de código](media/code-editing-code-coloring.png)

Para personalizar los colores, vaya a **Herramientas > Opciones > Entorno > Fuentes y colores** y modifique las entradas de Python en la lista **Mostrar elementos**:

![Opciones de fuentes y colores](media/code-editing-customize-colors.png)

> [!Tip]
> Para deshabilitar la coloración de código, vaya a **Herramientas > Opciones > Editor de texto > Python > Opciones avanzadas** y desactive **Otras opciones > Color names based on type** (Nombres de colores basados en tipo). Vea [Opciones: otras opciones](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Fragmentos de código

Los fragmentos de código son pedazos de código que se pueden insertar en los archivos mediante un acceso directo y la tecla Tab o bien con los comandos **Editar > IntelliSense > Insertar fragmento de código** y **Delimitar con**, seleccionando **Python** y luego el fragmento deseado.

Por ejemplo, `class` es un acceso directo para un fragmento de código que inserta una definición de clase. El fragmento de código aparece en la lista de finalización automática cuando se escribe `class`:

![Acceso directo del fragmento de código para la clase](media/code-editing-code-snippet-class.png)

Al presionar Tab, se genera el resto de la clase. Puede escribir sobre el nombre y la lista de bases, moviéndose entre los campos resaltados con Tab, y luego presionar Entrar para empezar a escribir el cuerpo.

![Resaltado en las áreas de un fragmento de código para completar](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Comandos de menú

Cuando use el comando de menú **Editar > IntelliSense > Insertar fragmento de código**, seleccione "Python" primero y luego un fragmento de código:

![Selección de un fragmento de código mediante el comando Insertar fragmento de código](media/code-editing-code-snippet-insert.png)

Del mismo modo, el comando **Editar > IntelliSense > Delimitar con**, coloca la selección actual en el editor de texto dentro de un elemento estructural elegido. Por ejemplo, suponga que tiene un poco de código similar al siguiente:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Al seleccionar este código y elegir el comando **Delimitar con** aparece una lista de fragmentos de código disponibles. Al elegir `def` en la lista se coloca el código seleccionado dentro de una definición de función, y puede utilizar la tecla Tab para desplazarse entre los argumentos y el nombre de la función resaltados:

![Uso del comando Delimitar con para fragmentos de código](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Examen de los fragmentos de código disponibles

Puede ver los fragmentos de código disponibles en el Administrador de fragmentos de código, que se abre con el comando de menús **Herramientas > Administrador de fragmentos de código**, y seleccionando **Python** como lenguaje:

![Administrador de fragmentos de código](media/code-editing-code-snippets-manager.png)

Para crear sus propios fragmentos de código, consulte [Tutorial: Crear un fragmento de código](../ide/walkthrough-creating-a-code-snippet.md).

Si escribe un fragmento de código excelente que le gustaría compartir, no dude en publicarlo de manera resumida y [hacérnoslo saber](https://github.com/Microsoft/PTVS/issues). Es posible que podamos incluirlo en una futura versión de Visual Studio.

## <a name="navigating-your-code"></a>Navegación por el código

La compatibilidad con Python en Visual Studio proporciona varios medios para desplazarse rápidamente dentro del código, incluidas las bibliotecas para las que hay código fuente disponible: la [barra de navegación](#navigation-bar), [Ir a definición](#go-to-definition), [Navegar a](#navigate-to) y [Buscar todas las referencias](#find-all-references). También se puede usar el [Examinador de objetos](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser) de Visual Studio.

### <a name="navigation-bar"></a>Barra de navegación

La barra de navegación se muestra en la parte superior de cada ventana del editor e incluye una lista de dos niveles de definiciones. La lista desplegable de la izquierda contiene la clase de nivel superior y las definiciones de funciones en el archivo actual; la lista desplegable de la derecha muestra una lista de definiciones dentro del ámbito que se muestra en la izquierda. A medida que recorra el editor, las listas se actualizan para mostrar el contexto actual y, además, puede seleccionar una entrada de estas listas para ir directamente a ella.

![Barra de navegación](media/code-editing-navigation-bar.png)

> [!Tip]
> Para ocultar la barra de navegación, vaya a **Herramientas > Opciones > Editor de texto > Python > General** y desactive **Configuración > Barra de navegación**.

### <a name="go-to-definition"></a>Ir a definición

**Ir a definición** rápidamente salta del uso de un identificador (por ejemplo, un nombre de función, clase o variable) al código fuente donde se define. Se invoca haciendo clic derecho en un identificador y seleccionando **Ir a definición**, o colocando el símbolo de intercalación en el identificador y presionando F12. Funciona en todo su código y las bibliotecas externas siempre que el código fuente esté disponible. Si el código fuente de la biblioteca no está disponible, **Ir a definición** salta a la correspondiente instrucción `import` para una referencia de módulo, o mostrará un error.

![Ir a definición](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Navegar a

El comando **Editar > Navegar a...**  (Ctrl-coma) muestra un cuadro de búsqueda en el editor donde puede escribir cualquier cadena y consultar las posibles coincidencias en el código que define una función, una clase o una variable que contiene la cadena. Esta característica proporciona una función similar a **Ir a definición**, pero sin tener que buscar un uso de un identificador.

Haga doble clic en cualquier nombre, o seleccione con teclas de dirección y Entrar, para navegar a la definición de ese identificador.

![Navegar a](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Buscar todas las referencias

**Buscar todas las referencias** es una forma útil de detectar aquellas instancias en las que un identificador determinado se define y utiliza, incluidas las importaciones y las asignaciones. Se invoca haciendo clic derecho en un identificador y seleccionando **Buscar todas las referencias**, o colocando el símbolo de intercalación en el identificador y presionando Mayús+F12. Al hacer doble clic en un elemento de la lista se navega hasta su ubicación.

![Resultados de Buscar todas las referencias](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Vea también

- [Formato](formatting-python-code.md)
- [Refactorización](refactoring-python-code.md)
- [Detección de errores](linting-python-code.md)