---
title: "Extraer m&#233;todo (Refactorizaci&#243;n, C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.extractmethod"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactorización [C#], extraer método"
  - "Extraer método (operación de refactorización) [C#]"
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Extraer m&#233;todo (Refactorizaci&#243;n, C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Extraer método** es una operación de refactorización que proporciona una manera sencilla para crear un nuevo método a partir de un fragmento de código de un miembro existente.  
  
 Utilizando **Extraer método** se puede crear un nuevo método extrayendo una selección de código de dentro del bloque de código de un miembro existente.  El nuevo método que se ha extraído contiene el código seleccionado, y el código seleccionado del miembro existente se reemplaza por una llamada al nuevo método.  Convertir un fragmento de código en su propio método permite reorganizar el código de forma rápida y precisa para que sea posible volver a utilizarlo y lograr una mejor legibilidad.  
  
 **Extraer método** tiene las ventajas siguientes:  
  
-   Fomenta el uso de mejores métodos de codificación, dando énfasis a métodos discretos y reutilizables.  
  
-   Recomienda el código autodocumentado a través de una buena organización.  
  
     Si se utilizan nombres descriptivos, los métodos de alto nivel se pueden leer como una serie de comentarios.  
  
-   Fomenta la creación de métodos más detallados para simplificar la sustitución.  
  
-   Reduce la duplicación del código.  
  
### Para utilizar Extraer método  
  
1.  Cree una aplicación de consola denominada `ExtractMethod` y, a continuación, reemplace `Program` por el ejemplo de código siguiente.  
  
    ```c#  
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
  
2.  Seleccione el fragmento de código que se desea extraer:  
  
    ```c#  
    double area = PI * radius * radius;  
  
    ```  
  
3.  En el menú **Refactorizar**, haga clic en **Extraer método**.  
  
     Aparecerá el cuadro de diálogo **Extraer método**.  
  
     De forma alternativa, también puede escribir el método abreviado de teclado CTRL\+R, M para mostrar el cuadro de diálogo **Extraer método**.  
  
     O bien, puede hacer clic con el botón secundario del mouse en el código seleccionado, seleccionar **Refactorizar** y, a continuación, hacer clic en **Extraer método** para mostrar el cuadro de diálogo **Extraer método**.  
  
4.  Especifique un nombre para el nuevo método, por ejemplo `CircleArea`, en el cuadro de texto **Nombre del nuevo método**.  
  
     Aparecerá una vista previa de la nueva firma de método en **Vista previa de la firma del método**.  
  
5.  Haga clic en **Aceptar**.  
  
## Comentarios  
 Cuando se utiliza el comando **Extraer método**, el nuevo método se inserta a continuación del miembro de origen en la misma clase.  
  
## Tipos parciales  
 Si la clase es un tipo parcial, **Extraer método** genera el nuevo método inmediatamente después del miembro de origen.  **Extraer método** determina la firma del nuevo método, creando un método estático si el código incluido en el nuevo método no hace ninguna referencia a los datos de la instancia.  
  
## Parámetros de tipo genérico  
 Si extrae un método que tiene un parámetro de tipo genérico sin restricciones, el código generado no agregará el modificador `ref` a dicho parámetro a no ser que se le asigne un valor.  Si el método extraído admite tipos de referencia como el argumento de tipo genérico, deberá agregar manualmente el modificador `ref` al parámetro en la firma del método.  
  
## Métodos anónimos  
 Si intenta extraer parte de un método anónimo que incluye una referencia a una variable local que se declara o a la que se hace referencia fuera del método anónimo, Visual Studio le advertirá que se pueden producir cambios semánticos.  
  
 Cuando un método anónimo utiliza el valor de una variable local, el valor se obtiene en el momento en que se ejecuta el método anónimo.  Cuando un método anónimo se extrae en otro método, el valor de la variable local se obtiene en el momento de la llamada al método extraído.  
  
 El siguiente ejemplo ilustra este cambio semántico.  Si se ejecuta este código, **11** se imprimirá en la consola.  Si usa **Extraer método** para extraer el área de código que está marcada con comentarios de código en su propio método y, a continuación, ejecuta el código refactorizado, **10** se imprimirá en la consola.  
  
```c#  
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
  
 Para evitar esta situación, convierta las variables locales que se usan en el método anónimo en campos de la clase.  
  
## Vea también  
 [Refactorización \(C\#\)](../csharp-ide/refactoring-csharp.md)