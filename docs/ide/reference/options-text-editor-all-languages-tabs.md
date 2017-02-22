---
title: "Opciones, editor de texto, todos los lenguajes, pesta&#241;as | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs"
helpviewer_keywords: 
  - "sangrías, Editor de código"
  - "Editor de código, comportamiento predeterminado"
  - "pestañas, configuración en el Editor de código"
  - "Todos los lenguajes, Editor de texto, Opciones (cuadro de diálogo)"
  - "editores, Editor de código"
  - "Editor de código, aplicar sangría"
  - "Editor de código, pestañas"
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opciones, editor de texto, todos los lenguajes, pesta&#241;as
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En este cuadro de diálogo se puede cambiar el comportamiento predeterminado del Editor de código.  Esta configuración también afecta a los demás editores basados en el Editor de código, como la vista Código fuente del Diseñador HTML.  Para mostrar estas opciones, seleccione **Opciones** en el menú **Herramientas**.  Dentro de la carpeta **Editor de texto**, expanda la subcarpeta **Todos los lenguajes** y, a continuación, elija **Tabulaciones**.  
  
> [!CAUTION]
>  En esta página se establecen opciones predeterminadas para todos los lenguajes de programación.  Recuerde que si se restablece una opción en este cuadro de diálogo, se restablecerán las opciones Tabulaciones para todos los lenguajes según las opciones aquí seleccionadas.  Para cambiar las opciones del Editor de texto para un lenguaje solamente, expanda la subcarpeta de dicho lenguaje y seleccione su página de opciones.  
  
 Si se han seleccionado configuraciones diferentes para lenguajes de programación concretos en las páginas de opciones Tabulaciones, se mostrará el mensaje "Los valores de la sangría para formatos de texto individuales están en conflicto entre sí" cuando difieran las opciones de **Sangría**; y el mensaje "Los valores del tabulador para formatos de texto individuales están en conflicto entre sí" cuando difieran las opciones de **Tabulación**.  Por ejemplo, se mostrará este mensaje si se selecciona la opción **Sangría automática** para Visual Basic y la opción **Bloquear sangría** para Visual C\+\+.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Sangría  
 None  
 Cuando está seleccionada, no se aplica sangría a las nuevas líneas.  El punto de inserción se coloca en la primera columna de una nueva línea.  
  
 Bloque  
 Cuando está seleccionada, se aplica sangría automáticamente a las nuevas líneas.  El punto de inserción se coloca en el mismo punto inicial que la línea anterior.  
  
 Automática  
 Cuando está seleccionada, las nuevas líneas se ajustan al contexto del código, de acuerdo con otras configuraciones de formato de código y convenciones de IntelliSense para el lenguaje de programación correspondiente.  Esta opción no está disponible para todos los lenguajes de programación.  
  
 Por ejemplo, a las líneas incluidas entre una llave de apertura \( { \) y otra de cierre \( } \) se les puede aplicar automáticamente una sangría de una tabulación adicional a partir de la posición de las llaves alineadas.  
  
## Tabulaciones  
 Tamaño de tabulación  
 Establece la distancia en espacios entre las tabulaciones.  El valor predeterminado es cuatro espacios.  
  
 Tamaño de sangría  
 Establece el tamaño en espacios de una sangría automática.  El valor predeterminado es cuatro espacios.  Se insertan caracteres de tabulación, caracteres de espacio o ambos, para llenar el tamaño especificado.  
  
 Insertar espacios  
 Cuando está seleccionada, las operaciones de sangría insertarán sólo caracteres de espacio, no caracteres de tabulación.  Si el **Tamaño de sangría** se establece en 5, se insertarán cinco caracteres de espacio siempre que presione la tecla TAB o haga clic en el botón **Aumentar sangría** de la barra de herramientas **Formato**.  
  
 Mantener tabulaciones  
 Cuando está seleccionada, las operaciones de sangría insertarán tantos caracteres de tabulación como sea posible.  Cada carácter TAB rellena el número de espacios especificado en la opción **Tamaño de tabulación**.  Si el **Tamaño de sangría** no es un múltiplo par del **Tamaño de tabulación**, se agregan caracteres de espacio en blanco para igualar la diferencia.  
  
## Vea también  
 [Opciones, Editor de texto, Todos los lenguajes](../../ide/reference/options-text-editor-all-languages.md)   
 [General, Entorno, Opciones \(Cuadro de diálogo\)](../../ide/reference/general-environment-options-dialog-box.md)