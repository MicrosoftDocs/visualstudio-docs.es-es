---
title: ¿Cómo se puede depurar una infracción de acceso de C++? | Microsoft Docs
ms.custom: ''
ms.date: 05/23/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: b131ba4acf761a11aa9f39807d1db3202b021c9d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="how-can-i-debug-a-c-access-violation"></a>¿Cómo se puede depurar una infracción de acceso de C++?
## <a name="problem-description"></a>Descripción del problema  
 El programa produce una infracción de acceso. ¿Cómo se puede depurar este error?  
  
## <a name="solution"></a>Soluciones  
 Si se produce una infracción de acceso en una línea de código que desreferencia varios punteros, puede ser difícil averiguar qué puntero produjo la infracción de acceso. A partir de Visual Studio 2015 Update 1, el cuadro de diálogo de excepción ahora indica explícitamente el puntero que produjo la infracción de acceso.  
  
 Por ejemplo, con el siguiente código, debería obtener una infracción de acceso:  
  
```C++  
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
  
 Si no puede determinar por qué el puntero ha provocado una infracción de acceso, realice el seguimiento del código para asegurarse de que el puntero que causa el problema se ha asignado correctamente.  Si se pasa como un parámetro, asegúrese de que se pasa correctamente y no está creando accidentalmente una [shallow copia](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). A continuación, compruebe que los valores no se cambian involuntariamente en algún lugar en el programa mediante la creación de un punto de interrupción de datos para el puntero en cuestión para asegurarse de que no se esté modificando en otra parte del programa. Para obtener más información sobre los puntos de interrupción de datos, vea la sección sobre los puntos de interrupción de datos en [Using Breakpoints](../debugger/using-breakpoints.md).  
  
## <a name="see-also"></a>Vea también  
 [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)