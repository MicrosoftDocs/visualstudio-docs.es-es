---
title: Crear un elemento de proyecto de acción personalizada con la plantilla de elemento, parte 2
titleSuffix: ''
description: En este tutorial, agregue un asistente para recopilar información de los usuarios cuando usen una plantilla de elemento para agregar un elemento de proyecto de acción personalizado en un sitio de SharePoint.
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
ms.openlocfilehash: 4b6fad27342c086e551320977cdf712f816b383c
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217949"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 2
  Después de definir un tipo personalizado de elemento de proyecto de SharePoint y asociarlo a una plantilla de elemento en Visual Studio, es posible que también desee proporcionar un asistente para la plantilla. Puede usar el Asistente para recopilar información de los usuarios cuando usen la plantilla para agregar una nueva instancia del elemento de proyecto a un proyecto. La información que recopile puede usarse para inicializar el elemento de proyecto.

 En este tutorial, agregará un asistente al elemento de proyecto acción personalizada que se muestra en [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Cuando un usuario agrega un elemento de proyecto de acción personalizado a un proyecto de SharePoint, el asistente recopila información sobre la acción personalizada (como su ubicación y la dirección URL a la que navegar cuando un usuario final la selecciona) y agrega esta información al archivo *Elements.xml* del nuevo elemento de proyecto.

 En este tutorial se muestran las siguientes tareas:

- Crear un asistente para un tipo de elemento de proyecto de SharePoint personalizado asociado a una plantilla de elemento.

- Definir una interfaz de usuario del asistente personalizada que se parezca a los asistentes integrados para los elementos de proyecto de SharePoint en Visual Studio.

- Usar parámetros reemplazables para inicializar los archivos de proyecto de SharePoint con los datos recopilados en el asistente.

- Depurar y probar el asistente.

> [!NOTE]
> Puede descargar un ejemplo de [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) que muestra cómo crear actividades personalizadas para un flujo de trabajo.

## <a name="prerequisites"></a>Requisitos previos
 Para realizar este tutorial, primero debe crear la solución CustomActionProjectItem completando el [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 También necesitará los siguientes componentes en el equipo de desarrollo para completar este tutorial:

- Ediciones compatibles de Windows, SharePoint y Visual Studio.

- Visual Studio SDK. En este tutorial se usa la plantilla de **Proyecto VSIX** en el SDK para crear un paquete VSIX para implementar el elemento de proyecto. Para obtener más información, vea [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.

- Asistentes para plantillas de elementos y proyectos de Visual Studio. Para obtener más información, vea [Cómo: usar asistentes con plantillas de proyecto](../extensibility/how-to-use-wizards-with-project-templates.md) y la <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaz.

- Acciones personalizadas en SharePoint. Para obtener más información, vea [acción personalizada](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

## <a name="create-the-wizard-project"></a>Crear el proyecto del asistente
 Para completar este tutorial, debe agregar un proyecto a la solución CustomActionProjectItem que creó en [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Implementará la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> y definirá la interfaz de usuario del asistente de este proyecto.

#### <a name="to-create-the-wizard-project"></a>Para crear el proyecto de asistente

1. En Visual Studio, abra la solución CustomActionProjectItem

2. En **Explorador de soluciones**, abra el menú contextual del nodo de la solución, elija **Agregar** y, a continuación, elija **nuevo proyecto**.

3. En el cuadro de diálogo **nuevo proyecto** , expanda los nodos **Visual C#** o **Visual Basic** y, a continuación, elija el nodo **Windows** .

4. En la parte superior del cuadro de diálogo **nuevo proyecto** , asegúrese de que se elige **.NET Framework 4,5** en la lista de versiones de la .NET Framework.

5. Elija la plantilla de proyecto **biblioteca de controles de usuario de WPF** , asigne al proyecto el nombre **ItemTemplateWizard** y, a continuación, elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **ItemTemplateWizard** a la solución.

6. Elimine el elemento UserControl1 del proyecto.

## <a name="configure-the-wizard-project"></a>Configurar el proyecto de asistente
 Antes de crear el asistente, debe agregar una ventana de Windows Presentation Foundation (WPF), un archivo de código y referencias de ensamblado al proyecto.

#### <a name="to-configure-the-wizard-project"></a>Para configurar el proyecto de asistente

1. En **Explorador de soluciones**, abra el menú contextual del nodo de proyecto **ItemTemplateWizard** y, a continuación, elija **propiedades**.

2. En el **Diseñador de proyectos**, asegúrese de que la versión de .NET Framework de destino esté establecida en .NET Framework 4,5.

     En los proyectos de Visual C#, puede establecer este valor en la pestaña **aplicación** . En el caso de los proyectos de Visual Basic, puede establecer este valor en la pestaña **compilar** . Para obtener más información, consulte [Cómo: usar como destino una versión de la .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

3. En el proyecto **ItemTemplateWizard** , agregue un elemento **Window (WPF)** al proyecto y, a continuación, asigne al elemento el nombre **WizardWindow**.

4. Agregue dos archivos de código que se denominan CustomActionWizard y Strings.

5. Abra el menú contextual del proyecto **ItemTemplateWizard** y, a continuación, elija **Agregar referencia**.

6. En el cuadro de diálogo **Administrador de referencias-ItemTemplateWizard** , en el nodo **ensamblados** , elija el nodo **extensiones** .

7. Active las casillas situadas junto a los siguientes ensamblados y, a continuación, elija el botón **Aceptar** :

    - EnvDTE

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

8. En **Explorador de soluciones**, en la carpeta **referencias** del proyecto ItemTemplateWizard, elija la referencia **EnvDTE** .

9. En la ventana **propiedades** , cambie el valor de la propiedad **incrustar tipos de interoperabilidad** a **false**.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Definir la ubicación predeterminada y las cadenas de identificador para las acciones personalizadas
 Cada acción personalizada tiene una ubicación e identificador que se especifica en los `GroupID` `Location` atributos y del `CustomAction` elemento en el archivo de *Elements.xml* . En este paso, definirá algunas de las cadenas válidas para estos atributos en el proyecto ItemTemplateWizard. Al completar este tutorial, estas cadenas se escriben en el archivo *Elements.xml* en el elemento de proyecto acción personalizada cuando los usuarios especifican una ubicación y un identificador en el asistente.

 Para simplificar, este ejemplo solo admite un subconjunto de las ubicaciones e identificadores predeterminados disponibles. Para obtener una lista completa, vea [ubicaciones e identificadores de acción personalizados predeterminados](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14)).

#### <a name="to-define-the-default-location-and-id-strings"></a>Para definir las cadenas de identificador y ubicación predeterminadas

1. Ábra.

2. En el proyecto **ItemTemplateWizard** , reemplace el código del archivo de código Strings por el código siguiente.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs" id="Snippet6":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb" id="Snippet6":::

## <a name="create-the-wizard-ui"></a>Crear la interfaz de usuario del asistente
 Agregue XAML para definir la interfaz de usuario del asistente y agregue código para enlazar algunos de los controles del asistente a las cadenas de identificador. El asistente que se crea es similar al asistente integrado para los proyectos de SharePoint en Visual Studio.

#### <a name="to-create-the-wizard-ui"></a>Para crear la interfaz de usuario del asistente

1. En el proyecto **ItemTemplateWizard** , abra el menú contextual del archivo **WizardWindow. Xaml** y, a continuación, elija **abrir** para abrir la ventana en el diseñador.

2. En la vista XAML, reemplace el código XAML actual por el siguiente. El XAML define una interfaz de usuario que incluye un encabezado, controles para especificar el comportamiento de la acción personalizada y botones de navegación en la parte inferior de la ventana.

    > [!NOTE]
    > El proyecto tendrá algunos errores de compilación después de agregar este código. Estos errores desaparecerán al agregar código en pasos posteriores.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml" id="Snippet9":::

    > [!NOTE]
    > La ventana que se crea en este código XAML se deriva de la <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> clase base. Cuando se agrega un cuadro de diálogo personalizado de WPF a Visual Studio, se recomienda derivar el cuadro de diálogo de esta clase para tener un estilo coherente con otros cuadros de diálogo de Visual Studio y evitar problemas que, de otro modo, podrían producirse con cuadros de diálogo modales. Para obtener más información, vea [crear y administrar cuadros de diálogo modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Si va a desarrollar un proyecto de Visual Basic, quite el `ItemTemplateWizard` espacio de nombres del `WizardWindow` nombre de clase en el `x:Class` atributo del `Window` elemento. Este elemento aparece en la primera línea del código XAML. Cuando haya terminado, la primera línea debe ser similar al código siguiente:

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. En el archivo de código subyacente para el archivo WizardWindow. XAML, reemplace el código actual por el código siguiente.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs" id="Snippet7":::

## <a name="implement-the-wizard"></a>Implementar el asistente
 Defina la funcionalidad del asistente implementando la <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaz.

#### <a name="to-implement-the-wizard"></a>Para implementar el asistente

1. En el proyecto **ItemTemplateWizard** , abra el archivo de código **CustomActionWizard** y, a continuación, reemplace el código actual de este archivo por el código siguiente:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs" id="Snippet8":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb" id="Snippet8":::

## <a name="checkpoint"></a>Punto de control
 En este punto del tutorial, todo el código del asistente está en el proyecto. Compile el proyecto para asegurarse de que se compila sin errores.

#### <a name="to-build-your-project"></a>Para compilar el proyecto

1. En la barra de menús, elija **Compilar** > **Compilar solución**.

## <a name="associate-the-wizard-with-the-item-template"></a>Asociar el asistente a la plantilla de elemento
 Ahora que ha implementado el asistente, debe asociarlo a la plantilla de elemento de **acción personalizada** mediante la realización de tres pasos principales:

1. Firmar el ensamblado del asistente con un nombre seguro.

2. Obtener el token de clave pública del ensamblado del asistente.

3. Agregue una referencia al ensamblado del asistente en el archivo. vstemplate para la plantilla de elemento de **acción personalizada** .

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Para firmar el ensamblado del asistente con un nombre seguro

1. En **Explorador de soluciones**, abra el menú contextual del nodo de proyecto **ItemTemplateWizard** y, a continuación, elija **propiedades**.

2. En la pestaña **Firma**, active la casilla **Firmar el ensamblado**.

3. En la lista **Elija un archivo de clave de nombre seguro** , elija **\<New...>** .

4. En el cuadro de diálogo **crear clave de nombre seguro** , escriba un nombre, desactive la casilla **proteger mi archivo de clave con una contraseña** y, a continuación, elija el botón **Aceptar** .

5. En la barra de menús, elija **Compilar** > **Compilar solución**.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Para obtener el token de clave pública del ensamblado del asistente

1. En una ventana del símbolo del sistema de Visual Studio, ejecute el comando siguiente, reemplazando *PathToWizardAssembly* por la ruta de acceso completa al ensamblado de ItemTemplateWizard.dll creado para el proyecto ItemTemplateWizard en el equipo de desarrollo.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     El token de clave pública para el ensamblado de *ItemTemplateWizard.dll* se escribe en la ventana del símbolo del sistema de Visual Studio.

2. Mantenga abierta la ventana del símbolo del sistema de Visual Studio. Necesitará el token de clave pública para completar el procedimiento siguiente.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Para agregar una referencia al ensamblado del asistente del archivo .vstemplate

1. En **Explorador de soluciones**, expanda el nodo del proyecto **ItemTemplate** y, a continuación, abra el archivo *ItemTemplate. vstemplate* .

2. Cuando se acerque el final del archivo, agregue el siguiente elemento `WizardExtension` entre las etiquetas `</TemplateContent>` y `</VSTemplate>`. Reemplace el valor de *YourToken* del `PublicKeyToken` atributo por el token de clave pública que obtuvo en el procedimiento anterior.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     Para obtener más información sobre el `WizardExtension` elemento, vea [elemento WizardExtension &#40;plantillas de Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Guarde y cierre el archivo.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Agregar parámetros reemplazables al archivo *Elements.xml* en la plantilla de elemento
 Agregue varios parámetros reemplazables al archivo *Elements.xml* en el proyecto ItemTemplate. Estos parámetros se inicializan en el método `PopulateReplacementDictionary` de la clase `CustomActionWizard` que definió anteriormente. Cuando un usuario agrega un elemento de proyecto de acción personalizado a un proyecto, Visual Studio reemplaza automáticamente estos parámetros en el archivo *Elements.xml* del nuevo elemento de proyecto con los valores especificados en el asistente.

 Un parámetro reemplazable es un token que empieza y termina por el carácter del signo de dólar ($). Además de definir sus propios parámetros reemplazables, puede usar parámetros integrados que el sistema de proyectos de SharePoint define e inicializa. Para obtener más información, vea [Parámetros reemplazables](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Para agregar parámetros reemplazables al archivo de *Elements.xml*

1. En el proyecto ItemTemplate, reemplace el contenido del archivo *Elements.xml* por el siguiente código XML.

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

     El nuevo XML cambia los valores de los `Id` `GroupId` atributos,, `Location` , `Description` y `Url` a parámetros reemplazables.

2. Guarde y cierre el archivo.

## <a name="add-the-wizard-to-the-vsix-package"></a>Agregar el Asistente al paquete VSIX
 En el archivo source. Extension. vsixmanifest del Proyecto VSIX, agregue una referencia al proyecto de Asistente para que se implemente con el paquete VSIX que contiene el elemento de proyecto.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Para agregar el asistente al paquete VSIX

1. En **Explorador de soluciones**, abra el menú contextual del archivo **source. Extension. vsixmanifest** en el proyecto CustomActionProjectItem y, a continuación, elija **abrir** para abrir el archivo en el editor de manifiestos.

2. En el editor de manifiestos, elija la pestaña **activos** y, después, elija el botón **nuevo** .

     Aparecerá el cuadro de diálogo **Agregar nuevo activo** .

3. En la lista **tipo** , elija **Microsoft. VisualStudio. Assembly**.

4. En la lista **origen** , elija **un proyecto en la solución actual**.

5. En la lista **proyecto** , elija **ItemTemplateWizard** y elija el botón **Aceptar** .

6. En la barra de menús, **Elija compilar compilar**  >  **solución** y, a continuación, asegúrese de que la solución se compila sin errores.

## <a name="test-the-wizard"></a>Probar el asistente
 Ahora está preparado para probar el asistente. En primer lugar, empiece a depurar la solución CustomActionProjectItem en la instancia experimental de Visual Studio. A continuación, pruebe el Asistente para el elemento de proyecto acción personalizada en un proyecto de SharePoint en la instancia experimental de Visual Studio. Por último, compile y ejecute el proyecto SharePoint para comprobar que la acción personalizada funciona del modo esperado.

#### <a name="to-start-to-debug-the-solution"></a>Para iniciar la depuración de la solución

1. Reinicie Visual Studio con credenciales administrativas y abra la solución CustomActionProjectItem.

2. En el proyecto ItemTemplateWizard, abra el archivo de código CustomActionWizard y, a continuación, agregue un punto de interrupción a la primera línea de código en el `RunStarted` método.

3. En la barra de menús, elija **depurar**  >  **excepciones**.

4. En el cuadro de diálogo **excepciones** , asegúrese de que las casillas **iniciadas** y **no controladas** por el usuario para las **excepciones de Common Language Runtime** estén desactivadas y, a continuación, elija el botón **Aceptar** .

5. Para iniciar la depuración, elija la tecla **F5** o, en la barra de menús, elija **depurar**  >  **iniciar depuración**.

     Visual Studio instala la extensión en el proyecto%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Action Item\1.0 e inicia una instancia experimental de Visual Studio. Probará el elemento de proyecto en esta instancia de Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Para probar el asistente en Visual Studio

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **archivo**  >  **nuevo**  >  **proyecto**.

2. Expanda el nodo **Visual C#** o **Visual Basic** (en función del lenguaje que admita la plantilla de elemento), expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

3. En la lista de plantillas de proyecto, elija **proyecto de SharePoint 2010**, asigne al proyecto el nombre **CustomActionWizardTest** y, a continuación, elija el botón **Aceptar** .

4. En el **Asistente para la personalización de SharePoint**, escriba la dirección URL del sitio que desea usar para la depuración y, a continuación, elija el botón **Finalizar** .

5. En **Explorador de soluciones**, abra el menú contextual del nodo del proyecto, elija **Agregar** y, a continuación, elija **nuevo elemento**.

6. En el cuadro de diálogo **Agregar nuevo elemento-CustomItemWizardTest** , expanda el nodo **SharePoint** y, a continuación, expanda el nodo **2010** .

7. En la lista de elementos de proyecto, elija el elemento **acción personalizada** y, a continuación, elija el botón **Agregar** .

8. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `RunStarted`.

9. Continúe con la depuración del proyecto; para ello, elija la tecla **F5** o, en la barra de menús, elija **depurar**  >  **continuar**.

     Aparece el Asistente para personalización de SharePoint.

10. En **Ubicación**, elija el botón de opción de edición de la **lista** .

11. En la lista ID. de **Grupo** , elija **comunicaciones**.

12. En el cuadro **título** , escriba **Centro para desarrolladores de SharePoint**.

13. En el cuadro  **Descripción** , escriba **abre el sitio web del centro para desarrolladores de SharePoint**.

14. En el cuadro **dirección URL** , escriba **https://docs.microsoft.com/sharepoint/dev/** y, a continuación, elija el botón **Finalizar** .

     Visual Studio agrega un elemento denominado **CustomAction1** al proyecto y abre el archivo *Elements.xml* en el editor. Compruebe que *Elements.xml* contiene los valores que especificó en el asistente.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Para probar la acción personalizada en SharePoint

1. En la instancia experimental de Visual Studio, elija la tecla **F5** o, en la barra de menús, elija **depurar**  >  **iniciar depuración**.

     La acción personalizada se empaqueta e implementa en el sitio de SharePoint especificado por la propiedad **dirección URL del sitio** del proyecto y el explorador Web se abre en la página predeterminada de este sitio.

    > [!NOTE]
    > Si aparece el cuadro de diálogo **depuración de scripts deshabilitado** , elija el botón **sí** .

2. En el área listas del sitio de SharePoint, elija el vínculo **tareas** .

     Aparece la página **tareas-todas las tareas** .

3. En la pestaña **herramientas de lista** de la cinta de opciones, elija la pestaña **lista** y, a continuación, en el grupo **configuración** , elija Configuración de la **lista**.

     Aparece la página Configuración de la **lista** .

4. En el encabezado **comunicaciones** situado en la parte superior de la página, elija el vínculo del **Centro para desarrolladores de SharePoint** , compruebe que el explorador abre el sitio Web https://docs.microsoft.com/sharepoint/dev/ y, a continuación, cierre el explorador.

## <a name="cleaning-up-the-development-computer"></a>Limpieza del equipo de desarrollo
 Después de probar el elemento de proyecto, quite la plantilla de elemento de proyecto de la instancia experimental de Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Para limpiar el equipo de desarrollo

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **herramientas**  >  **extensiones y actualizaciones**.

     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

2. En la lista de extensiones, elija la extensión de **elemento de proyecto acción personalizada** y, a continuación, elija el botón **desinstalar** .

3. En el cuadro de diálogo que aparece, elija el botón **sí** para confirmar que desea desinstalar la extensión y, a continuación, elija el botón **reiniciar ahora** para completar la desinstalación.

4. Cierre ambas instancias de Visual Studio (la instancia experimental y la instancia de Visual Studio en la que está abierta la solución CustomActionProjectItem).

## <a name="see-also"></a>Consulte también
- [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Definir tipos de elementos de proyecto personalizados de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Cómo: Utilizar los asistentes con las plantillas de proyectos](../extensibility/how-to-use-wizards-with-project-templates.md)
- [Identificadores y ubicaciones de acciones personalizadas predeterminadas](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))
