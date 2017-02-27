---
title: "Reemplazar (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.replace"
helpviewer_keywords: 
  - "Edit.Replace (comando)"
  - "Reemplazar (comando)"
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Reemplazar (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Reemplaza texto en archivos utilizando un subconjunto de las opciones disponibles en la ficha **Reemplazar en archivos** de la ventana **Buscar y reemplazar**.  
  
## Sintaxis  
  
```  
Edit.Replace findwhat replacewith [/all] [/case]  
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]  
[/wild|/regex] [/word]  
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
  
 \/doc o \/d  
 Opcional.  Busca solamente en el documento actual.  Especifique sólo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 \/hidden o \/h  
 Opcional.  Busca en el texto oculto y contraído como, por ejemplo en los metadatos de un control en tiempo de diseño, la región oculta de un documento en esquema o una clase o método contraídos.  
  
 \/open o \/o  
 Opcional.  Busca en todos los documentos abiertos como si fueran un solo documento.  Especifique sólo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 \/options o \/t  
 Opcional.  Muestra una lista de los valores de opción de búsqueda actuales y no realiza ninguna búsqueda.  
  
 \/proc o \/p  
 Opcional.  Busca solamente en el procedimiento actual.  Especifique sólo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 \/regex o \/r  
 Opcional.  Utiliza los caracteres especiales predefinidos en el argumento `findwhat` como notaciones que representan modelos de texto en lugar de los literales de cadena.  Para obtener una lista completa de caracteres de expresiones regulares, vea [Expresiones regulares](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 \/reset o \/e  
 Opcional.  Devuelve las opciones de búsqueda a la configuración predeterminada sin realizar ninguna búsqueda.  
  
 \/sel o \/s  
 Opcional.  Busca solamente en la selección actual.  Especifique sólo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 \/up o \/u  
 Opcional.  Busca desde la ubicación actual en el archivo hacia la parte superior del archivo.  De forma predeterminada, las búsquedas comienzan en la ubicación actual del archivo y siguen hacia el final del archivo.  
  
 \/wild o \/l  
 Opcional.  Utiliza los caracteres especiales predefinidos en el argumento `findwhat` como notaciones que representan un carácter o una secuencia de caracteres.  
  
 \/word o \/w  
 Opcional.  Busca sólo palabras completas.  
  
## Ejemplo  
 Este ejemplo reemplaza `btnSend` por `btnSubmit` en todos los documentos abiertos.  
  
```  
>Edit.Replace btnSend btnSubmit /open  
```  
  
## Vea también  
 [Buscar y reemplazar texto](../../ide/finding-and-replacing-text.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)