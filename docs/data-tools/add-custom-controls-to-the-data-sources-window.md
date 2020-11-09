---
title: Agregar controles personalizados a la ventana de orígenes de datos
description: Agregue controles personalizados a la ventana orígenes de datos en Visual Studio. Personalizar la lista de controles enlazables. Agregar controles asociados.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: 004004a420374f3b0ce9504098ac5836cb307f1d
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382070"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Agregar controles personalizados a la ventana de orígenes de datos

Al arrastrar un elemento desde la ventana orígenes de datos a una superficie de diseño para crear un control enlazado a datos, puede seleccionar el tipo de control que cree. Cada elemento de la ventana tiene una lista desplegable que muestra los controles que puede elegir. El tipo de datos del elemento determina el conjunto de controles asociados a cada elemento. Si el control que desea crear no aparece en la lista, puede seguir las instrucciones de este tema para agregar el control a la lista.

Para obtener más información sobre cómo seleccionar los controles enlazados a datos que se van a crear para los elementos en la ventana orígenes de datos, vea [establecer el control que se creará al arrastrar desde la ventana orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="customize-the-bindable-controls-list"></a>Personalizar la lista de controles enlazables

Para agregar o quitar controles de la lista de controles disponibles para los elementos de la ventana orígenes de datos que tienen un tipo de datos específico, realice los pasos siguientes.

### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Para seleccionar los controles que se van a mostrar para un tipo de datos

1. Asegúrese de que el Diseñador de Windows Forms o de WPF está abierto.

2. En la ventana **orígenes de datos** , haga clic en un elemento que forme parte de un origen de datos que haya agregado a la ventana y, a continuación, haga clic en el menú desplegable del elemento.

   > [!TIP]
   > Si la ventana orígenes de datos no está abierta, ábrala seleccionando **Ver**  >  **otros**  >  **orígenes de datos** de Windows.

3. En el menú desplegable, haga clic en **personalizar**. Se abre uno de los cuadros de diálogo siguientes:

    - Si el **Diseñador de Windows Forms** está abierto, se abre la página **Personalización** de la interfaz de usuario de datos del cuadro de diálogo **Opciones** . Para obtener más información, vea [cuadro de diálogo Opciones de personalización](../ide/reference/options-windows-forms-designer-data-ui-customization.md)de la interfaz de usuario de datos.

    - Si el **Diseñador WPF** está abierto, se abre el cuadro de diálogo **personalizar enlace de control** .

4. En el cuadro de diálogo, seleccione un tipo de datos en la lista desplegable **tipo de datos** .

    - Para personalizar la lista de controles de una tabla o un objeto, seleccione **[lista]**.

    - Para personalizar la lista de controles de una columna de una tabla o de una propiedad de un objeto, seleccione el tipo de datos de la columna o propiedad en el almacén de datos subyacente.

    - Para personalizar la lista de controles para mostrar los objetos de datos que tienen formas definidas por el usuario, seleccione **[otros]**. Por ejemplo, seleccione **[Other]** si la aplicación tiene un control personalizado que muestra los datos de más de una propiedad de un objeto determinado.

5. En el cuadro **controles asociados** , seleccione cada control que desee que esté disponible para el tipo de datos seleccionado o desactive la selección de los controles que desea quitar de la lista.

    > [!NOTE]
    > Si el control que desea seleccionar no aparece en el cuadro **controles asociados** , debe agregar el control a la lista. Para obtener más información, vea [Agregar controles asociados](#add-associated-controls).

6. Haga clic en **OK**.

7. En la ventana **orígenes de datos** , haga clic en un elemento del tipo de datos al que acaba de asociar uno o varios controles y, a continuación, haga clic en el menú desplegable del elemento.

     Los controles seleccionados en el cuadro **controles asociados** aparecen ahora en el menú desplegable del elemento.

## <a name="add-associated-controls"></a>Agregar controles asociados

Si desea asociar un control a un tipo de datos, pero el control no aparece en el cuadro **controles asociados** , debe agregar el control a la lista. El control debe estar ubicado en la solución actual o en un ensamblado al que se hace referencia. También debe estar disponible en el **cuadro de herramientas** y tener un atributo que especifique el comportamiento del enlace de datos del control.

Para agregar controles a la lista de controles asociados:

1. Agregue el control deseado al **cuadro de herramientas** ; para ello, haga clic con el botón secundario en el **cuadro de herramientas** y seleccione **elegir elementos**.

     El control debe tener uno de los siguientes atributos:

    |Atributo|Descripción|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implemente este atributo en controles simples que muestren una única columna (o propiedad) de datos, como <xref:System.Windows.Forms.TextBox> .|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implemente este atributo en los controles que muestran listas (o tablas) de datos, como <xref:System.Windows.Forms.DataGridView> .|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implemente este atributo en controles que muestren listas (o tablas) de datos, pero que también necesiten presentar una única columna o propiedad, como <xref:System.Windows.Forms.ComboBox> .|

2. Por Windows Forms, en el cuadro de diálogo **Opciones** , abra la página de **Personalización** de la interfaz de usuario de datos. O bien, para WPF, abra el cuadro de diálogo **personalizar enlace de control** . Para obtener más información, vea [personalizar la lista de controles enlazables para un tipo de datos](#customize-the-bindable-controls-list).

3. En el cuadro **controles asociados** , ahora debe aparecer el control que acaba de agregar al cuadro de **herramientas** .

    > [!NOTE]
    > Solo los controles que se encuentran dentro de la solución actual o en un ensamblado al que se hace referencia se pueden agregar a la lista de controles asociados. (Los controles también deben implementar uno de los atributos de enlace de datos de la tabla anterior). Para enlazar datos a un control personalizado que no está disponible en la ventana orígenes de datos, arrastre el control desde el **cuadro de herramientas** hasta la superficie de diseño y, a continuación, arrastre el elemento al que se va a enlazar desde la ventana **orígenes de datos** hasta el control.

## <a name="see-also"></a>Vea también

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Cuadro de diálogo Opciones de personalización de la interfaz de usuario de datos](../ide/reference/options-windows-forms-designer-data-ui-customization.md)
