---
title: Controlar la visibilidad de un icono o un objeto Decorator
description: Obtenga información sobre cómo puede controlar la visibilidad de un icono o un elemento Decorator en función del estado de las propiedades del modelo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23df6dc45d1d96997a18942e7878a84a5d9f60a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942807"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controlar la visibilidad de un icono o un objeto Decorator
Un elemento *Decorator* es un icono o una línea de texto que aparece en una forma en un lenguaje específico de dominio (DSL). Puede hacer que el elemento Decorator aparezca y desaparezca en función del estado de las propiedades del modelo. Por ejemplo, en una forma que representa a una persona, puede tener iconos diferentes que aparecen según el sexo de la persona, el número de hijos, etc.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controlar la visibilidad de un icono o un elemento Decorator
 En el procedimiento siguiente se supone que ya ha definido una forma y su asignación a una clase de dominio. Para obtener más información, consulte [definición de un lenguaje Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Para controlar la visibilidad de un icono o un decorador de texto

1. En el diagrama de definición de DSL, agregue a la clase de forma los iconos o los decoradores de texto que desea que aparezcan.

   1. Haga clic con el botón secundario en la clase de forma, seleccione **Agregar** y, a continuación, haga clic en el tipo de elemento Decorator requerido.

   2. Establezca la propiedad **Position** del decorador. Más de un elemento Decorator puede tener la misma posición. Por ejemplo, podría tener iconos para el uso compartido de machos y hembras en la misma posición.

   3. Establezca la propiedad **icono predeterminado** de un decorador de icono.

2. Seleccione la asignación de elemento de diagrama, que es la línea gris entre la clase de forma y la clase de dominio en el diagrama de definición de DSL.

3. En la ventana detalles de DSL, en la pestaña **asignaciones de Decorator** , seleccione un elemento Decorator. Por ejemplo, MaleDecorator.

4. Active la casilla **filtro de visibilidad** .

5. Si la propiedad de dominio que debe controlar la visibilidad está en la clase de dominio inmediata, deje la **propiedad ruta de acceso a filtro** en blanco.

    En caso contrario, haga clic en el menú desplegable y navegue hasta la relación o clase en la que se encuentra la propiedad.

   - Para evitar un informe de errores, no debe desplazarse por una relación marcada con "*" en la herramienta de navegación.

6. Establezca la **propiedad filtro** en una propiedad de dominio. Por ejemplo, sexo.

7. En la lista de **entradas de visibilidad** , agregue valores de esta propiedad de dominio para los que el elemento Decorator debe estar visible. Por ejemplo, hombre.

8. Repita los pasos para cada icono.

9. **Transformar todas las plantillas**, compilar y ejecutar, y abrir un diagrama de prueba.

10. Al cambiar el valor de la propiedad de control, los elementos Decorator deben aparecer y desaparecer.

    Con frecuencia, desea que la visibilidad esté controlada por una fórmula más compleja que un conjunto simple de valores. Por ejemplo, para que un icono dependa del número de vínculos de un tipo determinado, o para que dependa de si un número está en un intervalo determinado. En ese caso, utilice el procedimiento siguiente.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Para controlar la visibilidad de un elemento Decorator basándose en una fórmula

1. Agregue una propiedad de dominio calculado a la clase de dominio. En la ventana **propiedades** , establezca los valores siguientes:

     **IsBrowsable =** `False` **-Esto oculta la propiedad del usuario**    

     **Kind =** `Calculated` **: Esto significa que se proporcionará código que calcula su valor**    

     **Nombre** , por ejemplo **DecoratorControl**

     **Automáticamente** = `Boolean`

     Para obtener más información, consulte [propiedades de almacenamiento calculado y personalizado](../modeling/calculated-and-custom-storage-properties.md).

2. Haga que la nueva propiedad controle la visibilidad del elemento Decorator.

    1. Seleccione la asignación de elemento de diagrama, que es la línea gris de la clase de dominio a la forma. En la ventana **detalles de DSL** , abra la pestaña **DecoratorMap** .

    2. Active la casilla **filtro de visibilidad** .

    3. En **propiedad de filtro**, seleccione la propiedad de control **DecoratorControl**.

    4. En **entradas de visibilidad**, escriba `True` .

3. Haga clic en **transformar todas las plantillas** en la barra de herramientas **Explorador de soluciones** .

4. Haga clic en **compilar solución** en el menú **compilar** .

5. Haga doble clic en el informe de errores que ha aparecido: "*YourClass* no contiene una definición para GetDecoratorControlValue...".

     El editor de texto se abre en Dsl\GeneratedCode\DomainClasses.cs. Encima del error resaltado se encuentra un comentario que le solicita que agregue un método.

6. Tenga en cuenta el espacio de nombres, la clase y el método que faltan.  Por ejemplo, Company. FamilyTree. person. GetDecoratorControlValue ().

7. En un archivo de código independiente, escriba una definición de clase parcial que contenga el método que falta. Por ejemplo:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Para obtener más información sobre cómo personalizar el modelo con código de programa, vea [navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

8. Vuelva a generar y ejecutar la solución.

## <a name="see-also"></a>Vea también

- [Definir formas y conectores](../modeling/defining-shapes-and-connectors.md)
- [Establecer una imagen de fondo en un diagrama](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)