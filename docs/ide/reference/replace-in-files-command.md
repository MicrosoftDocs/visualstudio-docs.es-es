---
title: "Reemplazar en archivos (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.replaceinfiles"
helpviewer_keywords: 
  - "Edit.ReplaceInFiles (comando)"
  - "Reemplazar en archivos (comando)"
  - "ReplaceInFiles (comando)"
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Reemplazar en archivos (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Reemplaza texto en archivos utilizando un subconjunto de las opciones disponibles en la ficha **Reemplazar en archivos** de la ventana **Buscar y reemplazar**.  
  
## Sintaxis  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
```  
  
## Argumentos  
 `findwhat`  
 Obligatorio.  Texto con el que debe coincidir.  
  
 `replacewith`  
 Obligatorio.  Texto para sustituir al texto coincidente.  
  
## Modificadores  
 \/all o \/a  
 Opcional.  Reemplaza todas las repeticiones del texto de búsqueda por el texto de reemplazo.  
  
 \/case o \/c  
 Opcional.  Sólo se encuentran coincidencias si los caracteres en mayúsculas y minúsculas coinciden exactamente con los especificados en el argumento `findwhat`.  
  
 \/ext: `extensions`  
 Opcional.  Especifica las extensiones de archivo que se van a buscar.  
  
 \/keep o \/k  
 Opcional.  Especifica que todos los archivos modificados queden abiertos.  
  
 \/lookin: `searchpath`  
 Opcional.  Directorio en el que se va a buscar.  Si la ruta de acceso contiene espacios, incluya la ruta de acceso completa entre comillas.  
  
 \/options o \/t  
 Opcional.  Muestra una lista de los valores de opción de búsqueda actuales y no realiza ninguna búsqueda.  
  
 \/regex o \/r  
 Opcional.  Utiliza los caracteres especiales predefinidos en el argumento `findwhat` como notaciones que representan modelos de texto en lugar de los literales de cadena.  Para obtener una lista completa de caracteres de expresiones regulares, vea [Expresiones regulares](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 \/reset o \/e  
 Opcional.  Devuelve las opciones de búsqueda a la configuración predeterminada sin realizar ninguna búsqueda.  
  
 \/stop  
 Opcional.  Detiene la operación de búsqueda actual si hay una en curso.  El reemplazo omite el resto de los argumentos cuando se ha especificado `/stop` .  Por ejemplo, para detener el reemplazo actual tiene que escribir lo siguiente:  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 \/sub o \/s  
 Opcional.  Busca en las subcarpetas del directorio especificado en el argumento \/lookin:`searchpath`.  
  
 \/text2 o \/2  
 Opcional.  Muestra los resultados del reemplazo en la ventana **Resultados de la búsqueda 2**.  
  
 \/wild o \/l  
 Opcional.  Utiliza los caracteres especiales predefinidos en el argumento `findwhat` como notaciones que representan un carácter o una secuencia de caracteres.  
  
 \/word o \/w  
 Opcional.  Busca sólo palabras completas.  
  
## Ejemplo  
 Este ejemplo busca `btnCancel` y lo reemplaza por `btnReset` en todos los archivos .cls situados en la carpeta "my visual studio projects" y muestra la información de reemplazo en la ventana **Resultados de la búsqueda 2**.  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## Vea también  
 [Buscar y reemplazar texto](../../ide/finding-and-replacing-text.md)   
 [Reemplazar en archivos](../../ide/replace-in-files.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)