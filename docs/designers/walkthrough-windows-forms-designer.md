---
title: Tutorial para el Diseñador de Windows Forms
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer, get started
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 64045221ad9200223264632d4bdbd33ff82d631f
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585350"
---
# <a name="walkthrough-get-started-with-windows-forms-designer"></a>Tutorial: Introducción a Diseñador de Windows Forms

El Diseñador de Windows Forms brinda muchas herramientas para compilar aplicaciones de Windows Forms. En este artículo se muestra cómo compilar una aplicación con las diversas herramientas proporcionadas por el diseñador, incluidas las tareas siguientes:

- Organizar los controles mediante guías de alineación.
- Realizar las tareas de diseñador mediante el uso de etiquetas inteligentes.
- Establecer los márgenes y rellenos de los controles.
- Organizar los controles con un control <xref:System.Windows.Forms.TableLayoutPanel>.
- Crear particiones del diseño de un control con un control <xref:System.Windows.Forms.SplitContainer>.
- Navegar por el diseño con la ventana Esquema del documento.
- Colocar controles con la pantalla de información de tamaño y ubicación.
- Establecer los valores de propiedad con la ventana Propiedades.

Cuando termine, un control personalizado se habrá ensamblado mediante el uso de muchas de las características de diseño disponibles en el Diseñador de Windows Forms. Con este control se implementa la interfaz de usuario (UI) de una calculadora sencilla. En la imagen siguiente se muestra el diseño general del control de la calculadora:

![Visita guiada de la interfaz de usuario de la calculadora](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>Creación del proyecto de control personalizado

El primer paso es crear el proyecto de control DemoCalculator.

1. Abra Visual Studio y cree un proyecto **Biblioteca de controles de Windows Forms**. Asígnele al proyecto el nombre **DemoCalculatorLib**.

   ::: moniker range=">=vs-2019"

   ![Plantilla Biblioteca de controles de Windows Forms en Visual Studio 2019](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. Para cambiar el nombre, en el **Explorador de soluciones**, haga clic con el botón derecho en **UserControl1.vb** o **UserControl1.cs**, seleccione **Cambiar nombre** y cambie el nombre de archivo a DemoCalculator.vb o DemoCalculator.cs. Seleccione **Sí** cuando se le pregunte si quiere cambiar el nombre de todas las referencias al elemento de código "UserControl1".

En el Diseñador de Windows Forms se muestra la superficie del diseñador para el control DemoCalculator. En esta vista, puede diseñar gráficamente la apariencia del control si selecciona controles y componentes en Cuadro de herramientas y los pone en la superficie del diseñador. Para más información sobre los controles personalizados, consulte [Variedades de controles personalizados](/dotnet/framework/winforms/controls/varieties-of-custom-controls).

## <a name="design-the-control-layout"></a>Diseño del control

El control DemoCalculator contiene varios controles de Windows Forms. En este procedimiento, organizará los controles con el Diseñador de Windows Forms.

1. En el Diseñador de Windows Forms, para cambiar el control DemoCalculator a un tamaño mayor, seleccione el controlador de tamaño en la esquina inferior derecha y arrástrelo hacia abajo y a la derecha. En la esquina inferior derecha de Visual Studio busque la información de tamaño y ubicación de los controles. Establezca el tamaño del control en 500 de ancho y 400 de alto y observe la información de tamaño a medida que ajusta el tamaño del control.

2. En **Cuadro de herramientas**, seleccione el nodo **Contenedores** para abrirlo. Seleccione el control **SplitContainer** y arrástrelo a la superficie del diseñador.

   El control`SplitContainer` se coloca en la superficie del diseñador del control DemoCalculator.

    > [!TIP]
    > El control `SplitContainer` se ajusta al tamaño del control DemoCalculator. Observe la ventana **Propiedades** para ver la configuración de las propiedades del control `SplitContainer`. Busque la propiedad <xref:System.Windows.Forms.SplitContainer.Dock%2A>. Su valor es [DockStyle.Fill](xref:System.Windows.Forms.DockStyle.Fill), lo que significa que el tamaño del control `SplitContainer` siempre se ajustará a los límites del control DemoCalculator. Cambie el tamaño del control DemoCalculator para comprobar este comportamiento.

3. En la ventana **Propiedades**, cambie el valor de la propiedad <xref:System.Windows.Forms.SplitContainer.Dock%2A> a `None`.

    El tamaño del control `SplitContainer` se reduce al tamaño predeterminado y ya no se ajusta al tamaño del control DemoCalculator.

4. Seleccione el glifo de etiquetas inteligentes (![Glifo de etiquetas inteligentes](media/smart-tag-glyph.gif)) en la esquina superior derecha del control `SplitContainer`. Seleccione **Acoplar en contenedor primario** para establecer la propiedad `Dock` en `Fill`.

    El control `SplitContainer` se acopla a los límites del control DemoCalculator.

    > [!NOTE]
    > Varios controles ofrecen etiquetas inteligentes para facilitar el diseño. Para obtener más información, vea [Tutorial: Realizar tareas comunes con etiquetas inteligentes en los controles de Windows Forms](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls).

5. Seleccione el borde vertical entre los paneles y arrástrelo a la derecha, para que el panel izquierdo tenga la mayor parte del espacio.

    `SplitContainer` divide el control DemoCalculator en dos paneles con un borde movible que los separa. En el panel de la izquierda estarán los botones y la pantalla de la calculadora y en el panel de la derecha, se mostrará un registro de las operaciones aritméticas que realice el usuario.

6. En la ventana **Propiedades**, cambie el valor de la propiedad `BorderStyle` a `Fixed3D`.

7. En **Cuadro de herramientas**, seleccione el nodo **Controles comunes** para abrirlo. Seleccione el control `ListView` y arrástrelo al panel derecho del control `SplitContainer`.

8. Seleccione el glifo de etiqueta inteligente del control `ListView`. En el panel de etiquetas inteligentes, cambie la configuración de `View` a `Details`.

9. En el panel de etiquetas inteligentes, seleccione **Editar columnas**.

   Se abre el cuadro de diálogo **Editor de la colección ColumnHeader**.

10. En el cuadro de diálogo **Editor de la colección ColumnHeader**, seleccione **Agregar** para agregar una columna en el control `ListView`. Cambie el valor de la propiedad `Text` de la columna a **Historial**. Seleccione **Aceptar** para crear la columna.

11. En el panel de etiquetas inteligentes, seleccione **Acoplar en contenedor primario** y, luego, seleccione el glifo de etiquetas inteligentes para cerrar el panel de etiquetas inteligentes.

12. En el **Cuadro de herramientas** del nodo **Contenedores**, arrastre un control `TableLayoutPanel` al panel izquierdo del control `SplitContainer`.

    El control `TableLayoutPanel` aparece en la superficie del diseñador con el panel de etiquetas inteligentes abierto. El control `TableLayoutPanel` organiza sus controles secundarios en una cuadrícula. El control `TableLayoutPanel` contendrá la pantalla y los botones del control DemoCalculator. Para obtener más información, vea [Tutorial: Organizar los controles mediante TableLayoutPanel](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel).

13. Seleccione **Editar filas y columnas** en el panel de etiquetas inteligentes.

    Se abre el cuadro de diálogo **Estilos de columna y fila**.

14. Seleccione el botón **Agregar** hasta que se muestren cinco columnas. Seleccione las cinco columnas y, luego, seleccione **Porcentaje** en el cuadro **Tipo de tamaño**. Establezca el valor **Porcentaje** en **20**. Esto establece cada columna en el mismo ancho.

15. En **Mostrar**, seleccione **Filas**.

16. Seleccione **Agregar** hasta que se muestren cinco filas. Seleccione las cinco filas y, luego, seleccione **Porcentaje** en el cuadro **Tipo de tamaño**. Establezca el valor **Porcentaje** en **20**. Esto establece cada fila en la misma altura.

17. Seleccione **Aceptar** para aceptar los cambios y, luego, seleccione el glifo de etiquetas inteligentes para cerrar el panel de etiquetas inteligentes.

18. En la ventana **Propiedades**, cambie el valor de la propiedad `Dock` a `Fill`.

## <a name="populate-the-control"></a>Relleno del control

Ahora que se configuró el diseño del control, puede rellenar el control DemoCalculator con botones y una pantalla.

1. En **Cuadro de herramientas**, haga doble clic en el icono del control `TextBox`.

   Un control `TextBox` se coloca en la primera celda del control `TableLayoutPanel`.

2. En la ventana **Propiedades**, cambie el valor de la propiedad ColumnSpan del control `TextBox` a **5**.

   El control `TextBox` se mueve a una posición centrada en su fila.

3. Cambie el valor de la propiedad `Anchor` del control `TextBox` a `Left`, `Right`.

   El control `TextBox` se expande horizontalmente para abarcar las cinco columnas.

4. Cambie el valor de la propiedad `TextBox` del control `TextAlign` a `Right`.

5. En la ventana **Propiedades**, expanda el nodo de la propiedad `Font`. Establezca `Size` en **14** y `Bold` en **true** para el control `TextBox`.

6. Seleccione el control `TableLayoutPanel`.

7. En **Cuadro de herramientas**, haga doble clic en el icono `Button`.

   Un control `Button` se coloca en la celda abierta siguiente del control `TableLayoutPanel`.

8. En **Cuadro de herramientas**, haga doble clic en el icono `Button` cuatro veces más para rellenar la segunda fila del control `TableLayoutPanel`.

9. Para seleccionar los cinco controles `Button`, mantenga presionada la tecla **Mayús** y selecciónelos. Presione **Ctrl**+**C** para copiar los controles `Button` en el Portapapeles.

10. Presione **Ctrl**+**V** tres veces para pegar copias de los controles `Button` en las filas restantes del control `TableLayoutPanel`.

11. Para seleccionar los 20 controles `Button`, mantenga presionada la tecla **Mayús** y selecciónelos.

12. En la ventana **Propiedades**, cambie el valor de la propiedad `Dock` a `Fill`.

    Todos los controles `Button` se acoplan para rellenar sus celdas contenedoras.

13. En la ventana **Propiedades**, expanda el nodo de la propiedad `Margin`. Establezca el valor de `All` en **5**.

    El tamaño de todos los controles `Button` se reduce para crear un margen mayor entre ellos.

14. Seleccione **button10** y **button20** y, luego, presione **Eliminar** para quitarlos del diseño.

15. Seleccione **button5** y **button15** y, luego, cambie el valor de la propiedad `RowSpan` a **2**. Estos serán los botones **Borrar** y **=** del control DemoCalculator.

## <a name="use-the-document-outline-window"></a>Uso de la ventana Esquema del documento

Cuando el control o formulario se rellena con varios controles, puede que le result más sencillo navegar por el diseño con la ventana Esquema del documento.

1. En la barra de menús, elija **Ver** > **Otras ventanas** > **Esquema del documento**.

   En la ventana Esquema del documento se muestra una vista de árbol del control DemoCalculator y sus controles constituyentes. Los controles contenedores, como`SplitContainer`, muestran sus controles secundarios como subnodos en el árbol. También puede cambiar el nombre de los controles en contexto con la ventana Esquema del documento.

2. En la ventana **Esquema del documento**, haga clic con el botón derecho en **button1** y seleccione **Cambiar nombre**. Cámbiele el nombre a sevenButton.

3. Con la ventana **Esquema del documento**, cámbiele el nombre a los controles `Button` desde el nombre generado por el diseñador al nombre de producción según la lista siguiente:

   - button1 a **sevenButton**

   - button2 a **eightButton**

   - button3 a **nineButton**

   - button4 a **divisionButton**

   - button5 a **clearButton**

   - button6 a **fourButton**

   - button7 a **fiveButton**

   - button8 a **sixButton**

   - button9 a **multiplicationButton**

   - button11 a **oneButton**

   - button12 a **twoButton**

   - button13 a **threeButton**

   - button14 a **subtractionButton**

   - button15 a **equalsButton**

   - button16 a **zeroButton**

   - button17 a **changeSignButton**

   - button18 a **decimalButton**

   - button19 a **additionButton**

4. Con las ventanas **Esquema del documento** y **Propiedades**, cambie el valor de la propiedad `Text` de cada nombre de control `Button` según la lista siguiente:

   - Cambie la propiedad de texto del control sevenButton a **7**

   - Cambie la propiedad de texto del control eightButton a **8**

   - Cambie la propiedad de texto del control nineButton a **9**

   - Cambie la propiedad de texto del control divisionButton a **/** (barra diagonal)

   - Cambie la propiedad de texto del control clearButton a **Borrar**

   - Cambie la propiedad de texto del control fourButton a **4**

   - Cambie la propiedad de texto del control fiveButton a **5**

   - Cambie la propiedad de texto del control sixButton a **6**

   - Cambie la propiedad de texto del control multiplicationButton a **\*** (asterisco)

   - Cambie la propiedad de texto del control oneButton a **1**

   - Cambie la propiedad de texto del control twoButton a **2**

   - Cambie la propiedad de texto del control threeButton a **3**

   - Cambie la propiedad de texto del control subtractionButton a **-** (guion)

   - Cambie la propiedad de texto del control equalsButton a **=** (signo igual)

   - Cambie la propiedad de texto del control zeroButton a **0**

   - Cambie la propiedad de texto del control changeSignButton a **+/-**

   - Cambie la propiedad de texto del control decimalButton a **.** (punto)

   - Cambie la propiedad de texto del control additionButton a **+** (signo más)

5. En la superficie del diseñador, seleccione todos los controles `Button` mientras mantiene presionada la tecla **Mayús**.

6. En la ventana **Propiedades**, expanda el nodo de la propiedad `Font`. Establezca `Size` en **14** y `Bold` en **true** para todos los controles `Button`.

Esto completa el diseño del control DemoCalculator. Todo lo que queda es proporcionan la lógica de calculadora.

## <a name="implement-event-handlers"></a>Implementación de controladores de eventos

Los botones del control DemoCalculator tienen controladores de eventos que se pueden usar para implementar gran parte de la lógica de calculadora. El Diseñador de Windows Forms le permite implementar los códigos auxiliares de todos los controladores de eventos para todos los botones con un solo doble clic.

1. En la superficie del diseñador, seleccione todos los controles `Button` mientras mantiene presionada la tecla **Mayús**.

2. Haga doble clic en uno de los controles `Button`.

   El Editor de código se abre en los controladores de eventos que genera el diseñador.

## <a name="test-the-control"></a>Prueba del control

Como el control DemoCalculator hereda de la clase <xref:System.Windows.Forms.UserControl>, puede probar su comportamiento con **UserControl Test Container**. Para obtener más información, vea [Cómo: Prueba del comportamiento de UserControl en tiempo de ejecución](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol).

1. Presione **F5** para compilar y ejecutar el control DemoCalculator en **UserControl Test Container**.

2. Seleccione el borde entre los paneles `SplitContainer` y arrástrelo a la izquierda y a la derecha. El tamaño de `TableLayoutPanel` y de todos sus controles secundarios cambia para ajustarse al espacio disponible.

3. Cuando termine de probar el control, seleccione **Cerrar**.

## <a name="use-the-control-on-a-form"></a>Uso del control en un formulario

El control DemoCalculator se puede usar en otros controles compuestos o en un formulario. En el procedimiento siguiente se describe cómo usarlo.

### <a name="create-the-project"></a>Crear el proyecto

El primer paso es crear el proyecto de la aplicación. Usará este proyecto para compilar la aplicación que muestra el control personalizado.

1. Cree un proyecto de **aplicación de Windows Forms** y asígnele el nombre **DemoCalculatorTest**.

2. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **DemoCalculatorTest** y, luego, seleccione **Agregar referencia** para abrir el cuadro de diálogo **Agregar referencia**.

3. Seleccione la pestaña **Proyectos** y, luego, haga doble clic con el proyecto DemoCalculatorLib para agregar la referencia al proyecto de prueba.

4. En el **Explorador de soluciones**, haga clic con el botón derecho en **DemoCalculatorTest** y, luego, seleccione **Establecer como proyecto de inicio**.

5. En el Diseñador de Windows Forms, aumente el tamaño del formulario a alrededor de **700 x 500**.

### <a name="use-the-control-in-the-forms-layout"></a>Uso del control en el diseño del formulario

Para usar el control DemoCalculator en una aplicación, deberá colocarlo en un formulario.

1. En **Cuadro de herramientas**, expanda el nodo **Componentes de DemoCalculatorLib**.

2. Arrastre el control **DemoCalculator** desde el **Cuadro de herramientas** al formulario. Mueva el control a la esquina superior derecha del formulario. Cuando el control esté cerca de los bordes del formulario, aparecerán las *guías de alineación*. Las guías de alineación indican la distancia de la propiedad `Padding` del formulario y de la propiedad `Margin` del control. Coloque el control en la ubicación que indican las guías de alineación.

   Para obtener más información, vea [Tutorial: Organizar los controles mediante guías de alineación](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines).

3. Arrastre un control `Button` desde el **Cuadro de herramientas** y suéltelo en el formulario.

4. Mueva el control `Button` alrededor del control DemoCalculator y observe dónde aparecen las guías de alineación. Con esta característica, puede alinear los controles de manera precisa y sencilla. Cuando haya finalizado, elimine el control `Button`.

5. Haga clic con el botón derecho en el control DemoCalculator y, luego, seleccione **Propiedades**.

6. Cambie el valor de la propiedad `Dock` a `Fill`.

7. Seleccione el formulario y, luego, expanda el nodo de la propiedad `Padding`. Cambie el valor de **Todos** a **20**.

   El tamaño del control DemoCalculator se reduce para ajustar el valor `Padding` nuevo del formulario.

8. Para cambiar el tamaño del formulario, arrastre los distintos controladores de tamaño a las distintas posiciones. Observe cómo cambia el tamaño del control DemoCalculator y se ajusta.

## <a name="next-steps"></a>Pasos siguientes

En este artículo se mostró cómo construir la interfaz de usuario de una calculadora sencilla. Para continuar, puede extender su funcionalidad implementando la lógica de calculadora y, luego, [publicar la aplicación mediante ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md). O bien, siga con otro tutorial en el que [creará un visor de imágenes con Windows Forms](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Vea también

- [Controles de Windows Forms](/dotnet/framework/winforms/controls/)
- [Accesibilidad para los controles de Windows Forms](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [Publicación mediante ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)