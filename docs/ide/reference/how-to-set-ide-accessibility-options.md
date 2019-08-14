---
title: Procedimiento Establecimiento de opciones de accesibilidad de IDE
description: Obtenga información sobre cómo establecer las opciones de accesibilidad en Visual Studio para que el entorno de desarrollo integrado (IDE) sea más fácil de usar para todos, incluidos los usuarios con problemas de visión para leer y con limitaciones para escribir.
ms.date: 08/22/2017
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a0b5835333bf8cd41ab653108054e2d3dd4c73e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919280"
---
# <a name="how-to-set-ide-accessibility-options"></a>Procedimiento Establecimiento de opciones de accesibilidad de IDE

> [!TIP]
> Para más información sobre las actualizaciones de accesibilidad recientes, vea la entrada de blog [Accessibility improvements in Visual Studio 2017 version 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Mejoras de accesibilidad en Visual Studio 2017 versión 15.3).

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contiene características que facilitan la lectura a las personas que tienen poca visión y la escritura a las personas que tienen una destreza manual limitada. Estas características incluyen el cambio del tamaño y el color del texto en los editores, el cambio del tamaño de texto y de los botones de opción en las barras de herramientas y la función Autocompletar para métodos y parámetros, entre otras.

Además, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite los diseños de teclado Dvorak, que hacen que los caracteres que se escriben con más frecuencia estén más accesibles. También puede personalizar las teclas de método abreviado predeterminadas disponibles con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obtener más información, vea [Identificar y personalizar métodos abreviados de teclado](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Restablecer la configuración](../environment-settings.md#reset-settings).

## <a name="editors-dialogs-and-tool-windows"></a>Editores, cuadros de diálogo y ventanas de herramientas

De manera predeterminada, los cuadros de diálogo y las ventanas de herramientas en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usan el mismo tamaño de fuente y los mismos colores que el sistema operativo. La configuración del color del marco del IDE, los cuadros de diálogo, las barras de herramientas y las ventanas de herramientas se basan en una combinación de colores: clara u oscura. Puede cambiar el tema de color actual en [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md).

También puede mostrar ventanas emergentes en la vista Código del editor. Estas ventanas pueden indicarle los miembros disponibles en el objeto actual y los parámetros para completar una función o instrucción. Estas ventanas pueden resultar útiles si tiene dificultades para escribir. En cambio, interfieren con el foco del editor de código, que puede ser problemático para algunos usuarios. Puede desactivar estas ventanas abriendo el cuadro de diálogo Opciones y desactivar **Lista de miembros automática** e **Información de parámetros** en el **Editor de texto**, **Todos los lenguajes**, página **General** en el cuadro de diálogo **Opciones**.

Puede reorganizar las ventanas del entorno de desarrollo integrado (IDE) para adaptarse mejor a su manera de trabajar. Puede acoplar, hacer flotante, ocultar u ocultar automáticamente cada ventana de herramientas.

Para obtener más información sobre cómo cambiar los diseños de ventanas, vea [Personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="changing-the-size-of-text"></a>Cambio del tamaño del texto

Puede cambiar la configuración de las ventanas de herramientas basadas en texto, como la ventana **Comandos**, la ventana **Inmediato** y la ventana **Salida**, en el panel **Fuentes y colores** de las opciones de **Entorno** en el cuadro de diálogo **Herramientas**. Cuando la opción **[Todas las ventanas de herramientas de texto]** está seleccionada en la lista desplegable **Mostrar configuración para**, la configuración predeterminada se muestra como **Predeterminada** en las listas desplegables **Primer plano del elemento** y **Fondo del elemento**. También puede cambiar la configuración de cómo se muestra el texto en el editor.

#### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Para cambiar el tamaño del texto en las ventanas de herramientas basadas en texto y en los editores

1. En el menú **Herramientas** , elija **Opciones**.

2. Pulse **Fuentes y colores** en la carpeta **Entorno**.

3. Seleccione una opción en el menú desplegable **Mostrar configuración para**.

     Para cambiar el tamaño de fuente del texto en un editor, pulse **Editor de texto**.

     Para cambiar el tamaño de fuente del texto en ventanas de herramientas basadas en texto, pulse **[Todas las ventanas de herramientas de texto]** .

     Para cambiar el tamaño de fuente del texto de información sobre herramientas en un editor, pulse **Información sobre herramientas del editor**.

     Para cambiar el tamaño de fuente del texto en elementos emergentes de finalización de instrucciones, pulse **Finalización de instrucciones**.

4. Desde **Mostrar elementos**, seleccione **Texto sin formato**.

5. En **Fuente**, seleccione un nuevo tipo de fuente.

6. En **Tamaño**, seleccione un nuevo tamaño de fuente.

    > [!NOTE]
    > Para restablecer el tamaño de texto para las ventanas de herramientas basadas en texto y los editores, pulse **Usar valores predeterminados**.

7. Elija **Aceptar**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Cambio de los colores que se usan en el IDE

También puede decidir cambiar los colores predeterminados del texto, los indicadores de margen, el espacio en blanco y los elementos de código en el editor.

> [!NOTE]
> Para usar colores de alto contraste para todas las ventanas de aplicaciones en su sistema operativo, presione <strong>ALT+</strong> izquierda y **MAYÚS+IMPR PANT** izquierda. Si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está abierto, cierre y vuelve a abrir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para implementar completamente los colores de alto contraste.

#### <a name="to-change-the-color-of-items-in-the-editor"></a>Para cambiar el color de elementos en el editor

1. En el menú **Herramientas** , elija **Opciones**.

2. En la carpeta **Entorno**, seleccione **Fuentes y colores**.

3. En **Mostrar configuración para**, seleccione **Editor de texto**.

4. Desde **Mostrar elementos**, seleccione un elemento cuya visualización necesita cambiar, como **Texto sin formato**, **Margen del indicador**, **Espacio en blanco visible**, **Nombre del atributo HTML** o **Atributo XML**.

5. Seleccione la configuración de pantalla en las siguientes opciones: **Primer plano del elemento**, **Fondo del elemento** y **Negrita**.

6. Elija **Aceptar**.

## <a name="toolbars"></a>Barras de herramientas

Para mejorar la accesibilidad y la facilidad de uso de la barra de herramientas, puede agregar texto a los botones de la barra de herramientas.

### <a name="to-assign-text-to-toolbar-buttons"></a>Para asignar texto a los botones de la barra de herramientas

1. En el menú **Herramientas**, pulse **Personalizar**.

2. En el cuadro de diálogo **Personalizar**, seleccione la pestaña **Comandos**.

3. Seleccione **Barra de herramientas** y, después, pulse el nombre de la barra de herramientas que contiene el botón para el que intenta mostrar el texto.

4. En la lista, seleccione el comando que intenta cambiar.

5. Pulse **Modificar selección**.

6. Pulse **Imagen y texto**.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Para modificar el texto mostrado en un botón

1. Vuelva a seleccionar **Modificar selección**.

2. Junto a **Nombre**, inserte un nuevo título para el botón seleccionado.

## <a name="see-also"></a>Vea también

* [Características de accesibilidad de Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Recursos para diseñar aplicaciones accesibles](../../ide/reference/resources-for-designing-accessible-applications.md)