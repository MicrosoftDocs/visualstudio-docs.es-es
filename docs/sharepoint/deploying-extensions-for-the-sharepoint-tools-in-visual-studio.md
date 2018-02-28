---
title: "Extensiones de implementación para las herramientas de SharePoint en Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 80cc884e45d9db10f6552fa44e611e87b7b4f801
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="deploying-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Extensiones de implementación para las Herramientas de SharePoint en Visual Studio
  Para implementar una extensión de herramientas de SharePoint, cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) que contiene el ensamblado de extensión y cualquier otro archivo que desee distribuir con la extensión. Un paquete VSIX es un archivo comprimido que sigue el estándar Open Packaging Conventions (OPC). Los paquetes VSIX tienen la extensión VSIX.  
  
 Después de crear un paquete VSIX, otros usuarios pueden ejecutar el archivo .vsix para instalar la extensión. Cuando un usuario instala la extensión, todos los archivos se instalan en la carpeta %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Para implementar la extensión, puede cargar el paquete VSIX para la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) sitio Web, también puede distribuir el paquete a los clientes por otros medios, como el paquete en un recurso compartido de red o algún otro sitio Web de hospedaje.  
  
 Para obtener más información sobre cómo crear paquetes VSIX y su implementación a la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847), consulte [trasvase extensiones de Visual Studio](/visualstudio/extensibility/shipping-visual-studio-extensions).  
  
 Puede crear un paquete VSIX mediante la **proyecto VSIX** plantilla en Visual Studio, o bien puede crear manualmente un paquete VSIX.  
  
## <a name="using-vsix-projects-to-create-vsix-packages"></a>Usar proyectos VSIX para crear paquetes VSIX  
 Puede usar el **proyecto VSIX** plantilla proporcionada por el SDK de Visual Studio para crear paquetes VSIX para extensiones de herramientas de SharePoint. Usando un proyecto VSIX proporciona varias ventajas con respecto a la creación manual de un paquete VSIX:  
  
-   Al compilar el proyecto, Visual Studio genera automáticamente el paquete VSIX. Las tareas como agregar los archivos de implementación al paquete y crear el archivo de [Content_Types] .xml para el paquete se realizan automáticamente.  
  
-   Puede configurar el proyecto VSIX para incluir la salida de compilación de su proyecto de extensión y otros archivos, como plantillas de proyecto y plantillas de elementos, en el paquete VSIX.  
  
 Para obtener más información sobre el uso de un proyecto VSIX, vea [plantilla de proyecto de VSIX](/visualstudio/extensibility/vsix-project-template).  
  
### <a name="organizing-your-projects"></a>Organizar los proyectos  
 De forma predeterminada, proyectos VSIX solamente generan paquetes VSIX, no los ensamblados. Por lo tanto, normalmente no se implementa una extensión de herramientas de SharePoint en un proyecto VSIX. Suele funcionar con al menos dos proyectos:  
  
-   Un proyecto VSIX.  
  
-   Un proyecto de biblioteca de clases que implementa la extensión.  
  
 También puede trabajar con proyectos adicionales para determinados tipos de extensiones:  
  
-   Un proyecto de biblioteca de clases que implementa los comandos de SharePoint que utilizan la extensión. Para ver un tutorial que muestra este escenario, vea [Tutorial: Extender el Explorador de servidores para mostrar elementos de Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Un proyecto de plantilla de elemento o una plantilla de proyecto que crea una plantilla de elemento o una plantilla de proyecto, si la extensión define un nuevo tipo de elemento de proyecto de SharePoint. Para ver un tutorial que muestra este escenario, vea [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
-   Un proyecto de biblioteca de clases que implementa a un asistente personalizado para una plantilla de elemento o una plantilla de proyecto, si la extensión incluye una plantilla. Para ver un tutorial que muestra este escenario, vea [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
 Si incluye todos los proyectos en la misma solución de Visual Studio, puede modificar el archivo source.extension.vsixmanifest del proyecto VSIX para incluir el resultado de compilación de los proyectos de biblioteca de clase.  
  
### <a name="editing-the-vsix-manifest"></a>Editar el manifiesto de VSIX  
 Debe editar el archivo source.extension.vsixmanifest del proyecto VSIX para incluir las entradas para todos los elementos que se van a incluir en la extensión. Cuando se abre el archivo source.extension.vsixmanifest desde su menú contextual, el archivo aparece en un diseñador que proporciona una interfaz de usuario para editar el XML en el archivo. Para obtener más información, consulte [el Diseñador de manifiestos VSIX](/visualstudio/extensibility/vsix-manifest-designer).  
  
 Debe agregar entradas al archivo source.extension.vsixmanifest para los siguientes elementos:  
  
-   El ensamblado de la extensión.  
  
-   El ensamblado que implementa los comandos de SharePoint que utilizan la extensión.  
  
-   Las plantillas de proyecto o plantillas de elementos que están asociadas con la extensión.  
  
-   Un asistente personalizado para una plantilla que está asociado con la extensión.  
  
 Los procedimientos siguientes describen cómo agregar entradas al archivo .vsixmanifest para cada uno de estos elementos.  
  
##### <a name="to-include-the-extension-assembly"></a>Para incluir el ensamblado de extensión  
  
1.  En el proyecto VSIX, abra el menú contextual del archivo source.extension.vsixmanifest y, a continuación, elija **abrir**.  
  
     El archivo se abre en el diseñador  
  
2.  En el **activos** pestaña del editor, elija la **New** botón.  
  
     El **Agregar nuevo activo** abre el cuadro de diálogo.  
  
3.  En el **tipo** elija **Microsoft.VisualStudio.MefComponent**.  
  
4.  En el **origen** lista, siga uno de los siguientes pasos:  
  
    -   Si el ensamblado de extensión se compila desde un proyecto que se encuentra en la misma solución que el proyecto VSIX, elija **un proyecto de la solución actual**. En el **proyecto** lista, elija el nombre del proyecto.  
  
    -   Si el ensamblado de extensión se incluye como un archivo en el proyecto, elija **archivo en filesystem**. En el **ruta de acceso** lista, escriba la ruta de acceso completa al archivo de ensamblado de extensión o use la **examinar** botón para buscar y seleccione el archivo de ensamblado.  
  
5.  Elija el botón **Aceptar** .  
  
##### <a name="to-include-a-sharepoint-command-assembly"></a>Para incluir un ensamblado de comando de SharePoint  
  
1.  En el proyecto VSIX, abra el menú contextual del archivo source.extension.vsixmanifest y, a continuación, elija la **abrir** botón.  
  
     El archivo se abre en el diseñador.  
  
2.  En el **activos** sección del editor, elija la **New** botón.  
  
     El **Agregar nuevo activo** abre el cuadro de diálogo.  
  
3.  En el **tipo** cuadro, escriba **SharePoint.Commands.v4**.  
  
4.  En el **origen** lista, siga uno de los siguientes pasos:  
  
    -   Si el ensamblado de comando se compila desde un proyecto que se encuentra en la misma solución que el proyecto VSIX, elija **un proyecto de la solución actual**. En el **proyecto** lista, elija el nombre del proyecto.  
  
    -   Si el ensamblado de comando se incluye como un archivo en el proyecto, elija **archivo en filesystem**. En el **ruta de acceso** lista, escriba la ruta de acceso completa al archivo de ensamblado de extensión o use la **examinar** botón para buscar y seleccione el archivo de ensamblado.  
  
5.  Elija el botón **Aceptar** .  
  
##### <a name="to-include-a-template-that-you-create"></a>Para incluir una plantilla que se crea  
  
1.  En el proyecto VSIX, abra el menú contextual del archivo source.extension.vsixmanifest y, a continuación, elija la **abrir** botón.  
  
     El archivo se abre en el diseñador.  
  
2.  En el **activos** sección del editor, elija la **New** botón.  
  
     El **Agregar nuevo activo** abre el cuadro de diálogo.  
  
3.  En el **tipo** elija **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate**.  
  
4.  En el **origen** elija **un proyecto de la solución actual**.  
  
5.  En el **proyecto** lista, elija el nombre del proyecto y, a continuación, elija la **Aceptar** botón.  
  
6.  En **el Explorador de soluciones**, abra el menú contextual para el proyecto de plantilla de proyecto o una plantilla de elemento y, a continuación, elija **descargar el proyecto**.  
  
7.  Vuelva a abrir el menú contextual del nodo de proyecto y, a continuación, elija **editar***YourTemplateProjectName***.csproj** o **editar**  *YourTemplateProjectName***.vbproj**.  
  
8.  Busque el elemento `VSTemplate` siguiente en el archivo del proyecto.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. Reemplace este elemento por el código XML siguiente.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     El elemento `OutputSubPath` especifica las carpetas adicionales en la ruta de acceso en la que se crea la plantilla de proyecto al compilar el proyecto. Las carpetas especificadas aquí garantizan que la plantilla de elemento estará disponible sólo cuando los clientes abran el **Agregar nuevo proyecto** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, elija la **2010**  nodo.  
  
10. Guarde y cierre el archivo.  
  
11. En **el Explorador de soluciones**, abra el menú contextual para el proyecto de plantilla de proyecto o una plantilla de elemento y, a continuación, elija **recargar el proyecto**.  
  
##### <a name="to-include-a-template-that-you-create-manually"></a>Para incluir una plantilla que crea manualmente  
  
1.  En el proyecto VSIX, agregue una nueva carpeta para el proyecto para que contenga la plantilla.  
  
2.  En esta nueva carpeta, cree las siguientes subcarpetas y, a continuación, agregue el archivo de plantilla (.zip) para la *identificador de configuración regional* carpeta.  
  
     *YourTemplateFolder*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *Identificador de configuración regional*  
  
     *YourTemplateName*.zip  
  
     Por ejemplo, si tiene una plantilla de elemento denominada ContosoCustomAction.zip compatible con la configuración regional Inglés (Estados Unidos), la ruta de acceso completa podría ser ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip.  
  
3.  En **el Explorador de soluciones**, elija el archivo de plantilla (*YourTemplateName*.zip).  
  
4.  En el **propiedades** ventana, establezca el **acción de compilación** propiedad **contenido**.  
  
5.  Abra el menú contextual del archivo source.extension.vsixmanifest y, a continuación, elija **abiertos**.  
  
     El archivo se abre en el diseñador.  
  
6.  En el **activos** sección del editor, elija la **New** botón.  
  
     El **Agregar nuevo activo** abre el cuadro de diálogo.  
  
7.  En el **tipo** elija **Microsoft.VisualStudio.ItemTemplate** o **Microsoft.VisualStudio.ProjectTemplate**.  
  
8.  En el **origen** elija **archivo en filesystem**.  
  
9. En el **ruta de acceso** , escriba la ruta de acceso completa al ensamblado (por ejemplo, **ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip**, o usar el **examinar**botón para buscar y seleccionar el ensamblado y, a continuación, elija la **Aceptar** botón.  
  
##### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Para incluir a un Asistente para una plantilla de proyecto o elemento  
  
1.  En el proyecto VSIX, abra el menú contextual del archivo source.extension.vsixmanifest y, a continuación, elija **abrir**.  
  
     El archivo se abre en el diseñador.  
  
2.  En el **activos** sección del editor, elija la **New** botón.  
  
     El **Agregar nuevo activo** abre el cuadro de diálogo.  
  
3.  En el **tipo** elija **Microsoft.VisualStudio.Assembly**.  
  
4.  En el **origen** lista, siga uno de los siguientes pasos:  
  
    -   Si el ensamblado del asistente se compila desde un proyecto que se encuentra en la misma solución que el proyecto VSIX, elija **un proyecto de la solución actual**. En el **proyecto** lista, elija el nombre del proyecto.  
  
    -   Si el ensamblado del asistente se incluye como un archivo en el proyecto, elija **archivo en filesystem**. En el **ruta de acceso** campo, escriba la ruta de acceso completa al archivo de ensamblado o use la **examinar** botón para buscar y seleccionar el ensamblado.  
  
5.  Elija el botón **Aceptar** .  
  
### <a name="related-walkthroughs"></a>Tutoriales relacionados  
 En la tabla siguiente enumera los tutoriales que muestran cómo utilizar un proyecto VSIX para implementar diferentes tipos de extensiones de herramientas de SharePoint.  
  
|Tipo de extensión|Tutoriales relacionados|  
|--------------------|--------------------------|  
|Una extensión que incluye únicamente el ensamblado de extensión|[Tutorial: Extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Tutorial: Creación de una extensión de proyecto de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Tutorial: Llamar al modelo de objetos de cliente de SharePoint en una extensión del Explorador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|Una extensión que incluye los comandos de SharePoint|[Tutorial: Creación de un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Tutorial: Extender el Explorador de servidores para mostrar elementos web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Tutorial: Crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|Una extensión que incluye una plantilla de Visual Studio|[Tutorial: Crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Tutorial: Crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|Una extensión que incluye a un asistente de plantilla|[Tutorial: Crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Tutorial: Crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## <a name="creating-vsix-packages-manually"></a>Creación manual de los paquetes VSIX  
 Si desea crear manualmente el paquete VSIX para la extensión de herramientas de SharePoint, siga los pasos siguientes:  
  
1.  Cree el archivo extension.vsixmanifest y el archivo [Content_Types] .xml en una nueva carpeta. Para obtener más información, consulte [Anatomía de un paquete VSIX](/visualstudio/extensibility/anatomy-of-a-vsix-package).  
  
2.  En el Explorador de Windows, haga clic en la carpeta que contiene los dos archivos XML, haga clic en Enviar a y, a continuación, haga clic en carpeta comprimida (en zip). Cambie el nombre del archivo .zip resultante a Filename.vsix, donde nombreDeArchivo es el nombre del archivo redistribuible que instala el paquete.  
  
3.  Agregue el ensamblado de extensión al paquete VSIX. Si la extensión contiene un comando de SharePoint, agregue también el ensamblado que implementa el comando de SharePoint para el paquete VSIX.  
  
4.  Modifique el archivo extension.vsixmanifest:  
  
    -   Agregar un `Microsoft.VisualStudio.MefComponent` elemento bajo el `Assets` elemento y, después, establezca el valor del nuevo elemento a la ruta de acceso relativa del ensamblado que implementa la extensión en el paquete VSIX. Para obtener más información, consulte [elemento MEFComponent (Esquema VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
    -   Si la extensión contiene un comando de SharePoint que llama al modelo de objetos de servidor de SharePoint, agregue un `Microsoft.VisualStudio.Assembly` elemento bajo el `Assets` elemento. Establezca el valor del nuevo elemento en la ruta de acceso relativa del ensamblado que implementa el comando de SharePoint en el paquete VSIX. Para obtener más información, consulte [elemento activo (Esquema VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
    -   Si la extensión incluye una plantilla de proyecto o una plantilla de elemento, agregue un `ProjectTemplate` o `ItemTemplate` elemento bajo el `Assets` elemento. Establezca el valor del nuevo elemento en la ruta de acceso relativa de la carpeta que contiene la plantilla en el paquete VSIX. Para obtener más información, consulte [elemento ProjectTemplate (Esquema VSX)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1) y [elemento ItemTemplate (Esquema VSX)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
    -   Si la extensión contiene un asistente personalizado para una plantilla de proyecto o una plantilla de elemento, agregue un `Assembly` elemento bajo el `Assets` elemento. Establezca el valor del nuevo elemento en la ruta de acceso relativa del ensamblado en el paquete VSIX y, a continuación, establezca el `AssemblyName` atributo por el nombre completo del ensamblado (incluida la versión, referencia cultural y token de clave pública). Para obtener más información, consulte [elemento Dependency (Esquema VSX)](http://msdn.microsoft.com/en-us/1f63f60a-98ad-48ec-8e44-4eba383d3e37).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el contenido de un archivo extension.vsixmanifest para una extensión de herramientas de SharePoint. La extensión se implementa en un ensamblado que se denomina Contoso.ProjectExtension.dll. La extensión incluye un ensamblado de comando de SharePoint que se denomina Contoso.ExtensionCommands.dll y una plantilla de elementos en una carpeta que se denomina **elementos** en el paquete VSIX. En este ejemplo se da por supuesto que los dos ensamblados están en la misma carpeta que el archivo extension.vsixmanifest del paquete VSIX.  
  
```  
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">  
  <Metadata>  
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />  
    <DisplayName>CustomActionProjectItem</DisplayName>  
    <Description>Empty VSIX Project.</Description>  
  </Metadata>  
  <Installation>  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />  
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />  
  </Assets>  
</PackageManifest>  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Depuración de las extensiones para las Herramientas de SharePoint en Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  