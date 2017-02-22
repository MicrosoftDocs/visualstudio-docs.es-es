---
title: "Opciones, editor de texto, C#, IntelliSense | Microsoft Docs"
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
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense"
helpviewer_keywords: 
  - "IntelliSense [J#], opciones"
  - "subrayados, ondulados"
  - "IntelliSense [C#], opciones"
  - "IntelliSense [C#], subrayados ondulados"
  - "subrayados ondulados"
  - "Cuadro de diálogo Opciones del Editor de texto, IntelliSense"
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 25
caps.handback.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opciones, editor de texto, C#, IntelliSense
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilice la página de propiedades **IntelliSense** si desea modificar la configuración que afecta al comportamiento de IntelliSense para Visual C\# .  Para obtener acceso a la página de propiedades **IntelliSense**, haga clic en **Opciones**, en el menú **Herramientas** y, a continuación, en la carpeta **Editor de texto**, haga clic en **C\#**; por último, seleccione **IntelliSense**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 La página de propiedades **IntelliSense** contiene las propiedades siguientes:  
  
## Listas de finalización  
 **Mostrar la lista de finalización después de escribir un carácter**  
 Cuando esta opción está seleccionada, IntelliSense muestra la lista de finalización automáticamente al comenzar a escribir.  Cuando no está seleccionada, la finalización de IntelliSense sigue estando disponible en el menú **IntelliSense** o al presionar CTRL \+ BARRA ESPACIADORA.  
  
 **Colocar palabras clave en las listas de finalización**  
 Cuando esta opción está seleccionada, IntelliSense agrega palabras clave de C\#  \(por ejemplo, [clase](/dotnet/csharp/language-reference/keywords/class)\) a la lista de finalización.  
  
 **Colocar fragmentos de código en las listas de finalización**  
 Cuando esta opción está seleccionada, IntelliSense agrega alias de los fragmentos de código de C\# a la lista de finalización.  En caso de que el alias del fragmento de código sea igual a una palabra clave \(por ejemplo, [clase](/dotnet/csharp/language-reference/keywords/class)\), la palabra clave se reemplaza con el acceso directo.  Para obtener más información, vea [Fragmentos de código de Visual C\#](../../ide/visual-csharp-code-snippets.md).  
  
## Selección en listas de finalización  
 **Ejecutado escribiendo los siguientes caracteres:**  
 Especifica todos los caracteres que, una vez escritos, ejecutan la finalización automática de IntelliSense del elemento seleccionado en la lista de finalización.  
  
 **Ejecutado presionando la barra espaciadora**  
 Especifica que se ha de incluir la acción de presionar la barra espaciadora para ejecutar la finalización automática de IntelliSense del elemento seleccionado en la lista de finalización.  
  
 **Agregar nueva línea con Entrar al final de palabras completas**  
 Especifica que si se escriben todos los caracteres de una entrada en la lista de finalización y, a continuación, se presiona ENTRAR, se crea automáticamente una nueva línea y el cursor se mueve hacia esa línea.  
  
 Por ejemplo, si se escribe `else` y, a continuación, se presiona ENTRAR, aparecerá lo siguiente en el editor:  
  
 `else`  
  
 `|` \(ubicación del cursor\)  
  
 Sin embargo, si sólo escribe `el` y, a continuación, presiona ENTRAR, lo siguiente aparece en el editor:  
  
 `else|` \(ubicación del cursor\)  
  
## Selección de miembro de IntelliSense  
 **Preselecciona el miembro usado más recientemente**  
 Cuando se selecciona esta opción, IntelliSense preselecciona a los miembros que hayan seleccionado recientemente en el cuadro de miembros de los lista emergente para Autocompletar nombres de objetos, durante la sesión actual en el entorno de desarrollo integrado \(IDE\).  El historial de los miembros usados recientemente se borra entre cada sesión del IDE.  Para obtener más información, vea [IntelliSense para los miembros utilizados más recientemente](../../misc/intellisense-for-most-recently-used-members.md).  
  
## Vea también  
 [General, Entorno, Opciones \(Cuadro de diálogo\)](../../ide/reference/general-environment-options-dialog-box.md)   
 [Comentarios de documentación XML](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [Utilizar IntelliSense](../../ide/using-intellisense.md)