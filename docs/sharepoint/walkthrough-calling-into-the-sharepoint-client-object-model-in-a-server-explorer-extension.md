---
title: 'Tutorial: Llamar a en el modelo de objetos de cliente de SharePoint en una extensión de explorador de servidores | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4951d9960a3027e8d72bb0fbc72d551f123993ce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Tutorial: Llamar al modelo de objetos de cliente de SharePoint en una extensión del Explorador de servidores
  Este tutorial muestra cómo llamar al modelo de objetos de cliente de SharePoint desde una extensión para el **las conexiones de SharePoint** nodo **Explorador de servidores**. Para obtener más información sobre cómo usar el modelo de objetos de cliente de SharePoint, vea [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extensión que extiende el **las conexiones de SharePoint** nodo de **Explorador de servidores** de las maneras siguientes:  
  
    -   Agrega la extensión de un **Galería de elementos Web** nodo en cada nodo de sitio de SharePoint en **Explorador de servidores**. Este nuevo nodo contiene nodos secundarios que representan cada elemento Web en la Galería de elementos Web en el sitio.  
  
    -   La extensión define un nuevo tipo de nodo que representa una instancia del elemento Web. Este nuevo tipo de nodo es la base para los nodos secundarios bajo el nuevo **Galería de elementos Web** nodo. El nuevo tipo de nodo de elemento Web muestra información en el **propiedades** ventana acerca del elemento Web que representa el nodo.  
  
-   Compilar un paquete de extensión de Visual Studio (VSIX) para implementar la extensión.  
  
-   Depurar y probar la extensión.  
  
> [!NOTE]  
>  La extensión que se crea en este tutorial se parece a la extensión que se crea en [Tutorial: Extender el Explorador de servidores para mostrar elementos de Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). En este tutorial usa el modelo de objetos de servidor de SharePoint, pero en este tutorial realiza las mismas tareas a través del modelo de objetos de cliente.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:  
  
-   Ediciones compatibles de Windows, SharePoint y Visual Studio. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK. Este tutorial se utiliza la **proyecto VSIX** plantilla en el SDK para crear un paquete VSIX para implementar la extensión. Para obtener más información, consulte [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.  
  
-   Utilizando el modelo de objetos de cliente de SharePoint. Para obtener más información, consulte [modelo de objetos de cliente administrado](http://go.microsoft.com/fwlink/?LinkId=177797).  
  
-   Elementos Web de SharePoint. Para obtener más información, consulte [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="creating-the-projects"></a>Crear los proyectos  
 Para completar este tutorial, debe crear dos proyectos:  
  
-   Un proyecto VSIX para crear el paquete VSIX para implementar la **Explorador de servidores** extensión.  
  
-   Un proyecto de biblioteca de clases que implementa el **Explorador de servidores** extensión.  
  
 Comience el tutorial creando ambos proyectos.  
  
#### <a name="to-create-the-vsix-project"></a>Para crear el proyecto VSIX  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
3.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos y, a continuación, elija **extensibilidad**.  
  
    > [!NOTE]  
    >  El **extensibilidad** nodo solo está disponible si instala el SDK de Visual Studio. Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.  
  
4.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4.5** en la lista de versiones de .NET Framework.  
  
     Extensiones de herramientas de SharePoint requieren características de esta versión de .NET Framework.  
  
5.  Elija la **proyecto VSIX** plantilla.  
  
6.  En el **nombre** , escriba **NodoElementoWeb**y, a continuación, elija la **Aceptar** botón.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **NodoElementoWeb** proyecto al **el Explorador de soluciones**.  
  
#### <a name="to-create-the-extension-project"></a>Para crear la extensión de proyecto  
  
1.  En **el Explorador de soluciones**, abra el menú contextual del nodo de solución, elija **agregar**y, a continuación, elija **nuevo proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos y, a continuación, elija **Windows**.  
  
3.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4.5** en la lista de versiones de .NET Framework.  
  
4.  En la lista de plantillas de proyecto, elija **biblioteca de clases**.  
  
5.  En el **nombre** cuadro, escriba **ExtensiónNodoElementoWeb**y, a continuación, elija la **Aceptar** botón.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **ExtensiónNodoElementoWeb** proyecto a la solución y abre el archivo de código predeterminado Class1.  
  
6.  Elimine el archivo de código Class1 del proyecto.  
  
## <a name="configuring-the-extension-project"></a>Configurar el proyecto de extensión  
 Antes de escribir código para crear la extensión, debe agregar archivos de código y referencias de ensamblado al proyecto y debe actualizar el espacio de nombres predeterminado.  
  
#### <a name="to-configure-the-project"></a>Para configurar el proyecto  
  
1.  En el **ExtensiónNodoElementoWeb** del proyecto, agregue dos archivos de código que se denominan SiteNodeExtension y WebPartNodeTypeProvider.  
  
2.  Abra el menú contextual del proyecto ExtensiónNodoElementoWeb y, a continuación, elija **Agregar referencia**.  
  
3.  En el **Administrador de referencias - ExtensiónNodoElementoWeb** diálogo cuadro, elija la **Framework** nodo y, a continuación, seleccione las casillas de verificación para el System.ComponentModel.Composition y System.Windows.Forms ensamblados.  
  
4.  Elija la **extensiones** nodo, seleccione la casilla de verificación para cada uno de los siguientes ensamblados y, a continuación, elija la **Aceptar** botón:  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Abra el menú contextual para el **ExtensiónNodoElementoWeb** del proyecto y, a continuación, elija **propiedades**.  
  
     Se abrirá el **Diseñador de proyectos**.  
  
6.  Pulse la pestaña **Aplicación**.  
  
7.  En el **espacio de nombres predeterminado** cuadro (C#) o **espacio de nombres raíz** (Visual Basic), escriba **ServerExplorer.SharePointConnections.NodoElementoWeb**.  
  
## <a name="creating-icons-for-the-new-nodes"></a>Crear iconos para los nuevos nodos  
 Cree dos iconos para el **Explorador de servidores** extensión: un icono para el nuevo **Galería de elementos Web** nodo y otro icono para cada nodo de elemento Web secundario en el **Galería de elementos Web** nodo. Más adelante en este tutorial, escribirá código que asocie estos iconos a los nodos.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Para crear iconos para los nodos  
  
1.  En el **Diseñador de proyectos** para el proyecto ExtensiónNodoElementoWeb, elija la **recursos** ficha.  
  
2.  Elija el vínculo **este proyecto no contiene un archivo de recursos predeterminado. Haga clic aquí para crear uno.**  
  
     Visual Studio crea un archivo de recursos y lo abre en el diseñador.  
  
3.  En la parte superior del diseñador, elija la flecha situada en la **Agregar recurso** menú de comandos y, a continuación, elija **Agregar nuevo icono**.  
  
4.  Escriba **WebPartsNode** para el icono nuevo nombre y, a continuación, elija la **agregar** botón.  
  
     El nuevo icono se abre en el **Editor de imágenes**.  
  
5.  Editar la versión de 16 x 16 del icono para que tenga un diseño que pueda reconocer fácilmente.  
  
6.  Abra el menú contextual para la versión de 32 x 32 del icono y, a continuación, elija **Eliminar tipo de imagen**.  
  
7.  Repita los pasos del 3 al 7 para agregar un segundo icono a los recursos del proyecto y el nombre de este icono **elemento Web**.  
  
8.  En **el Explorador de soluciones**, en la **recursos** carpeta para la **ExtensiónNodoElementoWeb** proyecto, elija **NodoElementoWeb.ico**.  
  
9. En el **propiedades** ventana, abra el **acción de compilación** lista y, a continuación, elija **recurso incrustado**.  
  
10. Repita los dos últimos pasos para **ElementoWeb.ico**.  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>Agregar el nodo de la Galería de elementos Web al explorador de servidores  
 Cree una clase que agrega el nuevo **Galería de elementos Web** nodo para cada nodo de sitio de SharePoint. Para agregar el nuevo nodo, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaz. Implemente esta interfaz siempre que desee extender el comportamiento de un nodo existente en **Explorador de servidores**, como agregar un nuevo nodo secundario a un nodo.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Para agregar el nodo de la Galería de elementos Web al explorador de servidores  
  
1.  Pegue el código siguiente en el **SiteNodeExtension** archivo de código para el **ExtensiónNodoElementoWeb** proyecto.  
  
    > [!NOTE]  
    >  Tras agregar este código, el proyecto tendrá algunos errores de compilación. Estos errores desaparecerán al agregar código en pasos posteriores.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>Definir un tipo de nodo que representa un elemento Web  
 Cree una clase que define un nuevo tipo de nodo que representa un elemento Web. Visual Studio utiliza este nuevo tipo de nodo para mostrar los nodos secundarios bajo el **Galería de elementos Web** nodo. Cada uno de los siguientes nodos secundarios representa un único elemento Web en el sitio de SharePoint.  
  
 Para definir el nuevo tipo de nodo, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaz. Implemente esta interfaz siempre que desee definir un nuevo tipo de nodo **Explorador de servidores**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Para definir el tipo de nodo de elemento Web  
  
1.  Pegue el código siguiente en el **WebPartNodeTypeProvider** archivo de código para el **ExtensiónNodoElementoWeb** proyecto.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## <a name="checkpoint"></a>Punto de control  
 En este punto del tutorial, todo el código para el **Galería de elementos Web** nodo está en el proyecto. Compilar el **ExtensiónNodoElementoWeb** proyecto para asegurarse de que se compila sin errores.  
  
#### <a name="to-build-the-project"></a>Para compilar el proyecto  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el **ExtensiónNodoElementoWeb** del proyecto y, a continuación, elija **generar**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Crear un paquete VSIX para implementar la extensión  
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX. En primer lugar, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest incluido en el proyecto. A continuación, crear el paquete VSIX compilando la solución.  
  
#### <a name="to-configure-the-vsix-package"></a>Para configurar el paquete VSIX  
  
1.  En **el Explorador de soluciones**, en la **NodoElementoWeb** proyecto abierto **source.extension.vsixmanifest** archivo en el editor de manifiestos.  
  
     El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que requieren todos los paquetes VSIX. Para obtener más información acerca de este archivo, consulte [referencia de 1.0 de esquema de extensión VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  En el **Product Name** cuadro, escriba **nodo Galería de elementos Web para el Explorador de servidores**.  
  
3.  En el **autor** cuadro, escriba **Contoso**.  
  
4.  En el **descripción** cuadro, escriba **agrega un nodo de la Galería de elementos Web personalizados para el nodo Conexiones de SharePoint en el Explorador de servidores**.  
  
5.  En el **activos** pestaña del editor, elija la **New** botón.  
  
6.  En el **Agregar nuevo activo** cuadro de diálogo, en la **tipo** elija **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest. Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX. Para obtener más información, consulte [elemento MEFComponent (Esquema VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  En el **origen** elija **un proyecto de la solución actual**.  
  
8.  En el **proyecto** elija **ExtensiónNodoElementoWeb**y, a continuación, elija la **Aceptar** botón.  
  
9. En la barra de menús, elija **generar**, **generar solución**y, a continuación, asegúrese de que la solución se compila sin errores.  
  
10. Asegúrese de que la carpeta de salida de compilación del proyecto NodoElementoWeb contiene ahora el archivo WebPartNode.vsix.  
  
     De forma predeterminada, la carpeta de salida de la compilación es \bin\Debug, ubicada bajo la carpeta que contiene el archivo de proyecto.  
  
## <a name="testing-the-extension"></a>Probar la extensión  
 Ya estás listo para probar la nueva **Galería de elementos Web** nodo **Explorador de servidores**. Primero, empiece a depurar el proyecto de extensión en una instancia experimental de Visual Studio. A continuación, use la nueva **elementos Web** nodo en la instancia experimental de Visual Studio.  
  
#### <a name="to-start-debugging-the-extension"></a>Para comenzar a depurar la extensión  
  
1.  Reinicie Visual Studio con credenciales administrativas y, a continuación, abra el **NodoElementoWeb** solución.  
  
2.  En el proyecto ExtensiónNodoElementoWeb, abra el **SiteNodeExtension** archivo de código y, a continuación, agregue un punto de interrupción a las primeras líneas de código en el `NodeChildrenRequested` y `CreateWebPartNodes` métodos.  
  
3.  Elija la tecla F5 para iniciar la depuración.  
  
     Visual Studio instala la extensión en %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web extensión de nodo de la Galería de elementos para Explorer\1.0 de servidor e inicia una instancia experimental de Visual Studio. Probará el elemento de proyecto en esta instancia de Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Para probar la extensión  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **vista**, **Explorador de servidores**.  
  
2.  Compruebe que el sitio de SharePoint que desea usar para la prueba aparece bajo la **las conexiones de SharePoint** nodo **Explorador de servidores**. Si no aparece, siga estos pasos:  
  
    1.  Abra el menú contextual para **las conexiones de SharePoint**y, a continuación, elija **Agregar conexión**.  
  
    2.  En el **Agregar conexión de SharePoint** diálogo cuadro, escriba la dirección URL del sitio de SharePoint al que desea conectarse y, a continuación, elija la **Aceptar** botón.  
  
         Para especificar el sitio de SharePoint en el equipo de desarrollo, escriba **http://localhost**.  
  
3.  Expanda el nodo de conexión de sitio (que muestra la dirección URL del sitio) y, a continuación, expanda un nodo de sitio secundario (por ejemplo, **equipo sitio**).  
  
4.  Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el `NodeChildrenRequested` (método) y, a continuación, elija la tecla F5 para continuar depurando el proyecto.  
  
5.  En la instancia experimental de Visual Studio, expanda la **Galería de elementos Web** nodo, que aparece bajo el nodo de sitio de nivel superior.  
  
6.  Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el `CreateWebPartNodes` (método) y, a continuación, elija la tecla F5 para continuar depurando el proyecto.  
  
7.  En la instancia experimental de Visual Studio, compruebe que todos los elementos Web en el sitio conectado aparecen bajo la **Galería de elementos Web** nodo **Explorador de servidores**.  
  
8.  Abra el menú contextual para un elemento Web y, a continuación, elija **propiedades**.  
  
9. En el **propiedades** ventana, compruebe que aparecen los detalles acerca del elemento Web.  
  
10. En **Explorador de servidores**, abra el menú contextual para el mismo elemento Web y, a continuación, elija **mostrar el mensaje**.  
  
     En el cuadro de mensaje que aparece, elija la **Aceptar** botón.  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>Desinstalar la extensión de Visual Studio  
 Cuando termine de probar la extensión, desinstálelo desde Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>Para desinstalar la extensión  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **herramientas**, **extensiones y actualizaciones**.  
  
     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.  
  
2.  En la lista de extensiones, elija **nodo Galería de elementos Web para el Explorador de servidores**y, a continuación, elija la **desinstalar** botón.  
  
3.  En el cuadro de diálogo que aparece, elija la **Sí** botón.  
  
4.  Elija la **reiniciar ahora** botón para completar la desinstalación.  
  
     También se desinstala el elemento de proyecto.  
  
5.  Cierre ambas instancias de Visual Studio (la instancia experimental y la instancia de Visual Studio en el que está abierta la solución NodoElementoWeb).  
  
## <a name="see-also"></a>Vea también  
 [Llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Tutorial: Extender el Explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Editor de imágenes para iconos](/cpp/windows/image-editor-for-icons)   
 [Crear un icono u otra imagen &#40;Editor de imágenes para iconos&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  