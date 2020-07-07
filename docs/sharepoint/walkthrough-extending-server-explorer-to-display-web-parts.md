---
title: 'Tutorial: extender Explorador de servidores para mostrar elementos web | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e5221d1cce065a352051ca700cf0fc5ef4ae843
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015637"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Tutorial: extender Explorador de servidores para mostrar elementos Web
  En Visual Studio, puede usar el nodo **conexiones de SharePoint** de **Explorador de servidores** para ver los componentes de los sitios de SharePoint. Sin embargo, **Explorador de servidores** no muestra algunos componentes de forma predeterminada. En este tutorial, extenderá **Explorador de servidores** para que muestre la galería de elementos Web en cada sitio de SharePoint conectado.

 En este tutorial se muestran las siguientes tareas:

- La creación de una extensión de Visual Studio que extienda **Explorador de servidores** de las siguientes maneras:

  - La extensión agrega un nodo de la **Galería de elementos Web** en cada nodo del sitio de SharePoint en **Explorador de servidores**. Este nuevo nodo contiene nodos secundarios que representan cada elemento Web en la galería de elementos Web del sitio.

  - La extensión define un nuevo tipo de nodo que representa una instancia del elemento Web. Este nuevo tipo de nodo es la base para los nodos secundarios del nuevo nodo **Galería de elementos Web** . El nuevo tipo de nodo de elemento Web muestra información en la ventana **propiedades** sobre el elemento Web que representa. El tipo de nodo también incluye un elemento de menú contextual personalizado que puede usar como punto de partida para realizar otras tareas relacionadas con el elemento Web.

- Cree dos comandos personalizados de SharePoint a los que llama el ensamblado de extensión. Los comandos de SharePoint son métodos a los que pueden llamar los ensamblados de extensión para usar las API en el modelo de objetos de servidor para SharePoint. En este tutorial, creará comandos que recuperan información del elemento Web del sitio de SharePoint local en el equipo de desarrollo. Para obtener más información, consulte [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Compilar un paquete de extensión de Visual Studio (VSIX) para implementar la extensión.

- Depurar y probar la extensión.

> [!NOTE]
> Para obtener una versión alternativa de este tutorial que usa el modelo de objetos de cliente para SharePoint en lugar de su modelo de objetos de servidor, vea [Tutorial: llamar al modelo de objetos de cliente de SharePoint en una extensión de explorador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:

- Ediciones compatibles de Windows, SharePoint y Visual Studio.

- Visual Studio SDK. En este tutorial se usa la plantilla de **Proyecto VSIX** en el SDK para crear un paquete VSIX para implementar el elemento de proyecto. Para obtener más información, vea [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.

- Usar el modelo de objetos de servidor para SharePoint. Para obtener más información, vea [usar el modelo de objetos del lado servidor de SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- Elementos web en las soluciones de SharePoint. Para obtener más información, vea [información general sobre elementos Web](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Crear los proyectos
 Para completar este tutorial, debe crear tres proyectos:

- Un proyecto VSIX para crear el paquete VSIX para implementar la extensión.

- Proyecto de biblioteca de clases que implementa la extensión. Este proyecto debe tener como destino el .NET Framework 4,5.

- Proyecto de biblioteca de clases que define los comandos de SharePoint personalizados. Este proyecto debe tener como destino .NET Framework 3.5.

  Comience el tutorial creando ambos proyectos.

#### <a name="to-create-the-vsix-project"></a>Para crear el proyecto VSIX

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

3. En el cuadro de diálogo **nuevo proyecto** , expanda los nodos **Visual C#** o **Visual Basic** y, a continuación, elija el nodo **extensibilidad** .

    > [!NOTE]
    > El nodo **extensibilidad** solo está disponible si instala el SDK de Visual Studio. Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.

4. En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de la .NET Framework.

5. Elija la plantilla de **Proyecto VSIX** , asigne al proyecto el nombre **WebPartNode**y, a continuación, elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]agrega el proyecto **WebPartNode** a **Explorador de soluciones**.

#### <a name="to-create-the-extension-project"></a>Para crear la extensión de proyecto

1. En **Explorador de soluciones**, abra el menú contextual del nodo de la solución, elija **Agregar**y, a continuación, elija **nuevo proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , expanda el nodo **Visual C#** o **Visual Basic** nodo y, a continuación, elija el nodo **Windows** .

3. En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de la .NET Framework.

4. En la lista de plantillas de proyecto, elija **biblioteca de clases**, asigne al proyecto el nombre **ExtensiónNodoElementoWeb**y elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]agrega el proyecto **ExtensiónNodoElementoWeb** a la solución y abre el archivo de código predeterminado Class1.

5. Elimine el archivo de código Class1 del proyecto.

#### <a name="to-create-the-sharepoint-commands-project"></a>Para crear el proyecto Comandos de SharePoint

1. En **Explorador de soluciones**, abra el menú contextual del nodo de la solución, elija **Agregar**y, a continuación, elija **nuevo proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , expanda el nodo **Visual C#** o **Visual Basic** nodo y, a continuación, elija el nodo **Windows** .

3. En la parte superior del cuadro de diálogo, elija **.NET Framework 3,5** en la lista de versiones de la .NET Framework.

4. En la lista de plantillas de proyecto, elija **biblioteca de clases**, asigne al proyecto el nombre **WebPartCommands**y elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]agrega el proyecto **WebPartCommands** a la solución y abre el archivo de código predeterminado Class1.

5. Elimine el archivo de código Class1 del proyecto.

## <a name="configure-the-projects"></a>Configurar los proyectos
 Antes de escribir código para crear la extensión, debe agregar los archivos de código y las referencias de ensamblado, y configurar las opciones del proyecto.

#### <a name="to-configure-the-webpartnodeextension-project"></a>Para configurar el proyecto ExtensiónNodoElementoWeb

1. En el proyecto ExtensiónNodoElementoWeb, agregue cuatro archivos de código que tengan los siguientes nombres:

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. Abra el menú contextual del proyecto **ExtensiónNodoElementoWeb** y, a continuación, elija **Agregar referencia**.

3. En el cuadro de diálogo **Administrador de referencias-ExtensiónNodoElementoWeb** , elija la pestaña **marco de trabajo** y, a continuación, active la casilla para cada uno de los siguientes ensamblados:

    - System.ComponentModel.Composition

    - System.Windows.Forms

4. Elija la pestaña **extensiones** , active la casilla del ensamblado Microsoft. VisualStudio. SharePoint y, a continuación, elija el botón **Aceptar** .

5. En **Explorador de soluciones**, abra el menú contextual del nodo de proyecto **ExtensiónNodoElementoWeb** y, a continuación, elija **propiedades**.

     Se abrirá el **Diseñador de proyectos**.

6. Pulse la pestaña **Aplicación**.

7. En el cuadro **espacio de nombres predeterminado** (C#) o **espacio de nombres raíz** ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ), escriba **ServerExplorer. SharePointConnections. WebPartNode**.

#### <a name="to-configure-the-webpartcommands-project"></a>Para configurar el proyecto WebPartCommands

1. En el proyecto WebPartCommands, agregue un archivo de código denominado WebPartCommands.

2. En **Explorador de soluciones**, abra el menú contextual del nodo de proyecto **WebPartCommands** , elija **Agregar**y, a continuación, seleccione **elemento existente**.

3. En el cuadro de diálogo **Agregar elemento existente** , vaya a la carpeta que contiene los archivos de código del proyecto ExtensiónNodoElementoWeb y, a continuación, elija los archivos de código WebPartNodeInfo y WebPartCommandIds.

4. Elija la flecha situada junto al botón **Agregar** y, a continuación, elija **Agregar como vínculo** en el menú que aparece.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]agrega los archivos de código al proyecto WebPartCommands como vínculos. Como resultado, los archivos de código se encuentran en el proyecto ExtensiónNodoElementoWeb, pero el código de los archivos también se compila en el proyecto WebPartCommands.

5. Vuelva a abrir el menú contextual del proyecto **WebPartCommands** y elija **Agregar referencia**.

6. En el cuadro de diálogo **Administrador de referencias-WebPartCommands** , elija la pestaña **extensiones** , active la casilla para cada uno de los siguientes ensamblados y, a continuación, elija el botón **Aceptar** :

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

7. En **Explorador de soluciones**, vuelva a abrir el menú contextual del proyecto **WebPartCommands** y, a continuación, elija **propiedades**.

     Se abrirá el **Diseñador de proyectos**.

8. Pulse la pestaña **Aplicación**.

9. En el cuadro **espacio de nombres predeterminado** (C#) o **espacio de nombres raíz** ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ), escriba **ServerExplorer. SharePointConnections. WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Crear iconos para los nuevos nodos
 Cree dos iconos para la extensión de **Explorador de servidores** : un icono para el nuevo nodo de la **Galería de elementos Web** y otro icono para cada nodo de elemento Web secundario en el nodo **Galería de elementos** Web. Más adelante en este tutorial, escribirá código que asocia estos iconos con los nodos.

#### <a name="to-create-icons-for-the-nodes"></a>Para crear iconos para los nodos

1. En **Explorador de soluciones**, abra el menú contextual del proyecto **ExtensiónNodoElementoWeb** y, a continuación, elija **propiedades**.

2. Se abrirá el **Diseñador de proyectos**.

3. Elija la pestaña **recursos** y, a continuación, elija el **archivo este proyecto no contiene un archivo de recursos predeterminado. Haga clic aquí para crear un** vínculo.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]crea un archivo de recursos y lo abre en el diseñador.

4. En la parte superior del diseñador, elija la flecha situada junto al comando de menú **Agregar recurso** y, a continuación, elija **Agregar nuevo icono** en el menú que aparece.

5. En el cuadro de diálogo **Agregar nuevo recurso** , asigne al nuevo icono el nombre **WebPartsNode**y, a continuación, elija el botón **Agregar** .

     El icono nuevo se abre en el **Editor de imágenes**.

6. Edite la versión 16x16 del icono para que tenga un diseño que pueda reconocer fácilmente.

7. Abra el menú contextual de la versión 32x32 del icono y, a continuación, elija **eliminar tipo de imagen**.

8. Repita los pasos del 5 al 8 para agregar un segundo icono a los recursos del proyecto y asignar un nombre al **elemento Web**de este icono.

9. En **Explorador de soluciones**, en la carpeta **recursos** del proyecto **ExtensiónNodoElementoWeb** , abra el menú contextual de **WebPartsNode. ico**.

10. En la ventana **propiedades** , elija la flecha situada junto a **acción de compilación**y, a continuación, elija **recurso incrustado** en el menú que aparece.

11. Repita los dos últimos pasos para **WebPart. ico**.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Agregue el nodo de la galería de elementos Web a Explorador de servidores
 Cree una clase que agregue el nuevo nodo de la **Galería de elementos Web** a cada nodo del sitio de SharePoint. Para agregar el nuevo nodo, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaz. Implemente esta interfaz siempre que desee extender el comportamiento de un nodo existente en **Explorador de servidores**, como agregar un nodo secundario a un nodo.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Para agregar el nodo Galería de elementos Web a Explorador de servidores

1. En el proyecto ExtensiónNodoElementoWeb, abra el archivo de código SiteNodeExtension y, a continuación, pegue el código siguiente en él.

    > [!NOTE]
    > Después de agregar este código, el proyecto tendrá algunos errores de compilación, pero desaparecerán cuando agregue código en pasos posteriores.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definir un tipo de nodo que represente un elemento Web
 Cree una clase que defina un nuevo tipo de nodo que representa un elemento Web. Visual Studio usa este nuevo tipo de nodo para mostrar los nodos secundarios en el nodo de la **Galería de elementos Web** . Cada nodo secundario representa un único elemento Web en el sitio de SharePoint.

 Para definir el nuevo tipo de nodo, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaz. Implemente esta interfaz siempre que desee definir un nuevo tipo de nodo en **Explorador de servidores**.

#### <a name="to-define-the-web-part-node-type"></a>Para definir el tipo de nodo de elemento Web

1. En el proyecto ExtensiónNodoElementoWeb, abra el archivo de código WebPartNodeTypeProvder y, a continuación, pegue el código siguiente en él.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>Definir la clase de datos del elemento Web
 Defina una clase que contenga datos sobre un solo elemento Web en el sitio de SharePoint. Más adelante en este tutorial, creará un comando de SharePoint personalizado que recupera datos sobre cada elemento Web en el sitio y, a continuación, asigna los datos a las instancias de esta clase.

#### <a name="to-define-the-web-part-data-class"></a>Para definir la clase de datos del elemento Web

1. En el proyecto ExtensiónNodoElementoWeb, abra el archivo de código WebPartNodeInfo y, a continuación, pegue el código siguiente en él.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>Definición de los identificadores para los comandos de SharePoint
 Defina varias cadenas que identifiquen los comandos de SharePoint personalizados. Implementará estos comandos más adelante en este tutorial.

#### <a name="to-define-the-command-ids"></a>Para definir los identificadores de comando

1. En el proyecto ExtensiónNodoElementoWeb, abra el archivo de código WebPartCommandIds y, a continuación, pegue el código siguiente en él.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>Crear los comandos de SharePoint personalizados
 Cree comandos personalizados que llamen al modelo de objetos de servidor para SharePoint para recuperar datos sobre el elementos web en el sitio de SharePoint. Cada comando es un método al que se le ha <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> aplicado.

#### <a name="to-define-the-sharepoint-commands"></a>Para definir los comandos de SharePoint

1. En el proyecto WebPartCommands, abra el archivo de código WebPartCommands y, a continuación, pegue el código siguiente en él.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>Punto de control
 En este punto del tutorial, todo el código del nodo **Galería de elementos Web** y los comandos de SharePoint se encuentran ahora en los proyectos de. Compile la solución para asegurarse de que ambos proyectos se compilan sin errores.

#### <a name="to-build-the-solution"></a>Para compilar la solución

1. En la barra de menús, elija **Compilar** > **Compilar solución**.

    > [!WARNING]
    > En este momento, el proyecto WebPartNode puede tener un error de compilación porque el archivo de manifiesto VSIX no tiene un valor para Author. Este error desaparecerá cuando agregue un valor en pasos posteriores.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Crear un paquete VSIX para implementar la extensión
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX. En primer lugar, configure el paquete VSIX modificando el archivo source. Extension. vsixmanifest en el Proyecto VSIX. A continuación, cree el paquete VSIX compilando la solución.

#### <a name="to-configure-the-vsix-package"></a>Para configurar el paquete VSIX

1. En **Explorador de soluciones**, en el proyecto WebPartNode, abra el archivo **source. Extension. vsixmanifest** en el editor de manifiestos.

     El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que requieren todos los paquetes VSIX. Para obtener más información acerca de este archivo, vea [referencia de esquema de extensión VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. En el cuadro **nombre de producto** , escriba **nodo de la galería de elementos Web para explorador de servidores**.

3. En el cuadro **autor** , escriba **contoso**.

4. En el cuadro **Descripción** , escriba **Agregar un nodo de la galería de elementos web personalizado al nodo conexiones de SharePoint en explorador de servidores. Esta extensión usa un comando de SharePoint personalizado para llamar al modelo de objetos de servidor.**

5. Elija la pestaña **activos** del editor y, a continuación, elija el botón **nuevo** .

     Aparecerá el cuadro de diálogo **Agregar nuevo activo** .

6. En la lista **tipo** , elija **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest. Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX. Para obtener más información, vea [elemento MEFComponent (esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. En la lista **origen** , elija **un proyecto en la solución actual**.

8. En la lista **proyecto** , elija **ExtensiónNodoElementoWeb** y elija el botón **Aceptar** .

9. En el editor de manifiestos, vuelva a elegir el botón **nuevo** .

     Aparecerá el cuadro de diálogo **Agregar nuevo activo** .

10. En el cuadro **tipo** , escriba **SharePoint. Commands. V4**.

    > [!NOTE]
    > Este elemento especifica una extensión personalizada que desea incluir en la extensión de Visual Studio. Para obtener más información, vea [elemento asset (esquema VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

11. En la lista **origen** , elija el elemento de la lista **un proyecto en la solución actual** .

12. En la lista **proyecto** , elija **WebPartCommands**y elija el botón **Aceptar** .

13. En la barra de menús, **Elija compilar compilar**  >  **solución**y, a continuación, asegúrese de que la solución se compila sin errores.

14. Asegúrese de que la carpeta de salida de compilación del proyecto WebPartNode contiene ahora el archivo WebPartNode. vsix.

     De forma predeterminada, la carpeta de salida de la compilación es \bin\Debug, ubicada bajo la carpeta que contiene el archivo de proyecto.

## <a name="test-the-extension"></a>Prueba de la extensión
 Ahora está listo para probar el nuevo nodo de la **Galería de elementos Web** en **Explorador de servidores**. En primer lugar, inicie la depuración de la extensión en una instancia experimental de Visual Studio. A continuación, use el nuevo nodo **elementos Web** en la instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-start-debugging-the-extension"></a>Para comenzar a depurar la extensión

1. Reinicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenciales administrativas y, a continuación, abra la solución WebPartNode.

2. En el proyecto ExtensiónNodoElementoWeb, abra el archivo de código SiteNodeExtension y, a continuación, agregue un punto de interrupción a la primera línea de código en los `NodeChildrenRequested` `CreateWebPartNodes` métodos y.

3. Elija la tecla **F5** para iniciar la depuración.

     Visual Studio instala la extensión en la extensión de nodo de la galería de elementos de%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web para el servidor Explorer\1.0 e inicia una instancia experimental de Visual Studio. Probará el elemento de proyecto en esta instancia de Visual Studio.

#### <a name="to-test-the-extension"></a>Para probar la extensión

1. En la instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , en la barra de menús, elija **Ver**  >  **Explorador de servidores**.

2. Siga estos pasos si el sitio de SharePoint que desea usar para las pruebas no aparece en el nodo **conexiones de SharePoint** en **Explorador de servidores**:

    1. En **Explorador de servidores**, abra el menú contextual para **las conexiones de SharePoint**y, a continuación, elija **Agregar conexión**.

    2. En el cuadro de diálogo **Agregar conexión de SharePoint** , escriba la dirección URL del sitio de SharePoint al que desea conectarse y, a continuación, elija el botón **Aceptar** .

         Para especificar el sitio de SharePoint en el equipo de desarrollo, escriba **http://localhost** .

3. Expanda el nodo conexión de sitio (que muestra la dirección URL de su sitio) y, a continuación, expanda un nodo de sitio secundario (por ejemplo, **sitio de grupo**).

4. Compruebe que el código de la otra instancia de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se detiene en el punto de interrupción que estableció anteriormente en el `NodeChildrenRequested` método y, a continuación, presione **F5** para continuar depurando el proyecto.

5. En la instancia experimental de Visual Studio, compruebe que aparece un nuevo nodo denominado **Galería de elementos Web** en el nodo de sitio de nivel superior y, a continuación, expanda el nodo **Galería de elementos Web** .

6. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el `CreateWebPartNodes` método y, a continuación, elija la tecla **F5** para continuar depurando el proyecto.

7. En la instancia experimental de Visual Studio, compruebe que todos los elementos web del sitio conectado aparecen en el nodo **Galería de elementos Web** de **Explorador de servidores**.

8. En **Explorador de servidores**, abra el menú contextual de uno de los elementos Web y, a continuación, elija **propiedades**.

9. En la instancia de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que está depurando, compruebe que los detalles del elemento Web aparecen en la **ventana Propiedades** .

## <a name="uninstall-the-extension-from-visual-studio"></a>Desinstalar la extensión de Visual Studio
 Una vez finalizada la prueba de la extensión, desinstale la extensión de Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Para desinstalar la extensión

1. En la instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , en la barra de menús, elija **herramientas**  >  **extensiones y actualizaciones**.

     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

2. En la lista de extensiones, elija **extensión de nodo de la galería de elementos Web para explorador de servidores**y, a continuación, elija el botón **desinstalar** .

3. En el cuadro de diálogo que aparece, elija el botón **sí** para confirmar que desea desinstalar la extensión y, a continuación, elija el botón **reiniciar ahora** para completar la desinstalación.

4. Cierre ambas instancias de Visual Studio (la instancia experimental y la instancia de Visual Studio en la que está abierta la solución WebPartNode).

## <a name="see-also"></a>Consulte también
- [Extender el nodo conexiones de SharePoint en Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Tutorial: llamar al modelo de objetos de cliente de SharePoint en una extensión de Explorador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Editor de imágenes para iconos](/cpp/windows/image-editor-for-icons)
- [Crear un icono u otra imagen &#40;editor de imágenes para iconos&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
