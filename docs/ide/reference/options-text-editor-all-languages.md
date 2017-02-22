---
title: "Opciones, Editor de texto, Todos los lenguajes | Microsoft Docs"
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
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.General"
  - "VS.ToolsOptionsPages.Text_Editor.ResJSON.General"
  - "vs.toolsoptionspages.text_editor.all_languages.scrollbars"
helpviewer_keywords: 
  - "Editor de texto, Opciones (cuadro de diálogo)"
  - "finalización de instrucciones"
  - "ajuste de línea"
  - "General (cuadro de diálogo)"
  - "números de línea"
  - "espacio virtual"
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opciones, Editor de texto, Todos los lenguajes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En este cuadro de diálogo se puede cambiar el comportamiento predeterminado del Editor de código.  Esta configuración también afecta a los demás editores basados en el Editor de código, como la vista Código fuente del Diseñador HTML.  Para abrir este cuadro de diálogo, seleccione **Opciones** en el menú **Herramientas**.  Dentro de la carpeta **Editor de texto**, expanda la subcarpeta **Todos los lenguajes** y, a continuación, elija **General**.  
  
> [!CAUTION]
>  En esta página se establecen opciones predeterminadas para todos los lenguajes de programación.  Recuerde que si se restablece una opción en este cuadro de diálogo, se restablecerán las opciones General para todos los lenguajes según las opciones aquí seleccionadas.  Para cambiar las opciones del Editor de texto para un lenguaje solamente, expanda la subcarpeta de dicho lenguaje y seleccione su página de opciones.  
  
 Se mostrará una marca de verificación atenuada cuando se haya seleccionado una opción en las páginas de opciones General para algunos lenguajes de programación, pero no para otros.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Finalización de instrucciones  
 Lista de miembros automática  
 Cuando está seleccionada, IntelliSense mostrará listas emergentes de métodos, valores, propiedades y miembros disponibles al escribir en el editor.  Elija cualquier elemento de la lista emergente para insertarlo en el código.  Al seleccionar esta opción se habilita la opción **Ocultar miembros avanzados**.  
  
 Ocultar miembros avanzados  
 Cuando está seleccionada, se acortan las listas emergentes de finalización de instrucciones mostrando sólo los elementos que más se usan.  Los demás elementos se filtran en la lista.  
  
 Información de parámetros  
 Cuando está seleccionada, la sintaxis completa de la declaración o del procedimiento actual aparece bajo el punto de inserción del editor, con todos los parámetros disponibles.  El siguiente parámetro que se puede asignar aparecerá en negrita.  
  
## Valores  
 Habilitar espacio virtual  
 Cuando se selecciona esta opción y se desactiva **Ajuste de línea**, se puede hacer clic en cualquier punto más allá del final de una línea en el Editor de código y escribir.  Esta característica puede utilizarse para colocar los comentarios en un lugar coherente junto al código.  
  
 Ajuste de línea  
 Cuando está seleccionada, cualquier parte de una línea que se extienda horizontalmente más allá del área visible del editor aparecerá automáticamente en la siguiente línea.  Al seleccionar esta opción se habilita la opción **Mostrar glifos visuales para ajuste de línea**.  
  
> [!NOTE]
>  La característica **Espacio virtual** se desactiva mientras la opción **Ajuste de línea** esté activa.  
  
 Mostrar glifos visuales para ajuste de línea  
 Cuando está seleccionada, se muestra un indicador de flecha de retorno en el que una línea larga se ajusta en una segunda línea.  
  
 Desactive esta opción si prefiere no mostrar estos indicadores.  
  
> [!NOTE]
>  Estas flechas de aviso no se agregan al código ni se imprimen.  Sólo sirven como referencia.  
  
 Aplicar los comandos Cortar o Copiar a las líneas en blanco cuando no haya selección  
 Esta opción establece el comportamiento del editor cuando se coloca el punto de inserción en una línea en blanco, no se selecciona nada y, a continuación, se usa el comando Copiar o Cortar.  
  
-   Cuando se selecciona esta opción, la línea en blanco se copia o se corta.  Si se pega a continuación, se inserta una línea en blanco nueva.  
  
-   Cuando esta opción está desactivada, el comando Cortar quita las líneas en blanco.  Sin embargo, se conservan los datos en el Portapapeles.  Por consiguiente, si se utiliza el comando Pegar, se pegará el último contenido que se haya copiado en el Portapapeles.  Si no se ha copiado nada antes, no se pega nada.  
  
 Este valor no tiene ningún efecto en Copiar o Cortar cuando no es una línea en blanco.  Si no se selecciona nada, se copia o se corta la línea completa.  Si se pega a continuación, se pega el texto de toda la línea y el carácter de fin de línea.  
  
> [!TIP]
>  Con el fin de poder mostrar indicadores para los espacios, tabuladores y fines de la línea, y distinguir así las líneas con sangría de las que están completamente en blanco, en el menú **Edición** seleccione **Opciones avanzadas** y elija **Ver espacios en blanco**.  
  
## Display  
 Números de línea  
 Cuando está seleccionada, aparecerá un número de línea al lado de cada línea de código.  
  
> [!NOTE]
>  Estos números de línea no se agregan al código ni se imprimen.  Sólo sirven como referencia.  
  
 Habilitar navegación a direcciones URL con un solo clic  
 Al seleccionar esta opción, cuando el cursor del mouse pase sobre una dirección URL en el editor, su forma cambiará a una mano que señala.  Puede hacer clic en la dirección URL para mostrar la página indicada en el explorador web.  
  
 Barra de navegación  
 Cuando está seleccionada, se muestra la **Barra de navegación** en la parte superior del editor de código.  Las listas desplegables **Objetos** y **Miembros** permiten elegir un objeto particular del código, seleccionar entre los miembros y navegar a la declaración del miembro seleccionado en el Editor de código.  
  
## Vea también  
 [Opciones, editor de texto, todos los lenguajes, pestañas](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [General, Entorno, Opciones \(Cuadro de diálogo\)](../../ide/reference/general-environment-options-dialog-box.md)   
 [Utilizar IntelliSense](../../ide/using-intellisense.md)