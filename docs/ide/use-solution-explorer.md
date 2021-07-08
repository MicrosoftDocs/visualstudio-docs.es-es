---
title: Información sobre la ventana de herramientas Explorador de soluciones
description: Obtenga información sobre cómo puede usar la ventana de herramientas Explorador de soluciones de Visual Studio para crear y administrar archivos, proyectos y soluciones.
ms.date: 06/29/2021
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
helpviewer_keywords:
- solution explorer [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fbbae8b974a7e88abffd9a12eb253dfea6c7165b
ms.sourcegitcommit: 8fb1500acb7e6314fbb6b78eada78ef5d61d39bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2021
ms.locfileid: "113280488"
---
# <a name="how-to-use-solution-explorer"></a>Procedimiento para usar el Explorador de soluciones

Puede usar la ventana de herramientas Explorador de soluciones para crear y administrar soluciones y proyectos, y para ver e interactuar con el código. En este artículo, se detallarán las opciones de la interfaz de usuario (IU) que le ayudarán a hacerlo.

> [!NOTE]
> Este tema solo se aplica a Visual Studio para Windows.

## <a name="solution-explorer-tool-window"></a>Ventana de herramientas Explorador de soluciones

Para empezar, se examinará la ventana de herramientas Explorador de soluciones en el [IDE de Visual Studio](../get-started/visual-studio-ide.md), con una solución de consola de C# abierta que tiene dos proyectos.

[![Ventana de herramientas Explorador de soluciones en Visual Studio.](media/solution-explorer-tool-window.png)](media/solution-explorer-tool-window.png#lightbox)

La ventana de herramientas contiene los elementos de interfaz de usuario (IU) siguientes:

- **Barra de menús**, donde puede controlar cómo aparecen los archivos
- **Barra de búsqueda**, donde puede buscar archivos y tipos de archivo específicos
- **Ventana principal**, donde puede ver y administrar archivos, proyectos y soluciones
- **Nodo Solución**, donde puede administrar las soluciones
- **Nodo Proyecto**, donde puede administrar los proyectos
- **Nodo Dependencias**, donde puede administrar las dependencias del proyecto y la solución
- **Nodo Programa**, donde puede ver, editar y administrar el programa o la aplicación
- **[Pestaña Cambios de Git](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window)** , donde puede usar Git y GitHub desde Visual Studio para colaborar en proyectos con el equipo

> [!TIP]
> Si no ve la ventana de herramientas Explorador de soluciones, puede abrirla desde la barra de menús de Visual Studio mediante **Ver** > **Explorador de soluciones**, o bien presionar **Ctrl**+**Alt**+**L**.

## <a name="solution-explorer-menu-bar"></a>Barra de menús del Explorador de soluciones

Para continuar, se examinará con más detalle la barra de menús del Explorador de soluciones.

![Barra de menús del Explorador de soluciones en Visual Studio.](media/solution-explorer-menu-bar.png)

La barra de menús contiene los siguientes elementos de la interfaz de usuario, de izquierda a derecha:

- Botón **Atrás**, para alternar entre los resultados de la búsqueda
- Botón **Adelante**, para alternar entre los resultados de la búsqueda
- Botón **Inicio**, para volver a la vista predeterminada
- Botón **Cambiar**, para cambiar entre las soluciones y las vistas disponibles
- Botón y menú desplegable **Filtro de cambios pendientes**, para ver archivos abiertos o archivos con cambios pendientes
- Botón **Sincronizar con el documento activo**, para buscar un archivo desde el editor de código
- Botón **Actualizar**, que solo aparece cuando se selecciona una dependencia, como una función o un paquete
- Botón **Contraer todo**, para contraer la vista de archivo en la ventana principal
- Botón **Mostrar todos los archivos**, para ver todos los archivos, incluidos los [proyectos descargados](filtered-solutions.md#toggle-unloaded-project-visibility)
- Botón **Propiedades**, para ver y cambiar la configuración de archivos y componentes específicos
- Botón **Vista previa de elementos seleccionados**, para ver un archivo o componente seleccionado en el editor de código

### <a name="solution-explorer-right-click-context-menu"></a>Menú contextual del Explorador de soluciones

En el Explorador de soluciones hay varias propiedades de archivo con las que puede interactuar mediante el menú contextual. Para obtener más información sobre las opciones del menú contextual, vea la página [Administración de propiedades de proyecto y solución](managing-project-and-solution-properties.md).

## <a name="see-also"></a>Vea también

- [¿Qué son las soluciones y los proyectos en Visual Studio?](solutions-and-projects-in-visual-studio.md)
- [Personalizar los diseños de ventana de Visual Studio](customizing-window-layouts-in-visual-studio.md)
