---
title: 'Tutorial: Crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1 | Documentos de Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7397da630a5fd6f2c649d6f448627d7c77c55128
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059128"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Tutorial: Creación de un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1
  Puede extender el sistema de proyectos de SharePoint en Visual Studio creando sus propios tipos de elemento de proyecto. En este tutorial, creará un elemento de proyecto que se puede agregar a un proyecto de SharePoint para crear una acción personalizada en un sitio de SharePoint. La acción personalizada agrega un elemento de menú a la **acciones del sitio** menú del sitio de SharePoint.

 En este tutorial se muestran las siguientes tareas:

- Crear una extensión de Visual Studio que define un nuevo tipo de elemento de proyecto de SharePoint para una acción personalizada. El nuevo tipo de elemento de proyecto implementa varias características personalizadas:

  - Un menú contextual que actúa como un punto inicial para las tareas adicionales relacionadas con el elemento de proyecto, como mostrar un diseñador para la acción personalizada en Visual Studio.

  - Código que se ejecuta cuando un desarrollador cambia ciertas propiedades del elemento de proyecto y del proyecto que lo contiene.

  - Un icono personalizado que aparece junto al elemento de proyecto en **el Explorador de soluciones**.

- Crear una plantilla de elementos de Visual Studio para el elemento de proyecto.

- Compilar un paquete de extensión de Visual Studio (VSIX) para implementar la plantilla de elemento de proyecto y el ensamblado de la extensión.

- Depurar y probar el elemento de proyecto.

  Este es un tutorial independiente. Después de completar este tutorial, puede mejorar el elemento de proyecto si agrega un asistente a la plantilla de elemento. Para obtener más información, vea [Tutorial: Creación de un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

> [!NOTE]
>  Puede descargar una muestra de [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) que muestra cómo crear actividades personalizadas para un flujo de trabajo.

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:

- Ediciones compatibles de Microsoft Windows, SharePoint y Visual Studio.

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Este tutorial utiliza el **proyecto VSIX** plantilla en el SDK para crear un paquete VSIX para implementar el elemento de proyecto. Para obtener más información, consulte [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.

- Acciones personalizadas en SharePoint. Para obtener más información, consulte [acción personalizada](http://go.microsoft.com/fwlink/?LinkId=177800).

- Plantillas de elemento en Visual Studio. Para obtener más información, vea [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Crear los proyectos
 Para completar este tutorial, debe crear tres proyectos:

- Un proyecto VSIX. Este proyecto crea el paquete VSIX para implementar el elemento de proyecto de SharePoint.

- Un proyecto de plantilla de elemento. Este proyecto crea una plantilla de elemento que se puede utilizar para agregar el elemento de proyecto de SharePoint a un proyecto de SharePoint.

- Un proyecto de biblioteca de clases. Este proyecto implementa una extensión de Visual Studio que define el comportamiento del elemento de proyecto de SharePoint.

  Comience el tutorial creando ambos proyectos.

#### <a name="to-create-the-vsix-project"></a>Para crear el proyecto VSIX

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

3. En la lista en la parte superior de la **nuevo proyecto** diálogo cuadro, asegúrese de que **.NET Framework 4.5** está seleccionada.

4. En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos y, a continuación, elija el **extensibilidad** nodo.

    > [!NOTE]
    >  El **extensibilidad** nodo está disponible solo si instala el SDK de Visual Studio. Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.

5. Elija la **proyecto VSIX** plantilla.

6. En el **nombre** , escriba **CustomActionProjectItem**y, a continuación, elija el **Aceptar** botón.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **CustomActionProjectItem** proyecto a **el Explorador de soluciones**.

#### <a name="to-create-the-item-template-project"></a>Para crear el proyecto de plantilla de elemento

1. En **el Explorador de soluciones**, abra el menú contextual del nodo de solución, elija **agregar**y, a continuación, elija **nuevo proyecto**.

2. En la lista en la parte superior de la **nuevo proyecto** diálogo cuadro, asegúrese de que **.NET Framework 4.5** está seleccionada.

3. En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos y, a continuación, elija el **extensibilidad** nodo.

4. En la lista de plantillas de proyecto, elija el **plantilla de elemento de C#** o **plantilla de elemento de Visual Basic** plantilla.

5. En el **nombre** , escriba **ItemTemplate**y, a continuación, elija el **Aceptar** botón.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **ItemTemplate** proyecto a la solución.

#### <a name="to-create-the-extension-project"></a>Para crear la extensión de proyecto

1. En **el Explorador de soluciones**, abra el menú contextual del nodo de solución, elija **agregar**y, a continuación, elija **nuevo proyecto**.

2. En la lista en la parte superior de la **nuevo proyecto** diálogo cuadro, asegúrese de que **.NET Framework 4.5** está seleccionada.

3. En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos, elija el **Windows** nodo y, a continuación, elija el  **Biblioteca de clases** plantilla de proyecto.

4. En el **nombre** , escriba **ProjectItemDefinition**y, a continuación, elija el **Aceptar** botón.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **ProjectItemDefinition** proyecto a la solución y abre el archivo de código predeterminado Class1.

5. Elimine el archivo de código Class1 del proyecto.

## <a name="configure-the-extension-project"></a>Configurar el proyecto de extensión
 Antes de escribir el código para definir el tipo de elemento de proyecto de SharePoint, tiene que agregar los archivos de código y las referencias de ensamblado al proyecto de extensión.

#### <a name="to-configure-the-project"></a>Para configurar el proyecto

1. En **el Explorador de soluciones**, abra el menú contextual para el **ProjectItemDefinition** del proyecto, elija **agregar**, a continuación, elija **nuevo elemento**.

2. En la lista de elementos de proyecto, elija **archivo de código**.

3. En el **nombre** , escriba el nombre **CustomAction** con los valores adecuados la extensión de nombre de archivo y, a continuación, elija el **agregar** botón.

4. En **el Explorador de soluciones**, abra el menú contextual para el **ProjectItemDefinition** del proyecto y, a continuación, elija **Agregar referencia**.

5. En el **Administrador de referencias - ProjectItemDefinition** diálogo cuadro, elija el **ensamblados** nodo y, a continuación, elija el **Framework** nodo.

6. Active la casilla situada al lado de cada uno de los siguientes ensamblados:

    - System.ComponentModel.Composition

    - System.Windows.Forms

7. Elija la **extensiones** nodo, seleccione la casilla de verificación situada junto al ensamblado Microsoft.VisualStudio.Sharepoint y, a continuación, elija el **Aceptar** botón.

## <a name="define-the-new-sharepoint-project-item-type"></a>Definir el nuevo tipo de elemento de proyecto de SharePoint
 Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> para definir el comportamiento del nuevo tipo de elemento de proyecto. Implemente esta interfaz para definir un nuevo tipo de elemento de proyecto todas las veces que desee.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Para definir el nuevo tipo de elemento de proyecto de SharePoint

1. En el proyecto ProjectItemDefinition, abra el archivo de código CustomAction.

2. Reemplace el código de este archivo por el código siguiente.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Crear un icono para el elemento de proyecto en el Explorador de soluciones
 Cuando crea un elemento de proyecto de SharePoint personalizado, puede asociarle una imagen (un icono o mapa de bits). Esta imagen aparece junto al elemento de proyecto en **el Explorador de soluciones**.

 En el procedimiento siguiente se crea un icono para el elemento de proyecto y se incrusta en el ensamblado de la extensión. El <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> de la clase `CustomActionProjectItemTypeProvider` que creó anteriormente hace referencia a este icono.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Para crear un icono personalizado para el elemento de proyecto

1. En **el Explorador de soluciones**, abra el menú contextual para el **ProjectItemDefinition** del proyecto, elija **agregar**y, a continuación, elija **nuevo elemento...** .

2. En la lista de elementos de proyecto, elija el **archivo de icono** elemento.

    > [!NOTE]
    >  En proyectos de Visual Basic, debe elegir el **General** nodo para mostrar el **archivo de icono** elemento.

3. En el **nombre** , escriba **CustomAction_SolutionExplorer.ico**y, a continuación, elija el **agregar** botón.

     El nuevo icono se abre en el **Editor de imágenes**.

4. Modifique la versión 16x16 del archivo de icono para que tenga un diseño que pueda reconocer y guarde el archivo.

5. En **el Explorador de soluciones**, elija **CustomAction_SolutionExplorer.ico**.

6. En el **propiedades** ventana, elija la flecha situada junto a la **acción de compilación** propiedad.

7. En la lista que aparece, elija **recurso incrustado**.

## <a name="checkpoint"></a>Punto de control
 En este punto del tutorial, todo el código del elemento de proyecto está en el proyecto. Compile el proyecto para comprobar que se compila sin errores.

#### <a name="to-build-your-project"></a>Para compilar el proyecto

1. Abra el menú contextual para el **ProjectItemDefinition** proyecto y elija **compilar**.

## <a name="create-a-visual-studio-item-template"></a>Crear una plantilla de elemento de Visual Studio
 Para permitir que otros desarrolladores usen el elemento de proyecto, debe crear una plantilla de proyecto o una plantilla de elemento de proyecto. Los desarrolladores utilizan estas plantillas en Visual Studio para crear una instancia de su elemento de proyecto creando un nuevo proyecto o agregando un elemento a un proyecto existente. En este tutorial, use el proyecto ItemTemplate para configurar el elemento de proyecto.

#### <a name="to-create-the-item-template"></a>Para crear la plantilla de elementos

1. Elimine el archivo de código Class1 del proyecto ItemTemplate.

2. En el proyecto ItemTemplate, abra el *ItemTemplate.vstemplate* archivo.

3. Reemplace el contenido del archivo por el siguiente código XML y, a continuación, guarde y cierre el archivo.

    > [!NOTE]
    >  El siguiente código XML está diseñado para una plantilla de elemento de Visual C#. Si está creando una plantilla de elemento de Visual Basic, reemplace el valor del elemento `ProjectType` por `VisualBasic`.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
      <TemplateData>
        <DefaultName>CustomAction</DefaultName>
        <Name>Custom Action</Name>
        <Description>SharePoint Custom Action by Contoso</Description>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>1000</SortOrder>
        <Icon>ItemTemplate.ico</Icon>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
      <TemplateContent>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>
      </TemplateContent>
    </VSTemplate>
    ```

     Este archivo define el contenido y comportamiento de la plantilla de elementos. Para obtener más información sobre el contenido de este archivo, consulte [Visual Studio Template Schema Reference](/visualstudio/extensibility/visual-studio-template-schema-reference).

4. En **el Explorador de soluciones**, abra el menú contextual para el **ItemTemplate** del proyecto, elija **agregar**y, a continuación, elija **nuevo elemento**.

5. En el **Agregar nuevo elemento** diálogo cuadro, elija el **archivo de texto** plantilla.

6. En el **nombre** , escriba **CustomAction.spdata**y, a continuación, elija el **agregar** botón.

7. Agregue el siguiente código XML para el *CustomAction.spdata* de archivos y, a continuación, guarde y cierre el archivo.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     Este archivo contiene información sobre los archivos que están contenidos en el elemento de proyecto. El atributo `Type` del elemento `ProjectItem` debe estar establecido en la misma cadena que se pasa a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> en la definición del elemento de proyecto (la clase `CustomActionProjectItemTypeProvider` que creó anteriormente en este tutorial). Para obtener más información sobre el contenido de *.spdata* archivos, consulte [referencia de esquemas de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

8. En **el Explorador de soluciones**, abra el menú contextual para el **ItemTemplate** del proyecto, elija **agregar**y, a continuación, elija **nuevo elemento**.

9. En el **Agregar nuevo elemento** diálogo cuadro, elija el **archivo XML** plantilla.

10. En el **nombre** , escriba **Elements.xml**y, a continuación, elija el **agregar** botón.

11. Reemplace el contenido de la *Elements.xml* archivo con el siguiente código XML y, a continuación, guarde y cierre el archivo.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="Replace this with a GUID or some other unique string"
                    GroupId="SiteActions"
                    Location="Microsoft.SharePoint.StandardMenu"
                    Sequence="1000"
                    Title="Replace this with your title"
                    Description="Replace this with your description" >
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>
      </CustomAction>
    </Elements>
    ```

     Este archivo define una acción personalizada predeterminada que crea un elemento de menú en el **acciones del sitio** menú del sitio de SharePoint. Cuando un usuario elige el elemento de menú, la dirección URL especificada en el elemento `UrlAction` se abre en el explorador web. Para obtener más información sobre los elementos XML que puede usar para definir una acción personalizada, vea [definiciones de acciones personalizadas](http://go.microsoft.com/fwlink/?LinkId=177801).

12. Si lo desea, abra el *ItemTemplate.ico* de archivo y modificarlo para que tenga un diseño que pueda reconocer. Este icono se mostrará junto al elemento de proyecto en el **Agregar nuevo elemento** cuadro de diálogo.

13. En **el Explorador de soluciones**, abra el menú contextual para el **ItemTemplate** del proyecto y, a continuación, elija **descargar el proyecto**.

14. Abra el menú contextual para el **ItemTemplate** proyecto nuevo y, a continuación, elija **Editar ItemTemplate.csproj** o **Editar ItemTemplate.vbproj**.

15. Busque el elemento `VSTemplate` siguiente en el archivo del proyecto.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. Reemplace este elemento `VSTemplate` por el siguiente código XML y, a continuación, guarde y cierre el archivo.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     El elemento `OutputSubPath` especifica las carpetas adicionales en la ruta de acceso en la que se crea la plantilla de elemento al compilar el proyecto. Las carpetas especificadas aquí garantizan que la plantilla de elemento estará disponible sólo cuando los clientes abran el **Agregar nuevo elemento** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, elija el **2010**  nodo.

17. En **el Explorador de soluciones**, abra el menú contextual para el **ItemTemplate** del proyecto y, a continuación, elija **recargar el proyecto**.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Crear un paquete VSIX para implementar el elemento de proyecto
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX. Primero, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest incluido en el proyecto VSIX. A continuación, cree el paquete VSIX compilando la solución.

#### <a name="to-configure-and-create-the-vsix-package"></a>Para crear y configurar el paquete VSIX

1. En **el Explorador de soluciones**, abra el menú contextual para el **source.extension.vsixmanifest** de archivos en el proyecto CustomActionProjectItem y, a continuación, elija **abrir**.

     Visual Studio abre el archivo en el editor de manifiestos. El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que requieren todos los paquetes VSIX. Para obtener más información acerca de este archivo, consulte [referencia de 1.0 del esquema de extensión de VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. En el **Product Name** , escriba **Custom Action Project Item**.

3. En el **autor** , escriba **Contoso**.

4. En el **descripción** , escriba **SharePoint de un elemento de proyecto que representa una acción personalizada**.

5. En el **activos** ficha, elija la **New** botón.

     El **Agregar nuevo activo** aparece el cuadro de diálogo.

6. En el **tipo** elija **Microsoft.VisualStudio.ItemTemplate**.

    > [!NOTE]
    >  Este valor corresponde al elemento `ItemTemplate` del archivo extension.vsixmanifest. Este elemento identifica la subcarpeta del paquete VSIX que contiene la plantilla de elemento de proyecto. Para obtener más información, consulte [elemento ItemTemplate (Esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

7. En el **origen** elija **un proyecto de la solución actual**.

8. En el **proyecto** elija **ItemTemplate**y, a continuación, elija el **Aceptar** botón.

9. En el **activos** ficha, elija la **New** nuevamente en el botón.

     El **Agregar nuevo activo** aparece el cuadro de diálogo.

10. En el **tipo** elija **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    >  Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest. Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX. Para obtener más información, consulte [elemento MEFComponent (Esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. En el **origen** elija **un proyecto de la solución actual**.

12. En el **proyecto** elija **ProjectItemDefinition**.

13. Elija el botón **Aceptar** .

14. En la barra de menús, elija **compilar** > **compilar solución**y, a continuación, asegúrese de que el proyecto se compila sin errores.

15. Asegúrese de que la carpeta de salida de la compilación del proyecto CustomActionProjectItem contiene el archivo CustomActionProjectItem.vsix.

     De forma predeterminada, la carpeta de salida de la compilación es ..\bin\Debug en la carpeta que contiene el proyecto CustomActionProjectItem.

## <a name="test-the-project-item"></a>Probar el elemento de proyecto
 Ya puede probar el elemento de proyecto. Primero, empiece a depurar la solución CustomActionProjectItem en la instancia experimental de Visual Studio. A continuación, pruebe el **acción personalizada** elemento de proyecto en un proyecto de SharePoint en la instancia experimental de Visual Studio. Por último, compile y ejecute el proyecto SharePoint para comprobar que la acción personalizada funciona del modo esperado.

#### <a name="to-start-debugging-the-solution"></a>Para empezar a depurar la solución

1. Reinicie Visual Studio con credenciales administrativas y abra la solución CustomActionProjectItem.

2. Abra el archivo de código CustomAction y, a continuación, agregue un punto de interrupción a la primera línea de código en el método `InitializeType`.

3. Elija la **F5** tecla para iniciar la depuración.

     Visual Studio instala la extensión en %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Action Project Item\1 .0 e inicia una instancia experimental de Visual Studio. Probará el elemento de proyecto en esta instancia de Visual Studio.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Para probar el elemento de proyecto en Visual Studio

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **archivo** > **New** > **proyecto**.

2. Expanda **Visual C#** o **Visual Basic** (dependiendo del lenguaje que admita la plantilla de elemento), expanda **SharePoint**y, a continuación, elija el **2010**  nodo.

3. En la lista de plantillas de proyecto, elija **proyecto de SharePoint 2010**.

4. En el **nombre** , escriba **CustomActionTest**y, a continuación, elija el **Aceptar** botón.

5. En el **Asistente de personalización de SharePoint**, escriba la dirección URL del sitio que desea usar para la depuración y, a continuación, elija el **finalizar** botón.

6. En **el Explorador de soluciones**, abra el menú contextual del nodo de proyecto, elija **agregar**y, a continuación, elija **nuevo elemento**.

7. En el **Agregar nuevo elemento** diálogo cuadro, elija el **2010** nodo bajo el **SharePoint** nodo.

     Compruebe que la **acción personalizada** elemento aparece en la lista de elementos de proyecto.

8. Elija la **acción personalizada** elemento y, a continuación, elija el **agregar** botón.

     Visual Studio agrega un elemento que se denomina **CustomAction1** a su proyecto y abre el *Elements.xml* archivo en el editor.

9. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `InitializeType`.

10. Elija la **F5** tecla para continuar depurando el proyecto.

11. En la instancia experimental de Visual Studio, en **el Explorador de soluciones**, abra el menú contextual para el **CustomAction1** nodo y, a continuación, elija **Ver diseñador de acción personalizada**.

12. Compruebe que aparece un cuadro de mensaje y, a continuación, elija el **Aceptar** botón.

     Puede utilizar este menú contextual para proporcionar opciones o comandos adicionales a los desarrolladores, como mostrar un diseñador para la acción personalizada.

13. En la barra de menús, elija **vista** > **salida**.

     El **salida** abre la ventana.

14. En **el Explorador de soluciones**, abra el menú contextual para el **CustomAction1** elemento y, a continuación, cambie su nombre a **MyCustomAction**.

     En el **salida** ventana, aparece un mensaje de confirmación. Este mensaje lo escribe el controlador de eventos <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> que se definió en la clase `CustomActionProjectItemTypeProvider`. Puede controlar este y otros eventos de elementos de proyecto para implementar el comportamiento personalizado cuando el desarrollador modifica el elemento de proyecto.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Para probar la acción personalizada en SharePoint

1. En la instancia experimental de Visual Studio, abra el *Elements.xml* archivo que es un elemento secundario de la **MyCustomAction** elemento de proyecto.

2. En el *Elements.xml* de archivos, realice los cambios siguientes y, a continuación, guarde el archivo:

    - En el elemento `CustomAction`, establezca el atributo `Id` en un GUID o alguna otra cadena única como se muestra en el ejemplo siguiente:

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - En el elemento `CustomAction`, establezca el atributo `Title` tal y como se muestra en el siguiente ejemplo:

        ```xml
        Title="SharePoint Developer Center"
        ```

    - En el elemento `CustomAction`, establezca el atributo `Description` tal y como se muestra en el siguiente ejemplo:

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - En el elemento `UrlAction`, establezca el atributo `Url` tal y como se muestra en el siguiente ejemplo:

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. Elija la tecla **F5**.

     La acción personalizada se empaqueta e implementa en el sitio de SharePoint que se especifica en el **dirección URL del sitio** propiedad del proyecto. El explorador web se abre en la página predeterminada de este sitio.

    > [!NOTE]
    >  Si el **depuración de scripts deshabilitada** aparece el cuadro de diálogo, elija el **Sí** botón para continuar depurando el proyecto.

4. En el **acciones del sitio** menú, elija **Centro para desarrolladores de SharePoint**, compruebe que el explorador abre el sitio Web https://docs.microsoft.com/sharepoint/dev/y, a continuación, cierre el explorador web.

## <a name="clean-up-the-development-computer"></a>Limpiar el equipo de desarrollo
 Después de probar el elemento de proyecto, quite la plantilla de elemento de proyecto de la instancia experimental de Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Para limpiar el equipo de desarrollo

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **herramientas** > **extensiones y actualizaciones**.

     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

2. En la lista de extensiones, elija **Custom Action Project Item**y, a continuación, elija el **desinstalar** botón.

3. En el cuadro de diálogo que aparece, elija el **Sí** botón para confirmar que desea desinstalar la extensión.

4. Elija la **reiniciar ahora** botón para completar la desinstalación.

5. Cierre tanto la instancia experimental de Visual Studio como la instancia en la que se abre la solución CustomActionProjectItem.

## <a name="next-steps"></a>Pasos siguientes
 Después de completar este tutorial, puede agregar un asistente a la plantilla de elemento. Cuando un usuario agrega un elemento de proyecto acción personalizada para un proyecto de SharePoint, el asistente recopila información acerca de la acción (por ejemplo, su ubicación y la dirección URL de destino cuando se elige la acción) y agrega esta información para el *Elements.xml*archivo en el nuevo elemento de proyecto. Para obtener más información, vea [Tutorial: Creación de un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

## <a name="see-also"></a>Vea también

- [Tutorial: Creación de un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Definir tipos de elemento de proyecto de SharePoint personalizados](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Referencia de esquema de plantillas de Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Editor de imágenes para iconos](/cpp/windows/image-editor-for-icons)
- [Crear un icono u otra imagen &#40;Editor de imágenes para iconos&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)