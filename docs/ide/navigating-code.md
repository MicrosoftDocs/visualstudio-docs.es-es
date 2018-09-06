---
title: Comandos de navegación por el código
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code editor, navigation
- code editor, go to
- code editor, go to definition
- code editor, go to line
- code editor, peek definition
- code editor, navigation bar
- go to definition
- peek definition
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb711763e96cf6959a71b002f09cefa1ced44734
ms.sourcegitcommit: 4c60bcfa2281bcc1a28def6a8e02433d2c905be6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42626944"
---
# <a name="navigate-code"></a>Navegación en el código

Visual Studio ofrece numerosas formas de navegar por el código en el editor. En este tema se resumen las distintas maneras en las que se puede navegar por el código y se proporcionan vínculos a temas que incluyen más información.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Comandos Navegar hacia atrás y Navegar hacia delante

Puede usar los botones **Navegar hacia atrás** (**Ctrl**+**-**) y **Navegar hacia delante** (**Ctrl**+**Mayús**+**-**) de la barra de herramientas para mover el punto de inserción a ubicaciones anteriores o para volver a una ubicación más reciente desde una ubicación anterior. Estos botones retienen las últimas 20 ubicaciones del punto de inserción. Estos comandos también están disponibles en el menú **Vista**, en **Navegar hacia atrás** y **Navegar hacia delante**.

![Botones de navegación hacia adelante y atrás](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Barra de navegación

Puede usar la **barra de navegación** (los cuadros desplegables situados en la parte superior de la ventana de código) para navegar por el código de un código base. Puede elegir un tipo o un miembro para ir directamente a él. La barra de navegación aparece cuando se edita código en un código base de Visual Basic, C# o C++. En una clase parcial, los miembros definidos fuera del archivo de código actual pueden estar deshabilitados (se muestran en gris).

 ![Barra de navegación por el código](../ide/media/vside_navigation_bar.png)

Puede navegar por los cuadros desplegables como se indica a continuación:

- Para navegar a otro proyecto al que pertenece el archivo actual, selecciónelo en la lista desplegable izquierda.

- Para navegar a una clase o tipo, selecciónelo en la lista desplegable del centro.

- Para navegar directamente a un procedimiento u otro miembro de una clase, selecciónelo en la lista desplegable derecha.

- Para cambiar el foco de la ventana de código a la barra de navegación, presione la combinación de teclas de método abreviado **Ctrl**+**F2**.

- Para cambiar el foco de un cuadro a otro en la barra de navegación, presione la tecla **TAB**.

- Para seleccionar el elemento de la barra de navegación que tenga el foco y volver a la ventana del código, presione la tecla **ENTRAR**.

- Para devolver el foco de la barra de navegación al código sin necesidad de seleccionar nada, presione la tecla **Esc**.

Para ocultar la barra de navegación, cambie la opción **Barra de navegación** en la configuración de **Editor de texto Todos los lenguajes** (**Herramientas** > **Opciones** > **Editor de texto** > **Todos los lenguajes**), o bien puede cambiar la configuración de lenguajes individuales.

## <a name="find-all-references"></a>Buscar todas las referencias

Busca todas las referencias al elemento seleccionado en la solución. Puede usar esto para comprobar los posibles efectos secundarios de una refactorización grande o para comprobar el código no alcanzado. Presione **F8** para desplazarse entre los resultados. Para obtener más información, vea [Búsqueda de referencias en el código](finding-references.md).

Entrada        | Función
------------ | ---
**Teclado** | Coloque el cursor de texto en algún lugar del nombre de tipo y presione **Mayús**+**F12**.
**Mouse**    | Seleccione **Buscar todas las referencias** en el menú contextual.

## <a name="reference-highlighting"></a>Resaltado de referencia

Al hacer clic en un símbolo en el código fuente, se resaltan todas las instancias de ese símbolo en el documento. Los símbolos resaltados pueden incluir declaraciones y referencias, así como muchos otros símbolos que pueda devolver la función **Buscar todas las referencias** . Estos incluyen los nombres de clases, objetos, variables, métodos y propiedades. En el código de Visual Basic, también se resaltan las palabras clave de muchas estructuras de control. Para desplazarse al siguiente símbolo resaltado o al anterior, presione **Ctrl**+**Mayús**+**Flecha abajo** o **Ctrl**+**Mayús**+**Flecha arriba**. Puede cambiar el color de resaltado en **Herramientas** > **Opciones** > **Entorno** > **Fuentes y colores** > **Referencia resaltada**.

## <a name="go-to-commands"></a>Comandos Ir a

Ir a tiene los comandos siguientes, que están disponibles en el menú **Editar** en **Ir a**:

- **Ir a la línea** (**Ctrl**+**G**): moverse al número de línea especificado en el documento activo.

- **Ir a todo** (**Ctrl**+**T** o **Ctrl**+**,**): moverse a la línea, tipo, archivo, miembro o símbolo especificados.

- **Ir al archivo** (**Ctrl**+**1**, **Ctrl**+**F**): moverse al archivo especificado en la solución.

- **Ir al archivo reciente** (**Ctrl**+**1**, **Ctrl**+**R**): moverse al archivo especificado que visitó recientemente en la solución (novedad de Visual Studio 2017 versión 15.8).

- **Ir al tipo** (**Ctrl**+**1**, **Ctrl**+**T**): moverse al tipo especificado en la solución.

- **Ir al miembro** (**Ctrl**+**1**, **Ctrl**+**M**): moverse al miembro especificado en la solución.

- **Ir al símbolo** (**Ctrl**+**1**, **Ctrl**+**S**): moverse al símbolo especificado en la solución.

En Visual Studio 2017 versión 15.8 y posteriores, también están disponibles los siguientes comandos de navegación de **Ir a**:

- **Ir al siguiente problema del archivo** (**Alt**+**Av Pág**) e **Ir al problema anterior del archivo** (**Alt**+**Re Pág**)

- **Ir a la última ubicación de edición** (**Ctrl**+**Mayús**+**Retroceso**)

Obtenga más información relacionada con estos comandos en el tema sobre cómo [buscar código mediante comandos Ir a](../ide/go-to.md).

## <a name="go-to-definition"></a>Ir a definición

Ir a definición le lleva a la definición del elemento seleccionado. Vea [Ir a definición y Ver la definición](../ide/go-to-and-peek-definition.md) para obtener más información.

Entrada        | Función
------------ | ---
**Teclado** | Coloque el cursor de texto en algún lugar del nombre de tipo y presione **F12**
**Mouse**    | Haga clic con el botón derecho en el nombre de tipo y seleccione **Ir a definición**, o bien presione **CTRL** y haga clic en el nombre de tipo (nuevo en Visual Studio 2017 versión 15.4).

## <a name="peek-definition"></a>Definición de Peek

La opción Ver la definición muestra la definición del elemento seleccionado en una ventana sin necesidad de salir de la ubicación actual en el editor de código. Para obtener más información, vea [Cómo: Ver y editar código mediante Ver la definición](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) e [Ir a definición y Ver la definición](../ide/go-to-and-peek-definition.md).

Entrada        | Función
------------ | ---
**Teclado** | Coloque el cursor de texto en algún lugar del nombre de tipo y presione **Alt**+**F12**.
**Mouse**    | Haga clic con el botón derecho en el nombre de tipo y seleccione **Ver la definición**, o bien presione **CTRL** y haga clic en el nombre de tipo (si tiene activada la opción **Abrir definición en vista de inspección**).

## <a name="go-to-implementation"></a>Ir a implementación

Mediante el uso de Ir a implementación, puede navegar desde una clase base o escribir sus implementaciones. Si existen varias implementaciones, las verá en la ventana **Resultados de la búsqueda de símbolos**:

Entrada        | Función
------------ | ---
**Teclado** | Coloque el cursor de texto en algún lugar del nombre de tipo y presione **Ctrl**+**F12**.
**Mouse**    | Haga clic con el botón derecho en el nombre de tipo y seleccione **Ir a implementación**

## <a name="call-hierarchy"></a>Jerarquía de llamadas

Puede ver las llamadas a y desde un método en la [ventana Jerarquía de llamadas](../ide/reference/call-hierarchy.md):

Entrada        | Función
------------ | ---
**Teclado** | Coloque el cursor de texto en algún lugar del nombre de tipo y presione **Ctrl**+**K**, **Ctrl**+**T**.
**Mouse**    | Haga clic con el botón derecho en el nombre del miembro y seleccione **Ver jerarquía de llamadas**.

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Comandos Método siguiente y Método anterior (Visual Basic)

En los archivos de código de Visual Basic, use estos comandos para mover el punto de inserción hasta otros métodos. Seleccione **Editar** > **Método siguiente** o **Editar** > **Método anterior**.

## <a name="structure-visualizer"></a>Visualizador de estructura

La característica de visualizador de estructura en el editor de código muestra *líneas guía de estructura*, es decir, líneas discontinuas verticales que indican las llaves coincidentes en el código base. Esto hace que sea más fácil ver dónde empiezan y acaban los bloques lógicos.

![Visualizador de estructura](../ide/media/vside_structure_visualizer.png)

Para deshabilitar las líneas guía de estructura, vaya a **Herramientas** > **Opciones** > **Editor de texto** > **General** y desactive la casilla **Mostrar líneas guía de estructura**.

## <a name="enhanced-scroll-bar"></a>Barra de desplazamiento mejorada

Puede usar la barra de desplazamiento mejorada en una ventana de código para obtener una visión global de su código. En el modo de asignación, puede obtener vistas previas del código al mover el cursor hacia arriba y hacia abajo por la barra de desplazamiento. Para obtener más información, vea [Cómo: Hacer un seguimiento del código personalizando la barra de desplazamiento](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="codelens-information"></a>Información de CodeLens

Puede encontrar información relativa a determinado código, como los cambios realizados y quién los realizó, referencias, errores, elementos de trabajo, revisiones de código y estado de prueba unitaria cuando use CodeLens en el editor de código. CodeLens funciona como una pantalla de aviso cuando se utiliza Visual Studio Enterprise con Team Foundation Server. Vea [Buscar cambios en el código y otro historial](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Vea también

- [Características del editor de código](../ide/writing-code-in-the-code-and-text-editor.md)
- [Visualización de la jerarquía de llamadas](../ide/reference/call-hierarchy.md)
