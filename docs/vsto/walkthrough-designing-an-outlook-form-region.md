---
title: 'Tutorial: diseñar un área de formulario de Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01cfe55964a1d61c2ad200c9538ced9ff0aa5599
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985463"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Tutorial: diseñar un área de formulario de Outlook
  Las áreas de formulario personalizadas extienden los formularios estándar o personalizados de Microsoft Office Outlook. En este tutorial diseñará un área de formulario personalizada que aparece como una nueva página en la ventana del inspector de un elemento de contacto. Esta área de formulario muestra una asignación de cada dirección incluida para el contacto, enviando la información de la dirección al sitio web de búsqueda local de Windows Live. Para obtener información sobre las áreas de formulario, consulte [crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Crear un proyecto de complemento de VSTO de Outlook

- Agregar un área de formulario al proyecto de complemento de VSTO.

- Definir el diseño del área de formulario.

- Personalizar el comportamiento del área de formulario.

- Probar el área de formulario de Outlook.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] o posterior.

  ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") Para obtener una versión en vídeo de este tema, vea [el vídeo cómo: diseñar un área de formulario de Outlook](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90)).

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Crear un nuevo proyecto de complemento de VSTO de Outlook
 En primer lugar, cree un proyecto básico de complemento de VSTO.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Para crear un proyecto de complemento de VSTO de Outlook

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , cree un proyecto de complemento de VSTO de Outlook con el nombre **MapItAddIn**.

2. En el cuadro de diálogo **Nuevo proyecto** , seleccione **Crear directorio para la solución**.

3. Guarde el proyecto en cualquier directorio.

     Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Agregar un área de formulario al proyecto de complemento de VSTO de Outlook
 Una solución de complemento de VSTO de Outlook puede contener uno o varios elementos de área de formulario de Outlook. Agregue un elemento de área de formulario al proyecto mediante el asistente **nueva área de formulario de Outlook** .

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Para agregar un área de formulario al proyecto de complemento de VSTO de Outlook

1. En **Explorador de soluciones**, seleccione el proyecto **MapItAddIn** .

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **área de formulario de Outlook**, asigne al archivo el nombre **MapIt**y, a continuación, haga clic en **Agregar**.

     Se inicia el Asistente para **NewOutlook Form region** .

4. En la página **Seleccione cómo desea crear el área de formulario** , haga clic en **diseñar una nueva área de formulario**y, a continuación, haga clic en **siguiente**.

5. En la página **Seleccione el tipo de área de formulario que desea crear** , haga clic en **independiente**y, a continuación, haga clic en **siguiente**.

     Un área de formulario *independiente* agrega una nueva página a un formulario de Outlook. Para obtener más información sobre los tipos de áreas de formulario, consulte [crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md).

6. En la página **proporcione texto descriptivo y seleccione sus preferencias de presentación** , escriba **asígnela** en el cuadro **nombre** .

     Este nombre aparece en la cinta de opciones de la ventana del inspector cuando se abre el elemento de contacto.

7. Seleccione **inspectores que estén en modo de redacción** e **inspectores que estén en modo de lectura**y, a continuación, haga clic en **siguiente**.

8. En la página **identifique las clases de mensaje que mostrarán esta área de formulario** , desactive mensaje de **correo**, seleccione **contacto**y, a continuación, haga clic en **Finalizar**.

     Se agrega un archivo *MapIt.CS* o *MapIt. VB* al proyecto.

## <a name="design-the-layout-of-the-form-region"></a>Diseñar el diseño del área de formulario
 Desarrollar áreas de formulario visualmente mediante el *Diseñador de áreas de formulario*. Puede arrastrar controles administrados a la superficie del Diseñador de áreas de formulario. Use el diseñador y la ventana **propiedades** para ajustar el diseño y la apariencia del control.

### <a name="to-design-the-layout-of-the-form-region"></a>Para definir el diseño del área de formulario

1. En **Explorador de soluciones**, expanda el proyecto **MapItAddIn** y, a continuación, haga doble clic en *MapIt.CS* o *MapIt. VB* para abrir el diseñador de áreas de formulario.

2. Haga clic con el botón secundario en el diseñador y, a continuación, haga clic en **propiedades**.

3. En la ventana **propiedades** , establezca **tamaño** en **664, 469**.

     De esta forma se garantiza que el área de formulario sea suficientemente grande para mostrar una asignación.

4. En el menú **Ver** , haga clic en **Cuadro de herramientas**.

5. En la pestaña **controles comunes** del **cuadro de herramientas**, agregue un control **WebBrowser** al área de formulario.

     **WebBrowser** mostrará un mapa de cada dirección que se muestra para el contacto.

## <a name="customize-the-behavior-of-the-form-region"></a>Personalizar el comportamiento del área de formulario
 Agregue código a los controladores de eventos del área de formulario para personalizar el comportamiento de un área de formulario en tiempo de ejecución. Para esta área de formulario, el código examina las propiedades de un elemento de Outlook y determina si se va a mostrar el área de formulario Map It. Si muestra el área de formulario, el código se desplaza a la búsqueda local de Windows Live y carga una asignación de cada dirección incluida en el elemento de contacto de Outlook.

### <a name="to-customize-the-behavior-of-the-form-region"></a>Para personalizar el comportamiento del área de formulario

1. En **Explorador de soluciones**, haga clic con el botón secundario en *MapIt.CS* o *MapIt. VB*y, a continuación, haga clic en **Ver código**.

    *MapIt.CS* o *MapIt. VB* se abre en el editor de código.

2. Expanda la región de código **generador de áreas de formulario** .

    Se expone la clase de generador de áreas de formulario llamada `MapItFactory`.

3. Agregue el código siguiente al controlador de eventos `MapItFactory_FormRegionInitializing`. Se llama a este controlador de eventos cuando el usuario abre un elemento de contacto. El siguiente código determina si el elemento de contacto contiene una dirección. Si el elemento de contacto no contiene una dirección, este código establece la <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propiedad de la <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> clase en **true** y no se muestra el área de formulario. De lo contrario, el complemento de VSTO provoca el evento <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> y muestra el área de formulario.

    [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
    [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

4. Agregue el código siguiente al controlador de eventos <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Este código realiza las tareas siguientes:

   - Concatena cada dirección del elemento de contacto y crea una cadena de dirección URL.

   - Llama al método <xref:System.Windows.Forms.WebBrowser.Navigate%2A> del objeto <xref:System.Windows.Forms.WebBrowser> y pasa la cadena de dirección URL como parámetro.

     El sitio web de búsqueda local aparece en el área de formulario Map It y presenta las direcciones en el bloc de notas.

     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]

## <a name="test-the-outlook-form-region"></a>Probar el área de formulario de Outlook
 Al ejecutar el proyecto, Visual Studio abrirá Outlook. Abra un elemento de contacto para ver el área de formulario Map It. El área de formulario Map It aparece como página en el formulario de cualquier elemento de contacto que contenga una dirección.

### <a name="to-test-the-map-it-form-region"></a>Para comprobar el área de formulario Map It

1. Presione **F5** para ejecutar el proyecto.

     Se abre Outlook.

2. En Outlook, en la pestaña **Inicio** , haga clic en **nuevos elementos**y, a continuación, haga clic en **contacto**.

3. En el formulario de contacto, escriba **Ann Díaz** como nombre de contacto y, a continuación, especifique las tres direcciones siguientes.

    |Tipo de dirección|Dirección|
    |------------------|-------------|
    |**Business**|**4567 Main St. Buffalo, NY**|
    |**Página principal**|**1234 North St. Buffalo, NY**|
    |**Otros**|**3456 Main St. Seattle, WA**|

4. Guarde y cierre el elemento de contacto.

5. Vuelva a abrir el elemento de contacto **Ana Díaz** .

    En Outlook, esto se puede hacer en el grupo **Buscar** abriendo la libreta de direcciones de contactos o escribiendo Ana Díaz en **buscar personas**.

6. En el grupo **Mostrar** de la cinta de opciones del elemento, haga clic en **asignar** para abrir el área de formulario Map it.

     Aparece el área de formulario Map It y muestra el sitio web de búsqueda local. Las direcciones **empresa**, **Inicio**y **otras** aparecen en el panel de borrador. En dicho bloc, seleccione la dirección que desea asignar.

## <a name="next-steps"></a>Pasos siguientes
 Puede obtener más información sobre cómo personalizar la interfaz de usuario de una aplicación de Outlook en estos temas:

- Para obtener información sobre cómo personalizar la cinta de opciones de un elemento de Outlook, consulte [personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

## <a name="see-also"></a>Consulte también
- [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)
- [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Instrucciones para crear áreas de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Tutorial: importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Cómo: agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Acciones personalizadas en áreas de formulario de Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Cómo: impedir que Outlook muestre un área de formulario](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
