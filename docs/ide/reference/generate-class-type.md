---
title: Generación de una clase o tipo
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 94786ef10e427a0deb4f80471305509124f1638b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595636"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Generación de una clase o tipo en Visual Studio

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Permite generar el código de inmediato para una clase o un tipo.

**Cuándo:** Presenta una nueva clase o un tipo, y quiere declararlo de manera adecuada y de inmediato.

**Por qué:** Podría declarar la clase o el tipo antes de usarlo; pero esta característica generará la clase o el tipo de forma automática.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en la línea donde haya un subrayado ondulado de color rojo. El subrayado ondulado de color rojo señala una clase que aún no existe.

   - C#:

       ![Código resaltado (C#)](media/class-highlight-cs.png)

   - Visual Basic:

       ![Código resaltado (VB)](media/class-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
      - Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![bombilla de error](media/error-bulb.png) que aparece.
      - Haga clic en el botón ![bombilla de error](media/error-bulb.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

      ![Vista previa de generación de clase](media/class-preview-cs.png)

3. Seleccione una de las opciones del menú desplegable:

   - Generar clase "*TypeName*" en el nuevo archivo: Crea una clase denominada *TypeName* en un archivo denominado *TypeName*.cs/.vb
   - Generar clase "*TypeName*": Crea una clase denominada *TypeName* en el archivo actual.
   - Generar clase anidada "*TypeName*": Crea una clase denominada *TypeName* anidada dentro de la clase actual.
   - Generar nuevo tipo...: Crea una clase o estructura con todas las propiedades que especifique.

   > [!TIP]
   > Use el vínculo **Vista previa de los cambios** en la parte inferior de la ventana de vista previa [para ver todos los cambios ](../../ide/preview-changes.md) que se aplicarán antes de realizar la selección.

4. Si ha seleccionado el elemento **Generar nuevo tipo**, se abre el cuadro de diálogo **Generar tipo**. Configure la accesibilidad, la clase y la ubicación del nuevo tipo.

   ![Generar tipo](media/class-newtype-cs.png)

   Selección | Descripción
   --- | ---
   Access | Configure el tipo para que tenga acceso *Predeterminado*, *Interno* o *Público*.
   Kind | Esta propiedad puede establecerse como *clase* o *struct*.
   NOMBRE | No se puede cambiar y será el nombre que ya ha escrito.
   Proyecto | Si hay varios proyectos en la solución, puede elegir dónde desea que resida la clase/estructura.
   Nombre de archivo | Puede crear un nuevo archivo o agregar el tipo a un archivo existente.

Se crea la clase o el elemento struct. En C# también se crea un constructor.

- C#

   ![Resultado de la generación de clase (C#)](media/class-result-cs.png)

- Visual Basic

   ![Resultado de la generación de clase (VB)](media/class-result-vb.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
