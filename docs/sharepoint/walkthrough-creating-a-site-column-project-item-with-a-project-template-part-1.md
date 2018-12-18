---
title: 'Tutorial: Crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 1 | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 56f50a3c50156cbd932fc7a7247fd96c4c6c2834
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296260"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Tutorial: Crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 1
  Los proyectos de SharePoint son contenedores para uno o más elementos de proyecto de SharePoint. Puede extender el sistema de proyectos de SharePoint en Visual Studio si crea sus propios tipos de elemento de proyecto de SharePoint y, a continuación, los asocia a una plantilla de proyecto. En este tutorial, definirá un tipo de elemento de proyecto para crear una columna de sitio y, a continuación, creará una plantilla de proyecto que se puede usar para crear un nuevo proyecto que contenga un elemento de proyecto de columnas de sitio.  
  
 En este tutorial se muestran las siguientes tareas:  
  
- Crear una extensión de Visual Studio que define un nuevo tipo de elemento de proyecto de SharePoint para una columna de sitio. El tipo de elemento de proyecto incluye una propiedad personalizada simple que aparece en el **propiedades** ventana.  
  
- Crear una plantilla de proyecto de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el elemento de proyecto.  
  
- Compilar un paquete de extensión de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (VSIX) para implementar la plantilla de proyecto y el ensamblado de la extensión.  
  
- Depurar y probar el elemento de proyecto.  
  
  Este es un tutorial independiente. Después de completar este tutorial, puede mejorar el elemento de proyecto si agrega un asistente a la plantilla de proyecto. Para obtener más información, consulte [Tutorial: crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
> [!NOTE]  
> Para una serie de flujos de trabajo de ejemplo, vea [ejemplos de flujo de trabajo de SharePoint](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:  
  
- Ediciones compatibles de Microsoft Windows, SharePoint y [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Este tutorial utiliza el **proyecto VSIX** plantilla en el SDK para crear un paquete VSIX para implementar el elemento de proyecto. Para obtener más información, consulte [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.  
  
- Columnas de sitio de SharePoint. Para obtener más información, consulte [columnas](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
- Plantillas de proyecto de Visual Studio. Para obtener más información, vea [Crear plantillas para proyectos y elementos en Visual Studio](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="create-the-projects"></a>Crear los proyectos
 Para completar este tutorial, debe crear tres proyectos:  
  
- Un proyecto VSIX. Este proyecto crea el paquete VSIX para implementar el elemento de proyecto de columnas de sitio y la plantilla de proyecto.  
  
- Un proyecto de plantilla de proyecto. Este proyecto crea una plantilla de proyecto que se puede usar para crear un nuevo proyecto de SharePoint que contiene el elemento de proyecto de columnas de sitio.  
  
- Un proyecto de biblioteca de clases. Este proyecto implementa una extensión de Visual Studio que define el comportamiento del elemento de proyecto de columnas de sitio.  
  
  Comience el tutorial creando ambos proyectos.  
  
#### <a name="to-create-the-vsix-project"></a>Para crear el proyecto VSIX  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.  
  
3.  En la parte superior de la **nuevo proyecto** diálogo cuadro, asegúrese de que **.NET Framework 4.5** se elige en la lista de versiones de .NET Framework.  
  
4.  Expanda el **Visual Basic** o **Visual C#** nodos y, a continuación, elija el **extensibilidad** nodo.  
  
    > [!NOTE]  
    >  El **extensibilidad** nodo está disponible solo si instala el SDK de Visual Studio. Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.  
  
5.  En la lista de plantillas de proyecto, elija **proyecto VSIX**.  
  
6.  En el **nombre** , escriba **SiteColumnProjectItem**y, a continuación, elija el **Aceptar** botón.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **SiteColumnProjectItem** proyecto a **el Explorador de soluciones**.  
  
#### <a name="to-create-the-project-template-project"></a>Para crear el proyecto de plantilla de proyecto  
  
1.  En **el Explorador de soluciones**, abra el menú contextual del nodo de solución, elija **agregar**y, a continuación, elija **nuevo proyecto**.  
  
2.  En la parte superior de la **nuevo proyecto** diálogo cuadro, asegúrese de que **.NET Framework 4.5** se elige en la lista de versiones de .NET Framework.  
  
3.  Expanda el **Visual C#** o **Visual Basic** nodo y, a continuación, elija el **extensibilidad** nodo.  
  
4.  En la lista de plantillas de proyecto, elija el **plantilla de proyecto de C#** o **plantilla de proyecto de Visual Basic** plantilla.  
  
5.  En el **nombre** , escriba **SiteColumnProjectTemplate**y, a continuación, elija el **Aceptar** botón.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **SiteColumnProjectTemplate** proyecto a la solución.  
  
6.  Elimine el archivo de código Class1 del proyecto.  
  
7.  Si creó un proyecto de Visual Basic, elimine también los siguientes archivos del proyecto:  
  
    -   *MyApplication.Designer.vb*  
  
    -   MyApplication.myapp  
  
    -   *Resources.Designer.vb*  
  
    -   *Resources.resx*  
  
    -   *Settings.Designer.vb*  
  
    -   Settings.settings  
  
#### <a name="to-create-the-extension-project"></a>Para crear la extensión de proyecto  
  
1.  En **el Explorador de soluciones**, abra el menú contextual del nodo de solución, elija **agregar**y, a continuación, elija **nuevo proyecto**.  
  
2.  En la parte superior de la **nuevo proyecto** diálogo cuadro, asegúrese de que **.NET Framework 4.5** se elige en la lista de versiones de .NET Framework.  
  
3.  Expanda el **Visual C#** o **Visual Basic** nodos, elija el **Windows** nodo y, a continuación, elija el **biblioteca de clases** plantilla.  
  
4.  En el **nombre** , escriba **ProjectItemTypeDefinition** y, a continuación, elija el **Aceptar** botón.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **ProjectItemTypeDefinition** proyecto a la solución y abre el archivo de código predeterminado Class1.  
  
5.  Elimine el archivo de código Class1 del proyecto.  
  
## <a name="configure-the-extension-project"></a>Configurar el proyecto de extensión
 Agregue los archivos de código y las referencias de ensamblado para configurar el proyecto de extensión.  
  
#### <a name="to-configure-the-project"></a>Para configurar el proyecto  
  
1.  En el proyecto ProjectItemTypeDefinition, agregue un archivo de código que se denomina **SiteColumnProjectItemTypeProvider**.  
  
2.  En la barra de menús, elija **Proyecto** > **Agregar referencia**.  
  
3.  En el **Administrador de referencias - ProjectItemTypeDefinition** cuadro de diálogo, expanda el **ensamblados** nodo, elija el **Framework** nodo y, a continuación, seleccione el Casilla System.ComponentModel.Composition.  
  
4.  Elija la **extensiones** nodo, seleccione la casilla de verificación situada junto al ensamblado Microsoft.VisualStudio.SharePoint y, a continuación, elija el **Aceptar** botón.  
  
## <a name="define-the-new-sharepoint-project-item-type"></a>Definir el nuevo tipo de elemento de proyecto de SharePoint
 Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> para definir el comportamiento del nuevo tipo de elemento de proyecto. Implemente esta interfaz para definir un nuevo tipo de elemento de proyecto todas las veces que desee.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Para definir el nuevo tipo de elemento de proyecto de SharePoint  
  
1.  En el **SiteColumnProjectItemTypeProvider** archivo de código, reemplace el código predeterminado con el código siguiente y, a continuación, guarde el archivo.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## <a name="create-a-visual-studio-project-template"></a>Crear una plantilla de proyecto de Visual Studio
 Al crear una plantilla de proyecto, permite que otros desarrolladores creen proyectos de SharePoint que contengan elementos de proyecto de columnas de sitio. Una plantilla de proyecto de SharePoint incluye los archivos necesarios para todos los proyectos en Visual Studio, como *.csproj* o *.vbproj* y *.vstemplate* así como archivos son específicos de proyectos de SharePoint. Para obtener más información, consulte [crear elementos de plantillas y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 En este procedimiento, creará un proyecto de SharePoint vacío para generar los archivos específicos de los proyectos de SharePoint. A continuación, agregue estos archivos al proyecto SiteColumnProjectTemplate para incluirlos en la plantilla que se genera a partir de este proyecto. También configura el archivo de proyecto SiteColumnProjectTemplate para especificar dónde aparece la plantilla de proyecto en el **nuevo proyecto** cuadro de diálogo.  
  
#### <a name="to-create-the-files-for-the-project-template"></a>Para crear los archivos de la plantilla de proyecto  
  
1. Inicie una segunda instancia de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenciales administrativas.  
  
2. Crear un proyecto de SharePoint 2010 que se denomina **BaseSharePointProject**.  
  
   > [!IMPORTANT]  
   >  En el **Asistente de personalización de SharePoint**, no seleccione la **implementar como solución de granja de servidores** botón de opción.  
  
3. Agregar un elemento de elemento vacío al proyecto y, a continuación, llame al elemento **Field1**.  
  
4. Guarde el proyecto y, a continuación, cierre la segunda instancia de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
5. En la instancia de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que tiene en la solución sitecolumnprojectitem **el Explorador de soluciones**, abra el menú contextual para el **SiteColumnProjectTemplate** nodo de proyecto, elija  **Agregar**y, a continuación, elija **elemento existente**.  
  
6. En el **Agregar elemento existente** cuadro de diálogo, abra la lista de extensiones de archivo y, a continuación, elija **todos los archivos (\*.\*)** .  
  
7. En el directorio que contiene el proyecto BaseSharePointProject, seleccione el archivo key.snk y, a continuación, elija el **agregar** botón.  
  
   > [!NOTE]  
   >  En este tutorial, la plantilla de proyecto que se crea usa el mismo archivo key.snk para firmar cada proyecto que se crea mediante la plantilla. Para obtener información sobre cómo ampliar este ejemplo para crear un archivo key.snk diferente para cada instancia de proyecto, vea [Tutorial: crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
8. Repita los pasos del 5 al 8 para agregar los archivos siguientes de las subcarpetas especificadas en el directorio de BaseSharePointProject:  
  
   - *\Field1\Elements.Xml*  
  
   - *\Field1\SharePointProjectItem.spdata*  
  
   - *\Features\Feature1\Feature1.Feature*  
  
   - *\Features\Feature1\Feature1.Template.Xml*  
  
   - *\Package\Package.Package*  
  
   - *\Package\Package.Template.Xml*  
  
     Agregue estos archivos directamente al proyecto SiteColumnProjectTemplate; no vuelva a crear las subcarpetas Field1, Features ni Package en el proyecto. Para obtener más información acerca de estos archivos, consulte [crear elementos de plantillas y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Para configurar el modo en que los desarrolladores detectan la plantilla de proyecto en el cuadro de diálogo Nuevo proyecto
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el **SiteColumnProjectTemplate** nodo de proyecto y, a continuación, elija **descargar el proyecto**. Si se le solicite guardar los cambios en los archivos, elija el **Sí** botón.  
  
2.  Abra el menú contextual para el **SiteColumnProjectTemplate** nodo nuevo y, a continuación, elija **editar SiteColumnProjectTemplate.csproj** o **editar SiteColumnProjectTemplate.vbproj**.  
  
3.  En el archivo de proyecto, busque el elemento `VSTemplate` siguiente.  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  Reemplace este elemento por el código XML siguiente.  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     El elemento `OutputSubPath` especifica las carpetas adicionales en la ruta de acceso en la que se crea la plantilla de proyecto al compilar el proyecto. Las carpetas especificadas aquí garantizan que la plantilla de proyecto estará disponible sólo cuando los clientes abran el **nuevo proyecto** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, elija el **2010**  nodo.  
  
5.  Guarde y cierre el archivo.  
  
6.  En **el Explorador de soluciones**, abra el menú contextual para el **SiteColumnProjectTemplate** del proyecto y, a continuación, elija **recargar el proyecto**.  
  
## <a name="edit-the-project-template-files"></a>Editar los archivos de plantilla de proyecto
 En el proyecto SiteColumnProjectTemplate, edite los archivos siguientes para definir el comportamiento de la plantilla de proyecto:  
  
- *AssemblyInfo.cs* o *AssemblyInfo.vb*  
  
- *Elements.Xml*  
  
- *SharePointProjectItem.spdata*  
  
- *Feature1.Feature*  
  
- *Package.Package*  
  
- *SiteColumnProjectTemplate.vstemplate*  
  
- *ProjectTemplate.csproj* o *ProjectTemplate.vbproj*  
  
  En los procedimientos siguientes, agregará parámetros reemplazables a algunos de estos archivos. Un parámetro reemplazable es un token que empieza y termina por el carácter del signo de dólar ($). Cuando un usuario emplea esta plantilla de proyecto para crear un proyecto, Visual Studio reemplaza automáticamente estos parámetros en el nuevo proyecto por valores específicos. Para obtener más información, consulte [parámetros reemplazables](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Para modificar el archivo AssemblyInfo.cs o AssemblyInfo.vb
  
1.  En el proyecto SiteColumnProjectTemplate, abra el *AssemblyInfo.cs* o *AssemblyInfo.vb* de archivo y, a continuación, agregue la siguiente instrucción al principio de ella:  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     Cuando el **solución en espacio aislado** propiedad de un proyecto de SharePoint se establece en **True**, Visual Studio agrega el <xref:System.Security.AllowPartiallyTrustedCallersAttribute> al archivo de código AssemblyInfo. Sin embargo, el archivo de código AssemblyInfo de la plantilla de proyecto no importa el espacio de nombres <xref:System.Security> de forma predeterminada. Debe agregar esta **mediante** o **importaciones** instrucción para evitar errores de compilación.  
  
2.  Guarde y cierre el archivo.  
  
#### <a name="to-edit-the-elementsxml-file"></a>Para modificar el archivo Elements.xml
  
1.  En el proyecto SiteColumnProjectTemplate, reemplace el contenido de la *Elements.xml* archivo con el siguiente código XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     El nuevo XML agrega un elemento `Field` que define el nombre de la columna de sitio, su tipo base y el grupo en el que se hace una lista de la columna de sitio en la galería. Para obtener más información sobre el contenido de este archivo, consulte [esquema de definición de campo](http://go.microsoft.com/fwlink/?LinkId=184290).  
  
2.  Guarde y cierre el archivo.  
  
#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Para editar el archivo SharePointProjectItem.spdata
  
1. En el proyecto SiteColumnProjectTemplate, reemplace el contenido de la *SharePointProjectItem.spdata* archivo con el siguiente código XML.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
     <Files>  
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
     </Files>   
   </ProjectItem>  
   ```  
  
    El nuevo XML realiza los cambios siguientes en el archivo:  
  
   - Cambia el atributo `Type` del elemento `ProjectItem` a la misma cadena que se pasa a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> en la definición del elemento de proyecto (la clase `SiteColumnProjectItemTypeProvider` que creó anteriormente en este tutorial).  
  
   - Quita los atributos `SupportedTrustLevels` y `SupportedDeploymentScopes` del elemento `ProjectItem`. Estos valores de atributo son innecesarios porque los niveles de confianza y los ámbitos de implementación se especifican en la clase `SiteColumnProjectItemTypeProvider` en el proyecto ProjectItemTypeDefinition.  
  
     Para obtener más información sobre el contenido de *.spdata* archivos, consulte [referencia de esquemas de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
2. Guarde y cierre el archivo.  
  
#### <a name="to-edit-the-feature1feature-file"></a>Para modificar el archivo Feature1.feature
  
1. En el proyecto SiteColumnProjectTemplate, reemplace el contenido de la *Feature1.feature* archivo con el siguiente código XML.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
            imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
            deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
     <projectItems>  
       <projectItemReference itemId="$guid2$" />  
     </projectItems>  
   </feature>  
   ```  
  
    El nuevo XML realiza los cambios siguientes en el archivo:  
  
   - Cambia los valores de los atributos `Id` y `featureId` del elemento `feature` a `$guid4$`.  
  
   - Cambia los valores del atributo `itemId` del elemento `projectItemReference` a `$guid2$`.  
  
     Para obtener más información acerca de *.feature* archivos, consulte [crear elementos de plantillas y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2. Guarde y cierre el archivo.  
  
#### <a name="to-edit-the-packagepackage-file"></a>Para modificar el archivo Package.package
  
1. En el proyecto SiteColumnProjectTemplate, reemplace el contenido de la *Package.package* archivo con el siguiente código XML.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
            Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
     <features>  
       <featureReference itemId="$guid4$" />  
     </features>  
   </package>  
   ```  
  
    El nuevo XML realiza los cambios siguientes en el archivo:  
  
   - Cambia los valores de los atributos `Id` y `solutionId` del elemento `package` a `$guid3$`.  
  
   - Cambia los valores del atributo `itemId` del elemento `featureReference` a `$guid4$`.  
  
     Para obtener más información acerca de *.package* archivos, consulte [crear elementos de plantillas y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2. Guarde y cierre el archivo.  
  
#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Para editar el archivo sitecolumnprojecttemplate.vstemplate
  
1. En el proyecto SiteColumnProjectTemplate, reemplace el contenido del archivo SiteColumnProjectTemplate.vstemplate por una de las siguientes secciones de XML.  
  
   -   Si está creando una plantilla de proyecto de Visual C#, use el XML siguiente.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
     <TemplateData>  
       <Name>Site Column</Name>  
       <Description>Creates a new site column in SharePoint</Description>  
       <FrameworkVersion>3.5</FrameworkVersion>  
       <ProjectType>CSharp</ProjectType>  
       <CreateNewFolder>true</CreateNewFolder>  
       <CreateInPlace>true</CreateInPlace>  
       <ProvideDefaultName>true</ProvideDefaultName>  
       <DefaultName>SiteColumn</DefaultName>  
       <LocationField>Enabled</LocationField>  
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
       <Icon>SiteColumnProjectTemplate.ico</Icon>  
       <SortOrder>1000</SortOrder>  
     </TemplateData>  
     <TemplateContent>  
       <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
   -   Si está creando una plantilla de proyecto de Visual Basic, use el XML siguiente.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
     <TemplateData>  
       <Name>Site Column</Name>  
       <Description>Creates a new site column in SharePoint</Description>  
       <FrameworkVersion>3.5</FrameworkVersion>  
       <ProjectType>VisualBasic</ProjectType>  
       <CreateNewFolder>true</CreateNewFolder>  
       <CreateInPlace>true</CreateInPlace>  
       <ProvideDefaultName>true</ProvideDefaultName>  
       <DefaultName>SiteColumn</DefaultName>  
       <LocationField>Enabled</LocationField>  
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
       <Icon>SiteColumnProjectTemplate.ico</Icon>  
       <SortOrder>1000</SortOrder>  
     </TemplateData>  
     <TemplateContent>  
       <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
    El nuevo XML realiza los cambios siguientes en el archivo:  
  
   - Establece el `Name` en el valor **columna de sitio**. (Este nombre aparece en el **nuevo proyecto** cuadro de diálogo).  
  
   - Agrega elementos `ProjectItem` para cada uno de los archivos que se incluyen en cada instancia de proyecto.  
  
   - Usa el espacio de nombres "<http://schemas.microsoft.com/developer/vstemplate/2005>". Otros archivos de proyecto en este uso de la solución el "<http://schemas.microsoft.com/developer/msbuild/2003>" espacio de nombres. Por consiguiente, los mensajes de advertencia del esquema XML se generarán, pero puede pasarlos por alto en este tutorial.  
  
     Para obtener más información sobre el contenido de *.vstemplate* archivos, consulte [Visual Studio Template Schema Reference](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
2. Guarde y cierre el archivo.  
  
#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Para editar el archivo projecttemplate.csproj o projecttemplate.vbproj
  
1.  En el proyecto SiteColumnProjectTemplate, reemplace el contenido de la *ProjectTemplate.csproj* archivo o *ProjectTemplate.vbproj* archivo con una de las siguientes secciones de XML.  
  
    -   Si está creando una plantilla de proyecto de Visual C#, use el XML siguiente.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  Si está creando una plantilla de proyecto de Visual Basic, use el XML siguiente.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     El nuevo XML realiza los cambios siguientes en el archivo:  
  
    -   Usa el elemento `TargetFrameworkVersion` para especificar .NET Framework 3.5, no 4.5.  
  
    -   Agrega los elementos `SignAssembly` y `AssemblyOriginatorKeyFile` para firmar el resultado del proyecto.  
  
    -   Agrega elementos `Reference` para las referencias de ensamblado usadas por los proyectos de SharePoint.  
  
    -   Agrega elementos para cada archivo de forma predeterminada en el proyecto, como *Elements.xml* y *SharePointProjectItem.spdata*.  
  
2.  Guarde y cierre el archivo.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Crear un paquete VSIX para implementar la plantilla de proyecto
 Para implementar la extensión, utilice el proyecto VSIX en el **SiteColumnProjectItem** solución para crear un paquete VSIX. Primero, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest incluido en el proyecto VSIX. A continuación, cree el paquete VSIX compilando la solución.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Para crear y configurar el paquete VSIX  
  
1.  En **el Explorador de soluciones**, en el **SiteColumnProjectItem** del proyecto, abra el archivo source.extension.vsixmanifest en el editor de manifiestos.  
  
     El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que requieren todos los paquetes VSIX. Para obtener más información acerca de este archivo, consulte [referencia de 1.0 del esquema de extensión de VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  En el **Product Name** , escriba **columna de sitio**.  
  
3.  En el **autor** , escriba **Contoso**.  
  
4.  En el **descripción** , escriba **proyecto de SharePoint para crear columnas de sitio**.  
  
5.  Elija la **activos** pestaña y, a continuación, elija el **New** botón.  
  
     El **Agregar nuevo activo** abre el cuadro de diálogo.  
  
6.  En el **tipo** elija **Microsoft.VisualStudio.ProjectTemplate**.  
  
    > [!NOTE]  
    >  Este valor corresponde al elemento `ProjectTemplate` del archivo extension.vsixmanifest. Este elemento identifica la subcarpeta del paquete VSIX que contiene la plantilla de proyecto. Para obtener más información, consulte [elemento ProjectTemplate (Esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)).  
  
7.  En el **origen** elija **un proyecto de la solución actual**.  
  
8.  En el **proyecto** lista y elija **SiteColumnProjectTemplate**y, a continuación, elija el **Aceptar** botón.  
  
9. Elija la **New** nuevamente en el botón.  
  
     El **Agregar nuevo activo** abre el cuadro de diálogo.  
  
10. En el **tipo** elija **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest. Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX. Para obtener más información, consulte [elemento MEFComponent (Esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
11. En el **origen** elija **un proyecto de la solución actual**.  
  
12. En el **proyecto** elija **ProjectItemTypeDefinition**y, a continuación, elija el **Aceptar** botón.  
  
13. En la barra de menús, elija **compilar** > **compilar solución**y, a continuación, asegúrese de que el proyecto se compila sin errores.  
  
## <a name="test-the-project-template"></a>Probar la plantilla de proyecto
 Ya puede probar la plantilla de proyecto. Primero, empiece a depurar la solución SiteColumnProjectItem en la instancia experimental de Visual Studio. A continuación, pruebe el **columna de sitio** proyecto en la instancia experimental de Visual Studio. Por último, compile y ejecute el proyecto de SharePoint para comprobar que la columna de sitio funciona del modo esperado.  
  
#### <a name="to-start-debugging-the-solution"></a>Para empezar a depurar la solución  
  
1.  Reinicie Visual Studio con credenciales administrativas y abra la solución SiteColumnProjectItem.  
  
2.  
  
3.  En el archivo de código SiteColumnProjectItemTypeProvider, agregue un punto de interrupción a la primera línea de código en el `InitializeType` método y, a continuación, elija el **F5** tecla para iniciar la depuración.  
  
     Visual Studio instala la extensión para %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Columna de sitio\1 .0 e inicia una instancia experimental de Visual Studio. Probará el elemento de proyecto en esta instancia de Visual Studio.  
  
#### <a name="to-test-the-project-in-visual-studio"></a>Para probar el proyecto en Visual Studio  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **archivo** > **New** > **proyecto**.  
  
2.  Expanda el **Visual C#** o **Visual Basic** nodo (dependiendo del lenguaje que admita la plantilla de proyecto), expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.  
  
3.  En la lista de plantillas de proyecto, elija el **columna de sitio** plantilla.  
  
4.  En el **nombre** , escriba **SiteColumnTest** y, a continuación, elija el **Aceptar** botón.  
  
     En **el Explorador de soluciones**, aparecerá un nuevo proyecto con un elemento de proyecto que se denomina **Field1**.  
  
5.  Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el `InitializeType` método y, a continuación, elija el **F5** tecla para continuar depurando el proyecto.  
  
6.  En **el Explorador de soluciones**, elija el **Field1** nodo y, a continuación, elija el **F4** clave.  
  
     El **propiedades** abre la ventana.  
  
7.  En la lista de propiedades, compruebe que la propiedad **ejemplo de propiedad** aparece.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>Para probar la columna de sitio de SharePoint  
  
1.  En **el Explorador de soluciones**, elija el **SiteColumnTest** nodo.  
  
2.  En el **propiedades** ventana, en el cuadro de texto que se encuentra junto a la **dirección URL del sitio** propiedad, escriba **http://localhost**.  
  
     Este paso especifica el sitio de SharePoint local en el equipo de desarrollo que desea usar para la depuración.  
  
    > [!NOTE]  
    >  El **dirección URL del sitio** propiedad está vacía de forma predeterminada porque la plantilla de proyecto de la columna de sitio no proporciona un Asistente para la recopilación de este valor cuando se crea el proyecto. Para obtener información sobre cómo agregar un asistente que pida al desarrollador este valor y, a continuación, configura esta propiedad en el nuevo proyecto, vea [Tutorial: crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
3.  Elija la tecla **F5**.  
  
     La columna de sitio se empaqueta e implementa en el sitio de SharePoint que se especifica en el **dirección URL del sitio** propiedad del proyecto. El explorador web se abre en la página predeterminada de este sitio.  
  
    > [!NOTE]  
    >  Si el **depuración de scripts deshabilitada** aparece el cuadro de diálogo, elija el **Sí** botón para continuar depurando el proyecto.  
  
4.  En el **acciones del sitio** menú, elija **configuración del sitio**.  
  
5.  En el **configuración del sitio** página, en el **galerías** lista, elija el **columnas de sitio** vínculo.  
  
6.  En la lista de columnas de sitio, compruebe que un **columnas personalizadas** grupo contiene una columna que se denomina **SiteColumnTest**.  
  
7.  Cierre el explorador web.  
  
## <a name="clean-up-the-development-computer"></a>Limpiar el equipo de desarrollo
 Cuando termine de probar el proyecto, quite la plantilla de proyecto de la instancia experimental de Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Para limpiar el equipo de desarrollo  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **herramientas** > **extensiones y actualizaciones**.  
  
     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.  
  
2.  En la lista de extensiones, elija el **columna de sitio** extensión y, a continuación, elija el **desinstalar** botón.  
  
3.  En el cuadro de diálogo que aparece, elija el **Sí** botón para confirmar que desea desinstalar la extensión.  
  
4.  Elija la **cerrar** botón para completar la desinstalación.  
  
5.  Cierre ambas instancias de Visual Studio (la instancia experimental y la instancia de Visual Studio en la que se abre la solución SiteColumnProjectItem).  
  
## <a name="next-steps"></a>Pasos siguientes
 Después de completar este tutorial, puede agregar un asistente a la plantilla de proyecto. Cuando un usuario crea un proyecto de columnas de sitio, el asistente pide al usuario la dirección URL del sitio que se va a usar para depurar, le pregunta si la nueva solución es de espacio aislado y configura el nuevo proyecto con esta información. El asistente también recopila información acerca de la columna (por ejemplo, el tipo base y el grupo en el que se muestra la columna en la Galería de la columna de sitio) y agrega esta información para el *Elements.xml* archivo en el nuevo proyecto. Para obtener más información, consulte [Tutorial: crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## <a name="see-also"></a>Vea también
 [Tutorial: Crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Definir tipos de elemento de proyecto de SharePoint personalizados](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Guardar datos en las extensiones del sistema del proyecto de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Asociar datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
