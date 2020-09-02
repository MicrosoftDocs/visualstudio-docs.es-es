---
title: Refactorización de extracción de métodos (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e6d5e7913a7433fd4b30da490f33dd614c3e2b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667540"
---
# <a name="extract-method-refactoring-c"></a>Extraer método (Refactorización, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Extraer método** es una operación de refactorización que proporciona una manera sencilla de crear un nuevo método a partir de un fragmento de código en un miembro existente.

 Con **Extraer método**, puede crear un método nuevo extrayendo una selección de código desde dentro del bloque de código de un miembro existente. El nuevo método extraído contiene el código seleccionado y el código seleccionado en el miembro existente se reemplaza por una llamada al nuevo método. Convertir un fragmento de código en su propio método le permite reorganizar el código de forma rápida y precisa para mejorar la reutilización y la legibilidad.

 **Extraer método** tiene las siguientes ventajas:

- Fomenta mejores prácticas de codificación resaltando métodos discretos y reutilizables.

- Fomenta el código autodocumentado a través de una buena organización.

     Cuando se usan nombres descriptivos, los métodos de alto nivel pueden leer más como una serie de comentarios.

- Fomenta la creación de métodos más precisos para simplificar el reemplazo.

- Reduce la duplicación de código.

### <a name="to-use-extract-method"></a>Para usar extract (método)

1. Cree una aplicación de consola denominada `ExtractMethod` y, a continuación, reemplace `Program` por el siguiente código de ejemplo.

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

2. Seleccione el fragmento de código que desea extraer:

    ```csharp
    double area = PI * radius * radius;
    ```

3. En el menú **refactorizar** , haga clic en **Extraer método**.

     Aparecerá el cuadro de diálogo **Extraer método** .

     También puede escribir el método abreviado de teclado CTRL + R, M para mostrar el cuadro de diálogo **Extraer método** .

     También puede hacer clic con el botón secundario en el código seleccionado, seleccionar **refactorizar**y, a continuación, hacer clic en **Extraer método** para mostrar el cuadro de diálogo **Extraer método** .

4. Especifique un nombre para el nuevo método, como `CircleArea` , en el cuadro **nombre del método nuevo** .

     En la **vista previa**de la firma del método se muestra una vista previa de la nueva firma de método.

5. Haga clic en **Aceptar**.

## <a name="remarks"></a>Observaciones
 Cuando se usa el comando **Extract Method** , se inserta el nuevo método después del miembro de origen en la misma clase.

## <a name="partial-types"></a>Tipos parciales
 Si la clase es un tipo parcial, el **método Extract** genera el nuevo método inmediatamente después del miembro de origen. **Extraer método** determina la firma del nuevo método y crea un método estático cuando el código no hace referencia a ningún dato de instancia en el nuevo método.

## <a name="generic-type-parameters"></a>Parámetros de tipos genéricos
 Cuando se extrae un método que tiene un parámetro de tipo genérico sin restricciones, el código generado no agregará el `ref` modificador a ese parámetro a menos que se le asigne un valor. Si el método extraído va a admitir tipos de referencia como argumento de tipo genérico, debe agregar manualmente el `ref` modificador al parámetro en la Signatura del método.

## <a name="anonymous-methods"></a>Métodos anónimos
 Si intenta extraer parte de un método anónimo que incluye una referencia a una variable local que se declara o a la que se hace referencia fuera del método anónimo, Visual Studio le avisará de los posibles cambios semánticos.

 Cuando un método anónimo usa el valor de una variable local, el valor se obtiene en el momento en que se ejecuta el método anónimo. Cuando se extrae un método anónimo en otro método, el valor de la variable local se obtiene en el momento de la llamada al método extraído.

 En el ejemplo siguiente se muestra este cambio semántico. Si se ejecuta este código, se imprimirán **11** en la consola. Si usa **Extract Method** para extraer la región de código marcada por los comentarios de código en su propio método y, a continuación, ejecuta el código refactorizado, se imprimirán **10** en la consola.

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

 Para evitar esta situación, realice las variables locales que se usan en los campos de método anónimo de la clase.

## <a name="see-also"></a>Consulte también
 [Refactorización (C#)](../csharp-ide/refactoring-csharp.md)