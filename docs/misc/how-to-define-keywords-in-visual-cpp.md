---
title: "C&#243;mo: Definir palabras clave en Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "palabras clave del usuario"
  - "palabras reservadas, palabras clave definidas por el usuario"
  - "palabras clave definidas por el usuario"
  - "palabras clave reservadas, definidas por el usuario"
  - "usertype.dat"
  - "palabras clave [C++], definidas por el usuario"
ms.assetid: 2dfcf343-e861-4bde-b5a4-7deb6773d9c8
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# C&#243;mo: Definir palabras clave en Visual C++
Las palabras clave son identificadores reservados predefinidos que tienen un significado especial para el compilador. No se pueden usar como identificadores en un programa. Sin embargo, puede definir sus propias palabras clave para usar en Visual C\+\+ y puede asignar colores personalizados a la sintaxis de las palabras clave. Colorear la sintaxis aporta indicaciones visuales sobre la estructura y el estado del código.  
  
### Para definir sus propias palabras clave de Visual C\+\+  
  
1.  Use el [editor de código y texto](http://msdn.microsoft.com/es-es/508e1f18-99d5-48ad-b5ad-d011b21c6ab1) de Visual Studio o Notepad.exe para crear un archivo de texto denominado `usertype.dat`.  
  
2.  En `usertype.dat`, escriba cada palabra clave definida por el usuario en una línea independiente.  
  
3.  Guarde `usertype.dat` en el directorio que contiene devenv.exe. De forma predeterminada, la ruta de acceso de ese directorio es *\<unidad\>*:\\Archivos de programa\\[!INCLUDE[TLA#tla_visualstu](../misc/includes/tlasharptla_visualstu_md.md)] *\<número de versión principal.secundaria\>*\\Common7\\[!INCLUDE[TLA2#tla_ide](../misc/includes/tla2sharptla_ide_md.md)]. Dado que ese directorio es de solo lectura de forma predeterminada, necesita credenciales administrativas para guardar `usertype.dat`.  
  
4.  Cierre y reinicie Visual Studio.  
  
    > [!NOTE]
    >  No es posible cambiar el nombre ni volver a cargar el archivo `usertype.dat` durante una sesión de edición porque este archivo se lee durante la inicialización. Todos los valores de configuración de color definidos anteriormente tienen prioridad porque el mecanismo de color de la sintaxis comprueba el archivo `usertype.dat` en último lugar.  
  
5.  En el menú **Herramientas**, haga clic en **Opciones**. En el cuadro de diálogo **Opciones**, haga clic en **Entorno** y en **Fuentes y colores** y luego, en la lista **Mostrar elementos:**, haga clic en **Palabras clave de usuario de C\/C\+\+**.  
  
6.  Establezca las propiedades de fuente y color de las palabras clave definidas por el usuario, tal como se describe en [Fuentes y colores, Entorno, Opciones \(Cuadro de diálogo\)](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Para obtener más información, consulte [Palabras clave de C\+\+](/visual-cpp/cpp/keywords-cpp).  
  
## Vea también  
 [Ejecutar como miembro del grupo de usuarios](/visual-cpp/top/running-as-a-member-of-the-users-group)   
 [Métodos abreviados de teclado predeterminados](../ide/default-keyboard-shortcuts-in-visual-studio.md)