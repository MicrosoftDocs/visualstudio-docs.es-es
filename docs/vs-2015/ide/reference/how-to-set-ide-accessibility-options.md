---
title: 'Cómo: Establecer opciones de accesibilidad de IDE | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4ee29fd6309db34d4e0e4a013149e268051ab0e5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704395"
---
# <a name="how-to-set-ide-accessibility-options"></a>Cómo: Establecer opciones de accesibilidad de IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] contiene características que facilitan la lectura a las personas que tienen poca visión y la escritura a las personas que tienen una destreza manual limitada. Estas características incluyen el cambio del tamaño y el color del texto en los editores, el cambio del tamaño de texto y de los botones de opción en las barras de herramientas y la función Autocompletar para métodos y parámetros, entre otras.  
  
 Además, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] admite los diseños de teclado Dvorak, que hacen que los caracteres que se escriben con más frecuencia estén más accesibles. También puede personalizar las teclas de método abreviado predeterminadas disponibles con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Para obtener más información, vea [Identificar y personalizar métodos abreviados de teclado](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="editors-dialogs-and-tool-windows"></a>Editores, cuadros de diálogo y ventanas de herramientas  
 De manera predeterminada, los cuadros de diálogo y las ventanas de herramientas en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usan el mismo tamaño de fuente y los mismos colores que el sistema operativo. La configuración del color del marco del IDE, los cuadros de diálogo, las barras de herramientas y las ventanas de herramientas se basan en una combinación de colores: clara u oscura. Puede cambiar el tema del color actual en [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md).  
  
 También puede mostrar ventanas emergentes en la vista Código del editor. Estas ventanas pueden indicarle los miembros disponibles en el objeto actual y los parámetros para completar una función o instrucción. Estas ventanas pueden resultar útiles si tiene dificultades para escribir. En cambio, interfieren con el foco del editor de código, que puede ser problemático para algunos usuarios. Puede desactivar estas ventanas abriendo el cuadro de diálogo Opciones y desactivar **Lista de miembros automática** e **Información de parámetros** en el **Editor de texto**, **Todos los lenguajes**, página **General** en el cuadro de diálogo **Opciones**. Para obtener más información, vea [Cómo: Establecer opciones generales del editor](https://msdn.microsoft.com/704e4a7b-2162-4bed-8a47-f4f6ffec98c2).  
  
 Puede reorganizar las ventanas del entorno de desarrollo integrado (IDE) para adaptarse mejor a su manera de trabajar. Puede acoplar, hacer flotante, ocultar u ocultar automáticamente cada ventana de herramientas.  
  
 Para obtener más información sobre cómo cambiar los diseños de ventanas, vea [Personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
### <a name="changing-the-size-of-text"></a>Cambiar el tamaño del texto  
 Puede cambiar la configuración de las ventanas de herramientas basadas en texto, como la ventana **Comandos**, la ventana **Inmediato** y la ventana **Salida**, en el panel **Fuentes y colores** de las opciones de **Entorno** en el cuadro de diálogo **Herramientas**. Cuando la opción **[Todas las ventanas de herramientas de texto]** está seleccionada en la lista desplegable **Mostrar configuración para**, la configuración predeterminada se muestra como **Predeterminada** en las listas desplegables **Primer plano del elemento** y **Fondo del elemento**. También puede cambiar la configuración de cómo se muestra el texto en el editor.  
  
##### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Para cambiar el tamaño del texto en las ventanas de herramientas basadas en texto y en los editores  
  
1. En el menú **Herramientas** , elija **Opciones**.  
  
2. Pulse **Fuentes y colores** en la carpeta **Entorno**.  
  
3. Seleccione una opción en el menú desplegable **Mostrar configuración para**.  
  
     Para cambiar el tamaño de fuente del texto en un editor, pulse **Editor de texto**.  
  
     Para cambiar el tamaño de fuente del texto en ventanas de herramientas basadas en texto, pulse **[Todas las ventanas de herramientas de texto]**.  
  
     Para cambiar el tamaño de fuente del texto de información sobre herramientas en un editor, pulse **Información sobre herramientas del editor**.  
  
     Para cambiar el tamaño de fuente del texto en elementos emergentes de finalización de instrucciones, pulse **Finalización de instrucciones**.  
  
4. Desde **Mostrar elementos**, seleccione **Texto sin formato**.  
  
5. En **Fuente**, seleccione un nuevo tipo de fuente.  
  
6. En **Tamaño**, seleccione un nuevo tamaño de fuente.  
  
    > [!NOTE]
    > Para restablecer el tamaño de texto para las ventanas de herramientas basadas en texto y los editores, pulse **Usar valores predeterminados**.  
  
7. Elija **Aceptar**.  
  
### <a name="changing-the-colors-used-in-the-ide"></a>Cambiar los colores usados en el IDE  
 También puede decidir cambiar los colores predeterminados del texto, los indicadores de margen, el espacio en blanco y los elementos de código en el editor.  
  
> [!NOTE]
> Para usar colores de alto contraste para todas las ventanas de aplicaciones en su sistema operativo, presione <strong>ALT+</strong> izquierda y **MAYÚS+IMPR PANT** izquierda. Si [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] está abierto, cierre y vuelve a abrir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para implementar completamente los colores de alto contraste.  
  
##### <a name="to-change-the-color-of-items-in-the-editor"></a>Para cambiar el color de elementos en el editor  
  
1. En el menú **Herramientas** , elija **Opciones**.  
  
2. Pulse **Fuentes y colores** de la carpeta **Entorno**.  
  
3. En **Mostrar configuración para**, seleccione **Editor de texto**.  
  
4. Desde **Mostrar elementos**, seleccione un elemento cuya visualización necesita cambiar, como **Texto sin formato**, **Margen del indicador**, **Espacio en blanco visible**, **Nombre del atributo HTML** o **Atributo XML**.  
  
5. Seleccione la configuración de visualización desde las siguientes opciones: **Primer plano del elemento**, **Fondo del elemento** y **Negrita**.  
  
6. Elija **Aceptar**.  
  
## <a name="toolbars"></a>Barras de herramientas  
 Para mejorar la accesibilidad y la facilidad de uso de la barra de herramientas, puede agregar texto a los botones de la barra de herramientas.  
  
#### <a name="to-assign-text-to-toolbar-buttons"></a>Para asignar texto a los botones de la barra de herramientas  
  
1. En el menú **Herramientas**, pulse **Personalizar**.  
  
2. En el cuadro de diálogo **Personalizar**, seleccione la pestaña **Comandos**.  
  
3. Seleccione **Barra de herramientas** y, después, pulse el nombre de la barra de herramientas que contiene el botón para el que intenta mostrar el texto.  
  
4. En la lista, seleccione el comando que intenta cambiar.  
  
5. Pulse **Modificar selección**.  
  
6. Pulse **Imagen y texto**.  
  
#### <a name="to-modify-the-buttons-displayed-text"></a>Para modificar el texto mostrado del botón  
  
1. Vuelva a seleccionar **Modificar selección**.  
  
2. Junto a **Nombre**, inserte un nuevo título para el botón seleccionado.  
  
## <a name="see-also"></a>Vea también  
 [Características de accesibilidad de Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)   
 [Recursos para diseñar aplicaciones accesibles](../../ide/reference/resources-for-designing-accessible-applications.md)
