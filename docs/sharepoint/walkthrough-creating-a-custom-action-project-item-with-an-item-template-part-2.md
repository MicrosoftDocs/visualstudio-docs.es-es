---
title: 'Tutorial: Crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 2 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d9170c6ed32c7a807af8c869ca9616db3bdff683
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430466"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Tutorial: Creación de un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 2
  Después de definir un tipo de elemento de proyecto de SharePoint personalizado y asociarla a una plantilla de elementos en Visual Studio, también puede proporcionar a un Asistente para la plantilla. Puede usar al Asistente para recopilar información de los usuarios cuando usan la plantilla para agregar una nueva instancia del elemento de proyecto a un proyecto. La información que recopile puede usarse para inicializar el elemento de proyecto.

 En este tutorial, agregará un Asistente para el elemento de proyecto acción personalizada que se muestra en [Tutorial: Creación de un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Cuando un usuario agrega un elemento de proyecto acción personalizada para un proyecto de SharePoint, el asistente recopila información acerca de la acción personalizada (por ejemplo, su ubicación y la dirección URL de destino cuando un usuario final elige) y agrega esta información para el *Elements.xml* archivo en el nuevo elemento de proyecto.

 En este tutorial se muestran las siguientes tareas:

- Crear a un Asistente para un tipo de elemento de proyecto de SharePoint personalizado que está asociado con una plantilla de elemento.

- Definir un interfaz de usuario que es similar a los asistentes integrados para los elementos de proyecto de SharePoint en Visual Studio de asistente personalizada.

- Usar parámetros reemplazables para inicializar los archivos de proyecto de SharePoint con los datos recopilados en el asistente.

- Depurar y probar el asistente.

> [!NOTE]
> Puede descargar una muestra de [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) que muestra cómo crear actividades personalizadas para un flujo de trabajo.

## <a name="prerequisites"></a>Requisitos previos
 Para llevar a cabo este tutorial, primero debe crear la solución CustomActionProjectItem completando [Tutorial: Creación de un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 También necesitará los siguientes componentes en el equipo de desarrollo para completar este tutorial:

- Ediciones compatibles de Windows, SharePoint y Visual Studio.

- Visual Studio SDK. Este tutorial utiliza el **proyecto VSIX** plantilla en el SDK para crear un paquete VSIX para implementar el elemento de proyecto. Para obtener más información, consulte [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.

- Asistentes para plantillas de elementos y proyectos de Visual Studio. Para obtener más información, vea [Cómo: Usar asistentes con plantillas de proyecto](../extensibility/how-to-use-wizards-with-project-templates.md) y <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaz.

- Acciones personalizadas en SharePoint. Para obtener más información, consulte [acción personalizada](http://go.microsoft.com/fwlink/?LinkId=177800).

## <a name="create-the-wizard-project"></a>Crear el proyecto de Asistente
 Para completar este tutorial, debe agregar un proyecto a la solución CustomActionProjectItem que creó en [Tutorial: Creación de un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Implementará la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> y definirá la interfaz de usuario del asistente de este proyecto.

#### <a name="to-create-the-wizard-project"></a>Para crear el proyecto de Asistente

1. En Visual Studio, abra la solución CustomActionProjectItem

2. En **el Explorador de soluciones**, abra el menú contextual del nodo de solución, elija **agregar**y, a continuación, elija **nuevo proyecto**.

3. En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos y, a continuación, elija el **Windows** nodo.

4. En la parte superior de la **nuevo proyecto** diálogo cuadro, asegúrese de que **.NET Framework 4.5** se elige en la lista de versiones de .NET Framework.

5. Elija la **biblioteca de controles de usuario de WPF** plantilla de proyecto, asigne al proyecto **ItemTemplateWizard**y, a continuación, elija el **Aceptar** botón.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **ItemTemplateWizard** proyecto a la solución.

6. Elimine el elemento UserControl1 del proyecto.

## <a name="configure-the-wizard-project"></a>Configurar el proyecto de Asistente
 Antes de crear al asistente, debe agregar una ventana de Windows Presentation Foundation (WPF), un archivo de código y referencias de ensamblado al proyecto.

#### <a name="to-configure-the-wizard-project"></a>Para configurar el proyecto de asistente

1. En **el Explorador de soluciones**, abra el menú contextual de la **ItemTemplateWizard** nodo de proyecto y, a continuación, elija **propiedades**.

2. En el **Diseñador de proyectos**, asegúrese de que la plataforma de destino está establecida en .NET Framework 4.5.

     Para proyectos de Visual C#, puede establecer este valor en el **aplicación** ficha. Para proyectos de Visual Basic, puede establecer este valor en el **compilar** ficha. Para obtener más información, vea [Cómo: usar una versión de .NET Framework como destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

3. En el **ItemTemplateWizard** proyecto, agregue un **ventana (WPF)** elemento al proyecto y, a continuación, llame al elemento **WizardWindow**.

4. Agregue dos archivos de código que se denominan CustomActionWizard y cadenas.

5. Abra el menú contextual para el **ItemTemplateWizard** del proyecto y, a continuación, elija **Agregar referencia**.

6. En el **Administrador de referencias - ItemTemplateWizard** cuadro de diálogo el **ensamblados** nodo, elija el **extensiones** nodo.

7. Seleccione las casillas de verificación junto a los ensamblados siguientes y, a continuación, elija el **Aceptar** botón:

    - EnvDTE

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

8. En **el Explorador de soluciones**, en el **referencias** carpeta para el proyecto ItemTemplateWizard, elija el **EnvDTE** referencia.

9. En el **propiedades** ventana, cambie el valor de la **Embed Interop Types** propiedad **False**.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Definir la ubicación predeterminada y las cadenas de identificador para las acciones personalizadas
 Cada acción personalizada tiene una ubicación y un identificador que se especifica en el `GroupID` y `Location` los atributos de la `CustomAction` elemento en el *Elements.xml* archivo. En este paso, definirá algunas de las cadenas válidas para estos atributos en el proyecto ItemTemplateWizard. Al completar este tutorial, estas cadenas se escriben en el *Elements.xml* archivo en el elemento de proyecto acción personalizada cuando los usuarios especificar una ubicación y un identificador en el asistente.

 Por motivos de simplicidad, este ejemplo admite solo un subconjunto de las ubicaciones predeterminadas disponibles e identificadores. Para obtener una lista completa, consulte [Default Custom Action Locations e identificadores](http://go.microsoft.com/fwlink/?LinkId=181964).

#### <a name="to-define-the-default-location-and-id-strings"></a>Para definir la ubicación predeterminada y las cadenas de identificador

1. Abrir.

2. En el **ItemTemplateWizard** de proyecto, reemplace el código en el archivo de código las cadenas con el código siguiente.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]

## <a name="create-the-wizard-ui"></a>Crear al Asistente para interfaz de usuario
 Agregue XAML para definir la interfaz de usuario del asistente y agregue código para enlazar algunos de los controles en el Asistente para las cadenas de identificador. El asistente que se crea es similar al asistente integrado para los proyectos de SharePoint en Visual Studio.

#### <a name="to-create-the-wizard-ui"></a>Para crear al Asistente para la interfaz de usuario

1. En el **ItemTemplateWizard** de proyecto, abra el menú contextual para el **WizardWindow.xaml** de archivo y, a continuación, elija **abrir** para abrir la ventana en el diseñador.

2. En la vista XAML, reemplace el código XAML actual por el siguiente. El XAML define una interfaz de usuario que incluye un encabezado, los controles para especificar el comportamiento de la acción personalizada y botones de navegación en la parte inferior de la ventana.

    > [!NOTE]
    > El proyecto tendrá algunos errores de compilación después de agregar este código. Estos errores desaparecerán al agregar código en pasos posteriores.

     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]

    > [!NOTE]
    > La ventana que se crea en este XAML se deriva el <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> clase base. Cuando se agrega un cuadro de diálogo WPF personalizado en Visual Studio, se recomienda que el cuadro de diálogo se deriva de esta clase tiene un estilo coherente con otros cuadros de diálogo en Visual Studio y para evitar problemas que pueden producirse en caso contrario, con los cuadros de diálogo modal. Para obtener más información, consulte [creación y administración de los cuadros de diálogo Modal](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).

3. Si está desarrollando un proyecto de Visual Basic, quite el `ItemTemplateWizard` espacio de nombres desde el `WizardWindow` nombre de clase en el `x:Class` atributo de la `Window` elemento. Este elemento aparece en la primera línea del código XAML. Cuando haya terminado, la primera línea debe ser similar al código siguiente:

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. En el archivo de código subyacente del archivo WizardWindow.xaml, reemplace el código actual con el código siguiente.

     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]

## <a name="implement-the-wizard"></a>El Asistente para implementar
 Definir la funcionalidad del asistente implementando la <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaz.

#### <a name="to-implement-the-wizard"></a>Para implementar el asistente

1. En el **ItemTemplateWizard** proyecto, abra el **CustomActionWizard** archivo de código y, a continuación, reemplace el código actual de este archivo con el código siguiente:

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]

## <a name="checkpoint"></a>Punto de control
 En este punto del tutorial, todo el código del asistente está en el proyecto. Compile el proyecto para asegurarse de que se compila sin errores.

#### <a name="to-build-your-project"></a>Para compilar el proyecto

1. En la barra de menús, elija **Compilar** > **Compilar solución**.

## <a name="associate-the-wizard-with-the-item-template"></a>Asociar al Asistente para la plantilla de elemento
 Ahora que ha implementado el asistente, debe asociarlo con el **acción personalizada** plantilla de elemento siguiendo los tres pasos principales:

1. Firmar el ensamblado del asistente con un nombre seguro.

2. Obtener el token de clave pública del ensamblado del asistente.

3. Agregue una referencia al ensamblado del asistente en el archivo .vstemplate para la **acción personalizada** plantilla de elemento.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Para firmar el ensamblado del asistente con un nombre seguro

1. En **el Explorador de soluciones**, abra el menú contextual de la **ItemTemplateWizard** nodo de proyecto y, a continuación, elija **propiedades**.

2. En el **firma** ficha, seleccione el **firmar el ensamblado** casilla de verificación.

3. En el **elegir un archivo de clave de nombre seguro** elija  **\<nuevo... >**.

4. En el **crear clave de nombre seguro** diálogo cuadro, escriba un nombre, desactive la **proteger mi archivo de clave con una contraseña** casilla de verificación y, a continuación, elija el **Aceptar** botón.

5. En la barra de menús, elija **Compilar** > **Compilar solución**.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Para obtener el token de clave pública del ensamblado del asistente

1. En una ventana del símbolo del sistema de Visual Studio, ejecute el siguiente comando, reemplazando *PathToWizardAssembly* con la ruta de acceso completa al ensamblado ItemTemplateWizard.dll integrado para el proyecto ItemTemplateWizard en el desarrollo equipo.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     El token de clave pública para el *ItemTemplateWizard.dll* ensamblado se escribe en la ventana del símbolo del sistema de Visual Studio.

2. Mantenga abierta la ventana del símbolo del sistema de Visual Studio. Necesitará el token de clave pública para completar el procedimiento siguiente.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Para agregar una referencia al ensamblado del asistente del archivo .vstemplate

1. En **el Explorador de soluciones**, expanda el **ItemTemplate** nodo de proyecto y, a continuación, abra el *ItemTemplate.vstemplate* archivo.

2. Cuando se acerque el final del archivo, agregue el siguiente elemento `WizardExtension` entre las etiquetas `</TemplateContent>` y `</VSTemplate>`. Reemplace el *YourToken* valor de la `PublicKeyToken` atributo con el token de clave pública que obtuvo en el procedimiento anterior.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     Para obtener más información sobre la `WizardExtension` elemento, vea [elemento WizardExtension &#40;plantillas de Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).

3. Guarde y cierre el archivo.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Agregar parámetros reemplazables para el *Elements.xml* archivo en la plantilla de elemento
 Agregue varios parámetros reemplazables para el *Elements.xml* archivo en el proyecto ItemTemplate. Estos parámetros se inicializan en el método `PopulateReplacementDictionary` de la clase `CustomActionWizard` que definió anteriormente. Cuando un usuario agrega un elemento de proyecto acción personalizada a un proyecto, Visual Studio reemplaza automáticamente estos parámetros en el *Elements.xml* archivo en el nuevo elemento de proyecto con los valores especificados en el asistente.

 Un parámetro reemplazable es un token que empieza y termina por el carácter del signo de dólar ($). Además de definir sus propios parámetros reemplazables, puede usar parámetros integrados que define el sistema de proyectos de SharePoint y la inicializa. Para obtener más información, consulte [parámetros reemplazables](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Para agregar parámetros reemplazables para el *Elements.xml* archivo

1. En el proyecto ItemTemplate, reemplace el contenido de la *Elements.xml* archivo con el siguiente código XML.

    ```xml
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

2. Guarde y cierre el archivo.

## <a name="add-the-wizard-to-the-vsix-package"></a>Agregar al asistente al paquete VSIX
 En el archivo source.extension.vsixmanifest del proyecto VSIX, agregue una referencia al proyecto de Asistente para que se implementa con el paquete VSIX que contiene el elemento de proyecto.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Para agregar el asistente al paquete VSIX

1. En **el Explorador de soluciones**, abra el menú contextual de la **source.extension.vsixmanifest** de archivos en el proyecto CustomActionProjectItem y, a continuación, elija **abrir** para abrir el archivo en el editor de manifiestos.

2. En el editor de manifiestos, elija el **activos** y, después, elija el **New** botón.

     El **Agregar nuevo activo** aparece el cuadro de diálogo.

3. En el **tipo** elija **Microsoft.VisualStudio.Assembly**.

4. En el **origen** elija **un proyecto de la solución actual**.

5. En el **proyecto** elija **ItemTemplateWizard**y, a continuación, elija el **Aceptar** botón.

6. En la barra de menús, elija **compilar** > **compilar solución**y, a continuación, asegúrese de que la solución se compila sin errores.

## <a name="test-the-wizard"></a>El Asistente para prueba
 Ahora está preparado para probar el asistente. Primero, empiece a depurar la solución CustomActionProjectItem en la instancia experimental de Visual Studio. A continuación, pruebe al Asistente para el elemento de proyecto acción personalizada en un proyecto de SharePoint en la instancia experimental de Visual Studio. Por último, compile y ejecute el proyecto SharePoint para comprobar que la acción personalizada funciona del modo esperado.

#### <a name="to-start-to-debug-the-solution"></a>Para empezar a depurar la solución

1. Reinicie Visual Studio con credenciales administrativas y abra la solución CustomActionProjectItem.

2. En el proyecto ItemTemplateWizard, abra el archivo de código CustomActionWizard y, a continuación, agregue un punto de interrupción a la primera línea de código en el `RunStarted` método.

3. En la barra de menús, elija **depurar** > **excepciones**.

4. En el **excepciones** diálogo cuadro, asegúrese de que el **producida** y **User-unhandled** casillas de verificación de **excepciones Common Language Runtime**están desactivadas y, a continuación, elija el **Aceptar** botón.

5. Iniciar la depuración eligiendo el **F5** clave, o bien, en la barra de menús, elija **depurar** > **Iniciar depuración**.

     Visual Studio instala la extensión en %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Action Project item\1.0 e inicia una instancia experimental de Visual Studio. Probará el elemento de proyecto en esta instancia de Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Para probar el asistente en Visual Studio

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **archivo** > **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** nodo (dependiendo del lenguaje que admita la plantilla de elemento), expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.

3. En la lista de plantillas de proyecto, elija **proyecto de SharePoint 2010**, denomine el proyecto **CustomActionWizardTest**y, a continuación, elija el **Aceptar** botón.

4. En el **Asistente de personalización de SharePoint**, escriba la dirección URL del sitio que desea usar para la depuración y, a continuación, elija el **finalizar** botón.

5. En **el Explorador de soluciones**, abra el menú contextual del nodo de proyecto, elija **agregar**y, a continuación, elija **nuevo elemento**.

6. En el **Agregar nuevo elemento - CustomItemWizardTest** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, expanda el **2010** nodo.

7. En la lista de elementos de proyecto, elija el **acción personalizada** elemento y, a continuación, elija el **agregar** botón.

8. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `RunStarted`.

9. Continuar depurando el proyecto eligiendo la **F5** clave o, en la barra de menús, elija **depurar** > **continuar**.

     Aparece el Asistente de personalización de SharePoint.

10. En **ubicación**, elija el **Editar lista** botón de opción.

11. En el **Id. de grupo** elija **comunicaciones**.

12. En el **título** , escriba **Centro para desarrolladores de SharePoint**.

13. En el **descripción** , escriba **abre el sitio Web de SharePoint Developer Center**.

14. En el **URL** , escriba **https://docs.microsoft.com/sharepoint/dev/** y, a continuación, elija el **finalizar** botón.

     Visual Studio agrega un elemento que se denomina **CustomAction1** a su proyecto y abre el *Elements.xml* archivo en el editor. Compruebe que *Elements.xml* contiene los valores que especificó en el asistente.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Para probar la acción personalizada en SharePoint

1. En la instancia experimental de Visual Studio, elija el **F5** clave o, en la barra de menús, elija **depurar** > **Iniciar depuración**.

     La acción personalizada se empaqueta e implementa en el sitio de SharePoint especificado por el **dirección URL del sitio** propiedad del proyecto y el explorador web se abre en la página predeterminada de este sitio.

    > [!NOTE]
    > Si el **depuración de scripts deshabilitada** aparece el cuadro de diálogo, elija el **Sí** botón.

2. En el área de listas del sitio de SharePoint, elija el **tareas** vínculo.

     El **tareas: todas las tareas** aparece la página.

3. En el **herramientas de lista** pestaña de la cinta de opciones, elija la **lista** ficha y, a continuación, en el **configuración** grupo, elija **configuración de la lista**.

     El **configuración de la lista** aparece la página.

4. En el **comunicaciones** encabezado en la parte superior de la página, elija el **Centro para desarrolladores de SharePoint** vincular, compruebe que el explorador abre el sitio Web https://docs.microsoft.com/sharepoint/dev/y, a continuación, cierre el explorador.

## <a name="cleaning-up-the-development-computer"></a>Limpiar el equipo de desarrollo
 Después de probar el elemento de proyecto, quite la plantilla de elemento de proyecto de la instancia experimental de Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Para limpiar el equipo de desarrollo

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **herramientas** > **extensiones y actualizaciones**.

     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

2. En la lista de extensiones, elija el **Custom Action Project Item** extensión y, a continuación, elija el **desinstalar** botón.

3. En el cuadro de diálogo que aparece, elija el **Sí** botón para confirmar que desea desinstalar la extensión y, a continuación, elija el **reiniciar ahora** botón para completar la desinstalación.

4. Cierre ambas instancias de Visual Studio (la instancia experimental y la instancia de Visual Studio en el que está abierta la solución CustomActionProjectItem).

## <a name="see-also"></a>Vea también
- [Tutorial: Creación de un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Definir tipos de elemento de proyecto de SharePoint personalizados](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Referencia de esquema de plantillas de Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Cómo: Usar asistentes con plantillas de proyectos](../extensibility/how-to-use-wizards-with-project-templates.md)
- [Los identificadores y las ubicaciones predeterminadas de la acción personalizada](http://go.microsoft.com/fwlink/?LinkId=181964)
