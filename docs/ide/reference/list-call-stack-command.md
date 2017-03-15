---
title: "Mostrar pila de llamadas (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listcallstack"
helpviewer_keywords: 
  - "Debug.ListCallStack (comando)"
  - "mostrar pila de llamadas (comando)"
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Mostrar pila de llamadas (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Muestra la pila de llamadas actual.  
  
## Sintaxis  
  
```  
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]  
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]  
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]  
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]  
[/ShowExternalCode:yes|no] [Thread:n] [index]  
```  
  
## Argumentos  
 `index`  
 Opcional.  Establece el marco de pila actual y no muestra el resultado.  
  
## Modificadores  
 Se puede invocar todos los modificadores utilizando su forma completa o una forma abreviada.  
  
 \/Count:`number` \[o\] \/C:`number`  
 Opcional.  Número máximo de pilas de llamada que se van a mostrar.  El valor predeterminado es ilimitado.  
  
 \/ShowTypes:`yes`&#124;`no` \[o\] \/T:`yes`&#124;`no`  
 Opcional.  Especifica si se van a mostrar o no tipos de parámetro.  El valor predeterminado es `yes`.  
  
 \/ShowNames:`yes`&#124;`no` \[o\] \/N:`yes`&#124;`no`  
 Opcional.  Especifica si se van a mostrar o no nombres de parámetro.  El valor predeterminado es `yes`.  
  
 \/ShowValues:`yes`&#124;`no` \[o\] \/V:`yes`&#124;`no`  
 Opcional.  Especifica si se van a mostrar o no valores de parámetro.  El valor predeterminado es `yes`.  
  
 \/ShowModule:`yes`&#124;`no` \[o\] \/M:`yes`&#124;`no`  
 Opcional.  Especifica si se va a mostrar o no el nombre de módulo.  El valor predeterminado es `yes`.  
  
 \/ShowLineOffset:`yes`&#124;`no` \[o\] \/\#:`yes`&#124;`no`  
 Opcional.  Especifica si se va a mostrar o no el desplazamiento de línea.  El valor predeterminado es `no`.  
  
 \/ShowByteOffset:`yes`&#124;`no` \[o\] \/B:`yes`&#124;`no`  
 Opcional.  Especifica si se va a mostrar o no el desplazamiento de byte.  El valor predeterminado es `no`.  
  
 \/ShowLanguage:`yes`&#124;`no` \[o\] \/L:`yes`&#124;`no`  
 Opcional.  Especifica si se va a mostrar el lenguaje.  El valor predeterminado es `no`.  
  
 \/IncludeCallsAcrossThreads:`yes`&#124;`no` \[o\] \/I:`yes`&#124;`no`  
 Opcional.  Especifica si se van a incluir o no llamadas a otros subprocesos o desde ellos.  El valor predeterminado es `no`.  
  
 \/ShowExternalCode:`yes`&#124;`no`  
 Opcional.  Especifica si se va a mostrar o no Sólo mi código para la pila de llamadas.  Cuando Sólo mi código está desactivado, se muestra todo el código de no usuario.  Cuando Sólo mi código está activado, el código de no usuario se muestra como `[external]` en el resultado de la pila de llamadas.  
  
 Thread:`n`  
 Opcional.  Muestra la pila de llamadas para el subproceso `n`.  Si no se especifica ningún subproceso, muestra la pila de llamadas para el subproceso actual.  
  
## Comentarios  
 Los cambios realizados en los argumentos o los modificadores se aplican a las llamadas posteriores a este comando.  Si ejecuta solo `Debug.ListCallStack` , se muestra toda la pila de llamadas.  Por ejemplo, si especifica un índice  
  
```  
Debug.ListCallStack 2  
```  
  
 el marco de pila actual se establece en ese marco \(en este caso, el segundo marco\).  
  
 También puede escribir este comando utilizando su alias predefinido, kb.  Por ejemplo, puede especificar  
  
```  
kb 2  
```  
  
 para establecer el marco de pila actual en el segundo marco.  
  
## Ejemplo  
  
```  
>Debug.CallStack /Count:4 /ShowTypes:yes  
```  
  
## Vea también  
 [Mostrar desensamblador \(Comando\)](../../ide/reference/list-disassembly-command.md)   
 [Mostrar subprocesos \(Comando\)](../../ide/reference/list-threads-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)