---
title: "Estructuras de Visual C++ en el Diseñador de clases | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 85e2068e00f2164b44feb9aae61a47de426be735
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="visual-c-structures-in-class-designer"></a>Estructuras de Visual C++ en el Diseñador de clases
El Diseñador de clases admite estructuras de C++, que se declaran con la palabra clave `struct`. A continuación se muestra un ejemplo:  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 Para más información sobre cómo usar el tipo `struct`, vea [struct](/cpp/cpp/struct-cpp).  
  
 Una forma de estructura de C++ en un diagrama de clases se parece a una forma de clase y funciona como esta, salvo que en la etiqueta se muestra **Struct** y tiene las esquinas cuadradas en lugar de redondeadas.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> Struct|  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con código de Visual C++ (Diseñador de clases)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Clases y structs](/cpp/cpp/classes-and-structs-cpp)   
 [struct](/cpp/cpp/struct-cpp)