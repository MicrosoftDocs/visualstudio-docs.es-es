---
title: Estructuras de Visual C++ en el Diseñador de clases | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 19ffa241fdc1f58500c7065e2cee2a33340e33f8
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54794475"
---
# <a name="visual-c-structures-in-class-designer"></a>Estructuras de Visual C++ en el Diseñador de clases
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Diseñador de clases admite estructuras de C++, que se declaran con la palabra clave `struct`. A continuación se muestra un ejemplo:  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 Para más información sobre cómo usar el tipo `struct`, vea [struct](http://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6).  
  
 Una forma de estructura de C++ en un diagrama de clases se parece a una forma de clase y funciona como esta, salvo que en la etiqueta se muestra **Struct** y tiene las esquinas cuadradas en lugar de redondeadas.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> Struct|  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con código de Visual C++ (Diseñador de clases)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Clases y estructuras](http://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873)   
 [struct](http://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)
