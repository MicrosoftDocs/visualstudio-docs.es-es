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
ms.openlocfilehash: e325ab2d5a5a54a9aaf8378753ccbe8f3a72a5a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31569194"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Cómo: Utilizar caracteres de escape especiales en MSBuild
Ciertos caracteres tienen un significado especial en archivos del proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Algunos ejemplos de estos caracteres son los signos de punto y coma (;) y los asteriscos (*). Para obtener una lista completa de estos caracteres especiales, consulte [Caracteres especiales de MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Para utilizar estos caracteres especiales con su significado literal en un archivo del proyecto, es preciso especificarlos con la sintaxis %*xx*, en que *xx* representa el valor hexadecimal ASCII del carácter.  
  
## <a name="msbuild-special-characters"></a>Caracteres especiales de MSBuild  
 Un ejemplo de dónde se utilizan los caracteres especiales se encuentra en el atributo `Include` de las listas de elementos. Por ejemplo, la siguiente lista de elementos declara dos elementos: `MyFile.cs` y `MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Si quiere declarar un elemento que contiene un punto y coma en el nombre, debe usar la sintaxis %*xx* para escapar el punto y coma y evitar que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] declare dos elementos independientes. Por ejemplo, el elemento siguiente escapa el punto y coma y declara un elemento denominado `MyFile.cs;MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Para utilizar un carácter especial de MSBuild como carácter literal  
  
-   Utilice la notación %*xx* en lugar del carácter especial, en que *xx* representa el valor hexadecimal del carácter ASCII. Por ejemplo, para usar un asterisco (*) como un carácter literal, utilice el valor `%2A`.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Elementos de](../msbuild/msbuild-items.md) [MSBuild](../msbuild/msbuild.md)