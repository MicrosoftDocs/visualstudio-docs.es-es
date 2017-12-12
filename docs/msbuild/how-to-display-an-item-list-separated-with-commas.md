---
title: "Cómo: Mostrar una lista de elementos separados por comas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: "12"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: be7beec070d58f265912f61d37a2d213e50ea0c7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Cómo: Mostrar una lista de elementos separados por comas
Cuando se trabaja con listas de elementos en [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]), a veces resulta útil mostrar el contenido de las listas de elementos de tal forma que sea fácil de leer. O puede que tenga una tarea que toma una lista de elementos separados con una cadena de separación especial. En ambos casos, puede especificar una cadena de separación para una lista de elementos.  
  
## <a name="separating-items-in-a-list-with-commas"></a>Separar los elementos de una lista con comas  
 De manera predeterminada, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] usa signos de punto y coma para separar los elementos de una lista. Por ejemplo, considere un elemento `Message` con el valor siguiente:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Cuando la lista de elementos `@(TXTFile)` contiene los elementos App1.txt, App2.txt y App3.txt, el mensaje es:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Si quiere cambiar el comportamiento predeterminado, puede especificar su propio separador. La sintaxis para especificar un separador de lista de elementos es:  
  
 `@(ItemListName, '<separator>')`  
  
 El separador puede ser un solo carácter o una cadena y debe incluirse entre comillas simples.  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Para insertar una coma y un espacio entre los elementos  
  
-   Use una notación de elemento similar a la siguiente:  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, la tarea [Exec](../msbuild/exec-task.md) ejecuta la herramienta findstr para buscar cadenas de texto especificadas en el archivo Phrases.txt. En el comando findstr, las cadenas de búsqueda literal se indican mediante el modificador **/c:**, por lo que el separador de elementos `/c:` se inserta entre los elementos de la lista de elementos `@(Phrase)`.  
  
 En este ejemplo, el comando de línea de comandos equivalente es:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```xml  
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
  
## <a name="see-also"></a>Vea también  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Elementos](../msbuild/msbuild-items.md)