---
title: Modificación del estilo de objetos
titleSuffix: Blend for Visual Studio
description: Obtenga información sobre cómo modificar el estilo de los objetos en Blend para Visual Studio aplicando pinceles, estableciendo Estados visuales y aplicando estilos y plantillas reutilizables.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cfe54db27a16d95904412b5e1181d589ed2fcde8
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046785"
---
# <a name="modify-the-style-of-objects-in-blend-for-visual-studio"></a>Modificación del estilo de los objetos en Blend para Visual Studio

La manera más fácil de personalizar un objeto es establecer propiedades en el panel **Propiedades** .

Si desea volver a utilizar la configuración o un conjunto de configuraciones, cree un recurso reutilizable. Podría tratarse de un *estilo* , una *plantilla* o algo simple como un color personalizado. También puede hacer la apariencia de un control sea distinta en función de su estado. Por ejemplo, que un botón se vuelva verde cuando el usuario haga clic en él.

## <a name="brushes-modify-the-appearance-of-an-object"></a>Pinceles: modificar la apariencia de un objeto

Aplique un pincel a un objeto si desea cambiar su apariencia.

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Pintar una imagen o patrón repetitivos en un objeto

Pinte una imagen o patrón repetitivos en un objeto con un *pincel de diseño en mosaico* .

Para crear un pincel de diseño en mosaico, empiece por crear un recurso de *pincel de imagen* , *pincel con dibujo* o *pincel visual* .

Cree un pincel de imagen con una imagen. Las ilustraciones siguientes muestran el pincel de imagen, el pincel de imagen en mosaico y el pincel de imagen volteado.

![Pincel de imagen](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png) ![Imagen de pinceles en mosaico](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png) ![Imagen de pinceles invertida](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png)

Cree un pincel con dibujo mediante un dibujo vectorial como un trazado o forma. Las ilustraciones siguientes muestran el pincel con dibujo, el pincel con dibujo en mosaico y el pincel con dibujo volteado.

![Pincel con dibujo](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png) ![Pincel con dibujo en mosaico](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png) ![Pincel con dibujo invertido](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png)

Cree un pincel visual a partir de un control como un botón. Las ilustraciones siguientes muestran el pincel visual y el pincel visual en mosaico.

![Pincel visual](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png) ![Pincel visual en mosaico](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png)

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a>Estilos y plantillas: crear una apariencia coherente en todos los controles

Puede diseñar la apariencia y el comportamiento de un control una vez y aplicar ese diseño a otros controles para no tener que hacerlo de manera individual.

**¿Debe usar un estilo?** : Si quiere establecer las propiedades predeterminadas (como el color de un botón), use un *estilo* . Puede modificar un control incluso después de aplicarle un estilo.

**¿Debe usar una plantilla?** : Si quiere cambiar la estructura de un control, use una *plantilla* . Imagine que convierte un gráfico o un logotipo en un botón. El control no se puede modificar después de aplicarle una plantilla.

### <a name="create-a-template-or-style"></a>Crear una plantilla o un estilo

Hay dos maneras de crear una plantilla. puede convertir cualquier objeto de la mesa de trabajo en un control o puede basar la plantilla en un control existente.

Para convertir cualquier objeto en una plantilla de control, seleccione el objeto y, después, en el menú **Herramientas** , pulse **Crear en control** .

Si desea basar la plantilla en un control existente, seleccione un objeto en la mesa de trabajo. Después, en la parte superior de la mesa de trabajo, pulse el botón de ruta de navegación, pulse **Editar plantilla** y, después, seleccione **Editar una copia** o **Crear vacío** .

![Menú Editar plantilla](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png)

Para crear un estilo, seleccione el objeto y, después, en el menú **Objeto** , pulse **Editar estilo** y, después, pulse **Editar una copia** o **Crear vacío** .

- Seleccione **Editar una copia** para empezar con el estilo o la plantilla predeterminados del control.

- Seleccione **Crear vacío** para empezar desde cero.

La opción **Editar actual** solo aparece si edita un estilo o plantilla que ya ha creado, pero no aparecerá para un control que sigue usando una plantilla predeterminada del sistema.

En el cuadro de diálogo **Crear recurso de estilo** , puede ponerle un nombre al estilo o a la plantilla para poder usarlo más adelante, o puede aplicar el estilo o la plantilla a todos los controles de ese tipo.

![Cuadro de diálogo Crear recurso de estilo](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png)

> [!NOTE]
> No es posible crear estilos o plantillas para todos los tipos control. Si un control no los admite, el botón de ruta de navegación no aparecerá sobre la mesa de trabajo.
> Para volver al ámbito de edición del documento principal, haga clic en **Devolver ámbito a** ![Icono de Devolver ámbito a](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png).

### <a name="apply-a-style-or-template-to-a-control"></a>Aplicar un estilo o una plantilla a un control

Haga clic con el botón derecho en un objeto en la ventana [Objetos y escala de tiempo](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window), elija **Editar plantilla** y, luego, **Aplicar recurso** .

![Menú Aplicar recurso](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png)

### <a name="restore-the-default-style-or-template-of-a-control"></a>Restaurar el estilo o la plantilla predeterminados de un control

Seleccione el control y, en la ventana **Propiedades** **, busque la propiedad **Estilo** o **Plantilla** . Elija **Opciones avanzadas** y, después, haga clic en **Restablecer** en el menú contextual.

## <a name="visual-states"></a>Estados visuales

Los estados visuales le permiten cambiar la apariencia de un control según su estado. Los controles pueden tener una apariencia visual distinta según las interacciones del usuario. Por ejemplo, cuando un usuario hace clic en un botón, puede hacer que este se vuelva verde o que se ejecute una animación. El tiempo entre estados visuales se puede alargar o acortar mediante el uso de las transiciones.

![Mouse sobre el estado](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png)

**Vea un vídeo corto:** ![botón Reproducir](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Administrar el estado de los controles WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a>Recursos: crear colores, estilos y plantillas y volver a usarlos más adelante

Prácticamente cualquier elemento del proyecto se puede convertir en un recurso. Un recurso es tan solo un objeto que se puede volver a usar en diferentes sitios de la aplicación. Por ejemplo, puede crear un color, convertirlo en un recurso y después usar ese color en varios objetos. Para cambiar el color de todos esos objetos, simplemente cambie el recurso de color.

![Botón Convertir color en recurso](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png) ![Cuadro de diálogo Crear recurso de color](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png)

## <a name="see-also"></a>Consulte también

- [Crear una IU con Blend para Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
