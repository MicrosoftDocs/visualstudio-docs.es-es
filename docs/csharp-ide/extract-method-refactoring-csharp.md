---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-method
title: "Extraer método (refactorización, C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 18fc4c20b39341f884fb23b51822ce7f6e427007
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="extract-method-refactoring-c"></a>Extraer método (Refactorización, C#)
**Extraer método** es una operación de refactorización que proporciona una manera fácil de crear un nuevo método a partir de un fragmento de código en un miembro existente.  
  
 Usar **Extraer método**, puede crear un nuevo método extrayendo una selección de código desde dentro del bloque de código de un miembro existente. El nuevo método extraído contiene el código seleccionado y el código seleccionado del miembro existente se reemplaza por una llamada al método nuevo. Convertir un fragmento de código en su propio método le permite rápidamente y con precisión reorganizar el código para una mejor poder reutilizarla y mejorar la legibilidad.  
  
 **Extraer método** tiene las siguientes ventajas:  
  
-   Anima a las prácticas de codificación mejor enfatizando métodos discretos y reutilizables.  
  
-   Recomienda el código a través de la organización buena autodocumentado.  
  
     Cuando los nombres descriptivos son métodos de uso y de alto nivel pueden leer como una serie de comentarios.  
  
-   Anima a la creación de métodos más precisa para simplificar la sustitución.  
  
-   Reduce la duplicación de código.  
  
### <a name="to-use-extract-method"></a>Para utilizar Extraer método  
  
1.  Cree una aplicación de consola denominada `ExtractMethod` y, a continuación, reemplace `Program` por el siguiente código de ejemplo.  
  
    ```csharp  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2.  Seleccione el fragmento de código que desean extraer:  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3.  En el **refactorizar** menú, haga clic en **Extraer método**.  
  
     El **Extraer método** aparece el cuadro de diálogo.  
  
     Como alternativa, también puede escribir el método abreviado de teclado CTRL + R, M para mostrar el **Extraer método** cuadro de diálogo.  
  
     También puede hacer clic seleccionado de código, seleccione **refactorizar**y, a continuación, haga clic en **Extraer método** para mostrar la **Extraer método** cuadro de diálogo.  
  
4.  Especifique un nombre para el nuevo método, como `CircleArea`, en la **nombre del nuevo método** cuadro.  
  
     Muestra una vista previa de la nueva firma de método en **firma del método de vista previa**.  
  
5.  Haga clic en **Aceptar**.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se usa el **Extraer método** comando, se inserta el nuevo método después del miembro de origen en la misma clase.  
  
## <a name="partial-types"></a>Tipos parciales  
 Si la clase es un tipo parcial, a continuación, **Extraer método** genera el nuevo método inmediatamente después del miembro de origen. **Extraer método** determina la firma del nuevo método, creando un método estático cuando no se hace referencia a ningún dato de instancia por el código en el nuevo método.  
  
## <a name="generic-type-parameters"></a>Parámetros de tipos genéricos  
 Cuando se extrae un método que tiene un parámetro de tipo genérico sin restricciones, el código generado no agregará el `ref` modificador a ese parámetro, a menos que se asigna un valor a él. Si el método extraído admite tipos de referencia como argumento de tipo genérico, debe agregar manualmente el `ref` modificador para el parámetro en la firma del método.  
  
## <a name="anonymous-methods"></a>Métodos anónimos  
 Si intenta extraer parte de un método anónimo que incluye una referencia a una variable local que se declara o se hace referencia fuera del método anónimo, a continuación, Visual Studio generará una advertencia sobre pueden producir cambios semánticos.  
  
 Cuando un método anónimo utiliza el valor de una variable local, se obtiene el valor en el momento en que se ejecuta el método anónimo. Cuando un método anónimo se extrae en otro método, se obtiene el valor de la variable local en el momento de la llamada al método extraído.  
  
 En el ejemplo siguiente se ilustra este cambio semántico. Si se ejecuta este código, a continuación, **11** se imprimirán en la consola. Si usa **Extraer método** para extraer la región de código que está marcada con comentarios de código en su propio método y, a continuación, ejecute el código refactorizado, a continuación, **10** se imprimirán en la consola.  
  
```csharp  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 Para solucionar esta situación, convierta las variables locales que se usan en los campos de un método anónimo de la clase.  
  
## <a name="see-also"></a>Vea también  
 [Refactorización (C#)](refactoring-csharp.md)