---
title: Crear elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2
titleSuffix: ''
description: Agregue un asistente a una plantilla de proyecto de columna de sitio para recopilar datos de los usuarios cuando usen la plantilla para crear un proyecto de SharePoint que contenga el elemento de proyecto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bc664a50fc307c59d5c168b26c8af1bc6181ebad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918715"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2
  Después de definir un tipo personalizado de elemento de proyecto de SharePoint y asociarlo a una plantilla de proyecto en Visual Studio, es posible que desee proporcionar también un asistente para la plantilla. Puede usar el asistente con el fin de recopilar información de los usuarios cuando usan la plantilla para crear un nuevo proyecto que contiene el elemento de proyecto. La información que recopile puede usarse para inicializar el elemento de proyecto.

 En este tutorial, agregará un asistente a la plantilla de proyecto de columna de sitio que se muestra en [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Cuando un usuario crea un proyecto de columna de sitio, el asistente recopila información sobre la columna de sitio (como el tipo base y el grupo) y agrega esta información al archivo *Elements.xml* del nuevo proyecto.

 En este tutorial se muestran las siguientes tareas:

- Crear un asistente para un tipo de elemento de proyecto de SharePoint personalizado asociado a una plantilla de proyecto.

- Definir una interfaz de usuario de asistente personalizada similar a la de los asistentes integrados para los proyectos de SharePoint en Visual Studio.

- Crear dos *comandos de SharePoint* que se usan para llamar al sitio de SharePoint local mientras el asistente se está ejecutando. Los comandos de SharePoint son métodos que las extensiones de Visual Studio pueden usar para llamar a las API del modelo de objetos de servidor de SharePoint. Para obtener más información, vea [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Usar parámetros reemplazables para inicializar los archivos de proyecto de SharePoint con los datos recopilados en el asistente.

- Crear un nuevo archivo .snk en cada nueva instancia de proyecto de columnas de sitio. Este archivo se usa para firmar el resultado del proyecto a fin de que el ensamblado de la solución de SharePoint se pueda implementar en la memoria caché global de ensamblados.

- Depurar y probar el asistente.

> [!NOTE]
> Para obtener una serie de flujos de trabajo de ejemplo, vea [ejemplos de flujo de trabajo de SharePoint](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Requisitos previos
 Para realizar este tutorial, primero debe crear la solución SiteColumnProjectItem completando el [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 También necesitará los siguientes componentes en el equipo de desarrollo para completar este tutorial:

- Ediciones compatibles de Windows, SharePoint y Visual Studio.

- Visual Studio SDK. En este tutorial se usa la plantilla de **Proyecto VSIX** en el SDK para crear un paquete VSIX para implementar el elemento de proyecto. Para obtener más información, vea [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.

- Asistentes para plantillas de elementos y proyectos de Visual Studio. Para obtener más información, vea [Cómo: usar asistentes con plantillas de proyecto](../extensibility/how-to-use-wizards-with-project-templates.md) y la <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaz.

- Columnas de sitio de SharePoint. Para obtener más información, vea [columnas](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

## <a name="understand-the-wizard-components"></a>Comprender los componentes del asistente
 El asistente que se muestra en este tutorial contiene varios componentes. En la tabla siguiente se describen estos componentes.

|Componente|Descripción|
|---------------|-----------------|
|Implementación del asistente|Esta es una clase denominada `SiteColumnProjectWizard`, que implementa la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. Esta interfaz define los métodos que Visual Studio llama cuando el asistente se inicia y finaliza y, a veces, mientras se ejecuta.|
|Interfaz de usuario del asistente|Se trata de una ventana basada en WPF, denominada `WizardWindow`. Esta ventana incluye dos controles de usuario, denominados `Page1` y `Page2`. Estos controles de usuario representan las dos páginas del asistente.<br /><br /> En este tutorial, el método <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> de la implementación del asistente muestra la interfaz de usuario del asistente.|
|Modelo de datos del asistente|Esta es una clase intermediaria denominada `SiteColumnWizardModel`, que proporciona una capa entre la interfaz de usuario del asistente y la implementación del asistente. En este ejemplo se usa esta clase para ayudar a abstraer la implementación del asistente y la interfaz de usuario del asistente entre sí; esta clase no es un componente necesario de todos los asistentes.<br /><br /> En este tutorial, la implementación del asistente pasa un objeto `SiteColumnWizardModel` a la ventana del asistente cuando muestra la interfaz de usuario del asistente. La interfaz de usuario del asistente usa los métodos de este objeto para guardar los valores de los controles de la interfaz de usuario y para realizar tareas como comprobar que la dirección URL del sitio de entrada es válido. Una vez que el usuario finaliza el asistente, la implementación del asistente usa el objeto `SiteColumnWizardModel` para determinar el estado final de la interfaz de usuario.|
|Administrador de firma de proyectos|Esta es una clase auxiliar denominada `ProjectSigningManager`, que se usa en la implementación del asistente para crear un nuevo archivo key.snk en cada nueva instancia de proyecto.|
|Comandos de SharePoint|Estos son los métodos usados por el modelo de datos del asistente para llamar al sitio de SharePoint local mientras el asistente se está ejecutando. Dado que los comandos de SharePoint deben tener .NET Framework 3.5 como destino, se implementan en un ensamblado diferente al del resto del código del asistente.|

## <a name="create-the-projects"></a>Crear los proyectos
 Para completar este tutorial, debe agregar varios proyectos a la solución SiteColumnProjectItem que creó en [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):

- Un proyecto WPF. Implementará la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> y definirá la interfaz de usuario del asistente de este proyecto.

- Un proyecto de biblioteca de clases que define los comandos de SharePoint. Este proyecto debe tener como destino .NET Framework 3.5.

  Comience el tutorial creando ambos proyectos.

#### <a name="to-create-the-wpf-project"></a>Para crear el proyecto de WPF

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra la solución SiteColumnProjectItem.

2. En **Explorador de soluciones**, abra el menú contextual del nodo de la solución **SiteColumnProjectItem** , elija **Agregar** y, a continuación, elija **nuevo proyecto**.

3. En la parte superior del cuadro de diálogo **Agregar nuevo proyecto** , asegúrese de que se elige **.NET Framework 4,5** en la lista de versiones de la .NET Framework.

4. Expanda el nodo **Visual C#** o el nodo **Visual Basic** y elija el nodo **Windows** .

5. En la lista de plantillas de proyecto, elija **biblioteca de controles de usuario de WPF**, asigne al proyecto el nombre **ProjectTemplateWizard** y, a continuación, elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **ProjectTemplateWizard** a la solución y abre el archivo predeterminado UserControl1. Xaml.

6. Elimine el archivo UserControl1.xaml del proyecto.

#### <a name="to-create-the-sharepoint-commands-project"></a>Para crear el proyecto Comandos de SharePoint

1. En **Explorador de soluciones**, abra el menú contextual del nodo de la solución SiteColumnProjectItem, elija **Agregar** y, a continuación, elija **nuevo proyecto**.

2. En la parte superior del cuadro de diálogo **Agregar nuevo proyecto** , elija **.NET Framework 3,5** en la lista de versiones de la .NET Framework.

3. Expanda el nodo **Visual C#** o el nodo  **Visual Basic** y, a continuación, elija el nodo **Windows** .

4. Elija la plantilla de proyecto **biblioteca de clases** , asigne al proyecto el nombre **SharePointCommands** y, a continuación, elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **SharePointCommands** a la solución y abre el archivo de código predeterminado Class1.

5. Elimine el archivo de código Class1 del proyecto.

## <a name="configure-the-projects"></a>Configurar los proyectos
 Antes de crear el asistente, debe agregar algunos archivos de código y referencias de ensamblado a los proyectos.

#### <a name="to-configure-the-wizard-project"></a>Para configurar el proyecto de asistente

1. En **Explorador de soluciones**, abra el menú contextual del nodo de proyecto **ProjectTemplateWizard** y, a continuación, elija **propiedades**.

2. En el **Diseñador de proyectos**, elija la pestaña **aplicación** para un proyecto de Visual C# o la pestaña **compilar** para un proyecto Visual Basic.

3. Asegúrese de que la plataforma de destino se establezca en .NET Framework 4.5, no en .NET Framework 4.5 Client Profile.

     Para obtener más información, consulte [Cómo: usar como destino una versión de la .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

4. Abra el menú contextual del proyecto **ProjectTemplateWizard** , elija **Agregar** y, a continuación, elija **nuevo elemento**.

5. Elija el elemento **Window (WPF)** , asigne al elemento el nombre **WizardWindow** y, a continuación, elija el botón **Agregar** .

6. Agregue dos elementos de **control de usuario (WPF)** al proyecto y asígneles los nombres **Page1** y **página2**.

7. Agregue cuatro archivos de código al proyecto y asígneles los nombres siguientes:

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - CommandIds

8. Abra el menú contextual del nodo de proyecto **ProjectTemplateWizard** y, a continuación, elija **Agregar referencia**.

9. Expanda el nodo **ensamblados** , elija el nodo **extensiones** y, a continuación, active las casillas situadas junto a los siguientes ensamblados:

    - EnvDTE

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.SharePoint

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.Shell.Interop.10.0

    - Microsoft.VisualStudio.Shell.Interop.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

10. Elija el botón **Aceptar** para agregar los ensamblados al proyecto.

11. En **Explorador de soluciones**, en la carpeta **referencias** del proyecto **ProjectTemplateWizard** , elija **EnvDTE**.

12. En la ventana **propiedades** , cambie el valor de la propiedad **incrustar tipos de interoperabilidad** a **false**.

13. Si va a desarrollar un proyecto de Visual Basic, importe el espacio de nombres ProjectTemplateWizard en el proyecto mediante el **Diseñador de proyectos**.

     Para obtener más información, consulte [Cómo: agregar o quitar espacios de nombres importados &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).

#### <a name="to-configure-the-sharepointcommands-project"></a>Para configurar el proyecto SharePointcommands

1. En **Explorador de soluciones**, elija el nodo del proyecto **SharePointCommands** .

2. En la barra de menús, elija **proyecto**,  **Agregar elemento existente**.

3. En el cuadro de diálogo **Agregar elemento existente** , vaya a la carpeta que contiene los archivos de código para el proyecto ProjectTemplateWizard y, a continuación, elija el archivo de código **commandids** .

4. Elija la flecha situada junto al botón **Agregar** y, a continuación, elija la opción **Agregar como vínculo** en el menú que aparece.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el archivo de código al proyecto **SharePointCommands** como un vínculo. El archivo de código se encuentra en el proyecto **ProjectTemplateWizard** , pero el código del archivo también se compila en el proyecto **SharePointCommands** .

5. En el proyecto **SharePointCommands** , agregue otro archivo de código denominado Commands.

6. Elija el proyecto SharePointCommands y, a continuación, en la barra de menús, elija **proyecto**  >  **Agregar referencia**.

7. Expanda el nodo **ensamblados** , elija el nodo **extensiones** y, a continuación, active las casillas situadas junto a los siguientes ensamblados:

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

8. Elija el botón **Aceptar** para agregar los ensamblados al proyecto.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Crear el modelo de asistente, el administrador de firmas y los identificadores de comando de SharePoint
 Agregue el código al proyecto de ProjectTemplateWizard para implementar los componentes siguientes en el ejemplo:

- Los identificadores de comando de SharePoint. Estas cadenas identifican los comandos de SharePoint usados por el asistente. Más adelante en este tutorial, agregará código al proyecto SharePointCommands para implementar los comandos.

- El modelo de datos del asistente.

- El administrador de firma del proyecto.

  Para obtener más información acerca de estos componentes, vea [comprender los componentes del asistente](#understand-the-wizard-components).

#### <a name="to-define-the-sharepoint-command-ids"></a>Para definir los identificadores de comando de SharePoint

1. En el proyecto ProjectTemplateWizard, abra el archivo de código CommandIds y, a continuación, reemplace todo el contenido de este archivo por el código siguiente.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]

#### <a name="to-create-the-wizard-model"></a>Para crear el modelo de asistente

1. Abra el archivo de código SiteColumnWizardModel y reemplace todo el contenido de este archivo por el código siguiente.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]

#### <a name="to-create-the-project-signing-manager"></a>Para crear el administrador de firma de proyecto

1. Abra el archivo de código ProjectSigningManager y reemplace todo el contenido de este archivo por el código siguiente.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]

## <a name="create-the-wizard-ui"></a>Crear la interfaz de usuario del asistente
 Agregue XAML para definir la interfaz de usuario de la ventana del asistente y los dos controles de usuario que proporcionan la interfaz de usuario para las páginas del asistente, y agregue el código para definir el comportamiento de la ventana y los controles de usuario. El asistente que se crea es similar al asistente integrado para los proyectos de SharePoint en Visual Studio.

> [!NOTE]
> En los siguientes pasos, el proyecto tendrá algunos errores de compilación después de agregar XAML o el código al proyecto. Estos errores desaparecerán al agregar código en pasos posteriores.

#### <a name="to-create-the-wizard-window-ui"></a>Para crear la interfaz de usuario de la ventana del asistente

1. En el proyecto ProjectTemplateWizard, abra el menú contextual del archivo WizardWindow. XAML y, a continuación, elija **abrir** para abrir la ventana en el diseñador.

2. En la vista XAML del diseñador, reemplace el código XAML actual por el siguiente. El XAML define una interfaz de usuario que incluye un título, un control <xref:System.Windows.Controls.Grid> que contiene las páginas del asistente y los botones de navegación en la parte inferior de la ventana.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]

    > [!NOTE]
    > La ventana que se crea en este código XAML se deriva de la <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> clase base. Cuando se agrega un cuadro de diálogo de WPF personalizado en Visual Studio, se recomienda derivar el cuadro de diálogo de esta clase para que tenga un estilo coherente con otros cuadros de diálogo de Visual Studio y para evitar los problemas de cuadro de diálogo modal que pueden producirse en caso contrario. Para obtener más información, vea [crear y administrar cuadros de diálogo modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Si va a desarrollar un proyecto de Visual Basic, quite el `ProjectTemplateWizard` espacio de nombres del `WizardWindow` nombre de clase en el `x:Class` atributo del `Window` elemento. Este elemento aparece en la primera línea del código XAML. Cuando haya terminado, la primera línea debe ser similar a la del ejemplo siguiente.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Abra el archivo de código subyacente del archivo WizardWindow.xaml.

5. Reemplace el contenido de este archivo, excepto las declaraciones de `using` en la parte superior del mismo, por el código siguiente.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]

#### <a name="to-create-the-first-wizard-page-ui"></a>Para crear la interfaz de usuario de la primera página del asistente

1. En el proyecto ProjectTemplateWizard, abra el menú contextual del archivo Page1. XAML y, a continuación, elija **abrir** para abrir el control de usuario en el diseñador.

2. En la vista XAML del diseñador, reemplace el código XAML actual por el siguiente. El código XAML define una interfaz de usuario que incluye un cuadro de texto donde los usuarios pueden escribir la dirección URL de los sitios locales que desean usar para depurar. La interfaz de usuario también incluye botones de opción con los que los usuarios pueden especificar si el proyecto está en un espacio aislado.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]

3. Si está desarrollando un proyecto de Visual Basic, quite el espacio de nombres `ProjectTemplateWizard` del nombre de clase `Page1` del atributo `x:Class` del elemento `UserControl`. Esta es la primera línea del código XAML. Cuando termine, la primera línea tendrá el aspecto siguiente:

    ```xml
    <UserControl x:Class="Page1"
    ```

4. Reemplace el contenido del archivo Page1.xaml, excepto las declaraciones `using` en la parte superior del archivo, por el código siguiente.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]

#### <a name="to-create-the-second-wizard-page-ui"></a>Para crear la interfaz de usuario de la segunda página del asistente

1. En el proyecto ProjectTemplateWizard, abra el menú contextual del archivo Page2. XAML y, a continuación, elija **abrir**.

     Se abre el control de usuario en el diseñador.

2. En la vista XAML, reemplace el código XAML actual por el siguiente. El XAML define una interfaz de usuario que incluye una lista desplegable para elegir el tipo base de la columna de sitio, un cuadro combinado para especificar un grupo integrado o personalizado en los que se muestra la columna de sitio en la galería y un cuadro de texto para especificar el nombre de la columna de sitio.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]

3. Si está desarrollando un proyecto de Visual Basic, quite el espacio de nombres `ProjectTemplateWizard` del nombre de clase `Page2` del atributo `x:Class` del elemento `UserControl`. Esta es la primera línea del código XAML. Cuando termine, la primera línea tendrá el aspecto siguiente:

    ```xml
    <UserControl x:Class="Page2"
    ```

4. Reemplace el contenido del archivo de código subyacente para el archivo Page2.xaml, excepto para las declaraciones `using` de la parte superior del archivo, por el código siguiente.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]

## <a name="implement-the-wizard"></a>Implementar el asistente
 Para definir la funcionalidad principal del asistente, implemente la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. Esta interfaz define los métodos que Visual Studio llama cuando el asistente se inicia y finaliza y, a veces, mientras se ejecuta.

#### <a name="to-implement-the-wizard"></a>Para implementar el asistente

1. En el proyecto ProjectTemplateWizard, abra el archivo de código SiteColumnProjectWizard.

2. Reemplace todo el contenido de este archivo por el código siguiente:

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]

## <a name="create-the-sharepoint-commands"></a>Crear los comandos de SharePoint
 Cree dos comandos personalizados que llamen al modelo de objetos de servidor de SharePoint. Un comando determina si la dirección URL del sitio que el usuario escribe en el asistente es válida. El otro comando obtiene todos los tipos de campo del sitio de SharePoint especificado para que los usuarios puedan seleccionar el que desean usar como base para la nueva columna de sitio.

#### <a name="to-define-the-sharepoint-commands"></a>Para definir los comandos de SharePoint

1. En el proyecto **SharePointCommands** , abra el archivo de código Commands.

2. Reemplace todo el contenido de este archivo por el código siguiente:

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]

## <a name="checkpoint"></a>Punto de control
 En este punto del tutorial, todo el código del asistente está en el proyecto. Compile el proyecto para asegurarse de que se compila sin errores.

#### <a name="to-build-your-project"></a>Para compilar el proyecto

1. En la barra de menús, elija **Compilar** > **Compilar solución**.

## <a name="removing-the-keysnk-file-from-the-project-template"></a>Quitar el archivo Key. snk de la plantilla de proyecto
 En el [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), la plantilla de proyecto que ha creado contiene un archivo Key. snk que se usa para firmar cada instancia de proyecto de columna de sitio. Este archivo key.snk ya no es necesario porque el asistente genera ahora un nuevo archivo key.snk para cada proyecto. Quite el archivo key.snk de la plantilla de proyecto y quite las referencias a este archivo.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Para quitar el archivo key.snk de la plantilla de proyecto

1. En **Explorador de soluciones**, en el nodo **SiteColumnProjectTemplate** , abra el menú contextual del archivo **key. snk** y, a continuación, elija **eliminar**.

2. En el cuadro de diálogo de confirmación que aparece, elija el botón **Aceptar**.

3. En el nodo **SiteColumnProjectTemplate** , abra el archivo SiteColumnProjectTemplate. vstemplate y, a continuación, quite el siguiente elemento de él.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. Guarde y cierre el archivo.

5. En el nodo **SiteColumnProjectTemplate** , abra el archivo ProjectTemplate. csproj o ProjectTemplate. vbproj y, a continuación, quite el siguiente `PropertyGroup` elemento de él.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6. Quite el siguiente elemento `None`.

    ```xml
    <None Include="key.snk" />
    ```

7. Guarde y cierre el archivo.

## <a name="associating-the-wizard-with-the-project-template"></a>Asociar el asistente a la plantilla de proyecto
 Ahora que ha implementado el asistente, debe asociar el asistente con la plantilla de proyecto de **columna de sitio** . Hay tres procedimientos principales que debe completar para ello:

1. Firmar el ensamblado del asistente con un nombre seguro.

2. Obtener el token de clave pública del ensamblado del asistente.

3. Agregue una referencia al ensamblado del asistente en el archivo. vstemplate para la plantilla de proyecto de **columna de sitio** .

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Para firmar el ensamblado del asistente con un nombre seguro

1. En **Explorador de soluciones**, abra el menú contextual del proyecto **ProjectTemplateWizard** y, a continuación, elija **propiedades**.

2. En la pestaña **Firma**, active la casilla **Firmar el ensamblado**.

3. En la lista **Elija un archivo de clave de nombre seguro** , elija **\<New...>** .

4. En el cuadro de diálogo **crear clave de nombre seguro** , escriba un nombre para el nuevo archivo de clave, desactive la casilla **proteger mi archivo de clave con una contraseña** y, a continuación, elija el botón **Aceptar** .

5. Abra el menú contextual del proyecto **ProjectTemplateWizard** y, a continuación, elija **compilar** para crear el archivo de ProjectTemplateWizard.dll.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Para obtener el token de clave pública del ensamblado del asistente

1. En el **menú Inicio**, elija **todos los programas**, elija **Microsoft Visual Studio**, elija **Visual Studio Tools** y, a continuación, elija **símbolo del sistema para desarrolladores**.

     Se abre una ventana Símbolo del sistema de Visual Studio.

2. Ejecute el comando siguiente, reemplazando *PathToWizardAssembly* por la ruta de acceso completa al ensamblado ProjectTemplateWizard.dll del proyecto ProjectTemplateWizard en el equipo de desarrollo:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     El token de clave pública del ensamblado ProjectTemplateWizard.dll se escribe en la ventana del símbolo del sistema de Visual Studio.

3. Mantenga abierta la ventana del símbolo del sistema de Visual Studio. Necesitará el token de clave pública durante el procedimiento siguiente.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Para agregar una referencia al ensamblado del asistente del archivo .vstemplate

1. En **Explorador de soluciones**, expanda el nodo del proyecto **SiteColumnProjectTemplate** y abra el archivo SiteColumnProjectTemplate. vstemplate.

2. Cuando se acerque el final del archivo, agregue el siguiente elemento `WizardExtension` entre las etiquetas `</TemplateContent>` y `</VSTemplate>`. Reemplace el valor del *token* del `PublicKeyToken` atributo por el token de clave pública que obtuvo en el procedimiento anterior.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     Para obtener más información sobre el `WizardExtension` elemento, vea [elemento WizardExtension &#40;plantillas de Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Guarde y cierre el archivo.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Agregar parámetros reemplazables al archivo de Elements.xml en la plantilla de proyecto
 Agregue varios parámetros reemplazables al archivo *Elements.xml* en el proyecto SiteColumnProjectTemplate. Estos parámetros se inicializan en el método `RunStarted` de la clase `SiteColumnProjectWizard` que definió anteriormente. Cuando un usuario crea un proyecto de columna de sitio, Visual Studio reemplaza automáticamente estos parámetros en el archivo *Elements.xml* del nuevo proyecto con los valores especificados en el asistente.

 Un parámetro reemplazable es un token que empieza y termina por el carácter del signo de dólar ($). Además de definir sus propios parámetros reemplazables, puede usar los parámetros integrados que se definen y se inicializan en el sistema de proyectos de SharePoint. Para obtener más información, vea [Parámetros reemplazables](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Para agregar parámetros reemplazables al archivo Elements.xml

1. En el proyecto SiteColumnProjectTemplate, reemplace el contenido del archivo *Elements.xml* por el siguiente código XML.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
             Name="$fieldname$"
             DisplayName="$fieldname$"
             Type="$selectedfieldtype$"
             Group="$selectedgrouptype$">
      </Field>
    </Elements>
    ```

     El nuevo XML cambia los valores de los atributos `Name`, `DisplayName`, `Type` y `Group` por parámetros reemplazables personalizados.

2. Guarde y cierre el archivo.

## <a name="add-the-wizard-to-the-vsix-package"></a>Agregar el Asistente al paquete VSIX
 Para implementar el asistente con el paquete VSIX que contiene la plantilla de proyecto de columna de sitio, agregue las referencias del proyecto de asistente y del proyecto de comandos de SharePoint al archivo source.extension.vsixmanifest del proyecto VSIX.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Para agregar el asistente al paquete VSIX

1. En **Explorador de soluciones**, en el proyecto **SiteColumnProjectItem** , abra el menú contextual del archivo **source. Extension. vsixmanifest** y, a continuación, elija **abrir**.

     Visual Studio abre el archivo en el editor de manifiestos.

2. En la pestaña **activos** del editor, elija el botón **nuevo** .

     Se abre el cuadro de diálogo **Agregar nuevo activo** .

3. En la lista **tipo** , elija **Microsoft. VisualStudio. Assembly**.

4. En la lista **origen** , elija **un proyecto en la solución actual**.

5. En la lista **proyecto** , elija **ProjectTemplateWizard** y, a continuación, elija el botón **Aceptar** .

6. En la pestaña **activos** del editor, vuelva a elegir el botón **nuevo** .

     Se abre el cuadro de diálogo **Agregar nuevo activo** .

7. En la lista **tipo** , escriba **SharePoint. Commands. V4**.

8. En la lista **origen** , elija **un proyecto en la solución actual**.

9. En la lista **proyecto** , elija el proyecto **SharePointCommands** y, a continuación, elija el botón **Aceptar** .

10. En la barra de menús, **Elija compilar compilar**  >  **solución** y, a continuación, asegúrese de que la solución se compila sin errores.

## <a name="test-the-wizard"></a>Probar el asistente
 Ahora está preparado para probar el asistente. Primero, empiece a depurar la solución SiteColumnProjectItem en la instancia experimental de Visual Studio. A continuación, pruebe el asistente para el proyecto de columna de sitio en la instancia experimental de Visual Studio. Por último, compile y ejecute el proyecto para comprobar que la columna de sitio funciona del modo esperado.

#### <a name="to-start-debugging-the-solution"></a>Para empezar a depurar la solución

1. Reinicie Visual Studio con credenciales administrativas y abra la solución SiteColumnProjectItem.

2. En el proyecto ProjectTemplateWizard, abra el archivo de código SiteColumnProjectWizard y, a continuación, agregue un punto de interrupción a la primera línea de código en el método `RunStarted`.

3. En la barra de menús, elija **depurar**  >  **excepciones**.

4. En el cuadro de diálogo **excepciones** , asegúrese de que las casillas **iniciadas** y **no controladas** por el usuario para las **excepciones de Common Language Runtime** estén desactivadas y, a continuación, elija el botón **Aceptar** .

5. Para iniciar la depuración, elija la tecla **F5** o, en la barra de menús, elija **depurar**  >  **iniciar depuración**.

     Visual Studio instala la extensión en %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Columna de sitio\1 .0 e inicia una instancia experimental de Visual Studio. Probará el elemento de proyecto en esta instancia de Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Para probar el asistente en Visual Studio

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **archivo**  >  **nuevo**  >  **proyecto**.

2. Expanda los nodos **Visual C#** o **Visual Basic** (en función del lenguaje que admita la plantilla de proyecto), expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

3. En la lista de plantillas de proyecto, elija **columna de sitio**, asigne al proyecto el nombre **SiteColumnWizardTest** y, a continuación, elija el botón **Aceptar** .

4. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `RunStarted`.

5. Continúe con la depuración del proyecto; para ello, elija la tecla **F5** o, en la barra de menús, elija **depurar**  >  **continuar**.

6. En el **Asistente para la personalización de SharePoint**, escriba la dirección URL del sitio que desea usar para la depuración y, a continuación, elija el botón **siguiente** .

7. En la segunda página del **Asistente para la personalización de SharePoint**, realice las selecciones siguientes:

   - En la lista **tipo** , elija **booleano**.

   - En la lista **Grupo** , elija **columnas sí/no personalizadas**.

   - En el cuadro **nombre** , escriba **mi columna sí/no** y, a continuación, elija el botón **Finalizar** .

     En **Explorador de soluciones**, aparece un nuevo proyecto que contiene un elemento de proyecto denominado **Campo1** y Visual Studio abre el archivo de *Elements.xml* del proyecto en el editor.

8. Compruebe que *Elements.xml* contiene los valores que especificó en el asistente.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Para probar la columna de sitio de SharePoint

1. En la instancia experimental de Visual Studio, elija la tecla **F5** .

     La columna de sitio se empaqueta e implementa en el sitio de SharePoint que especifica la propiedad **dirección URL del sitio** del proyecto. El explorador web se abre en la página predeterminada de este sitio.

    > [!NOTE]
    > Si aparece el cuadro de diálogo **depuración de scripts deshabilitado** , elija el botón **sí** para continuar con la depuración del proyecto.

2. En el menú **acciones del sitio** , elija Configuración del **sitio**.

3. En la página Configuración del sitio, en **galerías**, elija el vínculo **columnas de sitio** .

4. En la lista de columnas de sitio, compruebe que un grupo **personalizado sí/no** contiene una columna denominada **mi columna sí/no** y, a continuación, cierre el explorador Web.

## <a name="clean-up-the-development-computer"></a>Limpiar el equipo de desarrollo
 Después de probar el elemento de proyecto, quite la plantilla de proyecto de la instancia experimental de Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Para limpiar el equipo de desarrollo

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **herramientas**  >  **extensiones y actualizaciones**.

     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

2. En la lista de extensiones, elija **columna de sitio** y, a continuación, elija el botón **desinstalar** .

3. En el cuadro de diálogo que aparece, elija el botón **sí** para confirmar que desea desinstalar la extensión y, a continuación, elija el botón **reiniciar ahora** para completar la desinstalación.

4. Cierre tanto la instancia experimental de Visual Studio como la instancia en la que se abre la solución CustomActionProjectItem.

     Para obtener información sobre cómo implementar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extensiones, vea [envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

## <a name="see-also"></a>Vea también
- [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Definir tipos de elementos de proyecto personalizados de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Cómo: Utilizar los asistentes con las plantillas de proyectos](../extensibility/how-to-use-wizards-with-project-templates.md)
