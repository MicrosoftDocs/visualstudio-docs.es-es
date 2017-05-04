---
title: "Deploying Extensions for the SharePoint Tools in Visual Studio | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, deploying extensions"
ms.assetid: 69927d95-acdf-4fd8-ac43-28e9a7fa8a38
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Deploying Extensions for the SharePoint Tools in Visual Studio
  Para implementar una extensión de herramientas de SharePoint, cree un paquete de extensión de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) que contenga el ensamblado de la extensión y cualquier otro archivo que desee distribuir con ella.  Un paquete VSIX es un archivo comprimido que sigue la norma OPC \(Open Packaging Conventions\).  Los paquetes VSIX tienen la extensión .vsix.  
  
 Después de crear un paquete VSIX, otros usuarios pueden ejecutar el archivo .vsix para instalar la extensión.  Cuando un usuario instala la extensión, todos los archivos se instalan en la carpeta %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions.  Para implementar la extensión, puede cargar el paquete VSIX en el sitio web de [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) o bien puede distribuir el paquete a sus clientes por otros medios; por ejemplo, puede hospedar el paquete en un recurso compartido de red o en otro sitio web.  
  
 Para obtener más información sobre la creación de paquetes VSIX y su implementación en [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847), vea [Envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Puede crear un paquete VSIX con la plantilla **Proyecto VSIX** de Visual Studio o bien puede crearlo manualmente.  
  
## Usar proyectos VSIX para crear paquetes VSIX  
 Puede usar la plantilla **Proyecto VSIX** proporcionada por Visual Studio SDK para crear paquetes VSIX para las extensiones de herramientas de SharePoint.  Al utilizar un proyecto VSIX, cuenta con varias ventajas con respecto a la creación manual de un paquete VSIX:  
  
-   Al compilar el proyecto, Visual Studio genera automáticamente el paquete VSIX.  Las tareas como agregar los archivos de implementación al paquete y crear el archivo \[Content\_Types\].xml para el paquete se llevan a cabo de forma automática.  
  
-   Puede configurar el proyecto VSIX para incluir el resultado de la compilación del proyecto de extensión y otros archivos, como plantillas de proyecto y plantillas de elemento, en el paquete VSIX.  
  
 Para obtener más información sobre el uso de un proyecto VSIX, vea [Plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).  
  
### Organizar los proyectos  
 De forma predeterminada, los proyectos VSIX generan solo los paquetes VSIX, no los ensamblados.  Por consiguiente, normalmente una extensión de herramientas de SharePoint no se implementa en un proyecto VSIX.  Por lo general se trabaja con al menos dos proyectos:  
  
-   Un proyecto VSIX.  
  
-   Un proyecto de biblioteca de clases que implementa la extensión.  
  
 También puede trabajar con proyectos adicionales para ciertos tipos de extensiones:  
  
-   Un proyecto de biblioteca de clases que implementa cualquier comando de SharePoint usado por la extensión.  Para obtener un tutorial que muestra este escenario, vea [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Un proyecto de plantilla de elemento o plantilla de proyecto que crea una plantilla de elemento o una plantilla de proyecto, si la extensión define un nuevo tipo de elemento de proyecto de SharePoint.  Para obtener un tutorial que muestra este escenario, vea [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
-   Un proyecto de biblioteca de clases que implementa un asistente personalizado para una plantilla de elemento o una plantilla de proyecto, si la extensión incluye una plantilla.  Para obtener un tutorial que muestra este escenario, vea [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
 Si incluye todos los proyectos en la misma solución de Visual Studio, puede modificar el archivo source.extension.vsixmanifest del proyecto VSIX para que incluya el resultado de la compilación de los proyectos de biblioteca de clases.  
  
### Modificar el manifiesto de VSIX  
 Debe modificar el archivo source.extension.vsixmanifest del proyecto VSIX para incluir las entradas de todos los elementos que desea incluir en la extensión.  Al abrir el archivo source.extension.vsixmanifest del menú contextual, el archivo aparece en un diseñador que proporciona una interfaz de usuario para editar XML en el archivo.  Para obtener más información, vea [Diseñador de manifiestos VSIX](../extensibility/media/vsix-manifest-designer.png).  
  
 Debe agregar entradas al archivo source.extension.vsixmanifest para los siguientes elementos:  
  
-   El ensamblado de la extensión.  
  
-   El ensamblado que implementa los comandos de SharePoint que usa la extensión.  
  
-   Las plantillas de proyecto o plantillas de elemento asociadas a la extensión.  
  
-   Un asistente personalizado para una plantilla asociada a la extensión.  
  
 En los procedimientos siguientes se describe cómo agregar entradas al archivo .vsixmanifest para cada uno de estos elementos.  
  
##### Para incluir el ensamblado de la extensión  
  
1.  En el proyecto VSIX, abra el menú contextual para el archivo source.extension.vsixmanifest y, a continuación **Abrir**.  
  
     El archivo se abre en el diseñador  
  
2.  En la pestaña **Activos** de editor, elija el botón **Nuevo** .  
  
     El cuadro de diálogo **Agregar nuevo activo** abra.  
  
3.  En la lista **Tipo** , elija **Microsoft.VisualStudio.MefComponent**.  
  
4.  En la lista **Origen** , realice uno de los pasos siguientes:  
  
    -   Si el ensamblado de la extensión se compila desde un proyecto que se encuentra en la misma solución que el proyecto VSIX, elija **Un proyecto de la solución actual**.  En la lista **Proyecto** , elija el nombre del proyecto.  
  
    -   Si el ensamblado de la extensión se incluye como un archivo en el proyecto, elija **Archivo en filesystem**.  En la lista **Ruta de acceso** , escriba la ruta de acceso completa al archivo de ensamblado de la extensión, o utilice el botón **Examinar** para establecer y elija el archivo de ensamblado.  
  
5.  Elija el botón **Aceptar** .  
  
##### Para incluir un ensamblado de comando de SharePoint  
  
1.  En el proyecto VSIX, abra el menú contextual para el archivo source.extension.vsixmanifest, y después elija el botón **Abrir** .  
  
     El archivo se abre en el diseñador.  
  
2.  En la sección **Activos** de editor, elija el botón **Nuevo** .  
  
     El cuadro de diálogo **Agregar nuevo activo** abra.  
  
3.  En el cuadro **Tipo** , entre en **SharePoint.Commands.v4**.  
  
4.  En la lista **Origen** , realice uno de los pasos siguientes:  
  
    -   Si el ensamblado de comando se compila desde un proyecto que se encuentra en la misma solución que el proyecto VSIX, elija **Un proyecto de la solución actual**.  En la lista **Proyecto** , elija el nombre del proyecto.  
  
    -   Si el ensamblado de comando se incluye como un archivo en el proyecto, elija **Archivo en filesystem**.  En la lista **Ruta de acceso** , escriba la ruta de acceso completa al archivo de ensamblado de la extensión, o utilice el botón **Examinar** para establecer y elija el archivo de ensamblado.  
  
5.  Elija el botón **Aceptar** .  
  
##### Para incluir una plantilla creada  
  
1.  En el proyecto VSIX, abra el menú contextual para el archivo source.extension.vsixmanifest, y después elija el botón **Abrir** .  
  
     El archivo se abre en el diseñador.  
  
2.  En la sección **Activos** de editor, elija el botón **Nuevo** .  
  
     El cuadro de diálogo **Agregar nuevo activo** abra.  
  
3.  En la lista **Tipo** , elija **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate**.  
  
4.  En la lista **Origen** , elija **Un proyecto de la solución actual**.  
  
5.  En la lista **Proyecto** , elija el nombre del proyecto, y elija el botón **Aceptar** .  
  
6.  En **Explorador de soluciones**, abra el menú contextual para el proyecto de plantilla de proyecto o de la plantilla de elementos y, a continuación **Descargar el proyecto**.  
  
7.  Abrir el menú contextual para el nodo del proyecto de nuevo y, a continuación **Editar***TheTemplateProjectName***.csproj** o **Editar***TheTemplateProjectName***.vbproj**.  
  
8.  Busque el elemento `VSTemplate` siguiente en el archivo del proyecto.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. Reemplace este elemento con el XML siguiente.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     El elemento `OutputSubPath` especifica las carpetas adicionales en la ruta de acceso en la que se crea la plantilla de proyecto al compilar el proyecto.  Las carpetas especificadas aquí garantizan que la plantilla de elemento solo estará disponible cuando abren los clientes el cuadro de diálogo **Agregar nuevo proyecto** , expanda el nodo **SharePoint** , y después elija el nodo **2010** .  
  
10. Guarde y cierre el archivo.  
  
11. En **Explorador de soluciones**, abra el menú contextual para el proyecto de plantilla de proyecto o de la plantilla de elementos y, a continuación **Volver a cargar el proyecto**.  
  
##### Para incluir una plantilla creada manualmente  
  
1.  En el proyecto VSIX, agregue una nueva carpeta al proyecto donde se incluirá la plantilla.  
  
2.  En esta nueva carpeta, cree las siguientes subcarpetas y, a continuación, agregue el archivo de plantilla \(.zip\) a la carpeta *Id. de configuración regional*.  
  
     *YourTemplateFolder*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *Id. de configuración regional*  
  
     *YourTemplateName*.zip  
  
     Por ejemplo, si tiene una plantilla de elemento denominada ContosoCustomAction.zip compatible con la configuración regional de inglés \(Estados Unidos\), la ruta de acceso completa podría ser ItemTemplates\\SharePoint\\SharePoint14\\1033\\ContosoCustomAction .zip.  
  
3.  En **Explorador de soluciones**, elija el archivo de plantilla \(*YourTemplateName*.zip\).  
  
4.  En la ventana **Propiedades**, establezca la propiedad **Acción de compilación** en **Contenido**.  
  
5.  Abrir el menú contextual para el archivo source.extension.vsixmanifest y, a continuación **Abrir**.  
  
     El archivo se abre en el diseñador.  
  
6.  En la sección **Activos** de editor, elija el botón **Nuevo** .  
  
     El cuadro de diálogo **Agregar nuevo activo** abra.  
  
7.  En la lista **Tipo** , elija **Microsoft.VisualStudio.ItemTemplate** o **Microsoft.VisualStudio.ProjectTemplate**.  
  
8.  En la lista **Origen** , elija **Archivo en filesystem**.  
  
9. En el campo **Ruta de acceso** , escriba la ruta de acceso completa al ensamblado \(por ejemplo, **ItemTemplates \\SharePoint\\SharePoint14\\1033\\ContosoCustomAction .zip**, o utilice el botón **Examinar** para localizar y para elegir el ensamblado, y después elija el botón **Aceptar** .  
  
##### Para incluir un asistente para una plantilla de proyecto o una plantilla de elemento  
  
1.  En el proyecto VSIX, abra el menú contextual para el archivo source.extension.vsixmanifest y, a continuación **Abrir**.  
  
     El archivo se abre en el diseñador.  
  
2.  En la sección **Activos** de editor, elija el botón **Nuevo** .  
  
     El cuadro de diálogo **Agregar nuevo activo** abra.  
  
3.  En la lista **Tipo** , elija **Microsoft.VisualStudio.Assembly**.  
  
4.  En la lista **Origen** , realice uno de los pasos siguientes:  
  
    -   Si el ensamblado del asistente se compila desde un proyecto que se encuentra en la misma solución que el proyecto VSIX, elija **Un proyecto de la solución actual**.  En la lista **Proyecto** , elija el nombre del proyecto.  
  
    -   Si el ensamblado del asistente se incluye como un archivo en el proyecto, elija **Archivo en filesystem**.  En el campo **Ruta de acceso** , escriba la ruta de acceso completa al archivo de ensamblado, o utilice el botón **Examinar** para localizar y para elegir el ensamblado.  
  
5.  Elija el botón **Aceptar** .  
  
### Tutoriales relacionados  
 En la tabla siguiente se hace una lista de los tutoriales que muestran cómo usar un proyecto VSIX para implementar diferentes tipos de extensiones de herramientas de SharePoint.  
  
|Tipo de extensión|Tutoriales relacionados|  
|-----------------------|-----------------------------|  
|Una extensión que incluye solo el ensamblado de la extensión|[Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|Una extensión que incluye comandos de SharePoint|[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|Una extensión que incluye una plantilla de Visual Studio|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Tutorial: Crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|Una extensión que incluye un asistente de plantilla|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## Crear paquetes VSIX de forma manual  
 Si desea crear el paquete VSIX para su extensión de herramientas de SharePoint de forma manual, siga estos pasos:  
  
1.  Cree el archivo extension.vsixmanifest, el archivo \[Content\_Types\].xml y el archivo de paquete VSIX \(archivo .vsix\).  Para obtener más información, vea [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md) y [Procedimiento: empaquetar manualmente una extensión &#40;implementación VSIX&#41;](~/misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
2.  Agregue el ensamblado de la extensión al paquete VSIX.  Si la extensión incluye un comando de SharePoint, agregue también el ensamblado que lo implementa al paquete VSIX.  
  
3.  Modifique el archivo extension.vsixmanifest:  
  
    -   Agregue un elemento `Microsoft.VisualStudio.MefComponent` bajo el elemento `Assets` , y establezca el valor del nuevo elemento en la ruta de acceso relativa del ensamblado que implementa la extensión en el paquete VSIX.  Para obtener más información, vea [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/es-es/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
    -   Si la extensión incluye un comando de SharePoint que llama al modelo de objetos de servidor de SharePoint, agregue un elemento `Microsoft.VisualStudio.Assembly` bajo el elemento `Assets` .  Establezca el valor del nuevo elemento en la ruta de acceso relativa del ensamblado que implementa el comando de SharePoint en el paquete VSIX.  Para obtener más información, vea [Elemento de activo \(esquema VSX\)](http://msdn.microsoft.com/es-es/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
    -   Si la extensión incluye una plantilla de proyecto o una plantilla de elemento, agregue un elemento `ProjectTemplate` o `ItemTemplate` bajo el elemento `Assets` .  Establezca el valor del nuevo elemento en la ruta de acceso relativa de la carpeta que contiene la plantilla en el paquete VSIX.  Para obtener más información, vea [NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/es-es/87add64c-9dcd-495f-8815-209dab182cb1) y [NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/es-es/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
    -   Si la extensión incluye un asistente personalizado para una plantilla de proyecto o una plantilla de elemento, agregue un elemento `Assembly` bajo el elemento `Assets` .  Establezca el valor del nuevo elemento en la ruta de acceso relativa del ensamblado en el paquete VSIX, y establezca el atributo `AssemblyName` en el nombre del ensamblado completo \(incluidos versión, referencia cultural, y token de clave pública\).  Para obtener más información, vea [Elemento dependency \(esquema VSX\)](http://msdn.microsoft.com/es-es/1f63f60a-98ad-48ec-8e44-4eba383d3e37).  
  
### Ejemplo  
 En el ejemplo siguiente se muestra el contenido de un archivo extension.vsixmanifest para una extensión de herramientas de SharePoint.  La extensión se implementa en un ensamblado denominado Contoso.ProjectExtension.dll.  La extensión incluye un ensamblado de comando de SharePoint denominado Contoso.ExtensionCommands.dll y una plantilla de elemento bajo una carpeta que se denomina **ItemTemplates** en el paquete VSIX.  En este ejemplo se supone que ambos ensamblados se encuentran en la misma carpeta que el archivo extension.vsixmanifest del paquete VSIX.  
  
```  
<PackageManifest Version=”2.0.0” xmlns=”http://schemas.microsoft.com/developer/vsx-schema/2011”>  
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
  
## Vea también  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  