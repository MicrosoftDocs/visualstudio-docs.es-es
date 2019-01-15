---
title: Diseñador de flujo de trabajo - métodos abreviados de teclado en el Diseñador de flujo de trabajo
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c092a4bcb419039b145bccf3f6c0cd952f0ff85
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269584"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Métodos abreviados de teclado en el Diseñador de flujo de trabajo

Puede tener acceso a toda la funcionalidad principal del Diseñador de flujo de trabajo mediante el teclado.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Navegar por el Diseñador de flujo de trabajo mediante el teclado

Dentro de Visual Studio, los accesos directos de depuración y accesos directos globales se aplican en el Diseñador de flujo de trabajo. Además, se ha creado una serie de métodos abreviados de teclado específicos de diseñador de flujo de trabajo. En Visual Studio, se pueden reasignar todos los métodos abreviados de teclado. Sin embargo, en una aplicación hospedada en otro host, estos métodos abreviados de teclado están codificados de forma rígida.

### <a name="workflow-designer-keyboard-shortcuts"></a>Métodos abreviados de teclado del Diseñador de flujo de trabajo

En la tabla siguiente se resume los métodos abreviados de teclado asignados a los comandos del Diseñador de flujo de trabajo.

|Acceso directo|Finalidad|
|-|-------------|
|CTRL+E, A|Muestra u oculta el diseñador de argumentos.|
|CTRL+E, C|Contrae la actividad seleccionada en el sitio.|
|CTRL+E, E|Expande la actividad seleccionada en el sitio.|
|CTRL+E, F|Conecta las actividades seleccionadas en un diagrama de flujo.|
|CTRL+E, I|Muestra u oculta el diseñador de importaciones.|
|CTRL+E, M|El foco del teclado se desplaza al siguiente elemento en el orden de tabulación.|
|CTRL+E, N|Crea una nueva variable en el ámbito de la actividad seleccionada (o en la más cercana).|
|CTRL+E, O|Muestra u oculta el mapa general.|
|CTRL+E, P|Se desplaza hasta el elemento primario de la actividad seleccionada. De esta forma se sube un nivel en la ruta de navegación y cambia la actividad raíz en la superficie del diseñador.|
|CTRL+E, S|Agrega el elemento con foco de teclado a la selección actual.|
|CTRL+E, V|Muestra u oculta el diseñador de variables.|
|CTRL+E, X|Expande todas las actividades en el flujo de trabajo.|
|CTRL+ALT+F6|Mueve el foco de teclado del área de la interfaz de usuario al área siguiente en la secuencia. El orden es el siguiente:<br /><br /> 1.  Barra de ruta de navegación.<br />2.  Superficie del diseñador<br />3.  Diseñador de argumentos/variables/importaciones si está abierto<br />4.  Shell|

### <a name="flowchart"></a>Diagrama de flujo

La siguiente lista muestra los gestos que se utilizan para construir un diagrama de flujo con el teclado. Como se muestra en el resto del Diseñador de flujo de trabajo, las actividades se agregan a la superficie del diseñador mediante los métodos abreviados de cuadro de herramientas global proporcionados con Visual Studio.

- Para mover una actividad, seleccione la actividad y utilice las teclas de dirección para cambiar la posición.

- Para cambiar el tamaño de un diagrama de flujo, mueva una actividad más allá del borde actual del diagrama de flujo mediante las teclas de dirección. El diagrama de flujo cambia su tamaño automáticamente.

- Para establecer una actividad como nodo de inicio, use el **establecer como nodo inicial** comando en el menú contextual.

- Para conectar actividades:

    1.  Seleccione la actividad desplazándose hasta ella con la tecla de tabulación.

    2.  Presione CTRL+E, tantas veces como sea necesario para desplazar el foco de teclado a la actividad de destino.

    3.  Presione CTRL+E, S para agregar la actividad de destino a la selección.

    4.  Presione CTRL+E, F para agregar el conector desde el origen al destino.

Notas sobre cómo conectar las actividades mediante el teclado:

- Puede efectuar múltiples conexiones al mismo tiempo si agrega más actividades a la selección antes de presionar CTRL+E, F. Las conexiones se realizan en el orden en que se agregaron las actividades a la selección.

- Si una pareja de actividades no se puede conectar, por ejemplo si la actividad de origen ya tiene una conexión de salida, aún se pueden efectuar otras conexiones entre actividades en la selección siempre que sea posible.

- Cuando un **FlowDecision** se incluye en la selección y la **FlowDecision** no tiene ningún conector de salida, el conector se coloca en el **True** rama.

### <a name="expression-editing"></a>Edición de Expresiones

De forma predeterminada, los métodos abreviados de teclado predeterminado para la edición de texto de Visual Basic se aplican en el editor de expresiones en el Diseñador de flujo de trabajo, con las siguientes limitaciones:

- La reasignación de métodos abreviados de teclado para los siguientes comandos no tiene efecto alguno. Cuando edite una expresión, solo puede utilizar los métodos abreviados de teclado predeterminados para tener acceso a estos comandos.

   - Cut
   - Copiar
   - Paste
   - Seleccionar todo
   - Undo
   - Redo

- Para reasignar los métodos abreviados de teclado para comandos de edición de expresiones dentro del Diseñador de flujo de trabajo en Visual Studio, edite los accesos directos en el ámbito del Diseñador de flujo de trabajo. Los cambios realizados en el ámbito del Editor de texto no se aplican automáticamente al diseñador de flujo de trabajo. Si desea reasignar los accesos directos en ambos lugares, debe aplicar los cambios dos veces (una vez para cada ámbito).