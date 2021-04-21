---
title: 'Tutorial: Diseño de un área de formulario de Outlook'
description: Obtenga información sobre cómo puede diseñar un área de formulario personalizada de Microsoft Outlook que aparece como una nueva página en la ventana Inspector de un elemento de contacto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 80c574799029f3fe8c4769d852886a625ffd93aa
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824289"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Tutorial: Diseño de un área de formulario de Outlook
  Las áreas de formulario personalizadas extienden los formularios estándar o personalizados de Microsoft Office Outlook. En este tutorial diseñará un área de formulario personalizada que aparece como una nueva página en la ventana del inspector de un elemento de contacto. Esta área de formulario muestra una asignación de cada dirección incluida para el contacto, enviando la información de la dirección al sitio web de búsqueda local de Windows Live. Para obtener información sobre las regiones de formulario, vea [Crear regiones de formulario de Outlook.](../vsto/creating-outlook-form-regions.md)

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

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] o una versión más reciente.

  ![vínculo al vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") Para obtener una versión de vídeo de este tema, vea [Vídeo sobre cómo: Diseñar un área de formulario de Outlook.](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90))

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Creación de un nuevo proyecto de complemento vsto de Outlook
 En primer lugar, cree un proyecto básico de complemento de VSTO.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Para crear un proyecto de complemento de VSTO de Outlook

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , cree un proyecto de complemento de VSTO de Outlook con el nombre **MapItAddIn**.

2. En el cuadro de diálogo **Nuevo proyecto** , seleccione **Crear directorio para la solución**.

3. Guarde el proyecto en cualquier directorio.

     Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Agregar un área de formulario al proyecto de complemento de VSTO de Outlook
 Una solución de complemento de VSTO de Outlook puede contener uno o varios elementos de área de formulario de Outlook. Agregue un elemento de área de formulario al proyecto mediante el Asistente **para nueva región de formulario de Outlook.**

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Para agregar un área de formulario al proyecto de complemento de VSTO de Outlook

1. En **Explorador de soluciones**, seleccione el **proyecto MapItAddIn.**

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. En el **cuadro de diálogo Agregar nuevo** elemento, seleccione Área de formulario de **Outlook,** asigne el nombre **MapIt** al archivo y, a continuación, haga clic **en Agregar**.

     Se **inicia el Asistente para área de formulario NewOutlook.**

4. En la **página Seleccionar cómo desea crear el área** de formulario, haga clic en Diseñar un nuevo área de formulario y, **a** continuación, haga clic **en Siguiente.**

5. En la **página Seleccionar el tipo de área de formulario que desea crear,** haga **clic** en Independiente y, a continuación, en **Siguiente.**

     Un *área* de formulario independiente agrega una nueva página a un formulario de Outlook. Para obtener más información sobre los tipos de área de formulario, vea [Crear regiones de formulario de Outlook.](../vsto/creating-outlook-form-regions.md)

6. En la **página Proporcionar texto descriptivo y seleccionar las preferencias para** mostrar, escriba **Asignarlo** en el **cuadro** Nombre.

     Este nombre aparece en la cinta de opciones de la ventana del inspector cuando se abre el elemento de contacto.

7. Seleccione **Inspectores que están en modo de redacción** e **Inspectores** que están en modo de lectura y, a continuación, haga clic **en Siguiente.**

8. En la **página Identificar las clases de mensaje** que mostrarán este área de formulario, desactive Mensaje de correo, seleccione Contacto y, a continuación, haga clic en **Finalizar.**  

     Se *agrega un archivo MapIt.cs* o *MapIt.vb* al proyecto.

## <a name="design-the-layout-of-the-form-region"></a>Diseño del diseño del área de formulario
 Desarrolle visualmente regiones de formulario mediante el diseñador *de área de formulario*. Puede arrastrar controles administrados a la superficie del Diseñador de áreas de formulario. Use el diseñador y la ventana **Propiedades para** ajustar el diseño y la apariencia del control.

### <a name="to-design-the-layout-of-the-form-region"></a>Para definir el diseño del área de formulario

1. En **Explorador de soluciones**, expanda el **proyecto MapItAddIn** y, a continuación, haga doble clic en *MapIt.cs* o *MapIt.vb* para abrir el Diseñador de regiones de formulario.

2. Haga clic con el botón derecho en el diseñador y, a continuación, haga clic **en Propiedades.**

3. En la **ventana** Propiedades, establezca **Tamaño** en **664, 469**.

     De esta forma se garantiza que el área de formulario sea suficientemente grande para mostrar una asignación.

4. En el menú **Ver** , haga clic en **Cuadro de herramientas**.

5. En la **pestaña Controles comunes** del cuadro de **herramientas**, agregue **un webBrowser** al área de formulario.

     **WebBrowser** mostrará un mapa de cada dirección que aparece para el contacto.

## <a name="customize-the-behavior-of-the-form-region"></a>Personalización del comportamiento del área de formulario
 Agregue código a los controladores de eventos del área de formulario para personalizar el comportamiento de un área de formulario en tiempo de ejecución. Para esta área de formulario, el código examina las propiedades de un elemento de Outlook y determina si se va a mostrar el área de formulario Map It. Si muestra el área de formulario, el código se desplaza a la búsqueda local de Windows Live y carga una asignación de cada dirección incluida en el elemento de contacto de Outlook.

### <a name="to-customize-the-behavior-of-the-form-region"></a>Para personalizar el comportamiento del área de formulario

1. En **Explorador de soluciones**, haga clic con el botón derecho *en MapIt.cs* o *MapIt.vb* y, a continuación, haga clic **en Ver código.**

    *MapIt.cs* *o MapIt.vb* se abren en el Editor de código.

2. Expanda la región **de código Generador de regiones** de formulario.

    Se expone la clase de generador de áreas de formulario llamada `MapItFactory`.

3. Agregue el código siguiente al controlador de eventos `MapItFactory_FormRegionInitializing`. Se llama a este controlador de eventos cuando el usuario abre un elemento de contacto. El siguiente código determina si el elemento de contacto contiene una dirección. Si el elemento de contacto no contiene una dirección, este código establece la propiedad de la clase en true y no se muestra el área <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> de formulario.  De lo contrario, el complemento de VSTO provoca el evento <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> y muestra el área de formulario.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::

4. Agregue el código siguiente al controlador de eventos <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Este código realiza las tareas siguientes:

   - Concatena cada dirección del elemento de contacto y crea una cadena de dirección URL.

   - Llama al método <xref:System.Windows.Forms.WebBrowser.Navigate%2A> del objeto <xref:System.Windows.Forms.WebBrowser> y pasa la cadena de dirección URL como parámetro.

     El sitio web de búsqueda local aparece en el área de formulario Map It y presenta las direcciones en el bloc de notas.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet2":::

## <a name="test-the-outlook-form-region"></a>Prueba del área de formulario de Outlook
 Al ejecutar el proyecto, Visual Studio abrirá Outlook. Abra un elemento de contacto para ver el área de formulario Map It. El área de formulario Map It aparece como página en el formulario de cualquier elemento de contacto que contenga una dirección.

### <a name="to-test-the-map-it-form-region"></a>Para comprobar el área de formulario Map It

1. Presione **F5** para ejecutar el proyecto.

     Se abre Outlook.

2. En Outlook, en la pestaña **Inicio** , haga clic **en Nuevos elementos** y, a continuación, haga clic en **Contacto.**

3. En el formulario de contacto, escriba **Ann Beebe** como nombre del contacto y, a continuación, especifique las tres direcciones siguientes.

    |Tipo de dirección|Dirección|
    |------------------|-------------|
    |**Business**|**4567 Main St. Ny**|
    |**Página principal**|**1234 North St. York, NY**|
    |**Otros**|**3456 Main St. Seattle, WA**|

4. Guarde y cierre el elemento de contacto.

5. Vuelva a **abrir el elemento de contacto de Ann Beebe.**

    En Outlook, esto se  puede hacer en el grupo Buscar; para ello, abra la libreta de direcciones para contactos o escriba Ann Beebe en **Buscar personas.**

6. En el **grupo Mostrar** de la cinta de opciones del elemento, haga **clic** en Asignarlo para abrir el área de formulario Asignarlo.

     Aparece el área de formulario Map It y muestra el sitio web de búsqueda local. Las **direcciones Business**, **Home** y **Other** aparecen en el panel de scratch. En dicho bloc, seleccione la dirección que desea asignar.

## <a name="next-steps"></a>Pasos siguientes
 Puede obtener más información sobre cómo personalizar la interfaz de usuario de una aplicación de Outlook en estos temas:

- Para obtener información sobre cómo personalizar la cinta de opciones de un elemento de Outlook, vea [Personalizar una cinta de opciones para Outlook.](../vsto/customizing-a-ribbon-for-outlook.md)

## <a name="see-also"></a>Consulte también
- [Acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)
- [Creación de regiones de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Directrices para crear regiones de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Asociación de un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Acciones personalizadas en las regiones de formulario de Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Cómo: Impedir que Outlook muestre un área de formulario](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
