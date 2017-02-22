---
title: "Buscar (Comando) | Microsoft Docs"
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
  - "edit.find"
helpviewer_keywords: 
  - "Edit.Find (comando)"
  - "Buscar (comando)"
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Buscar (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Busca archivos mediante un subconjunto de las opciones disponibles en la ficha de **Buscar en archivos** de la ventana de **Buscar y reemplazar** .  
  
## Sintaxis  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## Argumentos  
 `findwhat`  
 Obligatorio.  Texto con el que debe coincidir.  
  
## Modificadores  
 \/case o \/c  
 Opcional.  Sólo se encuentran coincidencias si los caracteres en mayúsculas y minúsculas coinciden exactamente con los especificados en el argumento `findwhat`.  
  
 \/doc o \/d  
 Opcional.  Busca solamente en el documento actual.  Especifique sólo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 \/markall o \/m  
 Opcional.  Coloca un gráfico en cada línea que contenga una coincidencia de búsqueda dentro del documento actual.  
  
 \/open o \/o  
 Opcional.  Busca en todos los documentos abiertos como si fueran un solo documento.  Especifique sólo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 \/options o \/t  
 Opcional.  Muestra una lista de los valores de opción de búsqueda actuales y no realiza ninguna búsqueda.  
  
 \/proc o \/p  
 Opcional.  Busca solamente en el procedimiento actual.  Especifique sólo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 \/reset o \/e  
 Opcional.  Devuelve las opciones de búsqueda a la configuración predeterminada sin realizar ninguna búsqueda.  
  
 \/sel o \/s  
 Opcional.  Busca solamente en la selección actual.  Especifique sólo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 \/up o \/u  
 Opcional.  Busca desde la ubicación actual del archivo hacia el comienzo del archivo.  De forma predeterminada, las búsquedas comienzan en la ubicación actual del archivo y siguen hacia el final del archivo.  
  
 \/regex o \/r  
 Opcional.  Utiliza los caracteres especiales predefinidos en el argumento `findwhat` como notaciones que representan modelos de texto en lugar de los literales de cadena.  Para obtener una lista completa de caracteres de expresiones regulares, vea [Expresiones regulares](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 \/wild o \/l  
 Opcional.  Utiliza los caracteres especiales predefinidos en el argumento `findwhat` como notaciones que representan un carácter o una secuencia de caracteres.  
  
 \/word o \/w  
 Opcional.  Busca sólo palabras completas.  
  
## Ejemplo  
 En este ejemplo se realiza una búsqueda con distinción de mayúsculas y minúsculas de la palabra "somestring" en la sección de código seleccionada actualmente.  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## Vea también  
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)