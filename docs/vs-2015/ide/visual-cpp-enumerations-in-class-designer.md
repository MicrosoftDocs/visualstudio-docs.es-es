---
title: Enumeraciones de Visual C++ en el Diseñador de clases | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b9d88cb954e89cfd6401f674fbbbc901ac634982
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236364"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Enumeraciones de Visual C++ en el Diseñador de clases
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
 Para obtener más información sobre cómo usar el tipo `enum`, vea [Enumerations (Enumeraciones)](http://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3).  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con código de Visual C++ (Diseñador de clases)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Enumeraciones](http://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3)



