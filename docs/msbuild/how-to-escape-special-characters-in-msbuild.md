---
title: 'Cómo: Utilizar caracteres de escape especiales en MSBuild | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d921236fe44c7402bb26800c02624e2c391301a
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077071"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Cómo: Usar caracteres de escape especiales en MSBuild
Ciertos caracteres tienen un significado especial en archivos del proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Algunos ejemplos de estos caracteres son los signos de punto y coma (;) y los asteriscos (*). Para obtener una lista completa de estos caracteres especiales, vea [Caracteres especiales de MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Para usar estos caracteres especiales como literales en un archivo de proyecto, es preciso especificarlos con la sintaxis %\<xx>, donde \<xx> representa el valor hexadecimal ASCII del carácter.  
  
## <a name="msbuild-special-characters"></a>Caracteres especiales de MSBuild  
 Un ejemplo de dónde se utilizan los caracteres especiales se encuentra en el atributo `Include` de las listas de elementos. Por ejemplo, la siguiente lista de elementos declara dos elementos: *MyFile.cs* y *MyClass.cs*.  
  
```xml  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Si quiere declarar un elemento que contiene un punto y coma en el nombre, debe usar la sintaxis %\<xx> para aplicar una secuencia de escape al punto y coma, y evitar que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] declare dos elementos independientes. Por ejemplo, el elemento siguiente aplica una secuencia de escape al punto y coma, y declara un elemento denominado *MyFile.cs;MyClass.cs*.  
  
```xml  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Para utilizar un carácter especial de MSBuild como carácter literal  
  
-   Use la notación %\<xx> en lugar del carácter especial, donde \<xx> representa el valor hexadecimal del carácter ASCII. Por ejemplo, para usar un asterisco (*) como un carácter literal, utilice el valor `%2A`.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild.md)   
 [Elementos](../msbuild/msbuild-items.md)   
