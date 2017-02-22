---
title: "Mostrar memoria (Comando) | Microsoft Docs"
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
  - "debug.listmemory"
helpviewer_keywords: 
  - "Debug.ListMemory (comando)"
  - "Mostrar memoria (comando)"
  - "ListMemory (comando)"
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Mostrar memoria (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Muestra el contenido del intervalo de memoria especificado.  
  
## Sintaxis  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## Argumentos  
 `expression`  
 Opcional.  Dirección de memoria desde la que se va a comenzar a mostrar memoria.  
  
## Modificadores  
 \/ANSI&#124;Unicode  
 Opcional.  Muestra la memoria en forma de caracteres correspondientes a los bytes de memoria, ANSI o Unicode.  
  
 \/Count:`number`  
 Opcional.  Determina cuántos bytes de memoria se van a mostrar, a partir de `expression`.  
  
 \/Format:`formattype`  
 Opcional.  Tipo de formato para ver la información de memoria en la ventana **Memoria**; puede ser OneByte, TwoBytes, FourBytes, EightBytes, Flotante \(32 bits\) o Doble \(64 bits\).  Si se utiliza OneByte, `/Unicode` no está disponible.  
  
 \/Hex&#124;Signed&#124;Unsigned  
 Opcional.  Especifica el formato para ver números como signed, unsigned o hexadecimal.  
  
## Comentarios  
 En lugar de escribir un comando **Debug.ListMemory** completo con todos los modificadores, puede invocar el comando utilizando alias predefinidos con ciertos modificadores preestablecidos en los valores especificados.  Por ejemplo, en lugar de escribir:  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 puede escribir:  
  
```  
>df /Count:30 /Unicode  
```  
  
 Aquí se muestra una lista de los alias disponibles para el comando **Debug.ListMemory**:  
  
|Alias|Comando y modificadores|  
|-----------|-----------------------------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory \/Ansi|  
|**db**|Debug.ListMemory \/Format:OneByte|  
|**dc**|Debug.ListMemory \/Format:FourBytes \/Ansi|  
|**dd**|Debug.ListMemory \/Format:FourBytes|  
|**df**|Debug.ListMemory\/Format:Float|  
|**dq**|Debug.ListMemory \/Format:EightBytes|  
|**du**|Debug.ListMemory \/Unicode|  
  
## Ejemplo  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## Vea también  
 [Mostrar pila de llamadas \(Comando\)](../../ide/reference/list-call-stack-command.md)   
 [Mostrar subprocesos \(Comando\)](../../ide/reference/list-threads-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)