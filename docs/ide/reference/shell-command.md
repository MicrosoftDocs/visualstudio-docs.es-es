---
title: "Shell (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.shell"
helpviewer_keywords: 
  - "archivos .exe"
  - "archivos exe"
  - "ejecutables, ejecutar desde Visual Studio"
  - "Shell (comando)"
  - "Shell, iniciar archivos .exe"
  - "Tools.Shell (comando)"
  - "Visual Studio, ejecutables desde"
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Shell (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Inicia programas ejecutables desde dentro de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Sintaxis  
  
```  
Tools.Shell [/command] [/output] [/dir:folder] path [args]  
```  
  
## Argumentos  
 `path`  
 Obligatorio.  Nombre de archivo y ruta de acceso del archivo que se va a ejecutar o del documento que se va a abrir.  Se requiere una ruta de acceso completa si el archivo especificado no está en alguno de los directorios de la variable de entorno PATH.  
  
 `args`  
 Opcional.  Cualquier argumento que se va a pasar al programa invocado.  
  
## Modificadores  
 \/commandwindow \[o\] \/command \[o\] \/c \[o\] \/cmd  
 Opcional.  Especifica que los resultados del ejecutable se muestren en la ventana **Comando**.  
  
 \/dir:`folder` \[o\] \/d: `folder`  
 Opcional.  Especifica el directorio de trabajo que se va a establecer cuando se ejecute el programa.  
  
 \/outputwindow \[o\] \/output \[o\] \/out \[o\] \/o  
 Opcional.  Especifica que los resultados del ejecutable se muestren en la **Ventana de salida**.  
  
## Comentarios  
 Los modificadores \/dir \/o \/c tienen que especificarse inmediatamente después de `Tools.Shell`.  Todo lo que se especifique a continuación del nombre del ejecutable se le pasa como argumentos de línea de comandos.  
  
 Puede utilizarse el alias predefinido `Shell` en lugar de `Tools.Shell`.  
  
> [!CAUTION]
>  Si el argumento `path` proporciona la ruta de acceso del directorio y el nombre de archivo, debe incluir el nombre completo de la ruta de acceso entre comillas literales \("""\), como en el ejemplo siguiente:  
  
```  
Tools.Shell """C:\Program Files\SomeFile.exe"""  
```  
  
 El procesador `Shell` interpreta cada conjunto de tres comillas dobles \("""\) como un único carácter de comillas dobles.  Así, el ejemplo anterior pasa realmente la cadena de ruta de acceso siguiente al comando `Shell`:  
  
```  
"C:\Program Files\SomeFile.exe"  
```  
  
> [!CAUTION]
>  Si no escribe la cadena de ruta de acceso entre comillas literales \("""\), Windows utilizará únicamente la parte de la cadena que hay hasta el primer espacio en blanco.  Por ejemplo, si la cadena de ruta de acceso anterior no estuviera entrecomillada correctamente, Windows buscaría un archivo denominado "Program" en el directorio raíz C:\\.  Si existiera realmente un archivo ejecutable C:\\Program.exe, aunque fuera uno instalado por modificación ilícita, Windows intentaría ejecutar ese programa en lugar del programa "c:\\Program Files\\SomeFile.exe" deseado.  
  
## Ejemplo  
 El comando siguiente utiliza xcopy.exe para copiar el archivo `MyText.txt` en la carpeta `Text`.  El resultado de xcopy.exe se muestra en la ventana **Comandos** y en la **Ventana de salida**.  
  
```  
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Resultados \(Ventana\)](../../ide/reference/output-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)