---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint project items, creating custom templates"
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 41ed9c1c-4239-4d80-934b-975fde744288
caps.latest.revision: 152
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 151
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1
  Puede extender el sistema de proyectos de SharePoint en Visual Studio creando sus propios tipos de elemento de proyecto.  En este tutorial, creará un elemento de proyecto que se puede agregar a un proyecto de SharePoint para crear una acción personalizada en un sitio de SharePoint.  La acción personalizada agrega un elemento de menú al menú **Acciones del sitio** del sitio de SharePoint.  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear una extensión de Visual Studio que define un nuevo tipo de elemento de proyecto de SharePoint para una acción personalizada.  El nuevo tipo de elemento de proyecto implementa varias características personalizadas:  
  
    -   Un menú contextual que actúa como un punto inicial para las tareas adicionales relacionadas con el elemento de proyecto, como mostrar un diseñador para la acción personalizada en Visual Studio.  
  
    -   Código que se ejecuta cuando un desarrollador cambia ciertas propiedades del elemento de proyecto y del proyecto que lo contiene.  
  
    -   Un icono personalizado que aparece al lado del elemento de proyecto en el **Explorador de soluciones**.  
  
-   Crear una plantilla de elementos de Visual Studio para el elemento de proyecto.  
  
-   Compilar un paquete de extensión de Visual Studio \(VSIX\) para implementar la plantilla de elemento de proyecto y el ensamblado de la extensión.  
  
-   Depurar y probar el elemento de proyecto.  
  
 Este es un tutorial independiente.  Después de completar este tutorial, puede mejorar el elemento de proyecto si agrega un asistente a la plantilla de elemento.  Para obtener más información, vea [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
> [!NOTE]  
>  Puede descargar un ejemplo que contiene los proyectos completos, el código y otros archivos para este tutorial en la siguiente ubicación: [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Requisitos previos  
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows, SharePoint y Visual Studio.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  En este tutorial se utiliza la plantilla **Proyecto VSIX** del SDK para crear un paquete VSIX e implementar el elemento.  Para obtener más información, vea [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.  
  
-   Acciones personalizadas en SharePoint.  Para obtener más información, vea una [acción personalizada](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
-   Plantillas de elemento en Visual Studio.  Para obtener más información, vea [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md).  
  
## Crear los proyectos  
 Para completar este tutorial, debe crear tres proyectos:  
  
-   Un proyecto VSIX.  Este proyecto crea el paquete VSIX para implementar el elemento de proyecto de SharePoint.  
  
-   Un proyecto de plantilla de elemento.  Este proyecto crea una plantilla de elemento que se puede utilizar para agregar el elemento de proyecto de SharePoint a un proyecto de SharePoint.  
  
-   Un proyecto de biblioteca de clases.  Este proyecto implementa una extensión de Visual Studio que define el comportamiento del elemento de proyecto de SharePoint.  
  
 Comience el tutorial creando ambos proyectos.  
  
#### Para crear el proyecto VSIX  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
3.  En la lista que aparece en la parte superior del cuadro de diálogo **Nuevo proyecto**, asegúrese de que **.NET Framework 4.5** esté seleccionado.  
  
4.  En el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Visual C\#** o **Visual Basic** y, a continuación, elija el nodo **Extensibilidad**.  
  
    > [!NOTE]  
    >  El nodo **Extensibilidad** solo está disponible si se instala Visual Studio SDK.  Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.  
  
5.  Elija la plantilla **Proyecto VSIX**.  
  
6.  En el cuadro **Nombre**, escriba **CustomActionProjectItem** y elija el botón **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **CustomActionProjectItem** al **Explorador de soluciones**.  
  
#### Para crear el proyecto de plantilla de elemento  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del nodo de la solución, elija **Agregar** y después **Nuevo proyecto**.  
  
    > [!NOTE]  
    >  En los proyectos de Visual Basic, el nodo de la solución aparece en el **Explorador de soluciones** solo cuando se activa la casilla **Mostrar solución siempre** en [General, Proyectos y soluciones, Cuadro de diálogo Opciones](http://msdn.microsoft.com/es-es/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  En la lista que aparece en la parte superior del cuadro de diálogo **Nuevo proyecto**, asegúrese de que **.NET Framework 4.5** esté seleccionado.  
  
3.  En el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Visual C\#** o **Visual Basic** y, a continuación, elija el nodo **Extensibilidad**.  
  
4.  En la lista de plantillas de proyecto, elija la plantilla **Plantilla de elemento de C\#** o **Plantilla de elemento de Visual Basic**.  
  
5.  En el cuadro **Nombre**, escriba **ItemTemplate** y elija el botón **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **ItemTemplate** a la solución.  
  
#### Para crear la extensión de proyecto  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del nodo de la solución, elija **Agregar** y después **Nuevo proyecto**.  
  
2.  En la lista que aparece en la parte superior del cuadro de diálogo **Nuevo proyecto**, asegúrese de que **.NET Framework 4.5** esté seleccionado.  
  
3.  En el cuadro de diálogo **Nuevo proyecto**, expanda los nodos **Visual C\#** o **Visual Basic** elija el nodo **Windows** y después elija la plantilla de proyecto **Biblioteca de clases**.  
  
4.  En el cuadro **Nombre**, escriba **ProjectItemDefinition** y elija el botón **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **ProjectItemDefinition** a la solución y abre el archivo de código predeterminado Class1.  
  
5.  Elimine el archivo de código Class1 del proyecto.  
  
## Configurar el proyecto de extensión  
 Antes de escribir el código para definir el tipo de elemento de proyecto de SharePoint, tiene que agregar los archivos de código y las referencias de ensamblado al proyecto de extensión.  
  
#### Para configurar el proyecto  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto **ProjectItemDefinition**, elija **Agregar** y luego **Nuevo elemento**.  
  
2.  En la lista de elementos de proyecto, elija **Archivo de código**.  
  
3.  En el cuadro **Nombre**, escriba el nombre **CustomAction** con la extensión de nombre de archivo correcta y elija el botón **Agregar**.  
  
4.  En el **Explorador de soluciones**, abra el menú contextual del proyecto **ProjectItemDefinition** y luego elija **Agregar referencia**.  
  
5.  En el cuadro de diálogo **Administrador de referencias – ProjectItemDefinition**, elija el nodo **Ensamblados** y **Framework**.  
  
6.  Active la casilla situada al lado de cada uno de los siguientes ensamblados:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  Elija el nodo **Extensiones**, active la casilla situada junto al ensamblado Microsoft.VisualStudio.SharePoint y después elija el botón **Aceptar**.  
  
## Definir el nuevo tipo de elemento de proyecto de SharePoint  
 Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> para definir el comportamiento del nuevo tipo de elemento de proyecto.  Implemente esta interfaz para definir un nuevo tipo de elemento de proyecto todas las veces que desee.  
  
#### Para definir el nuevo tipo de elemento de proyecto de SharePoint  
  
1.  En el proyecto ProjectItemDefinition, abra el archivo de código CustomAction.  
  
2.  Reemplace el código de este archivo por el código siguiente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/projectitemdefinition/customaction.vb#1)]  
  
## Crear un icono para el elemento de proyecto en el Explorador de soluciones  
 Cuando crea un elemento de proyecto de SharePoint personalizado, puede asociarle una imagen \(un icono o mapa de bits\).  Esta imagen aparece al lado del elemento de proyecto en el **Explorador de soluciones**.  
  
 En el procedimiento siguiente se crea un icono para el elemento de proyecto y se incrusta en el ensamblado de la extensión.  El <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> de la clase `CustomActionProjectItemTypeProvider` que creó anteriormente hace referencia a este icono.  
  
#### Para crear un icono personalizado para el elemento de proyecto  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto **ProjectItemDefinition**, elija **Agregar** y luego **Nuevo elemento…**.  
  
2.  En la lista de elementos de proyecto, elija el elemento **Archivo de icono**.  
  
    > [!NOTE]  
    >  En los proyectos Visual Basic, debe elegir el nodo **General** para mostrar el elemento **Archivo de icono**.  
  
3.  En el cuadro **Nombre**, escriba **CustomAction\_SolutionExplorer.ico** y elija el botón **Agregar**.  
  
     El nuevo icono se abre en el **Editor de imágenes**.  
  
4.  Modifique la versión 16x16 del archivo de icono para que tenga un diseño que pueda reconocer y guarde el archivo.  
  
5.  En el **Explorador de soluciones**, elija **CustomAction\_SolutionExplorer.ico**.  
  
6.  En la ventana **Propiedades**, elija la flecha situada junto a la propiedad **Acción de compilación**.  
  
7.  En la lista que aparece, elija **Recurso incrustado**.  
  
## Punto de control  
 En este punto del tutorial, todo el código del elemento de proyecto está en el proyecto.  Compile el proyecto para comprobar que se compila sin errores.  
  
#### Para compilar el proyecto  
  
1.  Abra el menú contextual del proyecto **ProjectItemDefinition** y elija **Compilar**.  
  
## Crear una plantilla de elementos de Visual Studio  
 Para permitir que otros desarrolladores usen el elemento de proyecto, debe crear una plantilla de proyecto o una plantilla de elemento de proyecto.  Los desarrolladores utilizan estas plantillas en Visual Studio para crear una instancia de su elemento de proyecto creando un nuevo proyecto o agregando un elemento a un proyecto existente.  En este tutorial, use el proyecto ItemTemplate para configurar el elemento de proyecto.  
  
#### Para crear la plantilla de elementos  
  
1.  Elimine el archivo de código Class1 del proyecto ItemTemplate.  
  
2.  En el proyecto ItemTemplate, abra el archivo ItemTemplate.vstemplate.  
  
3.  Reemplace el contenido del archivo por el siguiente código XML y, a continuación, guarde y cierre el archivo.  
  
    > [!NOTE]  
    >  El siguiente código XML está diseñado para una plantilla de elemento de Visual C\#.  Si está creando una plantilla de elemento de Visual Basic, reemplace el valor del elemento `ProjectType` por `VisualBasic`.  
  
    ```  
  
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
  
     Este archivo define el contenido y comportamiento de la plantilla de elementos.  Para obtener más información sobre el contenido de este archivo, vea [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
4.  En el **Explorador de soluciones**, abra el menú contextual del proyecto **ItemTemplate**, elija **Agregar** y luego **Nuevo elemento**.  
  
5.  En el cuadro de diálogo **Agregar nuevo elemento**, elija la plantilla **Archivo de texto**.  
  
6.  En el cuadro **Nombre**, escriba **CustomAction.spdata** y elija el botón **Agregar**.  
  
7.  Agregue el siguiente código XML al archivo CustomAction.spdata y, a continuación, guarde y cierre el archivo.  
  
    ```  
  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     Este archivo contiene información sobre los archivos que están contenidos en el elemento de proyecto.  El atributo `Type` del elemento `ProjectItem` debe estar establecido en la misma cadena que se pasa a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> en la definición del elemento de proyecto \(la clase `CustomActionProjectItemTypeProvider` que creó anteriormente en este tutorial\).  Para obtener más información sobre el contenido de los archivos .spdata, vea [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
8.  En el **Explorador de soluciones**, abra el menú contextual del proyecto **ItemTemplate**, elija **Agregar** y luego **Nuevo elemento**.  
  
9. En el cuadro de diálogo **Agregar nuevo elemento**, elija la plantilla **Archivo XML**.  
  
10. En el cuadro **Nombre**, escriba **Elements.xml** y elija el botón **Agregar**.  
  
11. Reemplace el contenido del archivo Elements.xml por el siguiente código XML y, a continuación, guarde y cierre el archivo.  
  
    ```  
  
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
  
     Este archivo define una acción personalizada predeterminada que crea un elemento en el menú **Acciones del sitio** del sitio de SharePoint.  Cuando un usuario elige el elemento de menú, la dirección URL especificada en el elemento `UrlAction` se abre en el explorador web.  Para obtener más información sobre los elementos XML que se pueden usar para definir una acción personalizada, vea las [definiciones de acciones personalizadas](http://go.microsoft.com/fwlink/?LinkId=177801).  
  
12. Si lo desea. también puede abrir el archivo ItemTemplate.ico y modificarlo para que tenga un diseño que pueda reconocer.  Este icono se mostrará al lado del elemento de proyecto en el cuadro de diálogo **Agregar nuevo elemento**.  
  
13. En el **Explorador de soluciones**, abra el menú contextual del proyecto **ItemTemplate** y, a continuación, elija **Descargar el proyecto**.  
  
14. Abra de nuevo el menú contextual del proyecto **ItemTemplate** y, a continuación, elija **Editar ItemTemplate.csproj** o **Editar ItemTemplate.vbproj**.  
  
15. Busque el elemento `VSTemplate` siguiente en el archivo del proyecto.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. Reemplace este elemento `VSTemplate` por el siguiente código XML y, a continuación, guarde y cierre el archivo.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     El elemento `OutputSubPath` especifica las carpetas adicionales en la ruta de acceso en la que se crea la plantilla de elemento al compilar el proyecto.  Las carpetas especificadas aquí garantizan que la plantilla de elemento solo estará disponible cuando los clientes abran el cuadro de diálogo **Agregar nuevo elemento**, expandan el nodo **SharePoint** y, a continuación, elijan el nodo **2010**.  
  
17. En el **Explorador de soluciones**, abra el menú contextual del proyecto **ItemTemplate** y, a continuación, elija **Volver a cargar el proyecto**.  
  
## Crear un paquete VSIX para implementar el elemento de proyecto  
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX.  Primero, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest incluido en el proyecto VSIX.  A continuación, cree el paquete VSIX compilando la solución.  
  
#### Para crear y configurar el paquete VSIX  
  
1.  En el **Explorador de soluciones**, abra el menú contextual para el archivo **source.extension.vsixmanifest** en el proyecto CustomActionProjectItem y, a continuación, elija **Abrir**.  
  
     Visual Studio abre el archivo en el editor de manifiestos.  El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que requieren todos los paquetes VSIX.  Para obtener más información sobre este archivo, vea [Referencia de esquema de extensión VSIX](http://msdn.microsoft.com/es-es/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  En el cuadro **Nombre de producto**, escriba **Custom Action Project Item**.  
  
3.  En el cuadro **Autor**, escriba **Contoso**.  
  
4.  En el cuadro **Descripción**, escriba **Elemento de proyecto de SharePoint que representa una acción personalizada**.  
  
5.  En la pestaña **Activos**, elija el botón **Nuevo**.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo activo**.  
  
6.  En la lista **Tipo**, elija **Microsoft.VisualStudio.ItemTemplate**.  
  
    > [!NOTE]  
    >  Este valor corresponde al elemento `ItemTemplate` del archivo extension.vsixmanifest.  Este elemento identifica la subcarpeta del paquete VSIX que contiene la plantilla de elemento de proyecto.  Para obtener más información, vea [NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/es-es/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
7.  En la lista **Origen**, elija **Un proyecto de la solución actual**.  
  
8.  En la lista **Proyecto**, elija **ItemTemplate** y elija el botón **Aceptar**.  
  
9. En la pestaña **Activos**, elija el botón **Nuevo** otra vez.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo activo**.  
  
10. En la lista **Tipo**, elija **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest.  Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX.  Para obtener más información, vea [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/es-es/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. En la lista **Origen**, elija **Un proyecto de la solución actual**.  
  
12. En la lista **Proyecto**, elija **ProjectItemDefinition**.  
  
13. Elija el botón **Aceptar**.  
  
14. En la barra de menús, elija **Compilación**, **Compilar solución** y asegúrese de que el proyecto se compila sin errores.  
  
15. Asegúrese de que la carpeta de salida de la compilación del proyecto CustomActionProjectItem contiene el archivo CustomActionProjectItem.vsix.  
  
     De forma predeterminada, la carpeta de salida de la compilación es ..\\bin\\Debug en la carpeta que contiene el proyecto CustomActionProjectItem.  
  
## Probar el elemento de proyecto  
 Ya puede probar el elemento de proyecto.  Primero, empiece a depurar la solución CustomActionProjectItem en la instancia experimental de Visual Studio.  A continuación, pruebe el elemento de proyecto **Acción personalizada** de un proyecto de SharePoint en la instancia experimental de Visual Studio.  Por último, compile y ejecute el proyecto SharePoint para comprobar que la acción personalizada funciona del modo esperado.  
  
#### Para empezar a depurar la solución  
  
1.  Reinicie Visual Studio con credenciales administrativas y abra la solución CustomActionProjectItem.  
  
2.  Abra el archivo de código CustomAction y, a continuación, agregue un punto de interrupción a la primera línea de código en el método `InitializeType`.  
  
3.  Elija la tecla **F5** para iniciar la depuración.  
  
     Visual Studio instala la extensión en %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Custom Action Project Item\\1 .0 e inicia una instancia experimental de Visual Studio.  Probará el elemento de proyecto en esta instancia de Visual Studio.  
  
#### Para probar el elemento de proyecto en Visual Studio  
  
1.  En la barra de menús de la instancia experimental de Visual Studio, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  Expanda **Visual C\#** o **Visual Basic** \(en función del lenguaje que admita la plantilla de elemento\), expanda **SharePoint** y, a continuación, elija el nodo **2010**.  
  
3.  En la lista de plantillas de proyecto, elija **Proyecto de SharePoint 2010**.  
  
4.  En el cuadro **Nombre**, escriba **CustomActionTest** y elija el botón **Aceptar**.  
  
5.  En el **Asistente para personalización de SharePoint**, escriba la dirección URL del sitio que desea usar en la depuración y elija el botón **Finalizar**.  
  
6.  En el **Explorador de soluciones**, abra el menú contextual del nodo de proyecto, elija **Agregar** y luego **Nuevo elemento**.  
  
7.  En el cuadro de diálogo **Agregar nuevo elemento**, elija el nodo **2010** en el nodo **SharePoint**.  
  
     Compruebe que el elemento **Acción personalizada** aparece en la lista de elementos de proyecto.  
  
8.  Elija el elemento **Acción personalizada** y, a continuación, el botón **Agregar**.  
  
     Visual Studio agrega un elemento denominado **CustomAction1** a su proyecto y abre el archivo Elements.xml en el editor.  
  
9. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `InitializeType`.  
  
10. Elija la tecla **F5** para continuar depurando el proyecto.  
  
11. En la instancia experimental de Visual Studio, en el **Explorador de soluciones**, abra el menú contextual del nodo **CustomAction1** y, a continuación, elija **Ver diseñador de acción personalizada**.  
  
12. Compruebe que aparece un cuadro de mensaje y, a continuación, elija el botón **Aceptar**.  
  
     Puede utilizar este menú contextual para proporcionar opciones o comandos adicionales a los desarrolladores, como mostrar un diseñador para la acción personalizada.  
  
13. En la barra de menús, elija **Ver**, **Resultados**.  
  
     Se abre la ventana **Resultados**.  
  
14. En el **Explorador de soluciones**, abra el menú contextual para el elemento **CustomAction1**, y después cambie su nombre a **MyCustomAction**.  
  
     En la ventana **Resultados** aparece un mensaje de confirmación.  Este mensaje lo escribe el controlador de eventos <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> que se definió en la clase `CustomActionProjectItemTypeProvider`.  Puede controlar este y otros eventos de elementos de proyecto para implementar el comportamiento personalizado cuando el desarrollador modifica el elemento de proyecto.  
  
#### Para probar la acción personalizada en SharePoint  
  
1.  En la instancia experimental de Visual Studio, abra el archivo Elements.xml que es un elemento secundario del elemento de proyecto **MyCustomAction**.  
  
2.  En el archivo Elements.xml, realice los cambios siguientes y guarde el archivo:  
  
    -   En el elemento `CustomAction`, establezca el atributo `Id` en un GUID o alguna otra cadena única como se muestra en el ejemplo siguiente:  
  
        ```  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   En el elemento `CustomAction`, establezca el atributo `Title` tal y como se muestra en el siguiente ejemplo:  
  
        ```  
        Title="SharePoint Developer Center"  
        ```  
  
    -   En el elemento `CustomAction`, establezca el atributo `Description` tal y como se muestra en el siguiente ejemplo:  
  
        ```  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   En el elemento `UrlAction`, establezca el atributo `Url` tal y como se muestra en el siguiente ejemplo:  
  
        ```  
        Url="http://msdn.microsoft.com/sharepoint/default.aspx"  
        ```  
  
3.  Elija la tecla F5.  
  
     La acción personalizada se empaqueta e implementa en el sitio de SharePoint que se especifica en la propiedad **URL del sitio** del proyecto.  El explorador web se abre en la página predeterminada de este sitio.  
  
    > [!NOTE]  
    >  Si aparece el cuadro de diálogo **Depuración de scripts deshabilitada**, elija el botón **Sí** para continuar depurando el proyecto.  
  
4.  En el menú **Acciones del sitio**, elija **Centro para desarrolladores de SharePoint**, compruebe que el explorador abre el sitio web http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx y luego cierre el explorador web.  
  
## Limpiar el equipo de desarrollo  
 Después de probar el elemento de proyecto, quite la plantilla de elemento de proyecto de la instancia experimental de Visual Studio.  
  
#### Para limpiar el equipo de desarrollo  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.  
  
2.  En la lista de extensiones, elija **Elemento proyecto acción personalizada** y, a continuación, **Desinstalar**.  
  
3.  En el cuadro de diálogo que aparece, elija el botón **Sí** para confirmar la desinstalación.  
  
4.  Elija el botón **Reiniciar ahora** para completar la desinstalación.  
  
5.  Cierre tanto la instancia experimental de Visual Studio como la instancia en la que se abre la solución CustomActionProjectItem.  
  
## Pasos siguientes  
 Después de completar este tutorial, puede agregar un asistente a la plantilla de elemento.  Cuando un usuario agrega un elemento de proyecto Acción personalizada a un proyecto de SharePoint, el asistente recopila información sobre la acción \(como su ubicación y la dirección URL a la que se va a navegar al elegirse la acción\) y agrega esta información al archivo Elements.xml del nuevo elemento de proyecto.  Para obtener más información, vea [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
## Vea también  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  