---
title: "Visual C++ Structures in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], structures"
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Structures in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Diseñador de clases admite estructuras de C\+\+, que se declaran con la palabra clave `struct`.  A continuación, se muestra un ejemplo:  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 Para obtener más información sobre cómo usar el tipo `struct`, vea [struct](/visual-cpp/cpp/struct-cpp).  
  
 Una forma de estructura de C\+\+ en un diagrama de clases se muestra y funciona como una forma de clase, salvo que en la etiqueta figura el texto **Struct** y tiene las esquinas cuadradas en lugar de redondeadas.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------------|-------------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> Struct|  
  
## Vea también  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Clases y structs](/visual-cpp/cpp/classes-and-structs-cpp)   
 [struct](/visual-cpp/cpp/struct-cpp)