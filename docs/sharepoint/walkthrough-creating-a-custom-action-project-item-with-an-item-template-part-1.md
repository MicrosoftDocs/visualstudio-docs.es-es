---
title: Crear un elemento de proyecto de acción personalizada con la plantilla de elemento, parte 1
titleSuffix: ''
description: Mediante una plantilla de elemento, cree un elemento de proyecto que se puede Agregar a un proyecto de SharePoint para crear una acción personalizada en un sitio de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 5d9d1d2cca8f8ffaec67c92b44e7a621d08ad673
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915276"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 1
  Puede extender el sistema de proyectos de SharePoint en Visual Studio creando sus propios tipos de elemento de proyecto. En este tutorial, creará un elemento de proyecto que se puede agregar a un proyecto de SharePoint para crear una acción personalizada en un sitio de SharePoint. La acción personalizada agrega un elemento de menú al menú **acciones del sitio** del sitio de SharePoint.

 En este tutorial se muestran las siguientes tareas:

- Crear una extensión de Visual Studio que define un nuevo tipo de elemento de proyecto de SharePoint para una acción personalizada. El nuevo tipo de elemento de proyecto implementa varias características personalizadas:

  - Un menú contextual que actúa como un punto inicial para las tareas adicionales relacionadas con el elemento de proyecto, como mostrar un diseñador para la acción personalizada en Visual Studio.

  - Código que se ejecuta cuando un desarrollador cambia ciertas propiedades del elemento de proyecto y del proyecto que lo contiene.

  - Icono personalizado que aparece junto al elemento de proyecto en **Explorador de soluciones**.

- Crear una plantilla de elementos de Visual Studio para el elemento de proyecto.

- Compilar un paquete de extensión de Visual Studio (VSIX) para implementar la plantilla de elemento de proyecto y el ensamblado de la extensión.

- Depurar y probar el elemento de proyecto.

  Este es un tutorial independiente. Después de completar este tutorial, puede mejorar el elemento de proyecto si agrega un asistente a la plantilla de elemento. Para obtener más información, vea [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

> [!NOTE]
> Puede descargar un ejemplo de [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) que muestra cómo crear actividades personalizadas para un flujo de trabajo.

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:

- Ediciones compatibles de Microsoft Windows, SharePoint y Visual Studio.

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. En este tutorial se usa la plantilla de **Proyecto VSIX** en el SDK para crear un paquete VSIX para implementar el elemento de proyecto. Para obtener más información, vea [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.

- Acciones personalizadas en SharePoint. Para obtener más información, vea [acción personalizada](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

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

3. En la lista de la parte superior del cuadro de diálogo **nuevo proyecto** , asegúrese de que está seleccionado **.NET Framework 4,5** .

4. En el cuadro de diálogo **nuevo proyecto** , expanda los nodos **Visual C#** o **Visual Basic** y, a continuación, elija el nodo **extensibilidad** .

    > [!NOTE]
    > El nodo **extensibilidad** solo está disponible si instala el SDK de Visual Studio. Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.

5. Elija la plantilla de **Proyecto VSIX** .

6. En el cuadro **nombre** , escriba **CustomActionProjectItem** y elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **CustomActionProjectItem** a **Explorador de soluciones**.

#### <a name="to-create-the-item-template-project"></a>Para crear el proyecto de plantilla de elemento

1. En **Explorador de soluciones**, abra el menú contextual del nodo de la solución, elija **Agregar** y, a continuación, elija **nuevo proyecto**.

2. En la lista de la parte superior del cuadro de diálogo **nuevo proyecto** , asegúrese de que está seleccionado **.NET Framework 4,5** .

3. En el cuadro de diálogo **nuevo proyecto** , expanda los nodos **Visual C#** o **Visual Basic** y, a continuación, elija el nodo **extensibilidad** .

4. En la lista de plantillas de proyecto, elija la plantilla de **elemento de C#** o la plantilla de plantilla de elemento de **Visual Basic** .

5. En el cuadro **nombre** , escriba **ItemTemplate** y, a continuación, elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **ItemTemplate** a la solución.

#### <a name="to-create-the-extension-project"></a>Para crear la extensión de proyecto

1. En **Explorador de soluciones**, abra el menú contextual del nodo de la solución, elija **Agregar** y, a continuación, elija **nuevo proyecto**.

2. En la lista de la parte superior del cuadro de diálogo **nuevo proyecto** , asegúrese de que está seleccionado **.NET Framework 4,5** .

3. En el cuadro de diálogo **nuevo proyecto** , expanda los nodos **Visual C#** o **Visual Basic** , elija el nodo **Windows** y, a continuación, elija la plantilla de proyecto **biblioteca de clases** .

4. En el cuadro **nombre** , escriba **ProjectItemDefinition** y elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **ProjectItemDefinition** a la solución y abre el archivo de código predeterminado Class1.

5. Elimine el archivo de código Class1 del proyecto.

## <a name="configure-the-extension-project"></a>Configurar el proyecto de extensión
 Antes de escribir el código para definir el tipo de elemento de proyecto de SharePoint, tiene que agregar los archivos de código y las referencias de ensamblado al proyecto de extensión.

#### <a name="to-configure-the-project"></a>Para configurar el proyecto

1. En **Explorador de soluciones**, abra el menú contextual del proyecto **ProjectItemDefinition** , elija **Agregar** y, a continuación, elija **nuevo elemento**.

2. En la lista de elementos de proyecto, elija **archivo de código**.

3. En el cuadro **nombre** , escriba el nombre **CustomAction** con la extensión de nombre de archivo adecuada y, a continuación, elija el botón **Agregar** .

4. En **Explorador de soluciones**, abra el menú contextual del proyecto **ProjectItemDefinition** y, a continuación, elija **Agregar referencia**.

5. En el cuadro de diálogo **Administrador de referencias-ProjectItemDefinition** , elija el nodo **ensamblados** y, a continuación, elija el nodo **marco** .

6. Active la casilla situada al lado de cada uno de los siguientes ensamblados:

    - System.ComponentModel.Composition

    - System.Windows.Forms

7. Elija el nodo **extensiones** , active la casilla situada junto al ensamblado Microsoft. VisualStudio. SharePoint y, a continuación, elija el botón **Aceptar** .

## <a name="define-the-new-sharepoint-project-item-type"></a>Definir el nuevo tipo de elemento de proyecto de SharePoint
 Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> para definir el comportamiento del nuevo tipo de elemento de proyecto. Implemente esta interfaz para definir un nuevo tipo de elemento de proyecto todas las veces que desee.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Para definir el nuevo tipo de elemento de proyecto de SharePoint

1. En el proyecto ProjectItemDefinition, abra el archivo de código CustomAction.

2. Reemplace el código de este archivo por el código siguiente.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Crear un icono para el elemento de proyecto en Explorador de soluciones
 Cuando crea un elemento de proyecto de SharePoint personalizado, puede asociarle una imagen (un icono o mapa de bits). Esta imagen aparece junto al elemento de proyecto en **Explorador de soluciones**.

 En el procedimiento siguiente se crea un icono para el elemento de proyecto y se incrusta en el ensamblado de la extensión. El <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> de la clase `CustomActionProjectItemTypeProvider` que creó anteriormente hace referencia a este icono.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Para crear un icono personalizado para el elemento de proyecto

1. En **Explorador de soluciones**, abra el menú contextual del proyecto **ProjectItemDefinition** , elija **Agregar** y, a continuación, elija **nuevo elemento..**..

2. En la lista de elementos de proyecto, elija el elemento de **archivo de icono** .

    > [!NOTE]
    > En proyectos de Visual Basic, debe elegir el nodo **General** para mostrar el elemento de **archivo de icono** .

3. En el cuadro **nombre** , escriba **CustomAction_SolutionExplorer. ico** y, a continuación, elija el botón **Agregar** .

     El icono nuevo se abre en el **Editor de imágenes**.

4. Modifique la versión 16x16 del archivo de icono para que tenga un diseño que pueda reconocer y guarde el archivo.

5. En **Explorador de soluciones**, elija **CustomAction_SolutionExplorer. ico**.

6. En la ventana **propiedades** , elija la flecha situada junto a la propiedad **acción de compilación** .

7. En la lista que aparece, elija **recurso incrustado**.

## <a name="checkpoint"></a>Punto de control
 En este punto del tutorial, todo el código del elemento de proyecto está en el proyecto. Compile el proyecto para comprobar que se compila sin errores.

#### <a name="to-build-your-project"></a>Para compilar el proyecto

1. Abra el menú contextual del proyecto **ProjectItemDefinition** y elija **compilar**.

## <a name="create-a-visual-studio-item-template"></a>Crear una plantilla de elementos de Visual Studio
 Para permitir que otros desarrolladores usen el elemento de proyecto, debe crear una plantilla de proyecto o una plantilla de elemento de proyecto. Los desarrolladores utilizan estas plantillas en Visual Studio para crear una instancia de su elemento de proyecto creando un nuevo proyecto o agregando un elemento a un proyecto existente. En este tutorial, use el proyecto ItemTemplate para configurar el elemento de proyecto.

#### <a name="to-create-the-item-template"></a>Para crear la plantilla de elementos

1. Elimine el archivo de código Class1 del proyecto ItemTemplate.

2. En el proyecto ItemTemplate, abra el archivo *ItemTemplate. vstemplate* .

3. Reemplace el contenido del archivo por el siguiente código XML y, a continuación, guarde y cierre el archivo.

    > [!NOTE]
    > El siguiente código XML está diseñado para una plantilla de elemento de Visual C#. Si está creando una plantilla de elemento de Visual Basic, reemplace el valor del elemento `ProjectType` por `VisualBasic`.

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

     Este archivo define el contenido y comportamiento de la plantilla de elementos. Para obtener más información sobre el contenido de este archivo, vea [referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

4. En **Explorador de soluciones**, abra el menú contextual del proyecto **ItemTemplate** , elija **Agregar** y, a continuación, elija **nuevo elemento**.

5. En el cuadro de diálogo **Agregar nuevo elemento** , elija la plantilla **archivo de texto** .

6. En el cuadro **nombre** , escriba **CustomAction. spdata** y, a continuación, elija el botón **Agregar** .

7. Agregue el siguiente código XML al archivo *CustomAction. spdata* y, a continuación, guarde y cierre el archivo.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     Este archivo contiene información sobre los archivos que están contenidos en el elemento de proyecto. El atributo `Type` del elemento `ProjectItem` debe estar establecido en la misma cadena que se pasa a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> en la definición del elemento de proyecto (la clase `CustomActionProjectItemTypeProvider` que creó anteriormente en este tutorial). Para obtener más información sobre el contenido de los archivos *. spdata* , vea [referencia de esquema de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

8. En **Explorador de soluciones**, abra el menú contextual del proyecto **ItemTemplate** , elija **Agregar** y, a continuación, elija **nuevo elemento**.

9. En el cuadro de diálogo **Agregar nuevo elemento** , elija la plantilla de **archivo XML** .

10. En el cuadro **nombre** , escriba **Elements.xml** y, a continuación, elija el botón **Agregar** .

11. Reemplace el contenido del archivo de *Elements.xml* por el siguiente código XML y, a continuación, guarde y cierre el archivo.

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

     Este archivo define una acción personalizada predeterminada que crea un elemento de menú en el menú **acciones del sitio** del sitio de SharePoint. Cuando un usuario elige el elemento de menú, la dirección URL especificada en el elemento `UrlAction` se abre en el explorador web. Para obtener más información sobre los elementos XML que se pueden usar para definir una acción personalizada, vea [definiciones de acciones personalizadas](/sharepoint/dev/schema/custom-action-definition-schema).

12. Opcionalmente, abra el archivo *ItemTemplate. ico* y modifíquelo para que tenga un diseño que pueda reconocer. Este icono se mostrará junto al elemento de proyecto en el cuadro de diálogo **Agregar nuevo elemento** .

13. En **Explorador de soluciones**, abra el menú contextual del proyecto **ItemTemplate** y, a continuación, elija **descargar el proyecto**.

14. Vuelva a abrir el menú contextual del proyecto **ItemTemplate** y, a continuación, elija **Editar ItemTemplate. csproj** o **Editar ItemTemplate. vbproj**.

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

     El elemento `OutputSubPath` especifica las carpetas adicionales en la ruta de acceso en la que se crea la plantilla de elemento al compilar el proyecto. Las carpetas especificadas aquí garantizan que la plantilla de elementos solo estará disponible cuando los clientes abran el cuadro de diálogo **Agregar nuevo elemento** , expandan el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

17. En **Explorador de soluciones**, abra el menú contextual del proyecto **ItemTemplate** y, a continuación, elija **volver a cargar el proyecto**.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Crear un paquete VSIX para implementar el elemento de proyecto
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX. Primero, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest incluido en el proyecto VSIX. A continuación, cree el paquete VSIX compilando la solución.

#### <a name="to-configure-and-create-the-vsix-package"></a>Para crear y configurar el paquete VSIX

1. En **Explorador de soluciones**, abra el menú contextual del archivo **source. Extension. vsixmanifest** en el proyecto CustomActionProjectItem y, a continuación, elija **abrir**.

     Visual Studio abre el archivo en el editor de manifiestos. El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que requieren todos los paquetes VSIX. Para obtener más información acerca de este archivo, vea [referencia de esquema de extensión VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. En el cuadro **nombre de producto** , escriba **acción personalizada elemento de proyecto**.

3. En el cuadro **autor** , escriba **contoso**.

4. En el cuadro **Descripción** , escriba **un elemento de proyecto de SharePoint que represente una acción personalizada**.

5. En la pestaña **activos** , elija el botón **nuevo** .

     Aparecerá el cuadro de diálogo **Agregar nuevo activo** .

6. En la lista **tipo** , elija **Microsoft. VisualStudio. ItemTemplate**.

    > [!NOTE]
    > Este valor corresponde al elemento `ItemTemplate` del archivo extension.vsixmanifest. Este elemento identifica la subcarpeta del paquete VSIX que contiene la plantilla de elemento de proyecto. Para obtener más información, vea [elemento ItemTemplate (esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

7. En la lista **origen** , elija **un proyecto en la solución actual**.

8. En la lista **proyecto** , elija **ItemTemplate** y, a continuación, elija el botón **Aceptar** .

9. En la pestaña **activos** , vuelva a elegir el botón **nuevo** .

     Aparecerá el cuadro de diálogo **Agregar nuevo activo** .

10. En la lista **tipo** , elija **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest. Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX. Para obtener más información, vea [elemento MEFComponent (esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. En la lista **origen** , elija **un proyecto en la solución actual**.

12. En la lista **proyecto** , elija **ProjectItemDefinition**.

13. Elija el botón **Aceptar** .

14. En la barra de menús, **Elija compilar compilar**  >  **solución** y, a continuación, asegúrese de que el proyecto se compila sin errores.

15. Asegúrese de que la carpeta de salida de la compilación del proyecto CustomActionProjectItem contiene el archivo CustomActionProjectItem.vsix.

     De forma predeterminada, la carpeta de salida de la compilación es ..\bin\Debug en la carpeta que contiene el proyecto CustomActionProjectItem.

## <a name="test-the-project-item"></a>Probar el elemento de proyecto
 Ya puede probar el elemento de proyecto. Primero, empiece a depurar la solución CustomActionProjectItem en la instancia experimental de Visual Studio. A continuación, pruebe el elemento de proyecto **acción personalizada** en un proyecto de SharePoint en la instancia experimental de Visual Studio. Por último, compile y ejecute el proyecto SharePoint para comprobar que la acción personalizada funciona del modo esperado.

#### <a name="to-start-debugging-the-solution"></a>Para empezar a depurar la solución

1. Reinicie Visual Studio con credenciales administrativas y abra la solución CustomActionProjectItem.

2. Abra el archivo de código CustomAction y, a continuación, agregue un punto de interrupción a la primera línea de código en el método `InitializeType`.

3. Elija la tecla **F5** para iniciar la depuración.

     Visual Studio instala la extensión en %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Action Project Item\1 .0 e inicia una instancia experimental de Visual Studio. Probará el elemento de proyecto en esta instancia de Visual Studio.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Para probar el elemento de proyecto en Visual Studio

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **archivo**  >  **nuevo**  >  **proyecto**.

2. Expanda **Visual C#** o **Visual Basic** (en función del lenguaje que admita la plantilla de elemento), expanda **SharePoint** y, a continuación, elija el nodo **2010** .

3. En la lista de plantillas de proyecto, elija **proyecto de SharePoint 2010**.

4. En el cuadro **nombre** , escriba **CustomActionTest** y elija el botón **Aceptar** .

5. En el **Asistente para la personalización de SharePoint**, escriba la dirección URL del sitio que desea usar para la depuración y, a continuación, elija el botón **Finalizar** .

6. En **Explorador de soluciones**, abra el menú contextual del nodo del proyecto, elija **Agregar** y, a continuación, elija **nuevo elemento**.

7. En el cuadro de diálogo **Agregar nuevo elemento** , elija el nodo **2010** debajo del nodo **SharePoint** .

     Compruebe que el elemento **acción personalizada** aparece en la lista de elementos de proyecto.

8. Elija el elemento **acción personalizada** y, a continuación, elija el botón **Agregar** .

     Visual Studio agrega un elemento denominado **CustomAction1** al proyecto y abre el archivo *Elements.xml* en el editor.

9. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `InitializeType`.

10. Elija la tecla **F5** para continuar depurando el proyecto.

11. En la instancia experimental de Visual Studio, en **Explorador de soluciones**, abra el menú contextual del nodo **CustomAction1** y, a continuación, elija **Ver diseñador de acciones personalizadas**.

12. Compruebe que aparece un cuadro de mensaje y, a continuación, elija el botón **Aceptar** .

     Puede utilizar este menú contextual para proporcionar opciones o comandos adicionales a los desarrolladores, como mostrar un diseñador para la acción personalizada.

13. En la barra de menús, elija **Ver**  >  **resultados**.

     Se abre la ventana de **salida** .

14. En **Explorador de soluciones**, abra el menú contextual para el elemento **CustomAction1** y, a continuación, cambie su nombre a **MyCustomAction**.

     En la ventana **salida** , aparece un mensaje de confirmación. Este mensaje lo escribe el controlador de eventos <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> que se definió en la clase `CustomActionProjectItemTypeProvider`. Puede controlar este y otros eventos de elementos de proyecto para implementar el comportamiento personalizado cuando el desarrollador modifica el elemento de proyecto.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Para probar la acción personalizada en SharePoint

1. En la instancia experimental de Visual Studio, abra el archivo *Elements.xml* que es un elemento secundario del elemento de proyecto **MyCustomAction** .

2. En el archivo de *Elements.xml* , realice los cambios siguientes y, a continuación, guarde el archivo:

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

     La acción personalizada se empaqueta e implementa en el sitio de SharePoint que se especifica en la propiedad **dirección URL del sitio** del proyecto. El explorador web se abre en la página predeterminada de este sitio.

    > [!NOTE]
    > Si aparece el cuadro de diálogo **depuración de scripts deshabilitado** , elija el botón **sí** para continuar con la depuración del proyecto.

4. En el menú **acciones del sitio** , elija centro para desarrolladores de **SharePoint**, compruebe que el explorador abre el sitio Web https://docs.microsoft.com/sharepoint/dev/ y, a continuación, cierre el explorador Web.

## <a name="clean-up-the-development-computer"></a>Limpiar el equipo de desarrollo
 Después de probar el elemento de proyecto, quite la plantilla de elemento de proyecto de la instancia experimental de Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Para limpiar el equipo de desarrollo

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **herramientas**  >  **extensiones y actualizaciones**.

     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

2. En la lista de extensiones, elija **elemento de proyecto acción personalizada** y, a continuación, elija el botón **desinstalar** .

3. En el cuadro de diálogo que aparece, elija el botón **sí** para confirmar que desea desinstalar la extensión.

4. Elija el botón **reiniciar ahora** para completar la desinstalación.

5. Cierre tanto la instancia experimental de Visual Studio como la instancia en la que se abre la solución CustomActionProjectItem.

## <a name="next-steps"></a>Pasos siguientes
 Después de completar este tutorial, puede agregar un asistente a la plantilla de elemento. Cuando un usuario agrega un elemento de proyecto de acción personalizado a un proyecto de SharePoint, el asistente recopila información sobre la acción (como su ubicación y la dirección URL a la que navegar cuando se elige la acción) y agrega esta información al archivo *Elements.xml* del nuevo elemento de proyecto. Para obtener más información, vea [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

## <a name="see-also"></a>Consulte también

- [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Definir tipos de elementos de proyecto personalizados de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Editor de imágenes para iconos](/cpp/windows/image-editor-for-icons)
- [Crear un icono u otra imagen &#40;editor de imágenes para iconos&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)