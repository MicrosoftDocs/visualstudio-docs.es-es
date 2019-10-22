---
title: Ventana Cuadro de herramientas
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb101dc1f272ae56ceb0058afb2806aec4154936
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747683"
---
# <a name="toolbox"></a>Cuadro de herramientas

La ventana **Cuadro de herramientas** muestra los controles que puede agregar a proyectos de Visual Studio. Para abrir el Cuadro de herramientas, elija **Cuadro de herramientas** en el menú **Ver**.

![Ventana Cuadro de herramientas](media/toolbox.png)

Puede arrastrar y colocar distintos controles en la superficie del diseñador que use y cambiar su tamaño y posición.

El Cuadro de herramientas aparece junto con las vistas de diseñador, como la vista de diseñador de un archivo XAML. En el **Cuadro de herramientas** solo se muestran los controles que se pueden usar en el diseñador actual. Puede buscar en el **Cuadro de herramientas** para filtrar más los elementos que aparecen.

> [!NOTE]
> Para algunos tipos de proyecto, el **Cuadro de herramientas** no puede mostrar todos los elementos.

La versión de .NET de destino del proyecto también afecta al conjunto de controles visible en el Cuadro de herramientas. Puede cambiar la versión del marco de destino desde las páginas de propiedades del proyecto, en caso necesario. Seleccione el modo del proyecto en el **Explorador de soluciones** y, luego, en la barra de menús, elija **Proyecto** > **Propiedades de proyecto**. En la pestaña **Aplicación**, use el menú desplegable **Plataforma de destino**.

## <a name="manage-the-toolbox-window-and-its-controls"></a>Administrar la ventana Cuadro de herramientas y sus controles

De manera predeterminada, el **Cuadro de herramientas** está contraído en la izquierda del IDE de Visual Studio y aparece cuando se desplaza el cursor por encima. Puede anclar el **Cuadro de herramientas** (haciendo clic en el icono **Anclar** de la barra de herramientas), de manera que permanezca abierto al mover el cursor. También puede desacoplar la ventana **Cuadro de herramientas** y arrastrarla a cualquier punto de la pantalla. Puede acoplar, desacoplar y ocultar el **Cuadro de herramientas** si hace clic con el botón derecho en su barra de herramientas y selecciona una de las opciones.

Puede reorganizar los elementos de una pestaña del **Cuadro de herramientas**, o bien puede agregar pestañas y elementos personalizados mediante los siguientes comandos del menú contextual:

- **Cambiar nombre de elemento**: permite cambiar el nombre del elemento seleccionado.

- **Mostrar todo**: muestra todos los controles posibles (no solo los correspondientes al diseñador actual).

- **Vista de lista**: muestra los controles en una lista vertical. Si se deja sin marcar, los controles aparecen horizontalmente.

- **Elegir elementos**: abre el cuadro de diálogo **Elegir elementos del cuadro de herramientas** para que pueda especificar los elementos que aparecen en el **Cuadro de herramientas**. Para mostrar u ocultar un elemento, active o desactive su casilla.

- **Ordenar elementos alfabéticamente**: ordena los elementos por el nombre.

- **Restablecer barra de herramientas**: restaura la configuración y los elementos predeterminados del **Cuadro de herramientas**.

- **Agregar pestaña**: agrega una nueva pestaña del **Cuadro de herramientas**.

- **Subir**: mueve el elemento seleccionado hacia arriba.

- **Bajar**: mueve el elemento seleccionado hacia abajo.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Crear y distribuir controles personalizados del cuadro de herramientas

Puede crear controles personalizados del **Cuadro de herramientas**, iniciando con una plantilla de proyecto basada en [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) o en [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Después, puede distribuir el control personalizado a sus compañeros de equipo o publicarlo en la web con el [Instalador de controles del Cuadro de herramientas](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="help-on-toolbox-tabs"></a>Ayuda acerca de las pestañas del Cuadro de herramientas

En los siguientes temas se proporciona más información sobre algunas de las pestañas disponibles del **Cuadro de herramientas**:

- [Cuadro de herramientas, Datos (Pestaña)](../../ide/reference/toolbox-data-tab.md)
- [Cuadro de herramientas, Componentes (Pestaña)](../../ide/reference/toolbox-components-tab.md)
- [Cuadro de herramientas, HTML (Pestaña)](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Vea también

- [Elegir elementos del Cuadro de herramientas, componentes de WPF](choose-toolbox-items-wpf-components.md)