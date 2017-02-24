---
title: "Enumeraciones de Visual C++ en el Diseñador de clases | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9f7b45efa01eb245cc4c933126578bbf9aa52f81

---
# <a name="visual-c-enumerations-in-class-designer"></a>Enumeraciones de Visual C++ en el Diseñador de clases
El Diseñador de clases admite tipos `enum` y `enum class` de ámbito de C++. A continuación se muestra un ejemplo:  
  
```  
enum CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
// or...  
enum class CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
```  
  
 Una forma de enumeración de C++ en un diagrama de clases se parece y funciona como una forma de estructura, salvo que en la etiqueta se muestra **Enum** o **Enum class**, es de color fucsia en lugar de azul y el borde de los márgenes superior e izquierdo está coloreado. Tanto las formas de enumeración como las formas de estructura tienen las esquinas cuadradas.  
  
 Para obtener más información sobre cómo usar el tipo `enum`, vea [Enumerations (Enumeraciones)](/visual-cpp/cpp/enumerations-cpp).  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con código de Visual C++ (Diseñador de clases)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Enumeraciones](/visual-cpp/cpp/enumerations-cpp)


<!--HONumber=Feb17_HO4-->


