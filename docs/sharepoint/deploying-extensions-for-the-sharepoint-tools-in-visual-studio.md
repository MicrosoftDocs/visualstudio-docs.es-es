---
title: Implementar extensiones para las herramientas de SharePoint en Visual Studio | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53e36d993e72da759c87e7d2d2f908818b3d9024
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580649"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Implementar extensiones para las herramientas de SharePoint en Visual Studio

Para implementar una extensión de herramientas de SharePoint, cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) que contenga el ensamblado de extensión y cualquier otro archivo que desee distribuir con la extensión. Un paquete VSIX es un archivo comprimido que sigue el estándar de convenciones de empaquetado abierto (OPC). Los paquetes VSIX tienen la extensión *. vsix* .

Después de crear un paquete VSIX, otros usuarios pueden ejecutar el archivo. VSIX para instalar la extensión. Cuando un usuario instala la extensión, todos los archivos se instalan en la carpeta%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions Para implementar la extensión, puede cargar el paquete VSIX en el sitio web de [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o puede distribuir el paquete a los clientes por otros medios, como hospedar el paquete en un recurso compartido de red o en algún otro sitio Web.

Para obtener más información sobre cómo crear paquetes VSIX e implementarlos en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/), vea [envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Puede crear un paquete VSIX mediante la plantilla de **Proyecto VSIX** en Visual Studio, o bien puede crear un paquete VSIX manualmente.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Usar proyectos VSIX para crear paquetes VSIX

Puede usar la plantilla de **Proyecto VSIX** que proporciona el SDK de Visual Studio para crear paquetes VSIX para las extensiones de herramientas de SharePoint. El uso de un proyecto VSIX proporciona varias ventajas sobre la creación manual de un paquete VSIX:

- Visual Studio genera automáticamente el paquete VSIX al compilar el proyecto. Las tareas como agregar los archivos de implementación al paquete y crear el archivo [Content_Types]. XML para el paquete se realizan automáticamente.

- Puede configurar el Proyecto VSIX para incluir la salida de la compilación del proyecto de extensión y otros archivos, como plantillas de proyecto y plantillas de elemento, en el paquete VSIX.

Para obtener más información sobre el uso de un proyecto VSIX, vea [plantilla de Proyecto VSIX](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Organice los proyectos

De forma predeterminada, los proyectos VSIX solo generan paquetes VSIX, no ensamblados. Por lo tanto, normalmente no se implementa una extensión de herramientas de SharePoint en un proyecto VSIX. Normalmente, se trabaja con al menos dos proyectos:

- Un proyecto VSIX.

- Proyecto de biblioteca de clases que implementa la extensión.

También puede trabajar con proyectos adicionales para determinados tipos de extensiones:

- Proyecto de biblioteca de clases que implementa los comandos de SharePoint que usa la extensión. Para ver un tutorial que muestra este escenario, vea [Tutorial: extender explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Plantilla de elemento o proyecto de plantilla de proyecto que crea una plantilla de elemento o una plantilla de proyecto, si la extensión define un nuevo tipo de elemento de proyecto de SharePoint. Para ver un tutorial que muestra este escenario, vea [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

- Proyecto de biblioteca de clases que implementa un asistente personalizado para una plantilla de elemento o una plantilla de proyecto, si la extensión incluye una plantilla. Para ver un tutorial que muestra este escenario, vea [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Si incluye todos los proyectos en la misma solución de Visual Studio, puede modificar el archivo source. Extension. vsixmanifest en el Proyecto VSIX para incluir la salida de la compilación de los proyectos de biblioteca de clases.

### <a name="edit-the-vsix-manifest"></a>Editar el manifiesto de VSIX

Debe editar el archivo source. Extension. vsixmanifest en el Proyecto VSIX para incluir entradas para todos los elementos que desee incluir en la extensión. Al abrir el archivo source. Extension. vsixmanifest desde su menú contextual, el archivo aparece en un diseñador que proporciona una interfaz de usuario para editar el XML en el archivo. Para obtener más información, vea [Diseñador de manifiestos VSIX](../extensibility/vsix-manifest-designer.md).

Debe agregar entradas al archivo source. Extension. vsixmanifest para los siguientes elementos:

- Ensamblado de la extensión.

- Ensamblado que implementa los comandos de SharePoint que usa la extensión.

- Todas las plantillas de proyecto o plantillas de elementos asociadas a la extensión.

- Un asistente personalizado para una plantilla que está asociada a la extensión.

En los procedimientos siguientes se describe cómo agregar entradas al archivo. vsixmanifest para cada uno de estos elementos.

#### <a name="to-include-the-extension-assembly"></a>Para incluir el ensamblado de extensión

1. En el Proyecto VSIX, abra el menú contextual del archivo source. Extension. vsixmanifest y, a continuación, elija **abrir**.

     El archivo se abre en el diseñador.

2. En la pestaña **activos** del editor, elija el botón **nuevo** .

     Se abre el cuadro de diálogo **Agregar nuevo activo** .

3. En la lista **tipo** , elija **Microsoft. VisualStudio. MefComponent**.

4. En la lista **origen** , realice uno de los pasos siguientes:

    - Si el ensamblado de extensión se compila desde un proyecto que está en la misma solución que el Proyecto VSIX, elija **un proyecto en la solución actual**. En la lista **proyecto** , elija el nombre del proyecto.

    - Si el ensamblado de extensión se incluye como un archivo en el proyecto, elija **archivo en sistema de archivos**. En la lista **ruta de acceso** , escriba la ruta de acceso completa al archivo de ensamblado de la extensión o use el botón **examinar** para buscar y elegir el archivo de ensamblado.

5. Elija el botón **Aceptar** .

#### <a name="to-include-a-sharepoint-command-assembly"></a>Para incluir un ensamblado de comandos de SharePoint

1. En el Proyecto VSIX, abra el menú contextual del archivo source. Extension. vsixmanifest y, a continuación, elija el botón **abrir** .

     El archivo se abre en el diseñador.

2. En la sección **activos** del editor, elija el botón **nuevo** .

     Se abre el cuadro de diálogo **Agregar nuevo activo** .

3. En el cuadro **tipo** , escriba **SharePoint. Commands. V4**.

4. En la lista **origen** , realice uno de los pasos siguientes:

    - Si el ensamblado de comandos se compila desde un proyecto que está en la misma solución que el Proyecto VSIX, elija **un proyecto en la solución actual**. En la lista **proyecto** , elija el nombre del proyecto.

    - Si el ensamblado de comandos se incluye como un archivo en el proyecto, elija **archivo en sistema de archivos**. En la lista **ruta de acceso** , escriba la ruta de acceso completa al archivo de ensamblado de la extensión o use el botón **examinar** para buscar y elegir el archivo de ensamblado.

5. Elija el botón **Aceptar** .

#### <a name="to-include-a-template-that-you-create"></a>Para incluir una plantilla que cree

1. En el Proyecto VSIX, abra el menú contextual del archivo source. Extension. vsixmanifest y, a continuación, elija el botón **abrir** .

     El archivo se abre en el diseñador.

2. En la sección **activos** del editor, elija el botón **nuevo** .

     Se abre el cuadro de diálogo **Agregar nuevo activo** .

3. En la lista **tipo** , elija **Microsoft. VisualStudio. ProjectTemplate** o **Microsoft. VisualStudio. ItemTemplate**.

4. En la lista **origen** , elija **un proyecto en la solución actual**.

5. En la lista **proyecto** , elija el nombre del proyecto y, a continuación, elija el botón **Aceptar** .

6. En **Explorador de soluciones**, abra el menú contextual para la plantilla de proyecto o el proyecto de plantilla de elemento y, a continuación, elija **descargar el proyecto**.

7. Vuelva a abrir el menú contextual del nodo del proyecto y, a continuación, elija **Editar**_YourTemplateProjectName_**. csproj** o **Editar**_YourTemplateProjectName_**. vbproj**.

8. Busque el elemento `VSTemplate` siguiente en el archivo del proyecto.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Reemplaza este elemento por el siguiente código XML.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     El elemento `OutputSubPath` especifica las carpetas adicionales en la ruta de acceso en la que se crea la plantilla de proyecto al compilar el proyecto. Las carpetas especificadas aquí garantizan que la plantilla de elementos solo estará disponible cuando los clientes abran el cuadro de diálogo **Agregar nuevo proyecto** , expandan el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

10. Guarde y cierre el archivo.

11. En **Explorador de soluciones**, abra el menú contextual para la plantilla de proyecto o el proyecto de plantilla de elemento y, a continuación, elija **volver a cargar el proyecto**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Para incluir una plantilla que cree manualmente

1. En el Proyecto VSIX, agregue una nueva carpeta al proyecto para que contenga la plantilla.

2. En esta nueva carpeta, cree las siguientes subcarpetas y, a continuación, agregue el archivo de plantilla (. zip) a la carpeta de ID. de *configuración regional* .

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *Identificador de configuración regional*

     *YourTemplateName*. zip

     Por ejemplo, si tiene una plantilla de elemento denominada ContosoCustomAction.zip que admite la configuración regional de inglés (Estados Unidos), la ruta de acceso completa podría estar *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3. En **Explorador de soluciones**, elija el archivo de plantilla (*YourTemplateName*. zip).

4. En la ventana **propiedades** , establezca la propiedad **acción de compilación** en **contenido**.

5. Abra el menú contextual del archivo source. Extension. vsixmanifest y, a continuación, elija **abrir**.

     El archivo se abre en el diseñador.

6. En la sección **activos** del editor, elija el botón **nuevo** .

     Se abre el cuadro de diálogo **Agregar nuevo activo** .

7. En la lista **tipo** , elija **Microsoft. VisualStudio. ItemTemplate** o **Microsoft. VisualStudio. ProjectTemplate**.

8. En la lista **origen** , elija **archivo en sistema de archivos**.

9. En el campo **ruta de acceso** , escriba la ruta de acceso completa al ensamblado (por ejemplo, *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*, o use el botón **examinar** para buscar y elegir el ensamblado y, a continuación, elija el botón **Aceptar** .

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Para incluir un asistente para una plantilla de proyecto o una plantilla de elemento

1. En el Proyecto VSIX, abra el menú contextual del archivo source. Extension. vsixmanifest y, a continuación, elija **abrir**.

     El archivo se abre en el diseñador.

2. En la sección **activos** del editor, elija el botón **nuevo** .

     Se abre el cuadro de diálogo **Agregar nuevo activo** .

3. En la lista **tipo** , elija **Microsoft. VisualStudio. Assembly**.

4. En la lista **origen** , realice uno de los pasos siguientes:

    - Si el ensamblado del asistente se compila desde un proyecto que está en la misma solución que el Proyecto VSIX, elija **un proyecto en la solución actual**. En la lista **proyecto** , elija el nombre del proyecto.

    - Si el ensamblado del asistente se incluye como un archivo en el proyecto, elija **archivo en sistema de archivos**. En el campo **ruta de acceso** , escriba la ruta de acceso completa al archivo de ensamblado o use el botón **examinar** para buscar y seleccionar el ensamblado.

5. Elija el botón **Aceptar** .

### <a name="related-walkthroughs"></a>Tutoriales relacionados

En la tabla siguiente se enumeran los tutoriales que muestran cómo usar un proyecto de VSIX para implementar distintos tipos de extensiones de herramientas de SharePoint.

|Tipo de extensión|Tutoriales relacionados|
|--------------------|--------------------------|
|Una extensión que solo incluye el ensamblado de extensión|[Tutorial: extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Tutorial: crear una extensión de proyecto de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Tutorial: llamar al modelo de objetos de cliente de SharePoint en una extensión de Explorador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Una extensión que incluye comandos de SharePoint|[Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Tutorial: extender Explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Una extensión que incluye una plantilla de Visual Studio|[Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Una extensión que incluye un asistente para plantillas|[Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Crear paquetes VSIX manualmente

Si desea crear manualmente el paquete VSIX para la extensión de herramientas de SharePoint, siga estos pasos:

1. Cree el archivo Extension. vsixmanifest y el archivo [Content_Types]. XML en una nueva carpeta. Para obtener más información, vea [anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md).

2. En el explorador de Windows, haga clic con el botón secundario en la carpeta que contiene los dos archivos XML, haga clic en enviar a y, a continuación, haga clic en carpeta comprimida (en zip). Cambie el nombre del archivo .zip resultante a Nombre de archivo.vsix, donde Nombre de archivo corresponde al nombre del archivo redistribuible que instala el paquete.

3. Agregue el ensamblado de extensión al paquete VSIX. Si la extensión incluye un comando de SharePoint, agregue también el ensamblado que implementa el comando de SharePoint al paquete VSIX.

4. Modifique el archivo Extension. vsixmanifest:

    - Agregue un `Microsoft.VisualStudio.MefComponent` elemento bajo el `Assets` elemento y, a continuación, establezca el valor del nuevo elemento en la ruta de acceso relativa del ensamblado que implementa la extensión en el paquete VSIX. Para obtener más información, vea [elemento MEFComponent (esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    - Si la extensión incluye un comando de SharePoint que llama al modelo de objetos de servidor para SharePoint, agregue un `Microsoft.VisualStudio.Assembly` elemento bajo el `Assets` elemento. Establezca el valor del nuevo elemento en la ruta de acceso relativa del ensamblado que implementa el comando de SharePoint en el paquete VSIX. Para obtener más información, vea [elemento asset (esquema VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

    - Si la extensión incluye una plantilla de proyecto o una plantilla de elemento, agregue un `ProjectTemplate` `ItemTemplate` elemento o bajo el `Assets` elemento. Establezca el valor del nuevo elemento en la ruta de acceso relativa de la carpeta que contiene la plantilla en el paquete VSIX. Para obtener más información, vea [elemento ProjectTemplate (esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) y [elemento ITEMTEMPLATE (esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    - Si la extensión incluye un asistente personalizado para una plantilla de proyecto o una plantilla de elemento, agregue un `Assembly` elemento bajo el `Assets` elemento. Establezca el valor del nuevo elemento en la ruta de acceso relativa del ensamblado en el paquete VSIX y, a continuación, establezca el `AssemblyName` atributo en el nombre completo del ensamblado (incluida la versión, la referencia cultural y el token de clave pública). Para obtener más información, vea [Dependency (elemento) (esquema VSX)](https://msdn.microsoft.com/1f63f60a-98ad-48ec-8e44-4eba383d3e37).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el contenido de un archivo Extension. vsixmanifest para una extensión de herramientas de SharePoint. La extensión se implementa en un ensamblado denominado Contoso.ProjectExtension.dll. La extensión incluye un ensamblado de comandos de SharePoint denominado Contoso.ExtensionCommands.dll y una plantilla de elemento en una carpeta denominada **ItemTemplates** en el paquete VSIX. En este ejemplo se da por supuesto que ambos ensamblados están en la misma carpeta que el archivo Extension. vsixmanifest del paquete VSIX.

```xml
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

## <a name="see-also"></a>Consulte también

- [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Extender el nodo conexiones de SharePoint en Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Depurar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
