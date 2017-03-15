---
title: "Opciones, editor de texto, C/C++, formato | Microsoft Docs"
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
  - "VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Cuadro de diálogo Opciones del Editor de texto, formato"
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opciones, editor de texto, C/C++, formato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Permite cambiar el comportamiento predeterminado del editor de código cuando se programa en C o C\+\+.  
  
 Para tener acceso a esta página, en el cuadro de diálogo **Opciones**, en el panel izquierdo, expanda **Editor de texto**, expanda **C\/C\+\+** y, a continuación, haga clic en **Formato**.  
  
> [!NOTE]
>  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté utilizando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Opciones de C\/C\+\+  
 **Habilitar información rápida sobre herramientas automática**  
 Habilita o deshabilita la característica de IntelliSense Información rápida.  
  
## Código inactivo  
 **Mostrar bloques inactivos**  
 El código que está inactivo debido a las declaraciones `#ifdef` aparece con un color diferente para facilitar su identificación.  
  
 **Deshabilitar opacidad de código inactivo**  
 El código inactivo se puede identificar utilizando el color en lugar de la transparencia.  
  
 **Porcentaje de opacidad del código inactivo**  
 Se puede personalizar el grado de opacidad de los bloques de código inactivos.  
  
## Sangría  
 **Aplicar sangría a las llaves**  
 Puede configurar cómo se alinean las llaves cuando se presiona ENTRAR después de comenzar un bloque de código, por ejemplo, una función o un bucle `for`.  Las llaves pueden estar alineadas con el primer carácter del bloque de código o con sangría.  
  
 **Sangría automática con tecla TAB**  
 Puede configurar lo que ocurre en la línea de código actual al presionar TAB.  Se aplica sangría a la línea o bien se inserta un carácter de tabulación.  
  
## Varios  
 **Enumerar tareas de comentario**  
 El editor puede analizar archivos de código fuente abiertos para buscar palabras preestablecidas en los comentarios.  Crea una entrada en la ventana **Lista de tareas** para todas las palabras clave que encuentra.  
  
 **Resaltar tokens de emparejamiento**  
 Cuando se coloca el cursor junto a una llave, el editor puede resaltar la llave correspondiente de modo que pueda ver el código incluido entre llaves más fácilmente.  
  
## Esquematización  
 **Especificar el modo de esquematización al abrir los archivos**  
 Cuando se coloca un archivo en el editor de texto, se puede habilitar la característica de esquematización.  Para obtener más información, vea [Esquematización](../../ide/outlining.md).  Cuando esta opción está seleccionada, la característica de esquematización se habilita al abrir un archivo.  
  
 **Esquematizar regiones pragma**  
 Cuando esta opción está seleccionada, se habilita la esquematización automática de las [directivas pragma](/visual-cpp/preprocessor/pragma-directives-and-the-pragma-keyword).  Esto permite expandir o contraer bloques de región pragma en modo de esquematización.  
  
 **Esquematizar bloques de instrucciones**  
 Al seleccionar esta opción, se habilita la esquematización automática de las construcciones de instrucción siguientes:  
  
-   [if\-else](/dotnet/csharp/language-reference/keywords/if-else)  
  
-   [switch \(Instrucción\) \(C\+\+\)](/visual-cpp/cpp/switch-statement-cpp)  
  
-   [while \(Instrucción\) \(C\+\+\)](/visual-cpp/cpp/while-statement-cpp)  
  
## Vea también  
 [General, Entorno, Opciones \(Cuadro de diálogo\)](../../ide/reference/general-environment-options-dialog-box.md)   
 [Utilizar IntelliSense](../../ide/using-intellisense.md)