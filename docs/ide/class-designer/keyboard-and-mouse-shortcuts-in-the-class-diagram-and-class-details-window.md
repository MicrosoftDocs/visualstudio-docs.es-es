---
title: Métodos abreviados de teclado y de mouse para el Diseñador de clases
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2541847c82a14099df703e0842e706a1e913315f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928209"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Métodos abreviados de teclado y de mouse en el Diagrama de clases y la ventana Detalles de clase

Puede usar el teclado junto con el mouse para llevar a cabo acciones de navegación en el **Diseñador de clases** y en la ventana **Detalles de clase**.

## <a name="use-the-mouse-in-class-designer"></a>Usar el mouse en el Diseñador de clases

Se admiten las siguientes acciones del mouse en los diagramas de clases:

|Combinación del mouse|Contexto|Descripción|
| - |-------------|-----------------|
|Doble clic|Shape (elementos)|Se abre el editor de código.|
|Doble clic|Conector de círculo|Expandir o contraer el círculo.|
|Doble clic|Etiqueta del conector de círculo|Invoca el comando **Mostrar interfaz**.|
|Rueda del mouse|Diagrama de clases|Desplazamiento vertical.|
|**Mayús** + rueda del mouse|Diagrama de clases|Desplazamiento horizontal.|
|**Ctrl** + rueda del mouse|Diagrama de clases|Zoom.|
|**Ctrl**+**Mayús** + clic|Diagrama de clases|Zoom.|

## <a name="use-the-mouse-in-the-class-details-window"></a>Usar el mouse en la ventana Detalles de clase

Puede usar un mouse para cambiar la apariencia de la ventana **Detalles de clase** y los datos que muestra de las siguientes maneras:

- Haga clic en cualquier celda modificable para editar su contenido. Los cambios se reflejan en todos los lugares en los que se almacenan o muestran los datos, así como en la ventana **Propiedades** y en el código fuente.

- Haga clic en cualquier celda de una fila para que la ventana **Propiedades** muestre las propiedades del elemento representado por la fila.

- Para cambiar el ancho de una columna, arrastre el límite del lado derecho del encabezado de columna hasta obtener el ancho deseado.

- Puede expandir o contraer nodos de compartimiento o de propiedad haciendo clic en los símbolos de flecha situados a la izquierda de la fila.

- La ventana **Detalles de clase** dispone de varios botones para crear nuevos miembros en la clase actual y para navegar entre los compartimientos de los miembros en la cuadrícula de la ventana **Detalles de clase**.

## <a name="use-the-keyboard-in-class-designer"></a>Usar el teclado en el Diseñador de clases

Se admiten las siguientes acciones del teclado en los diagramas de clases:

|Key|Contexto|Descripción|
|---------|-------------|-----------------|
|**Teclas de dirección**|Dentro de las formas de tipo|Navegación de tipo árbol por el contenido de la forma (permite efectuar un recorrido cíclico). Las teclas izquierda y derecha expanden y contraen el elemento actual, si es expansible, y navegan al elemento primario si no lo es (consulte los métodos de navegación por la vista de árbol para obtener información detallada sobre su comportamiento).|
|**Teclas de dirección**|Formas de nivel superior|Mover las formas en el diagrama.|
|**Mayús**+**teclas de dirección**|Dentro de las formas de tipo|Crear una selección continua compuesta por elementos de forma, como miembros, tipos anidados o compartimientos. Estos métodos abreviados no permiten el recorrido cíclico.|
|**Página principal**|Dentro de las formas de tipo|Navegar al título de la forma de nivel superior.|
|**Página principal**|Formas de nivel superior|Desplácese a la primera forma del diagrama.|
|**Fin**|Dentro de las formas de tipo|Navegar al último elemento visible dentro de la forma.|
|**Fin**|Formas de nivel superior|Navegar a la última forma del diagrama.|
|**Mayús**+**Inicio**|Dentro de la forma de tipo|Selecciona los elementos que contiene la forma, empezando por el elemento actual y finalizando con el elemento de nivel superior de la misma forma.|
|**Mayús**+**Fin**|Dentro de la forma de tipo|Igual que **Mayús**+**Inicio**, pero en dirección descendente.|
|**Entrar**|Todos los contextos|Invoca la acción predeterminada de la forma (también disponible con doble clic). En la mayoría de los casos se trata de la acción Ver código, pero en algunos elementos varía (círculos, encabezados de compartimiento o etiquetas de círculo).|
|**+** y **-**|Todos los contextos|Si el elemento que tiene el foco es expansible, estas teclas expanden o contraen el elemento.|
|**>**|Todos los contextos|En los elementos con elementos secundarios, expande el elemento (si se contrae) y navega al primer elemento secundario.|
|**<**|Todos los contextos|Se desplaza al elemento primario.|
|**Alt**+**Mayús**+**L**|Interior de las formas de tipo y sobre las formas de tipo.|Navega al círculo (si existe) de la forma seleccionada.|
|**Alt**+**Mayús**+**B**|Interior de las formas de tipo y sobre las formas de tipo.|Si la lista de tipos base se muestra en la forma de tipo y tiene más de un elemento, alterna el estado de expansión de la lista (contraer/expandir).|
|**Eliminar**|Sobre las formas de tipo y de comentario|Invoca el comando **Quitar del diagrama**.|
|**Eliminar**|Sobre cualquier otra cosa.|Invoca el comando **Eliminar del código** (miembros, parámetros, asociaciones, herencia, etiquetas de círculo).|
|**Ctrl**+**Supr**|Todos los contextos|Invoca el comando **Eliminar del código** en la selección.|
|**Tabulación**|Todos los contextos|Navega al siguiente elemento secundario del mismo elemento principal (permite el recorrido cíclico).|
|**Mayús**+**Tabulador**|Todos los contextos|Navega al elemento secundario anterior del mismo elemento primario (permite el recorrido cíclico).|
|**Barra espaciadora**|Todos los contextos|Alterna la selección sobre el elemento actual.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Usar el teclado en la ventana Detalles de clase

> [!NOTE]
> Se han elegido los siguientes enlaces de teclado para imitar la experiencia de escritura de código.

Use las siguientes teclas para navegar por la ventana **Detalles de clase**:

|||
|-|-|
|Key|Resultado|
|**,** (coma)|Si el cursor está en una fila de parámetro, al escribir una coma, se mueve al campo Nombre del parámetro siguiente. Si el cursor está en la última fila de parámetro de un método, se mueve al campo \<Agregar parámetro>, que permite crear un parámetro nuevo.<br /><br /> Si el cursor está en otra parte de la ventana **Detalles de clase**, al escribir una coma se agrega literalmente una coma al campo actual.|
|**;** (punto y coma) o **)** (paréntesis de cierre)|Mueve el cursor al campo Nombre de la siguiente fila de miembro en la cuadrícula de la ventana **Detalles de clase**.|
|**Tabulación**|Mueve el cursor al siguiente campo, primero de izquierda a derecha y luego de arriba abajo. Si el cursor se está moviendo desde un campo en el que se ha escrito texto, **Detalles de clase** procesa ese texto y lo almacena, siempre que no genere ningún error.<br /><br /> Si el cursor está en un campo vacío, como \<Agregar parámetro>, la tecla Tabulador lo mueve al primer campo de la fila siguiente.|
|**Barra espaciadora**|Mueve el cursor al siguiente campo, primero de izquierda a derecha y luego de arriba abajo. Si el cursor está en un campo vacío, como \<Agregar parámetro>, lo mueve al primer campo de la fila siguiente. Tenga en cuenta que si se escribe \<space> justo después de una coma, se pasará por alto.<br /><br /> Si el cursor está en el campo Resumen, al escribir un espacio se agrega un carácter de espacio.<br /><br /> Si el cursor está en la columna Ocultar de una fila determinada, al escribir un espacio se alterna el valor de la casilla Ocultar.|
|**Ctrl**+**Tab**|Cambiar a otra ventana del documento. Por ejemplo, cambia de la ventana **Detalles de clase** a un archivo de código abierto.|
|**Esc**|Si ha empezado a escribir texto en un campo, ESC actúa como tecla «deshacer» y restablece el contenido del campo a su valor anterior. Si la ventana Detalles de clase tiene el foco general sin que ninguna celda concreta tenga el foco, la tecla ESC quita el foco de la ventana **Detalles de clase**.|
|**Flecha arriba** y **flecha abajo**|Estas teclas mueven el cursor fila a fila, verticalmente, en la cuadrícula de la ventana **Detalles de clase**.|
|**Flecha izquierda**|Si el cursor está en la columna Nombre, al presionar la flecha izquierda se contrae el nodo actual de la jerarquía (si está abierto).|
|**Flecha derecha**|Si el cursor está en la columna Nombre, al presionar la flecha derecha se expande el nodo actual de la jerarquía (si está contraído).|

## <a name="see-also"></a>Vea también

- [Crear y configurar miembros de tipo](creating-and-configuring-type-members.md)