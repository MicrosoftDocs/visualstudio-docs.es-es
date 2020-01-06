---
title: 'Diseñador de flujo de trabajo: Cómo agregar actividades al cuadro de herramientas'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3cde4f3a41a1a07f982f85c0c19e9f16b047068
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593933"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Cómo agregar actividades al cuadro de herramientas

Las actividades se pueden agregar al **cuadro de herramientas** de la solución de varias maneras diferentes. Puede agregarlas desde dentro de su proyecto actual y hacer referencia a las misas desde un proyecto diferente o desde un ensamblado diferente.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Para agregar una actividad desde su proyecto actual

1. Agregue una nueva actividad personalizada al proyecto de flujo de trabajo actual. Para obtener más información sobre cómo agregar una nueva actividad personalizada al proyecto, vea [Cómo: agregar un nuevo elemento a un proyecto de flujo de trabajo](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2. Agregue lógica personalizada a su actividad.

3. Generar el proyecto. Si la compilación se realizó correctamente, se muestra una nueva categoría en el **cuadro de herramientas** denominada "\<*nombre del proyecto*>" con la actividad personalizada incluida en esa categoría.

    > [!NOTE]
    > Si se restablece el cuadro de herramientas, las actividades personalizadas se quitarán, incluso si la solución se compila de nuevo. Para volver a rellenar el cuadro de herramientas con actividades personalizadas después de que se haya restablecido, reinicie Visual Studio.

    > [!NOTE]
    > El cuadro de herramientas solo puede mostrar una actividad de un nombre especificado. Si dos actividades de distintos ensamblados tienen el mismo nombre de clase, solo se mostrará una.

    > [!NOTE]
    > El dominio de aplicación se comparte entre las instancias del editor; si se usan variables estáticas, se compartirán entre las instancias del editor también. Si este no es el comportamiento deseado, se debe usar un servicio para hacer un seguimiento de las instancias variables. Vea [usar el contexto de edición de ModelItem](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) para obtener información sobre el uso de servicios en el diseñador.

## <a name="to-add-an-activity-from-within-a-different-project"></a>Para agregar una actividad desde un proyecto diferente

1. Abra una solución que contenga al menos un proyecto de flujo de trabajo y un proyecto de biblioteca de actividades personalizado u otro proyecto de flujo de trabajo que defina una actividad personalizada.

2. Compile ambos proyectos. Si las compilaciones se realizaron correctamente, se muestra una nueva categoría en el **cuadro de herramientas** denominada "\<*nombre del proyecto*>" con la actividad personalizada incluida en esa categoría.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Para agregar una actividad al cuadro de herramientas desde un ensamblado

1. Abra una solución de flujo de trabajo.

2. En el menú **herramientas** , seleccione **elegir elementos del cuadro de herramientas**.

3. En el cuadro de diálogo **elegir elementos del cuadro de herramientas** , seleccione la pestaña **componentes de System. Activities** y, a continuación, haga clic en **examinar** para desplazarse al ensamblado que contiene la actividad personalizada que desea agregar.

4. Seleccione el ensamblado y haga clic en **Aceptar**. El componente de actividad personalizado se agrega a la lista de componentes y se selecciona automáticamente.

    1. Haga clic en **Aceptar** para cerrar el cuadro de diálogo.

5. Para mostrar el cuadro de herramientas, seleccione **cuadro de herramientas** en el menú **Ver** .

6. La actividad personalizada aparece en el **cuadro de herramientas** en la categoría que tenía el foco antes de que se agregara el elemento. Por ejemplo, si la categoría **General** se seleccionó en el **cuadro de herramientas** antes de agregar el elemento del cuadro de herramientas, la actividad aparece en la categoría **General** .

## <a name="see-also"></a>Vea también

- [Usar el Diseñador de flujo de trabajo](developing-applications-with-the-workflow-designer.md)
