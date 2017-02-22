---
title: "C&#243;mo: Administrar los modos del editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editor de código, modos"
  - "Editor de código, opciones de ver y mostrar"
  - "fuentes y tamaño"
  - "modo de pantalla completa"
  - "números de línea"
  - "números de línea, mostrar"
  - "vistas, cambiar modo"
  - "vistas, crear ventanas nuevas"
  - "vistas, números de línea"
  - "vistas, esquematizar"
  - "vistas, dividir"
  - "vistas, espacio virtual"
  - "vistas, ajuste de línea"
  - "modo de espacio virtual"
  - "ajuste de línea"
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Administrar los modos del editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Editor de código de Visual Studio dispone de varios modos de presentación.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Habilitar el modo Pantalla completa  
 Se puede elegir ocultar todas las ventanas de herramientas y ver sólo las ventanas de documento habilitando el modo **Pantalla completa**.  
  
#### Para habilitar el modo Pantalla completa  
  
-   Presione ALT \+ MAYÚS \+ ENTRAR para entrar o salir del modo **Pantalla completa**.  
  
     O bien  
  
-   Ejecute el comando `View.Fullscreen` en la ventana **Comando**.  
  
## Habilitar el modo Espacio virtual  
 En modo **Espacio virtual**, se insertan espacios al final de cada línea de código.  Seleccione esta opción para colocar los comentarios en una posición coherente al lado del código.  
  
#### Para habilitar el modo Espacio virtual  
  
1.  Seleccione **Opciones** en el menú **Herramientas**.  
  
2.  Expanda la carpeta **Editor de texto** y elija **Todos los lenguajes** para establecer esta opción globalmente, o elija una carpeta de lenguaje concreta.  Por ejemplo, para activar los números de línea sólo en Visual Basic, elija Basic en las opciones del Editor de texto.  
  
3.  Seleccione las opciones **General** y en **Configuración**, seleccione **Habilitar espacio virtual**.  
  
    > [!NOTE]
    >  **Espacio virtual** se habilita en modo **Selección de columnas**.  Cuando el modo **Espacio virtual** no está habilitado, el punto de inserción se desplaza directamente desde el final de una línea al primer carácter de la siguiente.  
  
## Vea también  
 [Personalizar el editor](../ide/customizing-the-editor.md)   
 [Cómo: Organizar y acoplar ventanas](../misc/how-to-arrange-and-dock-windows.md)   
 [Fuentes y colores, Entorno, Opciones \(Cuadro de diálogo\)](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)