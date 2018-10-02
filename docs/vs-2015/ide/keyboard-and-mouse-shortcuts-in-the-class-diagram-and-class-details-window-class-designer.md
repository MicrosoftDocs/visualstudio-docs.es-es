---
title: Métodos abreviados de teclado y de mouse en el diagrama de clases y la ventana de detalles de clase (Diseñador de clases) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 144c2d70cf734f8d1c9602fad96bf4e1c6d8a0c4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580545"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer"></a>Métodos abreviados de teclado y de mouse en el diagrama de clases y la ventana de detalles de clase (Diseñador de clases)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [teclado y accesos directos de mouse (ratón) en el diagrama de clase y la ventana Detalles de clase (Diseñador de clases)](https://docs.microsoft.com/visualstudio/ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer).  
  
Puede usar el teclado junto con el mouse para llevar a cabo acciones de navegación en el Diseñador de clases y en la ventana **Detalles de clase**.  
  
 **En este tema**  
  
-   [Usar el mouse en el Diseñador de clases](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDesigner)  
  
-   [Usar el mouse en la ventana Detalles de clase](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDetails)  
  
-   [Usar el teclado en el Diseñador de clases](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDesigner)  
  
-   [Usar el teclado en la ventana Detalles de clase](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDetails)  
  
##  <a name="MouseClassDesigner"></a> Usar el mouse en el Diseñador de clases  
 Se admiten las siguientes acciones del mouse en los diagramas de clases:  
  
|Combinación del mouse|Contexto|Descripción|  
|-----------------------|-------------|-----------------|  
|Doble clic|Shape (elementos)|Se abre el editor de código.|  
||Conector de círculo|Expandir o contraer el círculo.|  
||Etiqueta del conector de círculo|Invoca el comando **Mostrar interfaz**.|  
|Rueda del mouse|Diagrama de clases|Desplazamiento vertical.|  
|MAYÚS + rueda del mouse|Diagrama de clases|Desplazamiento horizontal.|  
|CTRL + rueda del mouse|Diagrama de clases|Zoom.|  
|CTRL + MAYÚS + clic|Diagrama de clases|Zoom.|  
  
##  <a name="MouseClassDetails"></a> Usar el mouse en la ventana Detalles de clase  
 Puede usar un mouse para cambiar la apariencia de la ventana Detalles de clase y los datos que muestra de las siguientes maneras:  
  
-   Haga clic en cualquier celda modificable para editar su contenido. Los cambios se reflejan en todos los lugares en los que se almacenan o muestran los datos, incluida la ventana Propiedades y el código fuente.  
  
-   Haga clic en cualquier celda de una fila para que la ventana Propiedades muestre las propiedades del elemento representado por la fila.  
  
-   Para cambiar el ancho de una columna, arrastre el límite del lado derecho del encabezado de columna hasta obtener el ancho deseado.  
  
-   Puede expandir o contraer nodos de compartimiento o de propiedad haciendo clic en los símbolos de flecha situados a la izquierda de la fila.  
  
-   La ventana Detalles de clase dispone de varios botones para crear nuevos miembros en la clase actual y para navegar entre los compartimientos de los miembros en la cuadrícula de la ventana Detalles de clase. Para obtener más información, consulte Botones de la ventana Detalles de clase.  
  
##  <a name="KeyboardClassDesigner"></a> Usar el teclado en el Diseñador de clases  
 Se admiten las siguientes acciones del teclado en los diagramas de clases:  
  
|Key|Contexto|Descripción|  
|---------|-------------|-----------------|  
|Teclas de dirección|Dentro de las formas de tipo|Navegación de tipo árbol por el contenido de la forma (permite efectuar un recorrido cíclico). Las teclas izquierda y derecha expanden y contraen el elemento actual, si es expansible, y navegan al elemento primario si no lo es (consulte los métodos de navegación por la vista de árbol para obtener información detallada sobre su comportamiento).|  
||Formas de nivel superior|Mover las formas en el diagrama.|  
|MAYÚS + teclas de dirección|Dentro de las formas de tipo|Crear una selección continua compuesta por elementos de forma, como miembros, tipos anidados o compartimientos. Estos métodos abreviados no permiten el recorrido cíclico.|  
|INICIO|Dentro de las formas de tipo|Navegar al título de la forma de nivel superior.|  
||Formas de nivel superior|Desplácese a la primera forma del diagrama.|  
|FIN|Dentro de las formas de tipo|Navegar al último elemento visible dentro de la forma.|  
||Formas de nivel superior|Navegar a la última forma del diagrama.|  
|MAYÚS+HOME|Dentro de la forma de tipo|Selecciona los elementos que contiene la forma, empezando por el elemento actual y finalizando con el elemento de nivel superior de la misma forma.|  
|MAYÚS+END|Dentro de la forma de tipo|Igual que MAYÚS + INICIO pero en dirección descendente.|  
|ENTRAR|Todos los contextos|Invoca la acción predeterminada de la forma (también disponible con doble clic). En la mayoría de los casos se trata de la acción Ver código, pero en algunos elementos varía (círculos, encabezados de compartimiento o etiquetas de círculo).|  
|+/-|Todos los contextos|Si el elemento que tiene el foco es expansible, estas teclas expanden o contraen el elemento.|  
|>|Todos los contextos|En los elementos con elementos secundarios, expande el elemento (si se contrae) y navega al primer elemento secundario.|  
|<|Todos los contextos|Se desplaza al elemento primario.|  
|ALT + MAYÚS + L|Interior de las formas de tipo y sobre las formas de tipo.|Navega al círculo (si existe) de la forma seleccionada.|  
|ALT + MAYÚS + B|Interior de las formas de tipo y sobre las formas de tipo.|Si la lista de tipos base se muestra en la forma de tipo y tiene más de un elemento, alterna el estado de expansión de la lista (contraer/expandir).|  
|SUPRIMIR|Sobre las formas de tipo y de comentario|Invoca el comando **Quitar del diagrama**.|  
||Sobre cualquier otra cosa.|Invoca el comando **Eliminar del código** (miembros, parámetros, asociaciones, herencia, etiquetas de círculo).|  
|CTRL+SUPR|Todos los contextos|Invoca el comando **Eliminar del código** en la selección.|  
|TAB|Todos los contextos|Navega al siguiente elemento secundario del mismo elemento principal (permite el recorrido cíclico).|  
|MAYÚS+TAB|Todos los contextos|Navega al elemento secundario anterior del mismo elemento primario (permite el recorrido cíclico).|  
|Barra espaciadora|Todos los contextos|Alterna la selección sobre el elemento actual.|  
  
##  <a name="KeyboardClassDetails"></a> Usar el teclado en la ventana Detalles de clase  
  
> [!NOTE]
>  Se han elegido los siguientes enlaces de teclado para imitar la experiencia de escritura de código.  
  
 Use las siguientes teclas para navegar por la ventana Detalles de clase:  
  
|||  
|-|-|  
|Key|Resultado|  
|, (coma)|Si el cursor está en una fila de parámetro, al escribir una coma, se mueve al campo Nombre del parámetro siguiente. Si el cursor está en la última fila de parámetro de un método, se mueve al campo \<Agregar parámetro>, que permite crear un parámetro nuevo.<br /><br /> Si el cursor está en otra parte de la ventana Detalles de clase, al escribir una coma se agrega una coma al campo actual.|  
|; (punto y coma)<br /><br /> o<br /><br /> ) (paréntesis de cierre)|Mover el cursor al campo Nombre de la siguiente fila de miembro en la cuadrícula de la ventana Detalles de clase.|  
|Tab|Mueve el cursor al siguiente campo, primero de izquierda a derecha y luego de arriba abajo. Si el cursor está en un campo en el que se ha escrito texto, la ventana Detalles de clase procesa el texto y lo almacena si no genera ningún error.<br /><br /> Si el cursor está en un campo vacío, como \<Agregar parámetro>, la tecla Tabulador lo mueve al primer campo de la fila siguiente.|  
|\<space>|Mueve el cursor al siguiente campo, primero de izquierda a derecha y luego de arriba abajo. Si el cursor está en un campo vacío, como \<Agregar parámetro>, lo mueve al primer campo de la fila siguiente. Tenga en cuenta que si se escribe \<space> justo después de una coma, se pasará por alto.<br /><br /> Si el cursor está en el campo Resumen, al escribir un espacio se agrega un carácter de espacio.<br /><br /> Si el cursor está en la columna Ocultar de una fila determinada, al escribir un espacio se alterna el valor de la casilla Ocultar.|  
|Ctrl+Tab|Cambiar a otra ventana del documento. Por ejemplo, cambia de la ventana Detalles de clase a un archivo de código abierto.|  
|ESC (Escape)|Si ha empezado a escribir texto en un campo, ESC actúa como tecla «deshacer» y restablece el contenido del campo a su valor anterior. Si la ventana Detalles de clase tiene el foco general sin que ninguna celda concreta tenga el foco, la tecla ESC quita el foco de la ventana Detalles de clase.|  
|Flecha arriba y flecha abajo|Estas teclas mueven el cursor fila a fila, verticalmente, en la cuadrícula de la ventana Detalles de clase.|  
|Flecha izquierda|Si el cursor está en la columna Nombre, al presionar la flecha izquierda se contrae el nodo actual de la jerarquía (si está abierto).|  
|Flecha derecha|Si el cursor está en la columna Nombre, al presionar la flecha derecha se expande el nodo actual de la jerarquía (si está contraído).|  
  
## <a name="see-also"></a>Vea también  
 [Crear y configurar miembros de tipo (Diseñador de clases)](../ide/creating-and-configuring-type-members-class-designer.md)



