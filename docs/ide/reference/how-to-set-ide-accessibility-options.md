---
title: "C&#243;mo: Establecer opciones de accesibilidad de IDE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "accesibilidad [Visual Studio]"
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# C&#243;mo: Establecer opciones de accesibilidad de IDE
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se incluyen características que facilitan su uso a las personas con problemas de visión o con limitaciones para escribir.  Entre estas características cabe destacar las siguientes: cambiar el tamaño y el color del texto de los editores, cambiar el tamaño del texto y de los botones de las barras de herramientas y finalizar automáticamente los métodos y parámetros.  
  
 Además, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es compatible con los diseños de teclado Dvorak, que permiten una mayor accesibilidad a los caracteres más presionados del teclado.  Asimismo, se pueden personalizar las teclas de método abreviado predeterminadas disponibles en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Para obtener más información, vea [Identificar y personalizar métodos abreviados de teclado](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Editores, cuadros de diálogo y ventanas de herramientas  
 De forma predeterminada, los cuadros de diálogo y ventanas de herramientas de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizan el mismo tamaño de fuente y colores que el sistema operativo.  Las definiciones de colores para el cuadro del IDE, cuadros de diálogo, de barras de herramientas, y las ventanas de herramientas se basan una combinación de colores: luz u otro oscuro.  Puede cambiar el tema de color actual en [General, Entorno, Opciones \(Cuadro de diálogo\)](../../ide/reference/general-environment-options-dialog-box.md).  
  
 También puede mostrar ventanas emergentes en la vista Código del editor.  Estas ventanas pueden solicitar los miembros disponibles en el objeto actual y los parámetros para completar una función o instrucción.  Estas ventanas pueden resultar útiles si tiene dificultades para escribir.  Sin embargo, interfieren con el foco en el editor de código, que puede resultar problemático para algunos usuarios.  Puede desactivar estas ventanas abriendo el cuadro de diálogo Opciones y borrando **Lista de miembros automática** y **Información de parámetros** en **Editor de texto**, **Todos los lenguajes**, página **General** en el cuadro **Opciones** .  Para obtener más información, vea [How to: Set General Editor Options](http://msdn.microsoft.com/es-es/704e4a7b-2162-4bed-8a47-f4f6ffec98c2).  
  
 Las ventanas del entorno de desarrollo integrado \(IDE\) se pueden reorganizar para adaptarlas al modo de trabajo del usuario.  Puede acoplar, desacoplar, ocultarlas, o automáticamente ocultar cada ventana de herramientas.  
  
 Para obtener más información sobre cómo cambiar los diseños de ventana, vea [Personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
### Cambiar el tamaño de texto  
 Puede cambiar la configuración de las ventanas de herramientas basadas en texto, como la ventana **Comando**, la ventana **Inmediato** y la **Ventana de salida** del panel **Fuentes y colores**, incluido en las opciones de **Entorno** del cuadro de diálogo **Herramientas**.  Cuando se selecciona la opción **\[Todas las ventanas de herramientas de texto\]** en la lista desplegable **Mostrar valores para**, la configuración predeterminada aparece como **Predeterminada** en las listas desplegables **Primer plano del elemento** y **Fondo del elemento**.  También puede cambiar la configuración de la forma en la que se muestra el texto en el editor.  
  
##### Para cambiar el tamaño del texto en ventanas de herramientas basadas en texto y editores  
  
1.  En el menú **Herramientas**, elija **Opciones**.  
  
2.  Elija **Fuentes y colores** en la carpeta **Entorno**.  
  
3.  Seleccione una opción en el menú desplegable **Mostrar valores para**.  
  
     Para cambiar el tamaño de fuente del texto de un editor, elija **Editor de texto**.  
  
     Para cambiar el tamaño de fuente del texto en ventanas de herramientas basadas en texto, elija **\[Todas las ventanas de herramientas de texto\]**.  
  
     Para cambiar el tamaño de fuente del texto de información sobre herramientas de un editor, elija **Información sobre herramientas del editor**.  
  
     Para cambiar el tamaño de fuente del texto en menús emergentes de finalización de instrucciones, elija **Finalización de instrucciones**.  
  
4.  En **Mostrar los elementos**, seleccione **Texto sin formato**.  
  
5.  En **Fuente**, seleccione otro tipo de fuente.  
  
6.  En **Tamaño**, seleccione otro tamaño de fuente.  
  
    > [!NOTE]
    >  Para restablecer el tamaño del texto de las ventanas de herramientas y editores basados en texto, elija **Usar predeterminados**.  
  
7.  Elija **Aceptar**.  
  
### Cambiar los colores utilizados en el IDE  
 También puede decidir cambiar los colores predeterminados del texto, los indicadores de margen, los espacios en blanco y los elementos de código del editor.  
  
> [!NOTE]
>  Para utilizar los colores de contraste alto en todas las ventanas de la aplicación del sistema operativo, presione **ALT\+ MAYÚS izquierda\+IMPR PANT**.  Si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está abierto, ciérrelo y vuélvalo a abrir para implementar los colores de contraste alto.  
  
##### Para cambiar el color de los elementos del editor  
  
1.  En el menú **Herramientas**, elija **Opciones**.  
  
2.  Elija **Fuentes y colores** en la carpeta **Entorno**.  
  
3.  En **Mostrar valores para**, elija **Editor de texto**.  
  
4.  En **Mostrar los elementos**, seleccione un elemento cuya apariencia deba cambiar, como **Texto sin formato**, **Margen del indicador**, **Espacio en blanco visible**, **Nombre del atributo HTML** o **Atributo XML**.  
  
5.  Seleccione la configuración de pantalla desde las opciones siguientes: **Primer plano del elemento**, **Fondo del elemento** y **Negrita**.  
  
6.  Elija **Aceptar**.  
  
## Barras de herramientas  
 Para mejorar utilidad y accesibilidad de la barra de herramientas, puede agregar texto a los botones de la barra de herramientas.  
  
#### Para asignar texto a los botones de la barra de herramientas  
  
1.  En el menú **Herramientas**, elija **Personalizar**.  
  
2.  En el cuadro de diálogo **Personalizar**, seleccione la ficha **Comandos**.  
  
3.  Seleccione **Barra de herramientas** y, a continuación, elija el nombre de la barra de herramientas que contiene el botón para el que desea mostrar el texto.  
  
4.  En la lista, seleccione el comando que desee cambiar.  
  
5.  Elija **Modificar selección**.  
  
6.  Elija **Imagen y texto**.  
  
#### Para modificar el texto que aparece en el botón  
  
1.  Vuelva a seleccionar **Modificar selección**.  
  
2.  Junto a **Nombre**, inserción proporciona una nueva leyenda para el botón seleccionado.  
  
## Vea también  
 [Características de accesibilidad de Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)   
 [Recursos para diseñar aplicaciones accesibles](../../ide/reference/resources-for-designing-accessible-applications.md)