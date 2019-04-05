---
title: Cómo depurar una infracción de acceso | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 073fc84d15cb31b4f7a4cc635524ab08a724911e
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/27/2019
ms.locfileid: "59002300"
---
# <a name="how-can-i-debug-an-access-violation"></a>Cómo depurar una infracción de acceso
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Descripción del problema  
 El programa produce una infracción de acceso. ¿Cómo se puede depurar este error?  
  
## <a name="solution"></a>Soluciones  
 Si se produce una infracción de acceso en una línea de código que desreferencia varios punteros, puede ser difícil averiguar qué puntero produjo la infracción de acceso. A partir de Visual Studio 2015 Update 1, el cuadro de diálogo de excepción ahora indica explícitamente el puntero que produjo la infracción de acceso.  
  
 Por ejemplo, con el siguiente código, debería obtener una infracción de acceso:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ClassB {  
public:  
      ClassC* C;  
      ClassB() {  
            C = new ClassC();  
      }  
     void printHello() {  
            cout << "hello world";  
      }  
};  
  
class ClassA {  
public:  
    ClassB* B;  
    ClassA() {  
            B = nullptr;  
      }  
};  
  
int main() {  
    ClassA* A = new ClassA();  
    A->B->printHello();  
}  
```  
  
 Si ejecuta este código en Visual Studio 2015 Update 1, verá el cuadro de diálogo de excepción siguiente:  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 Si no puede determinar por qué el puntero ha provocado una infracción de acceso, realice el seguimiento del código para asegurarse de que el puntero que causa el problema se ha asignado correctamente.  Si se pasa como parámetro, asegúrese de que se pasa correctamente y que no está creando accidentalmente una [copia superficial](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). A continuación, compruebe que los valores no se cambian involuntariamente en algún lugar del programa mediante la creación de un punto de interrupción de datos para el puntero en cuestión, para asegurarse de que no se esté modificando en otra parte del programa. Para obtener más información sobre los puntos de interrupción de datos, vea la sección sobre los puntos de interrupción de datos en [Using Breakpoints](../debugger/using-breakpoints.md).  
  
## <a name="see-also"></a>Vea también  
 [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)
