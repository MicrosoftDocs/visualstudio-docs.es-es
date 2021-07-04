---
title: Ventana Cuadro de herramientas
description: Obtenga información sobre la ventana Cuadro de herramientas y cómo muestra controles que puede agregar a proyectos de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/01/2020
ms.topic: reference
f1_keywords:
- vs.toolbox.general
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a4947562eb49501e60711111d8765716cbae5c6
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925220"
---
# <a name="toolbox"></a>Cuadro de herramientas

La ventana **Cuadro de herramientas** muestra los controles que puede agregar a proyectos de Visual Studio. Para abrir la ventana **Cuadro de herramientas**, elija **Ver** > **Cuadro de herramienta** en la barra de menús, o bien presione **Ctrl**+**Alt**+**X**.

![Captura de pantalla de la ventana Cuadro de herramientas en la que se muestran las opciones de la sección Contenedores.](media/vs-2019/toolbox.png "Captura de pantalla de la ventana Cuadro de herramientas")

Puede arrastrar y colocar distintos controles en la superficie del diseñador que use y cambiar su tamaño y posición.

La ventana Cuadro de herramientas aparece junto con las vistas de diseñador, como la vista de diseñador de un archivo XAML o un proyecto de aplicación de Windows Forms. En el **Cuadro de herramientas** solo se muestran los controles que se pueden usar en el diseñador actual. Puede buscar en el **Cuadro de herramientas** para filtrar más los elementos que aparecen.

> [!NOTE]
> Para algunos tipos de proyecto, el **Cuadro de herramientas** no puede mostrar todos los elementos.

La versión de .NET de destino del proyecto también afecta al conjunto de controles visible en el Cuadro de herramientas. Puede cambiar la versión del marco de destino desde las páginas de propiedades del proyecto, en caso necesario. Seleccione el modo del proyecto en el **Explorador de soluciones** y, luego, en la barra de menús, elija **Proyecto** > **Propiedades de proyecto**. En la pestaña **Aplicación**, use el menú desplegable **Plataforma de destino**.

::: moniker range=">=vs-2019"

![Captura de pantalla del cuadro de diálogo Aplicación en el que se muestran las opciones de la lista desplegable Plataforma de destino.](media/vs-2019/toolbox-change-dotnet-version.png "Captura de pantalla del cuadro de diálogo donde puede cambiar la versión de .NET")

::: moniker-end

## <a name="manage-the-toolbox-window-and-its-controls"></a>Administrar la ventana Cuadro de herramientas y sus controles

De manera predeterminada, el **Cuadro de herramientas** está contraído en el lado izquierdo del IDE de Visual Studio y aparece cuando el cursor se desplaza por encima. Puede anclar el **Cuadro de herramientas** (haciendo clic en el icono **Anclar** de la barra de herramientas), de manera que permanezca abierto al mover el cursor. También puede desacoplar la ventana **Cuadro de herramientas** y arrastrarla a cualquier punto de la pantalla. Puede acoplar, desacoplar y ocultar el **Cuadro de herramientas** si hace clic con el botón derecho en su barra de herramientas y selecciona una de las opciones.

> [!TIP]
> Si el cuadro de herramientas ya no aparece como contraído a lo largo del lado izquierdo del IDE de Visual Studio, puede volver a agregarlo si elige **Ventana** > **Restablecer diseños de ventana** en la barra de menús.

Puede reorganizar los elementos de una pestaña del **Cuadro de herramientas**, o bien puede agregar pestañas y elementos personalizados mediante los siguientes comandos del menú contextual:

- **Cambiar el nombre del elemento**: permite cambiar el nombre del elemento seleccionado.

- **Vista de lista**: muestra los controles en una lista vertical. Si se deja sin marcar, los controles aparecen horizontalmente.

- **Mostrar todo**: muestra todos los controles posibles (no solo los correspondientes al diseñador actual).

- **Elegir elementos**: abre el cuadro de diálogo **Elegir elementos del cuadro de herramientas** para que pueda especificar los elementos que aparecen en el **Cuadro de herramientas**. Para mostrar u ocultar un elemento, active o desactive su casilla.

- **Ordenar elementos alfabéticamente**: ordena los elementos por el nombre.

- **Restablecer barra de herramientas**: restaura la configuración y los elementos predeterminados del **Cuadro de herramientas**.

- **Agregar pestaña**: agrega una nueva pestaña del **Cuadro de herramientas**.

- **Subir**: mueve el elemento seleccionado hacia arriba.

- **Bajar**: mueve el elemento seleccionado hacia abajo.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Crear y distribuir controles personalizados del cuadro de herramientas

Puede crear controles personalizados del **Cuadro de herramientas**, iniciando con una plantilla de proyecto basada en [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) o en [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Después, puede distribuir el control personalizado a sus compañeros de equipo o publicarlo en la web con el [Instalador de controles del Cuadro de herramientas](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="next-steps"></a>Pasos siguientes

Examine los siguientes vínculos para obtener más información sobre algunas de las pestañas del **Cuadro de herramientas** disponibles:

- [Cuadro de herramientas, Datos (Pestaña)](../../ide/reference/toolbox-data-tab.md)
- [Cuadro de herramientas, Componentes (Pestaña)](../../ide/reference/toolbox-components-tab.md)
- [Cuadro de herramientas, HTML (Pestaña)](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Vea también

- [Elegir elementos del Cuadro de herramientas, componentes de WPF](choose-toolbox-items-wpf-components.md)
