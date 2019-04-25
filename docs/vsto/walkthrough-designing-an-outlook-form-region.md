---
title: 'Tutorial: Diseñar un formulario de Outlook'
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
ms.openlocfilehash: e6ad8a11e736595912b1b6c8757bd75dca1e53e6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097432"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Tutorial: Diseñar un formulario de Outlook
  Las áreas de formulario personalizadas extienden los formularios estándar o personalizados de Microsoft Office Outlook. En este tutorial diseñará un área de formulario personalizada que aparece como una nueva página en la ventana del inspector de un elemento de contacto. Esta área de formulario muestra una asignación de cada dirección incluida para el contacto, enviando la información de la dirección al sitio web de búsqueda local de Windows Live. Para obtener información acerca de las áreas de formulario, consulte [crear áreas de formulario](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Crear un proyecto de complemento de VSTO de Outlook

- Agregar un área de formulario al proyecto de complemento de VSTO.

- Definir el diseño del área de formulario.

- Personalizar el comportamiento del área de formulario.

- Probar el área de formulario de Outlook.

> [!NOTE]
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesita los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] o versiones más recientes.

  ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo al vídeo") para una versión en vídeo de este tema, consulte [vídeo Cómo: Diseñar un formulario de Outlook](http://go.microsoft.com/fwlink/?LinkID=140824).

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Cree un nuevo proyecto de complemento VSTO de Outlook
 En primer lugar, cree un proyecto básico de complemento de VSTO.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Para crear un proyecto de complemento de VSTO de Outlook

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de complemento VSTO de Outlook con el nombre **MapItAddIn**.

2. En el cuadro de diálogo **Nuevo proyecto** , seleccione **Crear directorio para la solución**.

3. Guarde el proyecto en cualquier directorio.

     Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Agregar un área de formulario al proyecto de complemento VSTO de Outlook
 Una solución de complemento de VSTO de Outlook puede contener uno o varios elementos de área de formulario de Outlook. Agregar un elemento de área de formulario al proyecto mediante el **nueva área de formulario de Outlook** asistente.

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Para agregar un área de formulario al proyecto de complemento de VSTO de Outlook

1. En **el Explorador de soluciones**, seleccione el **MapItAddIn** proyecto.

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **formulario de Outlook**, asigne el nombre **MapIt**y, a continuación, haga clic en **agregar**.

     El **área de formulario NewOutlook** se inicia el asistente.

4. En el **Seleccione cómo desea crear el área de formulario** página, haga clic en **diseñar una nueva área de formulario**y, a continuación, haga clic en **siguiente**.

5. En el **seleccione el tipo de área de formulario que desea crear** página, haga clic en **independiente**y, a continuación, haga clic en **siguiente**.

     Un *independiente* área de formulario agrega una nueva página a un formulario de Outlook. Para obtener más información sobre los tipos de región de formulario, consulte [crear áreas de formulario](../vsto/creating-outlook-form-regions.md).

6. En el **proporcione texto descriptivo y seleccione sus preferencias de presentación** , escriba **Map It** en el **nombre** cuadro.

     Este nombre aparece en la cinta de opciones de la ventana del inspector cuando se abre el elemento de contacto.

7. Seleccione **inspectores que están en modo de redacción** y **inspectores que están en modo de lectura**y, a continuación, haga clic en **siguiente**.

8. En el **identifique las clases de mensaje que mostrarán esta área de formulario** página, desactive **mensaje de correo**, seleccione **póngase en contacto con**y, a continuación, haga clic en **finalizar**.

     Un *MapIt.cs* o *MapIt.vb* archivo se agrega al proyecto.

## <a name="design-the-layout-of-the-form-region"></a>Definir el diseño del área de formulario
 Desarrollar las áreas de formulario con el *Diseñador de áreas de formulario*. Puede arrastrar controles administrados a la superficie del Diseñador de áreas de formulario. Use el diseñador y el **propiedades** ventana para ajustar el diseño de controles y apariencia.

### <a name="to-design-the-layout-of-the-form-region"></a>Para definir el diseño del área de formulario

1. En **el Explorador de soluciones**, expanda el **MapItAddIn** del proyecto y, a continuación, haga doble clic en *MapIt.cs* o *MapIt.vb* para abrir el área de formulario Diseñador.

2. Haga clic en el diseñador y, a continuación, haga clic en **propiedades**.

3. En el **propiedades** ventana, establezca **tamaño** a **664, 469**.

     De esta forma se garantiza que el área de formulario sea suficientemente grande para mostrar una asignación.

4. En el menú **Ver** , haga clic en **Cuadro de herramientas**.

5. Desde el **controles comunes** pestaña de la **cuadro de herramientas**, agregue un **WebBrowser** al área de formulario.

     El **WebBrowser** mostrará un mapa de cada dirección enumerada para el contacto.

## <a name="customize-the-behavior-of-the-form-region"></a>Personalizar el comportamiento del área de formulario
 Agregue código a los controladores de eventos del área de formulario para personalizar el comportamiento de un área de formulario en tiempo de ejecución. Para esta área de formulario, el código examina las propiedades de un elemento de Outlook y determina si se va a mostrar el área de formulario Map It. Si muestra el área de formulario, el código se desplaza a la búsqueda local de Windows Live y carga una asignación de cada dirección incluida en el elemento de contacto de Outlook.

### <a name="to-customize-the-behavior-of-the-form-region"></a>Para personalizar el comportamiento del área de formulario

1. En **el Explorador de soluciones**, haga clic en *MapIt.cs* o *MapIt.vb*y, a continuación, haga clic en **ver código**.

    *MapIt.cs* o *MapIt.vb* se abre en el Editor de código.

2. Expanda el **generador de áreas de formulario** región de código.

    Se expone la clase de generador de áreas de formulario llamada `MapItFactory`.

3. Agregue el código siguiente al controlador de eventos `MapItFactory_FormRegionInitializing`. Se llama a este controlador de eventos cuando el usuario abre un elemento de contacto. El siguiente código determina si el elemento de contacto contiene una dirección. Si el elemento de contacto no contiene una dirección, este código establece la <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propiedad de la <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> clase **true** y no se muestra el área de formulario. De lo contrario, el complemento de VSTO provoca el evento <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> y muestra el área de formulario.

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

2. En Outlook, en el **inicio** , haga clic **nuevos elementos**y, a continuación, haga clic en **póngase en contacto con**.

3. En el formulario de contacto, escriba **Ann Beebe** como el póngase en contacto con el nombre y, a continuación, especifique las tres direcciones siguientes.

    |Tipo de dirección|Dirección|
    |------------------|-------------|
    |**Business**|**4567 Main St. Buffalo, NY**|
    |**Página principal**|**1234 North St. Buffalo, NY**|
    |**Otros problemas**|**3456 Main St. Seattle, WA**|

4. Guarde y cierre el elemento de contacto.

5. Vuelva a abrir el **Ann Beebe** elemento de contacto.

    En Outlook, esto puede hacerse el **buscar** agrupe por abrir la libreta de direcciones para los contactos o escribiendo Ann Beebe en **buscar personas**.

6. En el **mostrar** grupo de cinta de opciones del elemento, haga clic en **Map It** para abrir el área de formulario Map It.

     Aparece el área de formulario Map It y muestra el sitio web de búsqueda local. El **Business**, **inicio**, y **otros** direcciones aparecen en el Bloc de notas. En dicho bloc, seleccione la dirección que desea asignar.

## <a name="next-steps"></a>Pasos siguientes
 Puede obtener más información sobre cómo personalizar la interfaz de usuario de una aplicación de Outlook en estos temas:

- Para obtener información sobre cómo personalizar la cinta de opciones de un elemento de Outlook, consulte [personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

## <a name="see-also"></a>Vea también
- [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)
- [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Directrices para crear áreas de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Acciones personalizadas en áreas de formulario de Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Cómo: Impedir que Outlook muestre un área de formulario](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
