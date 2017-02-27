---
title: "Mostrar registros (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listregisters"
helpviewer_keywords: 
  - "Debug.ListRegisters (comando)"
  - "mostrar registros (comando)"
  - "ListRegisters (comando)"
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Mostrar registros (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Muestra el valor de los registros seleccionado y le permite modificar la lista de registros para mostrar.  
  
## Sintaxis  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## Modificadores  
 \/Display \[{`register`&#124;`registerGroup`}...\]  
 Muestra los valores del parámetro `register` o `registerGroup` especificado.  Si no se especifica ningún parámetro `register` o `registerGroup`, se muestra la lista predeterminada de registros.  Si no se especifica ningún modificador, el comportamiento es el mismo.  Por ejemplo:  
  
 `Debug.ListRegisters /Display eax`  
  
 es equivalente a  
  
 `Debug.ListRegisters eax`  
  
 \/List  
 Muestra todos los grupos de registros de la lista.  
  
 \/Watch \[{`register`&#124;`registerGroup`}...\]  
 Agrega uno o más valores `register` o `registerGroup` a la lista.  
  
 \/Unwatch \[{`register`&#124;`registerGroup`}...\]  
 Quita uno o más valores `register` o `registerGroup` de la lista.  
  
## Comentarios  
 Puede utilizarse el alias `r` en lugar de `Debug.ListRegisters`.  
  
## Ejemplo  
 Este ejemplo utiliza el alias `r` de `Debug.ListRegisters` para mostrar los valores del grupo de registros `Flags`.  
  
```  
r /Display Flags  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fundamentos de la depuración: ventana Registros](../../debugger/debugging-basics-registers-window.md)   
 [Cómo: Utilizar la ventana Registros](../../debugger/how-to-use-the-registers-window.md)