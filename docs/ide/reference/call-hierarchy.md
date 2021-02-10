---
title: Búsqueda de llamadas a un método
description: Aprenda a usar la ventana Jerarquía de llamadas para desplazarse por todas las llamadas que se dirigen a un método, una propiedad o un constructor seleccionados y, en ocasiones, que parten de allí.
ms.custom: SEO-VS-2020
ms.date: 05/18/2018
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7384376b604f2097d68bf8bac06b2af0158e09b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836480"
---
# <a name="view-call-hierarchy"></a>Visualización de la jerarquía de llamadas

Al visualizar la jerarquía de llamadas del código, puede navegar por todas las llamadas a (y en ocasiones de) un método, una propiedad o un constructor seleccionados. Esto le permite comprender mejor cómo fluye el código y evaluar los efectos de los cambios en el código. Puede examinar varios niveles de código para ver cadenas complejas de llamadas de métodos y puntos de entrada adicionales al código. Esto le permite explorar todas las posibles rutas de acceso de ejecución.

En Visual Studio, puede ver una jerarquía de llamadas en tiempo de diseño. Esto significa que no tiene que establecer un punto de interrupción e iniciar el depurador para ver la pila de llamadas de tiempo de ejecución.

## <a name="use-the-call-hierarchy-window"></a>Uso de la ventana Jerarquía de llamadas

Para mostrar la ventana **Jerarquía de llamadas**, haga clic con el botón derecho en el nombre de un método, una propiedad o una llamada de constructor y seleccione **Ver jerarquía de llamadas**.

El nombre del miembro aparece en un panel de vista de árbol en la ventana **Jerarquía de llamadas**. Si expande el nodo del miembro, aparecen los subnodos **Llamadas a** *nombre del miembro* y, en C++, **Llamadas desde** *nombre del miembro*.

En el código de C++, puede ver las llamadas a y de un miembro:

![Jerarquía de llamadas del código C++ en Visual Studio](media/call-hierarchy-cpp.png)

En el código de C# y de Visual Basic, puede ver las llamadas a un miembro, pero no las llamadas desde:

![Jerarquía de llamadas del código C# en Visual Studio](media/call-hierarchy-csharp.png)

- Si expande el nodo **Llamadas a**, se muestran todos los miembros que llaman al miembro seleccionado.

- Si expande el nodo **Llamadas desde**, se muestran todos los miembros a los que llama el miembro seleccionado.

Luego puede expandir cada miembro que realiza llamadas para ver sus nodos **Llamadas a** y, en C++, **Llamadas desde**. Esto le permite navegar por la pila de autores de llamada, tal y como se muestra en la siguiente imagen:

![Ventana Jerarquía de llamadas con varios niveles expandidos](media/call-hierarchy-csharp-expanded.png)

Para los miembros que están definidos como virtuales o abstractos, se muestra un nodo **Invalida “nombre de método”**. Para los miembros de interfaz, se muestra un nodo **Implementa nombre de método**. Estos nodos expansibles aparecen en el mismo nivel que los nodos **Llamadas a** y **Llamadas desde**.

El cuadro **Ámbito de búsqueda** en la barra de herramientas contiene opciones para **Mi solución**, **Proyecto actual** y **Documento actual**.

Al seleccionar un miembro secundario en el panel de vista de árbol **Jerarquía de llamadas**:

- El panel de detalles **Jerarquía de llamadas** muestra todas las líneas de código en que el miembro primario llama a ese miembro secundario.

- La ventana **Definición de código**, si está abierta, muestra el código del miembro seleccionado (solo C++). Para más información sobre esta ventana, vea [Visualización de la estructura del código](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> La característica **Jerarquía de llamadas** no encuentra referencias a grupos de métodos, que incluyen los lugares en los que se agrega un método como controlador de eventos o se asigna a un delegado. Para buscar todas las referencias a un método, puede usar el comando **Buscar todas las referencias**.

## <a name="shortcut-menu-items"></a>Elementos del menú contextual

En la tabla siguiente, se describen varias opciones del menú contextual que están disponibles cuando hace clic con el botón derecho en un nodo en el panel de vista de árbol.

|Elemento del menú contextual|Descripción|
| - |-----------------|
|**Agregar como nueva raíz**|Agrega el nodo seleccionado al panel de vista de árbol como un nuevo nodo raíz. Esto le permite centrar la atención en un subárbol específico.|
|**Quitar raíz**|Quita el nodo raíz seleccionado del panel de vista de árbol. Esta opción solo está disponible desde un nodo raíz.<br /><br /> También puede usar el botón de la barra de herramientas **Quitar raíz** para quitar el nodo raíz seleccionado.|
|**Ir a definición**|Ejecuta el comando Ir a definición en el nodo seleccionado. De esta forma, se desplaza a la definición original de una llamada de miembro o definición de variable.<br /><br /> Para ejecutar el comando Ir a definición, también puede hacer doble clic en el nodo seleccionado o presionar F12 en el nodo seleccionado.|
|**Buscar todas las referencias**|Ejecuta el comando Buscar todas las referencias en el nodo seleccionado. De esta forma, busca todas las líneas de código en el proyecto que hacen referencia a una clase o un miembro.<br /><br /> También puede usar MAYÚS+F12 para ejecutar el comando Buscar todas las referencias en el nodo seleccionado.|
|**Copy**|Copia el contenido del nodo seleccionado (pero no sus subnodos).|
|**Actualizar**|Contrae el nodo seleccionado para que, al volver a expandirlo, se muestre la información actual.|
