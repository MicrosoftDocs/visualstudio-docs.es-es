---
title: Visualización de la jerarquía de llamadas en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2018
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d18af9f159c663cb061a32a61343eaa0a14d7503
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="view-call-hierarchy"></a>Visualización de la jerarquía de llamadas

Al visualizar la jerarquía de llamadas para su código, puede navegar desde y hasta las llamadas desde un método, una propiedad o un constructor seleccionado. Esto le permite comprender mejor cómo fluye el código y evaluar los efectos de los cambios en el código. Puede examinar varios niveles de código para ver cadenas complejas de llamadas de métodos y puntos de entrada adicionales al código. Esto le permite explorar todas las posibles rutas de acceso de ejecución.

En Visual Studio, puede ver una jerarquía de llamadas en tiempo de diseño. Esto significa que no tiene que establecer un punto de interrupción e iniciar el depurador para ver la pila de llamadas de tiempo de ejecución.

## <a name="use-the-call-hierarchy-window"></a>Uso de la ventana Jerarquía de llamadas

Para mostrar la ventana **Jerarquía de llamadas**, haga clic con el botón derecho en el nombre de un método, una propiedad o una llamada de constructor y después haga clic en **Ver jerarquía de llamadas**.

El nombre del miembro aparece en un panel de vista de árbol en la ventana **Jerarquía de llamadas**. Si expande el nodo del miembro, aparecen los subnodos **Llamadas a** *nombre del miembro* y **Llamadas desde** *nombre del miembro*. En la ilustración siguiente, se muestran estos nodos en la ventana **Jerarquía de llamadas**.

![Jerarquía de llamadas con un nodo abierto](../../ide/reference/media/onenode.png "OneNode")

- Si expande el nodo **Llamadas a**, se muestran todos los miembros que llaman al miembro seleccionado.

- Si expande el nodo **Llamadas desde**, se muestran todos los miembros a los que llama el miembro seleccionado.

Después, puede expandir cada uno de estos miembros del subnodo en los nodos **Llamadas a** y **Llamadas desde**. Esto le permite navegar por la pila de autores de llamadas, como se muestra en la siguiente ilustración.

![Jerarquía de llamadas con varios nodos abiertos](../../ide/media/multiplenodes.png "MultipleNodes")

Para los miembros que están definidos como virtuales o abstractos, se muestra un nodo **Invalida “nombre de método”**. Para los miembros de interfaz, se muestra un nodo **Implementa nombre de método**. Estos nodos expansibles aparecen en el mismo nivel que los nodos **Llamadas a** y **Llamadas desde**.

El cuadro **Ámbito de búsqueda** en la barra de herramientas contiene opciones para **Mi solución**, **Proyecto actual** y **Documento actual**.

Al seleccionar un miembro secundario en el panel de vista de árbol **Jerarquía de llamadas**:

- El panel de detalles **Jerarquía de llamadas** muestra todas las líneas de código en que el miembro primario llama a ese miembro secundario.

- La **ventana Definición de código**, si está abierta, muestra el código del miembro seleccionado (solo C++). Para más información sobre esta ventana, vea [Ver la estructura del código](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> La característica Jerarquía de llamadas no encuentra referencias a grupos de métodos, que incluyen los lugares en los que se agrega un método como controlador de eventos o se asigna a un delegado. Para buscar todas las referencias a un método, puede usar el comando **Buscar todas las referencias**.

### <a name="shortcut-menu-items"></a>Elementos del menú contextual

En la tabla siguiente, se describen varias opciones del menú contextual que están disponibles cuando hace clic con el botón derecho en un nodo en el panel de vista de árbol.

|Elemento del menú contextual|Description|
|-----------------------|-----------------|
|**Agregar como nueva raíz**|Agrega el nodo seleccionado al panel de vista de árbol como un nuevo nodo raíz. Esto le permite centrar la atención en un subárbol específico.|
|**Quitar raíz**|Quita el nodo raíz seleccionado del panel de vista de árbol. Esta opción solo está disponible desde un nodo raíz.<br /><br /> También puede usar el botón de la barra de herramientas **Quitar raíz** para quitar el nodo raíz seleccionado.|
|**Ir a definición**|Ejecuta el comando Ir a definición en el nodo seleccionado. De esta forma, se desplaza a la definición original de una llamada de miembro o definición de variable.<br /><br /> Para ejecutar el comando Ir a definición, también puede hacer doble clic en el nodo seleccionado o presionar F12 en el nodo seleccionado.|
|**Buscar todas las referencias**|Ejecuta el comando Buscar todas las referencias en el nodo seleccionado. De esta forma, busca todas las líneas de código en el proyecto que hacen referencia a una clase o un miembro.<br /><br /> También puede usar MAYÚS+F12 para ejecutar el comando Buscar todas las referencias en el nodo seleccionado.|
|**Copiar**|Copia el contenido del nodo seleccionado (pero no sus subnodos).|
|**Actualizar**|Contrae el nodo seleccionado para que, al volver a expandirlo, se muestre la información actual.|