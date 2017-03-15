---
title: "Cuadro Buscar/Comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.findcommandbox"
helpviewer_keywords: 
  - "Buscar/Comando (cuadro)"
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Cuadro Buscar/Comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede buscar los comandos de Visual Studio de texto y ejecución de casilla **Find\/Command** .  La casilla **Find\/Command** aún está disponible como control ToolBar, pero deja visible de manera predeterminada.  Puede mostrar el cuadro **Find\/Command** eligiendo **Agregue o quite los botones** en la barra de herramientas **Estándar** y elige **Buscar**.  
  
 Para ejecutar un comando de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , introdúzcala con un mayor que \(\>\) signo.  
  
 El cuadro **Buscar\/Comando** recuerda los últimos 20 elementos escritos y los muestra en la lista desplegable.  Puede navegar por la lista eligiendo las teclas de dirección.  
  
 ![Cuadro Buscar&#47;Comando](../ide/media/findcommandbox.png "FindCommandBox")  
Buscar\/Comando \(Cuadro\)  
  
## Buscar texto  
 De forma predeterminada, al especificar el texto en el cuadro **Find\/Command** y después elige la tecla ENTRAR, Visual Studio busca el documento actual o la ventana de herramientas mediante las opciones especificadas en el cuadro **Buscar en archivos** .  Para obtener más información, vea [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md).  
  
## Escribir comandos  
 Para utilizar la casilla **Find\/Command** para emitir un único comando o alias de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en lugar de buscar texto, escriba el comando de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , introdujo con un mayor que \(\>\) símbolos.  Por ejemplo:  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 También puede utilizar la ventana de comandos para escribir y ejecutar uno o varios comandos.  Algunos comandos o alias pueden escribirse y ejecutarse por sí solos, otros requieren argumentos en su sintaxis.  Para obtener una lista de los comandos que tienen argumentos, vea [Comandos de Visual Studio](../ide/reference/visual-studio-commands.md).  
  
## Carácter de escape  
 El carácter que va a continuación de un carácter de intercalación \(^\) en una línea de comandos se interpreta literalmente y no como carácter de control.  El símbolo de intercalación puede utilizarse para incrustar comillas \("\), espacios, barras diagonales iniciales, símbolos de intercalación o cualquier otro carácter literal en un valor de modificador o parámetro, con la excepción de nombres de modificador.  Por ejemplo,  
  
```  
>Edit.Find ^^t /regex  
```  
  
 Un símbolo de intercalación funciona del mismo modo tanto dentro como fuera de comillas.  Si el último carácter de la línea es un símbolo de intercalación, éste se omite.  
  
## Vea también  
 [Ventana de comandos](../ide/reference/command-window.md)   
 [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md)