---
title: Procedimiento Usar caracteres de escape especiales en MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94fc8d858e2db9bd1e00bb8770cf52672a900ab0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178347"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Cómo: Utilizar caracteres de escape especiales en MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ciertos caracteres tienen un significado especial en archivos del proyecto de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Algunos ejemplos de estos caracteres son los signos de punto y coma (;) y los asteriscos (*). Para obtener una lista completa de estos caracteres especiales, consulte [Caracteres especiales de MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Para usar estos caracteres especiales como literales en un archivo de proyecto, se deben especificar con la sintaxis%*XX*, donde *XX* representa el valor hexadecimal ASCII del carácter.  
  
## <a name="msbuild-special-characters"></a>Caracteres especiales de MSBuild  
 Un ejemplo de dónde se utilizan los caracteres especiales se encuentra en el atributo `Include` de las listas de elementos. Por ejemplo, la siguiente lista de elementos declara dos elementos: `MyFile.cs` y `MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Si quiere declarar un elemento que contiene un punto y coma en el nombre, debe usar la sintaxis %*xx* para escapar el punto y coma y evitar que [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] declare dos elementos independientes. Por ejemplo, el elemento siguiente escapa el punto y coma y declara un elemento denominado `MyFile.cs;MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Para utilizar un carácter especial de MSBuild como carácter literal  
  
- Utilice la notación %*xx* en lugar del carácter especial, en que *xx* representa el valor hexadecimal del carácter ASCII. Por ejemplo, para usar un asterisco (*) como un carácter literal, utilice el valor `%2A`.  
  
## <a name="see-also"></a>Consulte también  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Elementos de ](msbuild.md) [MSBuild](../msbuild/msbuild-items.md)
