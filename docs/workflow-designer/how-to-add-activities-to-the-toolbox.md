---
title: "Cómo: agregar actividades al cuadro de herramientas | Documentos de Microsoft"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 275917a56d451c35093bcb1b42aadcb599a4aa4e
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Cómo agregar actividades al cuadro de herramientas

Se pueden agregar actividades a la **cuadro de herramientas** en la solución de varias maneras diferentes. Puede agregarlas desde dentro de su proyecto actual y hacer referencia a las misas desde un proyecto diferente o desde un ensamblado diferente.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Para agregar una actividad desde su proyecto actual

1.  Agregue una nueva actividad personalizada al proyecto de flujo de trabajo actual. Para obtener más información acerca de cómo agregar una nueva actividad personalizada al proyecto, vea [Cómo: agregar un nuevo elemento a un proyecto de flujo de trabajo](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2.  Agregue lógica personalizada a su actividad.

3.  Compile el proyecto. Si la compilación se realizó correctamente, una nueva categoría en la **cuadro de herramientas** denominado "\<*nombre del proyecto*>" se muestra con la actividad personalizada incluida en esa categoría.

    > [!NOTE]
    > Si se restablece el cuadro de herramientas, las actividades personalizadas se quitarán, incluso si la solución se compila de nuevo. Para volver a rellenar el cuadro de herramientas con actividades personalizadas después de que se haya restablecido, reinicie [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

    > [!NOTE]
    > El cuadro de herramientas solo puede mostrar una actividad de un nombre especificado. Si dos actividades de distintos ensamblados tienen el mismo nombre de clase, solo se mostrará una.

    > [!NOTE]
    > El dominio de aplicación se comparte entre las instancias del editor; si se usan variables estáticas, se compartirán entre las instancias del editor también. Si este no es el comportamiento deseado, se debe usar un servicio para hacer un seguimiento de las instancias variables. Vea [utilizando el contexto de edición de ModelItem](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) para obtener información sobre el uso de los servicios en el diseñador.

## <a name="to-add-an-activity-from-within-a-different-project"></a>Para agregar una actividad desde un proyecto diferente

1.  Abra una solución que contenga al menos un proyecto de flujo de trabajo y un proyecto de biblioteca de actividades personalizado u otro proyecto de flujo de trabajo que defina una actividad personalizada.

2.  Compile ambos proyectos. Si las compilaciones se realizaron correctamente, una nueva categoría en la **cuadro de herramientas** denominado "\<*nombre del proyecto*>" se muestra con la actividad personalizada incluida en esa categoría.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Para agregar una actividad al cuadro de herramientas desde un ensamblado

1.  Abra una solución de flujo de trabajo.

2.  Desde el **herramientas** menú, seleccione **elegir elementos del cuadro de herramientas...** .

3.  En el **elegir elementos del cuadro de herramientas** cuadro de diálogo, seleccione la **componentes de System.Activities** ficha, a continuación, haga clic en **Examinar...**  para navegar hasta el ensamblado que contiene la actividad personalizada que desea agregar.

4.  Seleccione el ensamblado y haga clic en **Aceptar**. El componente de actividad personalizado se agrega a la lista de componentes y se selecciona automáticamente.

    1.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo.

5.  Para mostrar el cuadro de herramientas, seleccione **cuadro de herramientas** desde el **vista** menú.

6.  La actividad personalizada aparece en la **cuadro de herramientas** en la categoría que fue el foco antes de que se agregó el elemento. Por ejemplo, si la **General** categoría se ha seleccionado en el **cuadro de herramientas** antes de agregar el elemento de cuadro de herramientas, la actividad aparece en el **General** categoría.

## <a name="see-also"></a>Vea también

- [Usar el Diseñador de flujo de trabajo](../workflow-designer/using-the-workflow-designer.md)