---
title: "Tutorial: Crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 2 | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: 2d8165d3-4af9-4a5e-bdba-8b2a06b1dc8d
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 96f6e6f27938635628db66f2a6eb58a56cee0d18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2"></a>Tutorial: Crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 2
  Después de definir un tipo personalizado de elemento de proyecto de SharePoint y asociarlo a una plantilla de elementos en Visual Studio, también puede proporcionar un Asistente para la plantilla. Puede usar al Asistente para recopilar información de los usuarios cuando utilicen la plantilla para agregar una nueva instancia del elemento de proyecto a un proyecto. La información que recopile puede usarse para inicializar el elemento de proyecto.  
  
 En este tutorial, agregará un Asistente para el elemento de proyecto acción personalizada que se muestra en [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Cuando un usuario agrega un elemento de proyecto acción personalizada a un proyecto de SharePoint, el asistente recopila información sobre la acción personalizada (por ejemplo, su ubicación y la dirección URL al que navegar cuando un usuario final lo elija) y agrega esta información al archivo Elements.xml en el nuevo elemento de proyecto.  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear a un Asistente para un tipo de elemento de proyecto de SharePoint personalizado que está asociado a una plantilla de elementos.  
  
-   Definición de un asistente personalizado de interfaz de usuario que es similar a los asistentes integrados para elementos de proyecto de SharePoint en Visual Studio.  
  
-   Usar parámetros reemplazables para inicializar los archivos de proyecto de SharePoint con los datos recopilados en el asistente.  
  
-   Depurar y probar el asistente.  
  
> [!NOTE]  
>  Puede descargar un ejemplo que contiene los proyectos completos, código y otros archivos para este tutorial en la siguiente ubicación: [archivos de proyecto para ver tutoriales de extensibilidad de herramientas de SharePoint](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para llevar a cabo este tutorial, primero debe crear la solución CustomActionProjectItem siguiendo [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 También necesitará los siguientes componentes en el equipo de desarrollo para completar este tutorial:  
  
-   Ediciones compatibles de Windows, SharePoint y Visual Studio. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK. Este tutorial se utiliza la **proyecto VSIX** plantilla en el SDK para crear un paquete VSIX para implementar el elemento de proyecto. Para obtener más información, consulte [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.  
  
-   Asistentes para plantillas de elementos y proyectos de Visual Studio. Para obtener más información, consulte [Cómo: utilizar asistentes para plantillas de proyecto](../extensibility/how-to-use-wizards-with-project-templates.md) y <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaz.  
  
-   Acciones personalizadas en SharePoint. Para obtener más información, consulte [la acción personalizada](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
## <a name="creating-the-wizard-project"></a>Crear el proyecto de Asistente  
 Para completar este tutorial, debe agregar un proyecto a la solución CustomActionProjectItem que creó en [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Implementará la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> y definirá la interfaz de usuario del asistente de este proyecto.  
  
#### <a name="to-create-the-wizard-project"></a>Para crear el proyecto de Asistente  
  
1.  En Visual Studio, abra la solución CustomActionProjectItem  
  
2.  En **el Explorador de soluciones**, abra el menú contextual del nodo de solución, elija **agregar**y, a continuación, elija **nuevo proyecto**.  
  
3.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos y, a continuación, elija la **Windows** nodo.  
  
4.  En la parte superior de la **nuevo proyecto** diálogo cuadro, asegúrese de que **.NET Framework 4.5** se haya elegido en la lista de versiones de .NET Framework.  
  
5.  Elija la **biblioteca de controles de usuario de WPF** plantilla de proyecto, asigne al proyecto **ItemTemplateWizard**y, a continuación, elija la **Aceptar** botón.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Agrega el **ItemTemplateWizard** proyecto a la solución.  
  
6.  Elimine el elemento UserControl1 del proyecto.  
  
## <a name="configuring-the-wizard-project"></a>Configurar el proyecto de Asistente  
 Antes de crear al asistente, debe agregar una ventana de Windows Presentation Foundation (WPF), un archivo de código y referencias de ensamblado al proyecto.  
  
#### <a name="to-configure-the-wizard-project"></a>Para configurar el proyecto de asistente  
  
1.  En **el Explorador de soluciones**, abra el menú contextual de la **ItemTemplateWizard** nodo de proyecto y, a continuación, elija **propiedades**.  
  
2.  En el **Diseñador de proyectos**, asegúrese de que la plataforma de destino está establecida en .NET Framework 4.5.  
  
     Para proyectos de Visual C#, puede establecer este valor en el **aplicación** ficha. Para los proyectos de Visual Basic, puede establecer este valor en el **compilar** ficha. Para obtener más información, consulte [Cómo: Usar como destino una versión de .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
3.  En el **ItemTemplateWizard** del proyecto, agregue un **ventana (WPF)** elemento al proyecto y, a continuación, llame al elemento **WizardWindow**.  
  
4.  Agregue dos archivos de código que se denominan CustomActionWizard y cadenas.  
  
5.  Abra el menú contextual para el **ItemTemplateWizard** del proyecto y, a continuación, elija **Agregar referencia**.  
  
6.  En el **Administrador de referencias - ItemTemplateWizard** cuadro de diálogo, en la **ensamblados** nodo, elija la **extensiones** nodo.  
  
7.  Active las casillas situadas junto a los ensamblados siguientes y, a continuación, elija la **Aceptar** botón:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  En **el Explorador de soluciones**, en la **referencias** carpeta para el proyecto ItemTemplateWizard, elija la **EnvDTE** referencia.  
  
9. En el **propiedades** ventana, cambie el valor de la **incrustar tipos de interoperabilidad** propiedad **False**.  
  
## <a name="defining-the-default-location-and-id-strings-for-custom-actions"></a>Definir las cadenas de identificación y la ubicación predeterminada para las acciones personalizadas  
 Cada acción personalizada tiene una ubicación y un identificador que se especifica en el `GroupID` y `Location` atributos de la `CustomAction` elemento en el archivo Elements.xml. En este paso, va a definir algunas de las cadenas válidas para estos atributos en el proyecto ItemTemplateWizard. Al completar este tutorial, estas cadenas se escriben en el archivo Elements.xml en el elemento de proyecto acción personalizada cuando los usuarios especifican una ubicación y un identificador en el asistente.  
  
 Para simplificar, este ejemplo admite solo un subconjunto de las ubicaciones predeterminadas disponibles y el Id. Para obtener una lista completa, consulte [Default Custom Action Locations e identificadores](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### <a name="to-define-the-default-location-and-id-strings"></a>Para definir la ubicación predeterminada y las cadenas de Id.  
  
1.  Abrir.  
  
2.  En el **ItemTemplateWizard** proyecto de equipo y reemplace el código en el archivo de código de cadenas con el código siguiente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]  
  
## <a name="creating-the-wizard-ui"></a>Crear la interfaz de usuario del asistente  
 Agregue XAML para definir la interfaz de usuario del asistente y agregue algo de código para enlazar algunos de los controles en el Asistente para las cadenas de identificación. El asistente que se crea es similar al asistente integrado para los proyectos de SharePoint en Visual Studio.  
  
#### <a name="to-create-the-wizard-ui"></a>Para crear la interfaz de usuario del Asistente  
  
1.  En el **ItemTemplateWizard** proyecto de equipo y abra el menú contextual para el **WizardWindow.xaml** de archivos y, a continuación, elija **abrir** para abrir la ventana en el diseñador.  
  
2.  En la vista XAML, reemplace el código XAML actual por el siguiente. El código XAML define una interfaz de usuario que incluye un encabezado, los controles para especificar el comportamiento de los botones de navegación en la parte inferior de la ventana y la acción personalizada.  
  
    > [!NOTE]  
    >  El proyecto tendrá algunos errores de compilación después de agregar este código. Estos errores desaparecerán al agregar código en pasos posteriores.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  La ventana que se crea en este código XAML se deriva de la <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> clase base. Cuando se agrega un cuadro de diálogo WPF personalizado en Visual Studio, se recomienda derivar el cuadro de diálogo de esta clase para que tenga un estilo coherente con otros cuadros de diálogo de Visual Studio y para evitar problemas que pueden producirse en caso contrario, con cuadros de diálogo modales. Para obtener más información, consulte [crear y administrar cuadros de diálogo modales](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Si está desarrollando un proyecto de Visual Basic, quite el `ItemTemplateWizard` espacio de nombres desde el `WizardWindow` nombre de clase en el `x:Class` atributo de la `Window` elemento. Este elemento aparece en la primera línea del código XAML. Cuando haya terminado, la primera línea debe ser similar al código siguiente:  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  En el archivo de código subyacente del archivo WizardWindow.xaml, reemplace el código actual con el código siguiente.  
  
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]  
  
## <a name="implementing-the-wizard"></a>Implementar el asistente  
 Definir la funcionalidad del Asistente para implementar el <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaz.  
  
#### <a name="to-implement-the-wizard"></a>Para implementar el asistente  
  
1.  En el **ItemTemplateWizard** proyecto, abra el **CustomActionWizard** archivo de código y, a continuación, reemplace el código actual de este archivo por el código siguiente:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]  
  
## <a name="checkpoint"></a>Punto de control  
 En este punto del tutorial, todo el código del asistente está en el proyecto. Compile el proyecto para asegurarse de que se compila sin errores.  
  
#### <a name="to-build-your-project"></a>Para compilar el proyecto  
  
1.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
## <a name="associating-the-wizard-with-the-item-template"></a>Asociar al asistente a la plantilla de elemento  
 Ahora que ha implementado el asistente, debe asociar con el **la acción personalizada** plantilla de elemento siga tres pasos principales:  
  
1.  Firmar el ensamblado del asistente con un nombre seguro.  
  
2.  Obtener el token de clave pública del ensamblado del asistente.  
  
3.  Agregue una referencia al ensamblado del asistente en el archivo .vstemplate de la **la acción personalizada** plantilla de elemento.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Para firmar el ensamblado del asistente con un nombre seguro  
  
1.  En **el Explorador de soluciones**, abra el menú contextual de la **ItemTemplateWizard** nodo de proyecto y, a continuación, elija **propiedades**.  
  
2.  En el **firma** ficha, seleccione la **firmar el ensamblado** casilla de verificación.  
  
3.  En el **elegir un archivo de clave de nombre seguro** elija  **\<nuevo... >**.  
  
4.  En el **crear clave de nombre seguro** diálogo cuadro, escriba un nombre, desactive la **proteger mi archivo de clave con una contraseña** casilla de verificación y, a continuación, elija la **Aceptar** botón.  
  
5.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Para obtener el token de clave pública del ensamblado del asistente  
  
1.  En una ventana del símbolo del sistema de Visual Studio, ejecute el siguiente comando, reemplazando *PathToWizardAssembly* con la ruta de acceso completa al ensamblado ItemTemplateWizard.dll integrado del proyecto ItemTemplateWizard en el desarrollo equipo.  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     El token de clave pública del ensamblado ItemTemplateWizard.dll se escribe en la ventana de símbolo del sistema de Visual Studio.  
  
2.  Mantenga abierta la ventana del símbolo del sistema de Visual Studio. Necesitará el token de clave pública para completar el procedimiento siguiente.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Para agregar una referencia al ensamblado del asistente del archivo .vstemplate  
  
1.  En **el Explorador de soluciones**, expanda la **ItemTemplate** nodo de proyecto y, a continuación, abra el archivo ItemTemplate.vstemplate.  
  
2.  Cuando se acerque el final del archivo, agregue el siguiente elemento `WizardExtension` entre las etiquetas `</TemplateContent>` y `</VSTemplate>`. Reemplace el *YourToken* valor de la `PublicKeyToken` atributo con el token de clave pública que obtuvo en el procedimiento anterior.  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Para obtener más información sobre la `WizardExtension` elemento, vea [WizardExtension (elemento) &#40; Plantillas de Visual Studio &#41; ](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Guarde y cierre el archivo.  
  
## <a name="adding-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Agregar parámetros reemplazables al archivo Elements.xml de la plantilla de elemento  
 Agregue varios parámetros reemplazables al archivo Elements.xml del proyecto ItemTemplate. Estos parámetros se inicializan en el método `PopulateReplacementDictionary` de la clase `CustomActionWizard` que definió anteriormente. Cuando un usuario agrega un elemento de proyecto acción personalizada a un proyecto, Visual Studio reemplaza automáticamente estos parámetros en el archivo Elements.xml del nuevo elemento de proyecto con los valores especificados en el asistente.  
  
 Un parámetro reemplazable es un token que empieza y termina por el carácter del signo de dólar ($). Además de definir sus propios parámetros reemplazables, puede usar los parámetros integrados que define el sistema de proyectos de SharePoint y la inicializa. Para obtener más información, consulte [parámetros reemplazables](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Para agregar parámetros reemplazables al archivo Elements.xml  
  
1.  En el proyecto ItemTemplate, reemplace el contenido del archivo Elements.xml por el siguiente código XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     El nuevo XML cambia los valores de la `Id`, `GroupId`, `Location`, `Description`, y `Url` atributos a parámetros reemplazables.  
  
2.  Guarde y cierre el archivo.  
  
## <a name="adding-the-wizard-to-the-vsix-package"></a>Agregar el asistente al paquete VSIX  
 En el archivo source.extension.vsixmanifest del proyecto VSIX, agregue una referencia al proyecto de Asistente para que se implementa con el paquete VSIX que contiene el elemento de proyecto.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Para agregar el asistente al paquete VSIX  
  
1.  En **el Explorador de soluciones**, abra el menú contextual de la **source.extension.vsixmanifest** de archivos en el proyecto CustomActionProjectItem y, a continuación, elija **abrir** para abrir el archivo en el editor de manifiestos.  
  
2.  En el editor de manifiestos, elija la **activos** y, después, elija la **New** botón.  
  
     El **Agregar nuevo activo** aparece el cuadro de diálogo.  
  
3.  En el **tipo** elija **Microsoft.VisualStudio.Assembly**.  
  
4.  En el **origen** elija **un proyecto de la solución actual**.  
  
5.  En el **proyecto** elija **ItemTemplateWizard**y, a continuación, elija la **Aceptar** botón.  
  
6.  En la barra de menús, elija **generar**, **generar solución**y, a continuación, asegúrese de que la solución se compila sin errores.  
  
## <a name="testing-the-wizard"></a>Probar el asistente  
 Ahora está preparado para probar el asistente. Primero, empiece a depurar la solución CustomActionProjectItem en la instancia experimental de Visual Studio. A continuación, pruebe al Asistente para el elemento de proyecto acción personalizada en un proyecto de SharePoint en la instancia experimental de Visual Studio. Por último, compile y ejecute el proyecto SharePoint para comprobar que la acción personalizada funciona del modo esperado.  
  
#### <a name="to-start-to-debug-the-solution"></a>Para empezar a depurar la solución  
  
1.  Reinicie Visual Studio con credenciales administrativas y abra la solución CustomActionProjectItem.  
  
2.  En el proyecto ItemTemplateWizard, abra el archivo de código CustomActionWizard y, a continuación, agregue un punto de interrupción a la primera línea de código en el `RunStarted` método.  
  
3.  En la barra de menús, elija **depurar**, **excepciones**.  
  
4.  En el **excepciones** diálogo cuadro, asegúrese de que el **producida** y **no controlada por el usuario** casillas de verificación de **excepciones Common Language Runtime**están desactivadas y, a continuación, elija la **Aceptar** botón.  
  
5.  Empiece a depurar eligiendo la tecla F5 o, en la barra de menús, elija **depurar**, **Iniciar depuración**.  
  
     Visual Studio instala la extensión a %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Action Project item\1.0 e inicia una instancia experimental de Visual Studio. Probará el elemento de proyecto en esta instancia de Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Para probar el asistente en Visual Studio  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **archivo**, **New**, **proyecto**.  
  
2.  Expanda el **Visual C#** o **Visual Basic** (en función del lenguaje que admita la plantilla de elemento), expanda el **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
3.  En la lista de plantillas de proyecto, elija **proyecto de SharePoint 2010**, denomine el proyecto **CustomActionWizardTest**y, a continuación, elija la **Aceptar** botón.  
  
4.  En el **Asistente para personalización de SharePoint**, escriba la dirección URL del sitio que desea usar para la depuración y, a continuación, elija la **finalizar** botón.  
  
5.  En **el Explorador de soluciones**, abra el menú contextual del nodo de proyecto, elija **agregar**y, a continuación, elija **nuevo elemento**.  
  
6.  En el **Agregar nuevo elemento - CustomItemWizardTest** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, expanda el **2010** nodo.  
  
7.  En la lista de elementos de proyecto, elija la **la acción personalizada** de elemento y, a continuación, elija la **agregar** botón.  
  
8.  Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `RunStarted`.  
  
9. Continuar depurando el proyecto eligiendo la tecla F5 o, en la barra de menús, elija **depurar**, **continuar**.  
  
     Aparece el Asistente de personalización de SharePoint.  
  
10. En **ubicación**, elija la **Editar lista** botón de opción.  
  
11. En el **Id. de grupo** elija **comunicaciones**.  
  
12. En el **título** cuadro, escriba **Centro para desarrolladores de SharePoint**.  
  
13. En el **descripción** cuadro, escriba **abre el sitio Web del Centro para desarrolladores de SharePoint**.  
  
14. En el **URL** cuadro, escriba **http://msdn.microsoft.com/sharepoint/default.aspx**y, a continuación, elija la **finalizar** botón.  
  
     isual Studio agrega un elemento que se denomina **CustomAction1** a su proyecto y abre el archivo Elements.xml en el editor. Compruebe que Elements.xml contiene los valores especificados en el asistente.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Para probar la acción personalizada en SharePoint  
  
1.  En la instancia experimental de Visual Studio, presione la tecla F5 o, en la barra de menús, elija **depurar**, **Iniciar depuración**.  
  
     La acción personalizada se empaqueta e implementa en el sitio de SharePoint especificado por el **dirección URL del sitio** propiedad del proyecto y el explorador web se abre en la página predeterminada de este sitio.  
  
    > [!NOTE]  
    >  Si el **depuración de scripts deshabilitada** aparece el cuadro de diálogo, elija la **Sí** botón.  
  
2.  En el área de listas del sitio de SharePoint, elija el **tareas** vínculo.  
  
     El **tareas: todas las tareas** aparecerá la página.  
  
3.  En el **herramientas de lista** ficha de la cinta de opciones, elija la **lista** ficha y, a continuación, en la **configuración** grupo, elija **configuración de la lista**.  
  
     El **configuración de la lista** aparecerá la página.  
  
4.  En el **comunicaciones** encabezado cerca de la parte superior de la página, elija la **Centro para desarrolladores de SharePoint** vincular, compruebe que el explorador abre el sitio Web http://msdn.microsoft.com/sharepoint/ default.aspx y, a continuación, cierre el explorador.  
  
## <a name="cleaning-up-the-development-computer"></a>Limpiar el equipo de desarrollo  
 Después de probar el elemento de proyecto, quite la plantilla de elemento de proyecto de la instancia experimental de Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Para limpiar el equipo de desarrollo  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **herramientas**, **extensiones y actualizaciones**.  
  
     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.  
  
2.  En la lista de extensiones, elija la **elemento proyecto acción personalizada** extensión y, a continuación, elija la **desinstalar** botón.  
  
3.  En el cuadro de diálogo que aparece, elija la **Sí** botón para confirmar que desea desinstalar la extensión y, a continuación, elija la **reiniciar ahora** botón para completar la desinstalación.  
  
4.  Cierre ambas instancias de Visual Studio (la instancia experimental y la instancia de Visual Studio en el que está abierta la solución CustomActionProjectItem).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Definir tipos de elemento de proyecto personalizado de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Crear plantillas de proyecto y plantillas de elementos para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Referencia de esquema de plantillas de Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Cómo: utilizar los asistentes con plantillas de proyecto](../extensibility/how-to-use-wizards-with-project-templates.md)   
 [Identificadores y las ubicaciones predeterminadas de la acción personalizada](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  