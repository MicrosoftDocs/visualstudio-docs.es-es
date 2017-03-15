---
title: "Registrar resultados de la ventana de comandos (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.logcommandwindowoutput"
helpviewer_keywords: 
  - "Registrar resultados de la ventana de comandos (comando)"
  - "View.LogCommandWindowOutput (comando)"
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Registrar resultados de la ventana de comandos (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Copia todas las entradas y salidas de la ventana **Comando** a un archivo.  
  
## Sintaxis  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## Argumentos  
 `filename`  
 Opcional.  Nombre del archivo de registro.  De forma predeterminada, el archivo se crea en la carpeta de perfil del usuario.  Si ya existe el nombre de archivo, el registro se anexa al final del archivo existente.  Si no se especifica ningún archivo, se utiliza el último archivo especificado.  Si no existe ningún archivo anterior, se crea un archivo de registro predeterminado, denominado cmdline.log.  
  
> [!TIP]
>  Para cambiar la ubicación en la que se guarda el archivo de registro, escriba la ruta de acceso completa del archivo, delimitada por comillas contiene algún espacio en blanco.  
  
## Modificadores  
 \/on  
 Opcional.  Inicia el registro de la ventana **Comando** en el archivo especificado y anexa al archivo la nueva información.  
  
 \/off  
 Opcional.  Detiene el registro para la ventana **Comando**.  
  
 \/overwrite  
 Opcional.  Si el archivo especificado en el argumento `filename` coincide con un archivo existente, se sobrescribe el archivo.  
  
## Comentarios  
 Si no se especifica ningún archivo, se crea el archivo cmdline.log de forma predeterminada.  El alias predeterminado de este comando es Log.  
  
## Ejemplos  
 En este ejemplo se crea un nuevo archivo de registro, cmdlog, y se inicia el registro de comandos.  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 En este ejemplo se detiene el registro de comandos.  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 En este ejemplo se reanuda el registro de comandos en el archivo de registro utilizado anteriormente.  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)