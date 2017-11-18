---
title: "Métodos abreviados en el Diseñador de flujo de trabajo de teclado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d720b3647b077cfe66950d842163d774cb34e92
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Métodos abreviados de teclado en el Diseñador de flujo de trabajo
A través del teclado, se puede obtener acceso a la totalidad de la funcionalidad básica de [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Navegar por el Diseñador de flujo de trabajo mediante el teclado  
 En [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], los accesos directos globales y los accesos directos de depuración se aplican a [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. También, se han creado diversos métodos abreviados de teclado específicos para [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. En [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], todos los métodos abreviados de teclado se pueden reasignar. Sin embargo, en una aplicación hospedada en otro host, estos métodos abreviados de teclado están codificados de forma rígida.  
  
### <a name="workflow-designer-keyboard-shortcuts"></a>Métodos abreviados de teclado del Diseñador de flujo de trabajo  
 En la siguiente tabla se resumen los métodos abreviados de teclado predeterminados que se asignan a los comandos de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Acceso directo|Finalidad|  
|--------------|-------------|  
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
 La siguiente lista muestra los gestos que se utilizan para construir un diagrama de flujo con el teclado. Como en el resto de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], las actividades se agregan a la superficie del diseñador mediante los accesos directos del cuadro de herramientas global que se proporcionan con [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
-   Para mover una actividad, seleccione la actividad y utilice las teclas de dirección para cambiar la posición.  
  
-   Para cambiar el tamaño de un diagrama de flujo, mueva una actividad más allá del borde actual del diagrama de flujo mediante las teclas de dirección. El diagrama de flujo cambia su tamaño automáticamente.  
  
-   Para establecer una actividad como nodo de inicio, utilice la **establecer como nodo inicial** comando en el menú contextual.  
  
-   Para conectar actividades:  
  
    1.  Seleccione la actividad desplazándose hasta ella con la tecla de tabulación.  
  
    2.  Presione CTRL+E, tantas veces como sea necesario para desplazar el foco de teclado a la actividad de destino.  
  
    3.  Presione CTRL+E, S para agregar la actividad de destino a la selección.  
  
    4.  Presione CTRL+E, F para agregar el conector desde el origen al destino.  
  
 Notas sobre cómo conectar las actividades mediante el teclado:  
  
-   Puede efectuar múltiples conexiones al mismo tiempo si agrega más actividades a la selección antes de presionar CTRL+E, F. Las conexiones se realizan en el orden en que se agregaron las actividades a la selección.  
  
-   Si una pareja de actividades no se puede conectar, por ejemplo si la actividad de origen ya tiene una conexión de salida, aún se pueden efectuar otras conexiones entre actividades en la selección siempre que sea posible.  
  
-   Cuando un **FlowDecision** se incluye en la selección y la **FlowDecision** no tiene ningún conector saliente, el conector se coloca en el **True** bifurcación.  
  
### <a name="expression-editing"></a>Edición de Expresiones  
 De forma predeterminada, los métodos abreviados de teclado predeterminados para la modificación de texto en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] se aplican en el editor de expresiones de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], con las siguientes limitaciones:  
  
-   La reasignación de métodos abreviados de teclado para los siguientes comandos no tiene efecto alguno. Cuando edite una expresión, solo puede utilizar los métodos abreviados de teclado predeterminados para tener acceso a estos comandos.  
  
    1.  Cut  
  
    2.  Copiar  
  
    3.  Paste  
  
    4.  Seleccionar todo  
  
    5.  Undo  
  
    6.  Redo  
  
-   Para reasignar los métodos abreviados de teclado para los comandos de edición de expresiones dentro de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] en [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], modifique los accesos directos en el ámbito de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Los cambios realizados en el ámbito del Editor de texto no se aplican automáticamente a [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Si desea reasignar los accesos directos en ambos lugares, debe aplicar los cambios dos veces (una vez para cada ámbito).