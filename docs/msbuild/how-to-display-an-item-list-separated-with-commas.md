---
title: "C&#243;mo: Mostrar una lista de elementos separados por comas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, aplicar formato a las colecciones de elementos"
  - "MSBuild, separar elementos mediante punto y coma"
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# C&#243;mo: Mostrar una lista de elementos separados por comas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se usan listas de elementos en [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\), a veces resulta útil mostrar su contenido de manera que sea fácil de leer.  Otra opción consiste en disponer de una tarea que tome una lista de elementos separados con una cadena separadora especial.  En ambos casos, se puede especificar una cadena separadora para una lista de elementos.  
  
## Separar los elementos de una lista con comas  
 De forma predeterminada, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] usa el signo de punto y coma para separar los elementos de una lista.  Por ejemplo, considere un elemento `Message` con el valor siguiente:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Cuando la lista de elementos `@(TXTFile)` contiene los elementos App1.txt, App2.txt y App3.txt, el mensaje es:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Si desea cambiar el comportamiento predeterminado, puede especificar su propio separador.  La sintaxis para especificar un separador de la lista de elementos es la siguiente:  
  
 `@(ItemListName, '<separator>')`  
  
 El separador puede ser un carácter o una cadena de caracteres y se debe incluir entre comillas simples.  
  
#### Para insertar una coma y un espacio entre los elementos  
  
-   Utilice una notación del elemento similar a la siguiente:  
  
     `@(TXTFile, ', ')`  
  
## Ejemplo  
 En este ejemplo, la tarea [Exec](../msbuild/exec-task.md) ejecuta la herramienta findstr para buscar las cadenas de texto especificadas en el archivo Phrases.txt.  En el comando findstr, se indican las cadenas de búsqueda literales mediante el modificador **\/c:**, por lo que se inserta el separador `/c:` entre los elementos de la lista `@(Phrase)`.  
  
 Para este ejemplo, el comando de línea de comandos equivalente es:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## Vea también  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [elementos](../msbuild/msbuild-items.md)