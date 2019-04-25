---
title: 'Tutorial: Extender el Explorador de servidores para mostrar elementos Web | Documentos de Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 29fcd40a2fc64a12ed7b29845b0a9f0ea3db5589
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040577"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Tutorial: Extender el Explorador de servidores para mostrar elementos web
  En Visual Studio, puede usar el **conexiones de SharePoint** nodo de **Explorador de servidores** para ver los componentes de sitios de SharePoint. Sin embargo, **Explorador de servidores** no muestra algunos componentes de forma predeterminada. En este tutorial, podrá ampliar **Explorador de servidores** para que se muestre la Galería de elementos Web en cada uno conectado el sitio de SharePoint.

 En este tutorial se muestran las siguientes tareas:

- Crear una extensión de Visual Studio que extiende **Explorador de servidores** de las maneras siguientes:

    - La extensión se agrega un **Galería de elementos Web** nodo en cada nodo de sitio de SharePoint en **Explorador de servidores**. Este nuevo nodo contiene nodos secundarios que representan cada elemento Web en la Galería de elementos Web en el sitio.

    - La extensión define un nuevo tipo de nodo que representa una instancia del elemento Web. Este nuevo tipo de nodo es la base para los nodos secundarios en la nueva **Galería de elementos Web** nodo. El nuevo tipo de nodo de elemento Web muestra información en el **propiedades** ventana acerca del elemento Web que representa. El tipo de nodo también incluye un elemento de menú contextual personalizado que puede usar como punto de partida para realizar otras tareas relacionadas con el elemento Web.

- Cree dos comandos de SharePoint personalizados que llama el ensamblado de extensión. Comandos de SharePoint son métodos que pueden llamarse mediante ensamblados de extensión para usar las API en el modelo de objetos de servidor de SharePoint. En este tutorial, creará los comandos que recuperan información del elemento Web desde el sitio de SharePoint local en el equipo de desarrollo. Para obtener más información, consulte [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Creación de un paquete de extensión de Visual Studio (VSIX) para implementar la extensión.

- Depurar y probar la extensión.

> [!NOTE]
>  Para obtener una versión alternativa de este tutorial que usa el modelo de objetos de cliente para SharePoint en lugar de su modelo de objetos de servidor, consulte [Tutorial: Llamar al modelo de objetos de cliente de SharePoint en una extensión de explorador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:

- Ediciones compatibles de Windows, SharePoint y Visual Studio.

- Visual Studio SDK. Este tutorial utiliza el **proyecto VSIX** plantilla en el SDK para crear un paquete VSIX para implementar el elemento de proyecto. Para obtener más información, consulte [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.

- Mediante el modelo de objetos de servidor para SharePoint. Para obtener más información, consulte [mediante el modelo de objetos de servidor de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).

- Elementos Web en las soluciones de SharePoint. Para obtener más información, consulte [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803).

## <a name="create-the-projects"></a>Crear los proyectos
 Para completar este tutorial, debe crear tres proyectos:

- Un proyecto VSIX para crear el paquete VSIX para implementar la extensión.

- Un proyecto de biblioteca de clases que implementa la extensión. Este proyecto debe tener como destino .NET Framework 4.5.

- Un proyecto de biblioteca de clases que define los comandos de SharePoint personalizados. Este proyecto debe tener como destino .NET Framework 3.5.

  Comience el tutorial creando ambos proyectos.

#### <a name="to-create-the-vsix-project"></a>Para crear el proyecto VSIX

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

3. En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos y, a continuación, elija el **extensibilidad** nodo.

    > [!NOTE]
    >  El **extensibilidad** nodo está disponible solo si instala el SDK de Visual Studio. Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.

4. En la parte superior del cuadro de diálogo, elija **.NET Framework 4.5** en la lista de versiones de .NET Framework.

5. Elija la **proyecto VSIX** plantilla, el nombre del proyecto **NodoElementoWeb**y, a continuación, elija el **Aceptar** botón.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **NodoElementoWeb** proyecto a **el Explorador de soluciones**.

#### <a name="to-create-the-extension-project"></a>Para crear la extensión de proyecto

1. En **el Explorador de soluciones**, abra el menú contextual del nodo de solución, elija **agregar**y, a continuación, elija **nuevo proyecto**.

2. En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** nodo o **Visual Basic** nodo y, a continuación, elegiría **Windows** nodo.

3. En la parte superior del cuadro de diálogo, elija **.NET Framework 4.5** en la lista de versiones de .NET Framework.

4. En la lista de plantillas de proyecto, elija **biblioteca de clases**, denomine el proyecto **ExtensiónNodoElementoWeb**y, a continuación, elija el **Aceptar** botón.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **ExtensiónNodoElementoWeb** proyecto a la solución y abre el archivo de código predeterminado Class1.

5. Elimine el archivo de código Class1 del proyecto.

#### <a name="to-create-the-sharepoint-commands-project"></a>Para crear el proyecto Comandos de SharePoint

1. En **el Explorador de soluciones**, abra el menú contextual del nodo de solución, elija **agregar**y, a continuación, elija **nuevo proyecto**.

2. En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** nodo o **Visual Basic** nodo y, a continuación, elija el **Windows** nodo.

3. En la parte superior del cuadro de diálogo, elija **.NET Framework 3.5** en la lista de versiones de .NET Framework.

4. En la lista de plantillas de proyecto, elija **biblioteca de clases**, denomine el proyecto **WebPartCommands**y, a continuación, elija el **Aceptar** botón.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **WebPartCommands** proyecto a la solución y abre el archivo de código predeterminado Class1.

5. Elimine el archivo de código Class1 del proyecto.

## <a name="configure-the-projects"></a>Configurar los proyectos
 Antes de escribir código para crear la extensión, debe agregar referencias a ensamblados y archivos de código y configurar la configuración del proyecto.

#### <a name="to-configure-the-webpartnodeextension-project"></a>Para configurar el proyecto ExtensiónNodoElementoWeb

1. En el proyecto ExtensiónNodoElementoWeb, agregue cuatro archivos de código que tienen los nombres siguientes:

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. Abra el menú contextual para el **ExtensiónNodoElementoWeb** del proyecto y, a continuación, elija **Agregar referencia**.

3. En el **Administrador de referencias - ExtensiónNodoElementoWeb** diálogo cuadro, elija el **Framework** pestaña y, a continuación, seleccione la casilla de verificación para cada uno de los siguientes ensamblados:

    - System.ComponentModel.Composition

    - System.Windows.Forms

4. Elija la **extensiones** , seleccione la casilla de verificación para el ensamblado Microsoft.VisualStudio.SharePoint y, a continuación, elija el **Aceptar** botón.

5. En **el Explorador de soluciones**, abra el menú contextual para el **ExtensiónNodoElementoWeb** nodo de proyecto y, a continuación, elija **propiedades**.

     Se abrirá el **Diseñador de proyectos**.

6. Pulse la pestaña **Aplicación**.

7. En el **espacio de nombres predeterminado** cuadro (C#) o **espacio de nombres raíz** cuadro ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), escriba **ServerExplorer.SharePointConnections.NodoElementoWeb**.

#### <a name="to-configure-the-webpartcommands-project"></a>Para configurar el proyecto webpartcommands

1. En el proyecto WebPartCommands, agregue un archivo de código denominado WebPartCommands.

2. En **el Explorador de soluciones**, abra el menú contextual para el **WebPartCommands** nodo de proyecto, elija **agregar**y, a continuación, elija **elemento existente**.

3. En el **Agregar elemento existente** cuadro de diálogo, vaya a la carpeta que contiene los archivos de código del proyecto ExtensiónNodoElementoWeb y, a continuación, elija los archivos de código WebPartCommandIds y WebPartNodeInfo.

4. Elija la flecha situada junto a la **agregar** botón y, a continuación, elija **agregar como vínculo** en el menú que aparece.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega los archivos de código al proyecto WebPartCommands como vínculos. Como resultado, los archivos de código se encuentran en el proyecto ExtensiónNodoElementoWeb, pero también se compilan el código en los archivos en el proyecto WebPartCommands.

5. Abra el menú contextual para el **WebPartCommands** nuevo proyecto y elija **Agregar referencia**.

6. En el **Administrador de referencias - WebPartCommands** diálogo cuadro, elija el **extensiones** , seleccione la casilla de verificación para cada uno de los siguientes ensamblados y, a continuación, elija el **Aceptar** botón:

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

7. En **el Explorador de soluciones**, abra el menú contextual para el **WebPartCommands** proyecto nuevo y, a continuación, elija **propiedades**.

     Se abrirá el **Diseñador de proyectos**.

8. Pulse la pestaña **Aplicación**.

9. En el **espacio de nombres predeterminado** cuadro (C#) o **espacio de nombres raíz** cuadro ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), escriba **ServerExplorer.SharePointConnections.NodoElementoWeb**.

## <a name="create-icons-for-the-new-nodes"></a>Crear iconos para los nuevos nodos
 Cree dos iconos para el **Explorador de servidores** extensión: un icono para el nuevo **Galería de elementos Web** nodo y otro icono para cada nodo secundario del elemento Web la **Galería de elementos Web** nodo. Más adelante en este tutorial, escribirá código que asocie estos iconos a los nodos.

#### <a name="to-create-icons-for-the-nodes"></a>Para crear iconos para los nodos

1. En **el Explorador de soluciones**, abra el menú contextual para el **ExtensiónNodoElementoWeb** del proyecto y, a continuación, elija **propiedades**.

2. Se abrirá el **Diseñador de proyectos**.

3. Elija la **recursos** pestaña y, a continuación, elija el **este proyecto no contiene un archivo de recursos predeterminado. Haga clic aquí para crear una** vínculo.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea un archivo de recursos y lo abre en el diseñador.

4. En la parte superior del diseñador, elija la flecha situada junto a la **Agregar recurso** menú de comandos y, a continuación, elija **Agregar nuevo icono** en el menú que aparece.

5. En el **Agregar nuevo recurso** cuadro de diálogo, el nombre del nuevo icono **WebPartsNode**y, a continuación, elija el **agregar** botón.

     El nuevo icono se abre en el **Editor de imágenes**.

6. Editar la versión 16 x 16 del icono para que tenga un diseño que pueda reconocer fácilmente.

7. Abra el menú contextual para la versión de 32 x 32 del icono y, a continuación, elija **Eliminar tipo de imagen**.

8. Repita los pasos 5 a 8 para agregar un segundo icono a los recursos del proyecto y el nombre de este icono **WebPart**.

9. En **el Explorador de soluciones**, en el **recursos** carpeta para el **ExtensiónNodoElementoWeb** de proyecto, abra el menú contextual para **NodoElementoWeb.ico**.

10. En el **propiedades** ventana, elija la flecha situada junto a **acción de compilación**y, a continuación, elija **recurso incrustado** en el menú que aparece.

11. Repita los dos últimos pasos para **ElementoWeb.ico**.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Agregar el nodo de la Galería de elementos Web al explorador de servidores
 Cree una clase que agrega el nuevo **Galería de elementos Web** nodo para cada nodo de sitio de SharePoint. Para agregar el nuevo nodo, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaz. Implemente esta interfaz cuando desee extender el comportamiento de un nodo existente en **Explorador de servidores**, como agregar un nodo secundario a un nodo.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Para agregar el nodo de la Galería de elementos Web al explorador de servidores

1. En el proyecto ExtensiónNodoElementoWeb, abra el archivo de código SiteNodeExtension y, a continuación, pegue el código siguiente en él.

    > [!NOTE]
    >  Después de agregar este código, el proyecto tendrá algunos errores de compilación, pero desaparecerán cuando agregue código en pasos posteriores.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definir un tipo de nodo que representa un elemento web
 Cree una clase que define un nuevo tipo de nodo que representa un elemento Web. Visual Studio usa este nuevo tipo de nodo para mostrar los nodos secundarios bajo el **Galería de elementos Web** nodo. Cada nodo secundario representa un único elemento Web en el sitio de SharePoint.

 Para definir el nuevo tipo de nodo, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaz. Implemente esta interfaz siempre que desee definir un nuevo tipo de nodo en **Explorador de servidores**.

#### <a name="to-define-the-web-part-node-type"></a>Para definir el tipo de nodo de elemento web

1. En el proyecto ExtensiónNodoElementoWeb, abra el archivo de código WebPartNodeTypeProvder y, a continuación, pegue el código siguiente en él.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>Definir la clase de datos del elemento web
 Defina una clase que contiene datos sobre un único elemento Web en el sitio de SharePoint. Más adelante en este tutorial, creará un comando de SharePoint personalizado que recupera datos sobre cada elemento Web en el sitio y, a continuación, asigna los datos a instancias de esta clase.

#### <a name="to-define-the-web-part-data-class"></a>Para definir la clase de datos del elemento web

1. En el proyecto ExtensiónNodoElementoWeb, abra el archivo de código WebPartNodeInfo y, a continuación, pegue el código siguiente en él.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>Definir los identificadores para los comandos de SharePoint
 Definir varias cadenas que identifican los comandos de SharePoint personalizados. Más adelante en este tutorial, implementará estos comandos.

#### <a name="to-define-the-command-ids"></a>Para definir los identificadores de comando

1. En el proyecto ExtensiónNodoElementoWeb, abra el archivo de código WebPartCommandIds y, a continuación, pegue el código siguiente en él.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>Crear los comandos de SharePoint personalizados
 Crear comandos personalizados que llamen al modelo de objetos de servidor de SharePoint recuperar datos sobre los elementos Web en el sitio de SharePoint. Cada comando es un método que tiene el <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> aplicado a él.

#### <a name="to-define-the-sharepoint-commands"></a>Para definir los comandos de SharePoint

1. En el proyecto WebPartCommands, abra el archivo de código WebPartCommands y, a continuación, pegue el código siguiente en él.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>Punto de control
 En este punto del tutorial, todo el código para el **Galería de elementos Web** nodo y los comandos de SharePoint están ahora en los proyectos. Compile la solución para asegurarse de que ambos proyectos se compilan sin errores.

#### <a name="to-build-the-solution"></a>Para compilar la solución

1. En la barra de menús, elija **Compilar** > **Compilar solución**.

    > [!WARNING]
    >  En este momento, el proyecto NodoElementoWeb puede tener un error de compilación porque el archivo de manifiesto de VSIX no tiene un valor de autor. Este error desaparecerá cuando se agrega un valor en pasos posteriores.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Crear un paquete VSIX para implementar la extensión
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX. En primer lugar, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest del proyecto VSIX. A continuación, cree el paquete VSIX compilando la solución.

#### <a name="to-configure-the-vsix-package"></a>Para configurar el paquete VSIX

1. En **el Explorador de soluciones**, bajo el proyecto NodoElementoWeb, abra el **source.extension.vsixmanifest** archivo en el editor de manifiestos.

     El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que requieren todos los paquetes VSIX. Para obtener más información acerca de este archivo, consulte [referencia de 1.0 del esquema de extensión de VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. En el **Product Name** , escriba **nodo Galería de elementos Web Explorador de servidores**.

3. En el **autor** , escriba **Contoso**.

4. En el **descripción** , escriba **agrega un nodo de la Galería de elementos Web personalizados en el nodo Conexiones de SharePoint en el Explorador de servidores. Esta extensión utiliza un comando de SharePoint personalizado para llamar al modelo de objetos de servidor.**

5. Elija la **activos** pestaña del editor y, a continuación, elija el **New** botón.

     El **Agregar nuevo activo** aparece el cuadro de diálogo.

6. En el **tipo** elija **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    >  Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest. Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX. Para obtener más información, consulte [elemento MEFComponent (Esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. En el **origen** elija **un proyecto de la solución actual**.

8. En el **proyecto** elija **ExtensiónNodoElementoWeb** y, a continuación, elija el **Aceptar** botón.

9. En el editor de manifiestos, elija el **New** nuevamente en el botón.

     El **Agregar nuevo activo** aparece el cuadro de diálogo.

10. En el **tipo** , escriba **SharePoint.Commands.v4**.

    > [!NOTE]
    >  Este elemento especifica una extensión personalizada que se va a incluir en la extensión de Visual Studio. Para obtener más información, consulte [elemento activo (Esquema VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

11. En el **origen** lista, elija el **un proyecto de la solución actual** elemento de lista.

12. En el **proyecto** elija **WebPartCommands**y, a continuación, elija el **Aceptar** botón.

13. En la barra de menús, elija **compilar** > **compilar solución**y, a continuación, asegúrese de que la solución se compila sin errores.

14. Asegúrese de que la carpeta de salida de compilación del proyecto NodoElementoWeb contiene ahora el archivo WebPartNode.vsix.

     De forma predeterminada, la carpeta de salida de la compilación es \bin\Debug, ubicada bajo la carpeta que contiene el archivo de proyecto.

## <a name="test-the-extension"></a>Probar la extensión
 Ahora está listo para probar la nueva **Galería de elementos Web** nodo **Explorador de servidores**. Primero, empiece a depurar la extensión en una instancia experimental de Visual Studio. A continuación, use la nueva **elementos Web** nodo en la instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

#### <a name="to-start-debugging-the-extension"></a>Para comenzar a depurar la extensión

1. Reiniciar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenciales administrativas y, a continuación, abra la solución NodoElementoWeb.

2. En el proyecto ExtensiónNodoElementoWeb, abra el archivo de código SiteNodeExtension y, a continuación, agregue un punto de interrupción a la primera línea de código en el `NodeChildrenRequested` y `CreateWebPartNodes` métodos.

3. Elija la **F5** tecla para iniciar la depuración.

     Visual Studio instala la extensión a %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web extensión del nodo de la Galería de elementos de servidor Explorer\1.0 e inicia una instancia experimental de Visual Studio. Probará el elemento de proyecto en esta instancia de Visual Studio.

#### <a name="to-test-the-extension"></a>Para probar la extensión

1. En la instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], en la barra de menús, elija **vista** > **Explorador de servidores**.

2. Realice los pasos siguientes si no aparece el sitio de SharePoint que desea usar para las pruebas en el **conexiones de SharePoint** nodo **Explorador de servidores**:

    1. En **Explorador de servidores**, abra el menú contextual para **conexiones de SharePoint**y, a continuación, elija **Agregar conexión**.

    2. En el **Agregar conexión de SharePoint** diálogo cuadro, escriba la dirección URL del sitio de SharePoint a la que desea conectarse y, a continuación, elija el **Aceptar** botón.

         Para especificar el sitio de SharePoint en el equipo de desarrollo, escriba **http://localhost**.

3. Expanda el nodo de conexión de sitio (que muestra la dirección URL del sitio) y, a continuación, expanda un nodo de sitio secundario (por ejemplo, **Team Site**).

4. Compruebe que el código de la otra instancia de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se detiene en el punto de interrupción que estableció anteriormente en el `NodeChildrenRequested` método y, a continuación, elija **F5** para continuar depurando el proyecto.

5. En la instancia experimental de Visual Studio, compruebe que un nuevo nodo denominado **Galería de elementos Web** aparece bajo el nodo de sitio de nivel superior y, a continuación, expanda el **Galería de elementos Web** nodo.

6. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el `CreateWebPartNodes` método y, a continuación, elija el **F5** tecla para continuar depurando el proyecto.

7. En la instancia experimental de Visual Studio, compruebe que todos los elementos Web en el sitio conectado aparecen bajo el **Galería de elementos Web** nodo **Explorador de servidores**.

8. En **Explorador de servidores**, abra el menú contextual para uno de los elementos Web y, a continuación, elija **propiedades**.

9. En la instancia de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que está depurando, compruebe que los detalles sobre el elemento Web aparecen en la **propiedades** ventana.

## <a name="uninstall-the-extension-from-visual-studio"></a>Desinstale la extensión de Visual Studio
 Cuando termine de probar la extensión, desinstale la extensión de Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Para desinstalar la extensión

1. En la instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], en la barra de menús, elija **herramientas** > **extensiones y actualizaciones**.

     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

2. En la lista de extensiones, elija **extensión de nodo de la Galería de elementos Web Explorador de servidores**y, a continuación, elija el **desinstalar** botón.

3. En el cuadro de diálogo que aparece, elija el **Sí** botón para confirmar que desea desinstalar la extensión y, a continuación, elija el **reiniciar ahora** botón para completar la desinstalación.

4. Cierre ambas instancias de Visual Studio (la instancia experimental y la instancia de Visual Studio en el que está abierta la solución NodoElementoWeb).

## <a name="see-also"></a>Vea también
- [Extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Tutorial: Llamar al modelo de objetos de cliente de SharePoint en una extensión de explorador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Editor de imágenes para iconos](/cpp/windows/image-editor-for-icons)
- [Crear un icono u otra imagen &#40;Editor de imágenes para iconos&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
