---
title: Introducción a la edición para desarrolladores de JavaScript
description: En esta introducción al editor de código de Visual Studio se describen algunas de las formas en que Visual Studio hace que escribir y comprender el código JavaScript (así como desplazarse por él) sea más fácil.
ms.date: 12/13/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 111100038817d16d4655271f648aeb076bf1e9af
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58856637"
---
# <a name="learn-to-use-the-code-editor"></a>Aprender a usar el editor de código

En esta breve introducción al editor de código de Visual Studio veremos algunas de las formas en que Visual Studio hace que escribir y comprender el código (así como desplazarse por él) sea más fácil.

> [!TIP]
> Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/) para instalarlo de forma gratuita. Según la forma en que vaya a desarrollar la aplicación, es posible que tenga que instalar la **carga de trabajo de desarrollo Node.js** con Visual Studio.

En este artículo se da por hecho que ya está familiarizado con el desarrollo de JavaScript. Si no lo está, le aconsejamos que antes eche un vistazo a un tutorial del tipo [Crear una aplicación Node.js y Express](../javascript/tutorial-nodejs.md).

## <a name="add-a-new-project-file"></a>Agregar un nuevo archivo de proyecto

Puede usar el IDE para agregar nuevos archivos al proyecto.

1. Con el proyecto abierto en Visual Studio, haga doble clic en una carpeta o en el nodo de proyecto en el Explorador de soluciones (panel derecho) y elija **Agregar** > **Nuevo elemento**.

1. En el cuadro de diálogo **Nuevo archivo**, en la categoría **General**, elija el tipo de archivo que quiera agregar (como, por ejemplo, **Archivo JavaScript**) y, después, elija **Abrir**.

    El nuevo archivo se agrega al proyecto y se abre en el editor.

## <a name="use-intellisense-to-complete-words"></a>Usar IntelliSense para completar palabras

IntelliSense es un recurso impagable cuando se escribe código. Así, puede mostrar información sobre los miembros disponibles de un tipo o detalles de los parámetros para las distintas sobrecargas de un método. En el siguiente código, cuando se escribe `Router()`, se muestran los tipos de argumento que se pueden pasar. Esto se denomina ayuda de signatura.

![Usar IntelliSense](../javascript/media/write-code-signature-checking.png)

IntelliSense puede servir también para completar una palabra después de escribir una serie de caracteres y, así, eliminar cualquier tipo de ambigüedad. Si coloca el cursor después de la cadena `data` en el siguiente código y escribe `get`, IntelliSense mostrará las funciones definidas anteriormente en el código o que haya definidas en una biblioteca de terceros que esté agregada al proyecto.

![Usar IntelliSense](../javascript/media/write-code-intellisense.png)

IntelliSense también puede mostrar información sobre los tipos cuando se mantiene el puntero sobre elementos de programación.

Para proporcionar información de IntelliSense, el servicio de lenguaje puede usar archivos *d.ts* de TypeScript y comentarios de JSDoc. En las bibliotecas de JavaScript más comunes, los archivos *d.ts* se obtienen automáticamente. Para más información sobre cómo se obtiene la información de IntelliSense, vea [IntelliSense para JavaScript](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json).

## <a name="check-syntax"></a>Comprobar la sintaxis

El servicio de lenguaje usa ESLint para proporcionar funciones de comprobación de sintaxis y detección de errores. Si necesita establecer las opciones de comprobación de sintaxis en el editor, seleccione **Herramientas** > **Opciones** > **JavaScript/TypeScript** > **D**. Las opciones de detección de errores apuntan al archivo de configuración global de ESLint.

En el siguiente código vemos un resaltado en verde de la sintaxis (subrayado ondulado verde) en la expresión. Mueva el puntero sobre el resaltado de sintaxis.

![Ver error de sintaxis](../javascript/media/write-code-syntax-checking.png)

La última línea de este mensaje indica que el servicio de lenguaje esperaba una coma (`,`). El subrayado ondulado verde denota una advertencia, mientras que el rojo señala un error.

En el panel inferior puede hacer clic en la pestaña **Lista de errores** para ver la advertencia y una descripción junto con el nombre de archivo y número de línea.

![Ver lista de errores](../javascript/media/write-code-error-list.png)

Puede corregir el código insertando la coma (`,`) antes de `"data"`.

## <a name="comment-out-code"></a>Marcar código como comentario

La barra de herramientas, que es la fila de botones debajo de la barra de menús de Visual Studio, puede ayudar a mejorar la productividad mientras se codifica. Por ejemplo, puede alternar el modo de finalización de IntelliSense ([IntelliSense](../ide/using-intellisense.md) es una ayuda de codificación que muestra una lista de métodos coincidentes, entre otras cosas), aumentar o reducir una sangría de línea o comentar el código que no quiere compilar. En esta sección se comenta algún código.

Seleccione una o varias líneas de código en el editor y elija **Marcar como comentario las líneas seleccionadas**![Botón Marcar como comentario las líneas seleccionadas](../javascript/media/write-code-comment-out.png) en la barra de herramientas. Si prefiere usar el teclado, presione **Ctrl**+**K**, **Ctrl**+**C**.

Los caracteres de comentario de JavaScript `//` se agregan al principio de cada línea seleccionada para marcar el código como comentario.

## <a name="collapse-code-blocks"></a>Contraer bloques de código

Si necesita despejar la vista de algunos fragmentos de código, estos se puede contraer. Seleccione el cuadradito gris con el signo menos que se ve en el margen de la primera línea de una función. Si prefiere usar el teclado, coloque el cursor en cualquier lugar en el código del constructor y presione **Ctrl**+**M**, **Ctrl**+**M**.

![Botón para contraer de esquematización](../javascript/media/write-code-collapse-code.png)

El bloque de código se contrae para mostrar únicamente la primera línea seguida de un botón de puntos suspensivos (`...`). Para expandir el bloque de código de nuevo, haga clic en el mismo cuadro gris (que ahora tiene un signo más) o presione **CTRL**+**M**, **CTRL**+**M** otra vez. Esta característica se denomina [Esquematización](../ide/outlining.md) y es especialmente útil cuando se contraen funciones muy largas o clases enteras.

## <a name="view-definitions"></a>Ver definiciones

Gracias al editor de Visual Studio, es muy sencillo inspeccionar la definición de un tipo, función, etc. Una forma consiste en ir al archivo que contiene la definición, por ejemplo, seleccionando **Ir a definición** en cualquier lugar donde se haga referencia al elemento de programación. Otra más rápida aún (y que no desplaza el enfoque del archivo en el que está trabajando) es usar [Ver la definición](../ide/go-to-and-peek-definition.md#peek-definition). Vamos a ver la definición del método `render` en el siguiente ejemplo.

Haga clic con el botón derecho en `render` y elija **Ver la definición** en el menú de contenido. O bien, presione **Alt**+**F12**.

   Se abrirá una ventana emergente con la definición del método `render`. Puede desplazarse dentro de la ventana emergente o incluso ver la definición de otro tipo desde el código inspeccionado.

   ![Ventana Ver la definición](../javascript/media/write-code-peek-definition.png)

Para cerrar la ventana de definición inspeccionada, seleccione el pequeño cuadro con una "x" en la esquina superior derecha de la ventana emergente.

## <a name="use-code-snippets"></a>Uso de fragmentos de código

Visual Studio proporciona *fragmentos de código* muy prácticos que pueden servir para generar bloques de código de uso común de forma rápida y sencilla. Existen [fragmentos de código](../ide/code-snippets.md) disponibles para diferentes lenguajes de programación, JavaScript incluido. Vamos a agregar un bucle `for` al archivo de código.

Coloque el cursor donde quiera insertar el fragmento de código, haga clic con el botón derecho y seleccione **Fragmento de código** > **Insertar fragmento de código**.

![Fragmento de código en Visual Studio](../javascript/media/write-code-insert-snippet.png)

Se abre un cuadro **Insertar fragmento de código** en el editor. Elija **General** y, a continuación, haga doble clic en el elemento **for** de la lista.

![Fragmento de código de un bucle for en Visual Studio](../javascript/media/write-code-insert-snippet-for-loop.png)

Esto hace que el fragmento de código del bucle `for` se agregue al código:

```javascript
for (var i = 0; i < length; i++) {

}
```

Para ver los fragmentos de código disponibles para el lenguaje, seleccione **Editar** > **IntelliSense** > **Insertar fragmento de código** y luego elija la carpeta del lenguaje.

## <a name="see-also"></a>Vea también

- [Fragmentos de código](../ide/code-snippets.md)
- [Navegación en el código](../ide/navigating-code.md)
- [esquematizar](../ide/outlining.md)
- [Ir a definición y Ver la definición](../ide/go-to-and-peek-definition.md)
- [Refactorización](../ide/refactoring-in-visual-studio.md)
- [Usar IntelliSense](../ide/using-intellisense.md)
