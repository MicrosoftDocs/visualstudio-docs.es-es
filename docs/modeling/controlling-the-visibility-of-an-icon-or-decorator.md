---
title: Controlar la visibilidad de un icono o un objeto Decorator
description: Obtenga información sobre cómo puede controlar la visibilidad de un icono o decorador en función del estado de las propiedades del modelo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9c60d66188364ddd18be1d60a92b51ee5d7a9fc8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389623"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controlar la visibilidad de un icono o un objeto Decorator
Un *decorador* es un icono o línea de texto que aparece en una forma en un lenguaje específico del dominio (DSL). Puede hacer que el decorador aparezca y desaparezca en función del estado de las propiedades del modelo. Por ejemplo, en una forma que representa a una persona, podría tener iconos diferentes que aparecen en función del sexo de la persona, el número de hijos, y así sucesivamente.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Control de la visibilidad de un icono o decorador
 En el procedimiento siguiente se supone que ya ha definido una forma y su asignación a una clase de dominio. Para obtener más información, [vea How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Para controlar la visibilidad de un icono o decorador de texto

1. En el diagrama definición de DSL, agregue a la clase de forma los iconos o decoradores de texto que desea que aparezcan.

   1. Haga clic con el botón derecho en la clase de forma, **seleccione Agregar** y, a continuación, haga clic en el tipo necesario de decorador.

   2. Establezca la propiedad **Position** del decorador. Más de un decorador puede tener la misma posición. Por ejemplo, podría tener iconos para hombres y mujeres que compartan la misma posición.

   3. Establezca la **propiedad Icono** predeterminado de un decorador de iconos.

2. Seleccione el mapa de elementos de diagrama, que es la línea gris entre la clase de forma y la clase de dominio en el diagrama de definición de DSL.

3. En la ventana Detalles de DSL, en la pestaña **Decorator Maps (Mapas de decorador),** seleccione un decorador. Por ejemplo, MaleDecorator.

4. Active la casilla **Filtro de** visibilidad.

5. Si la propiedad de dominio que debe controlar la visibilidad está en la clase de dominio inmediato, deje Ruta de **acceso a la propiedad de filtro en** blanco.

    De lo contrario, haga clic en el menú desplegable y vaya a la relación o clase donde se encuentra la propiedad.

   - Para evitar un informe de errores, no debe navegar por una relación marcada con "*" en la herramienta de navegación.

6. Establezca la **propiedad Filter en** una propiedad de dominio. Por ejemplo, Gender.

7. En la **lista Entradas de visibilidad** , agregue valores de esta propiedad de dominio para la que el decorador debe estar visible. Por ejemplo, Varón.

8. Repita los pasos de cada icono.

9. **Transformar todas las plantillas,** compilar y ejecutar, y abrir un diagrama de prueba.

10. Al cambiar el valor de la propiedad de control, los decoradores deben aparecer y desaparecer.

    Con frecuencia, quiere que la visibilidad se controle mediante una fórmula más compleja que un conjunto simple de valores. Por ejemplo, para que un icono dependa del número de vínculos de un tipo determinado o para que dependa de si un número está en un intervalo determinado. En ese caso, use el procedimiento siguiente.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Para controlar la visibilidad de un decorador basado en una fórmula

1. Agregue una propiedad de dominio calculada a la clase de dominio. En la **ventana** Propiedades, establezca los valores siguientes:

     **IsBrowsable =** `False` **: oculta la propiedad del usuario.**    

     **Kind =** `Calculated` **: esto significa que proporcionará código que calcula su valor.**    

     **Nombre** por ejemplo **DecoratorControl**

     **Tipo** = `Boolean`

     Para obtener más información, vea [Propiedades de almacenamiento calculadas y personalizadas.](../modeling/calculated-and-custom-storage-properties.md)

2. Haga que la nueva propiedad controle la visibilidad del decorador.

    1. Seleccione el mapa de elementos de diagrama, que es la línea gris de la clase de dominio a la forma. En la **ventana Detalles de DSL,** abra la **pestaña DecoratorMap.**

    2. Active la casilla **Filtro de** visibilidad.

    3. En **Propiedad de filtro**, seleccione la propiedad de control **DecoratorControl**.

    4. En **Visibility Entries (Entradas de visibilidad),** escriba `True` .

3. Haga **clic en Transformar todas las** plantillas en la barra **Explorador de soluciones** herramientas.

4. Haga clic **en Compilar solución** en el **menú** Compilar.

5. Haga doble clic en el informe de errores que ha aparecido: "*YourClass* no contiene una definición para GetDecoratorControlValue ...".

     El editor de texto se abre en Dsl\GeneratedCode\DomainClasses.cs. Encima del error resaltado hay un comentario que le solicita que agregue un método.

6. Tenga en cuenta el espacio de nombres, la clase y el método que faltan.  Por ejemplo, Company.FamilyTree.Person.GetDecoratorControlValue().

7. En un archivo de código independiente, escriba una definición de clase parcial que contenga el método que falta. Por ejemplo:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Para obtener más información sobre cómo personalizar el modelo con código de programa, vea Navegar y [actualizar un modelo en código de programa.](../modeling/navigating-and-updating-a-model-in-program-code.md)

8. Recompile y ejecute la solución.

## <a name="see-also"></a>Vea también

- [Definir formas y conectores](../modeling/defining-shapes-and-connectors.md)
- [Establecer una imagen de fondo en un diagrama](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)