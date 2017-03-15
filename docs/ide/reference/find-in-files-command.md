---
title: "Buscar en archivos (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.findinfiles"
helpviewer_keywords: 
  - "Edit.FindInFiles (comando)"
  - "Buscar en archivos (comando)"
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Buscar en archivos (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Busca archivos utilizando un subconjunto de las opciones disponibles en la ficha **Buscar en archivos** de la ventana **Buscar y reemplazar**.  
  
## Sintaxis  
  
```  
Edit.FindinFiles findwhat [/case] [/ext:extensions]  
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]  
[/text2] [/wild|/regex] [/word]  
```  
  
## Argumentos  
 `findwhat`  
 Obligatorio.  Texto con el que debe coincidir.  
  
## Modificadores  
 \/case o \/c  
 Opcional.  Sólo se encuentran coincidencias si los caracteres en mayúsculas y minúsculas coinciden exactamente con los especificados en el argumento `findwhat`.  
  
 \/ext: `extensions`  
 Opcional.  Especifica las extensiones de archivo que se van a buscar.  Si no se especifican, se utiliza la extensión anterior si se indicó una previamente.  
  
 \/lookin: `searchpath`  
 Opcional.  Directorio en el que se va a buscar.  Si la ruta de acceso contiene espacios, incluya la ruta de acceso completa entre comillas.  
  
 \/names o \/n  
 Opcional.  Muestra una lista de los nombres de archivo que contienen coincidencias.  
  
 \/options o \/t  
 Opcional.  Muestra una lista de los valores de opción de búsqueda actuales y no realiza ninguna búsqueda.  
  
 \/regex o \/r  
 Opcional.  Utiliza los caracteres especiales predefinidos en el argumento `findwhat` como notaciones que representan modelos de texto en lugar de los literales de cadena.  Para obtener una lista completa de caracteres de expresiones regulares, vea [Expresiones regulares](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 \/reset o \/e  
 Opcional.  Devuelve las opciones de búsqueda a la configuración predeterminada sin realizar ninguna búsqueda.  
  
 \/stop  
 Opcional.  Detiene la operación de búsqueda actual si hay una en curso.  La búsqueda omite el resto de los argumentos cuando se ha especificado `/stop` .  Por ejemplo, para detener la búsqueda actual, tiene que escribir lo siguiente:  
  
```  
>Edit.FindinFiles /stop  
```  
  
 \/sub o \/s  
 Opcional.  Busca en las subcarpetas del directorio especificado en el argumento \/lookin:`searchpath`.  
  
 \/text2 o \/2  
 Opcional.  Muestra los resultados de la búsqueda en la ventana Resultados de la búsqueda 2.  
  
 \/wild o \/l  
 Opcional.  Utiliza los caracteres especiales predefinidos en el argumento `findwhat` como notaciones que representan un carácter o una secuencia de caracteres.  
  
 \/word o \/w  
 Opcional.  Busca sólo palabras completas.  
  
## Ejemplo  
 Este ejemplo busca btnCancel en todos los archivos .cls situados en la carpeta "My Visual Studio Projects" y muestra la información sobre coincidencias en la ventana Resultados de la búsqueda 2.  
  
```  
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2  
```  
  
## Vea también  
 [Buscar en archivos](../../ide/find-in-files.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)