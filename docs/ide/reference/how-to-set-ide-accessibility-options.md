---
title: Procedimiento Establecimiento de opciones de accesibilidad de IDE
description: Obtenga información sobre cómo establecer las opciones de accesibilidad en Visual Studio para que el entorno de desarrollo integrado (IDE) sea más fácil de usar para todos, incluidos los usuarios con problemas de visión para leer y con limitaciones para escribir.
ms.date: 08/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: how-to
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac857d961b1ae736645ba2cfda3f1ef5755d0fa1
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770288"
---
# <a name="how-to-set-ide-accessibility-options"></a>Procedimiento Establecimiento de opciones de accesibilidad de IDE

Visual Studio contiene características que facilitan la lectura a las personas que tienen poca visión y la escritura a las personas que tienen una destreza manual limitada. Por ejemplo, puede cambiar el tamaño y el color del texto en los editores, cambiar el tamaño del texto y los botones de las barras de herramientas y cambiar la configuración para ayudarle a completar una función o instrucción.

Además, Visual Studio admite las distribuciones de teclado Dvorak, que hacen que los caracteres que se escriben con más frecuencia sean más accesibles. También puede personalizar los métodos abreviados de teclado predeterminados disponibles con Visual Studio. Para obtener más información, vea [Identificar y personalizar métodos abreviados de teclado](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos aquí, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Restablecer la configuración](../environment-settings.md#reset-settings).

::: moniker range="vs-2017"

> [!TIP]
> Para más información sobre las actualizaciones de accesibilidad recientes, vea la entrada de blog [Accessibility improvements in Visual Studio 2017 version 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Mejoras de accesibilidad en Visual Studio 2017 versión 15.3).

::: moniker-end

## <a name="editors-dialogs-and-tool-windows"></a>Editores, cuadros de diálogo y ventanas de herramientas

De manera predeterminada, los cuadros de diálogo y las ventanas de herramientas de Visual Studio usan el mismo tamaño de fuente y los mismos colores que el sistema operativo. La configuración del color del marco del IDE, los cuadros de diálogo, las barras de herramientas y las ventanas de herramientas se basan en una combinación de colores: clara u oscura. Puede cambiar el tema de color actual en el [cuadro de diálogo Opciones: Entorno > General](../../ide/reference/general-environment-options-dialog-box.md).

También puede mostrar ventanas emergentes en la vista Código del editor. Estas ventanas pueden indicarle los miembros disponibles en el objeto actual y los parámetros para completar una función o instrucción. Estas ventanas pueden resultar útiles si tiene dificultades para escribir. En cambio, interfieren con el foco del editor de código, que puede ser problemático para algunos usuarios.

Aquí se muestra cómo desactivar las ventanas emergentes:

1. En el menú **Herramientas** , elija **Opciones**.

1. Elija **Editor de texto** > **Todos los idiomas** > **General**.

1. Desactive las casillas **Lista de miembros automática** e **Información de parámetros**.

Puede reorganizar las ventanas del entorno de desarrollo integrado (IDE) para adaptarse mejor a su manera de trabajar. Puede acoplar, hacer flotante, ocultar u ocultar automáticamente cada ventana de herramientas. Para más información sobre cómo cambiar los diseños de ventanas, consulte [Personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="change-the-size-of-text"></a>Cambio del tamaño del texto

Puede cambiar la configuración de las ventanas de herramientas basadas en texto, como la ventana **Comando**, la ventana **Inmediato** y la ventana **Salida** mediante **Herramientas** > **Opciones** > **Entorno** > **Fuentes y colores**.

Cuando la opción **[Todas las ventanas de herramientas de texto]** está seleccionada en la lista desplegable **Mostrar configuración para**, la configuración predeterminada se muestra como **Predeterminada** en las listas desplegables **Primer plano del elemento** y **Fondo del elemento**. Elija el botón **Personalizado** para cambiar esta configuración.

También puede cambiar la configuración de cómo se muestra el texto en el editor. Esta es la manera de hacerlo.

1. En el menú **Herramientas** , elija **Opciones**.

1. Elija **Entorno** > **Fuentes y colores**.

1. Seleccione una opción en el menú desplegable **Mostrar configuración para**.

    Para cambiar el tamaño de fuente del texto en un editor, pulse **Editor de texto**.

    Para cambiar el tamaño de fuente del texto en ventanas de herramientas basadas en texto, pulse **[Todas las ventanas de herramientas de texto]** .

    Para cambiar el tamaño de fuente del texto de información sobre herramientas en un editor, pulse **Información sobre herramientas del editor**.

    Para cambiar el tamaño de fuente del texto en elementos emergentes de finalización de instrucciones, pulse **Finalización de instrucciones**.

1. Desde **Mostrar elementos**, seleccione **Texto sin formato**.

1. En **Fuente**, seleccione un nuevo tipo de fuente.

1. En **Tamaño**, seleccione un nuevo tamaño de fuente.

    > [!TIP]
    > Para restablecer el tamaño de texto para las ventanas de herramientas basadas en texto y los editores, pulse **Usar valores predeterminados**.

7. Elija **Aceptar**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Cambio de los colores que se usan en el IDE

Puede decidir cambiar los colores predeterminados del texto, los indicadores de margen, el espacio en blanco y los elementos de código en el editor. Esta es la manera de hacerlo.

1. En el menú **Herramientas** , elija **Opciones**.

1. En la carpeta **Entorno**, seleccione **Fuentes y colores**.

1. En **Mostrar configuración para**, seleccione **Editor de texto**.

1. Desde **Mostrar elementos**, seleccione un elemento cuya visualización necesita cambiar, como **Texto sin formato**, **Margen del indicador**, **Espacio en blanco visible**, **Nombre del atributo HTML** o **Atributo XML**.

1. Seleccione la configuración de pantalla en las siguientes opciones: **Primer plano del elemento**, **Fondo del elemento** y **Negrita**.

1. Elija **Aceptar**.

> [!TIP]
> Para usar colores de alto contraste en todas las ventanas de aplicaciones en su sistema operativo, presione **Alt izq**+**Mayús izq**+**Impr Pant**. Si Visual Studio está abierto, ciérrelo y vuelva a abrirlo para implementar totalmente los colores de contraste alto.

## <a name="toolbars"></a>Barras de herramientas

Para mejorar la accesibilidad y la facilidad de uso de la barra de herramientas, puede agregar texto a los botones de la barra de herramientas.

### <a name="to-assign-text-to-toolbar-buttons"></a>Para asignar texto a los botones de la barra de herramientas

1. En el menú **Herramientas**, pulse **Personalizar**.

1. En el cuadro de diálogo **Personalizar**, seleccione la pestaña **Comandos**.

1. Seleccione **Barra de herramientas** y, después, elija el nombre de la barra de herramientas que contiene el botón para el que intenta mostrar el texto.

1. En la lista, seleccione el comando que intenta cambiar.

1. Pulse **Modificar selección**.

1. Pulse **Imagen y texto**.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Para modificar el texto mostrado en un botón

1. Vuelva a seleccionar **Modificar selección**.

1. Junto a **Nombre**, inserte un nuevo título para el botón seleccionado.

## <a name="see-also"></a>Vea también

* [Características de accesibilidad de Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Accesibilidad de Visual Studio para Mac](/visualstudio/mac/accessibility/)
* [Recursos para diseñar aplicaciones accesibles](../../ide/reference/resources-for-designing-accessible-applications.md)
