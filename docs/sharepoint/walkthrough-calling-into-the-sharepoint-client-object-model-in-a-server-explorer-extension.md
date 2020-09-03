---
title: 'Explorador de servidores: extender el nodo conexiones de SharePoint'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ebd7d500767e896ce9576a3d007a4357b9c5281c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014639"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Tutorial: llamar al modelo de objetos de cliente de SharePoint en una extensión de Explorador de servidores
  En este tutorial se muestra cómo llamar al modelo de objetos de cliente de SharePoint desde una extensión para el nodo **conexiones de SharePoint** en **Explorador de servidores**. Para obtener más información sobre cómo usar el modelo de objetos de cliente de SharePoint, vea [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

 En este tutorial se muestran las siguientes tareas:

- Crear una [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extensión que extienda el nodo **conexiones de SharePoint** de **Explorador de servidores** de las siguientes maneras:

  - La extensión agrega un nodo de la **Galería de elementos Web** en cada nodo del sitio de SharePoint en **Explorador de servidores**. Este nuevo nodo contiene nodos secundarios que representan cada elemento Web en la galería de elementos Web del sitio.

  - La extensión define un nuevo tipo de nodo que representa una instancia del elemento Web. Este nuevo tipo de nodo es la base para los nodos secundarios del nuevo nodo **Galería de elementos Web** . El nuevo tipo de nodo de elemento Web muestra información en la ventana **propiedades** sobre el elemento Web que el nodo representa.

- Compilar un paquete de extensión de Visual Studio (VSIX) para implementar la extensión.

- Depurar y probar la extensión.

> [!NOTE]
> La extensión que se crea en este tutorial es similar a la extensión que se crea en [Walkthrough: Extend explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). En este tutorial se usa el modelo de objetos de servidor de SharePoint, pero en este tutorial se realizan las mismas tareas con el modelo de objetos de cliente.

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:

- Ediciones compatibles de Windows, SharePoint y Visual Studio.

- Visual Studio SDK. En este tutorial se usa la plantilla de **Proyecto VSIX** en el SDK para crear un paquete VSIX para implementar la extensión. Para obtener más información, vea [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.

- Usar el modelo de objetos de cliente de SharePoint. Para obtener más información, vea [modelo de objetos de cliente administrado](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).

- Elementos Web de SharePoint. Para obtener más información, vea [información general sobre elementos Web](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Crear los proyectos
 Para completar este tutorial, debe crear dos proyectos:

- Un proyecto VSIX para crear el paquete VSIX para implementar la extensión de **Explorador de servidores** .

- Proyecto de biblioteca de clases que implementa la extensión de **Explorador de servidores** .

  Comience el tutorial creando ambos proyectos.

#### <a name="to-create-the-vsix-project"></a>Para crear el proyecto VSIX

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

3. En el cuadro de diálogo **nuevo proyecto** , expanda los nodos **Visual C#** o **Visual Basic** y, a continuación, elija **extensibilidad**.

    > [!NOTE]
    > El nodo **extensibilidad** solo está disponible si instala el SDK de Visual Studio. Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.

4. En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de la .NET Framework.

     Las extensiones de herramientas de SharePoint requieren características en esta versión del .NET Framework.

5. Elija la plantilla de **Proyecto VSIX** .

6. En el cuadro **nombre** , escriba **WebPartNode**y elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **WebPartNode** a **Explorador de soluciones**.

#### <a name="to-create-the-extension-project"></a>Para crear la extensión de proyecto

1. En **Explorador de soluciones**, abra el menú contextual del nodo de la solución, elija **Agregar**y, a continuación, elija **nuevo proyecto**.

2. En el cuadro de diálogo  **nuevo proyecto** , expanda los nodos **Visual C#** o **Visual Basic** y, a continuación, elija **Windows**.

3. En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de la .NET Framework.

4. En la lista de plantillas de proyecto, elija **biblioteca de clases**.

5. En el cuadro **nombre** , escriba **ExtensiónNodoElementoWeb**y elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **ExtensiónNodoElementoWeb** a la solución y abre el archivo de código predeterminado Class1.

6. Elimine el archivo de código Class1 del proyecto.

## <a name="configure-the-extension-project"></a>Configurar el proyecto de extensión
 Antes de escribir código para crear la extensión, debe agregar los archivos de código y las referencias de ensamblado al proyecto, y debe actualizar el espacio de nombres predeterminado.

#### <a name="to-configure-the-project"></a>Para configurar el proyecto

1. En el proyecto **ExtensiónNodoElementoWeb** , agregue dos archivos de código denominados SiteNodeExtension y WebPartNodeTypeProvider.

2. Abra el menú contextual del proyecto ExtensiónNodoElementoWeb y, a continuación, elija **Agregar referencia**.

3. En el cuadro de diálogo **Administrador de referencias-ExtensiónNodoElementoWeb** , elija el nodo **Framework** y, a continuación, active las casillas de los ensamblados System. ComponentModel. Composition y System. Windows. Forms.

4. Elija el nodo **extensiones** , active la casilla para cada uno de los siguientes ensamblados y, a continuación, elija el botón **Aceptar** :

    - Microsoft. SharePoint. Client

    - Microsoft. SharePoint. Client. Runtime

    - Microsoft.VisualStudio.SharePoint

5. Abra el menú contextual del proyecto **ExtensiónNodoElementoWeb** y, a continuación, elija **propiedades**.

     Se abrirá el **Diseñador de proyectos**.

6. Pulse la pestaña **Aplicación**.

7. En el cuadro **espacio de nombres predeterminado** (C#) o **espacio de nombres raíz** (Visual Basic), escriba **ServerExplorer. SharePointConnections. WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Crear iconos para los nuevos nodos
 Cree dos iconos para la extensión de **Explorador de servidores** : un icono para el nuevo nodo de la **Galería de elementos Web** y otro icono para cada nodo de elemento Web secundario en el nodo de la **Galería de elementos Web** . Más adelante en este tutorial, escribirá código que asocia estos iconos con los nodos.

#### <a name="to-create-icons-for-the-nodes"></a>Para crear iconos para los nodos

1. En el **Diseñador de proyectos** para el proyecto ExtensiónNodoElementoWeb, elija la pestaña **recursos** .

2. Elija el vínculo **este proyecto no contiene un archivo de recursos predeterminado. Haga clic aquí para crear uno.**

     Visual Studio crea un archivo de recursos y lo abre en el diseñador.

3. En la parte superior del diseñador, elija la flecha del comando de menú **Agregar recurso** y, a continuación, elija **Agregar nuevo icono**.

4. Escriba **WebPartsNode** para el nuevo nombre de icono y, después, elija el botón **Agregar** .

     El icono nuevo se abre en el **Editor de imágenes**.

5. Edite la versión 16x16 del icono para que tenga un diseño que pueda reconocer fácilmente.

6. Abra el menú contextual de la versión 32x32 del icono y, a continuación, elija **eliminar tipo de imagen**.

7. Repita los pasos del 3 al 7 para agregar un segundo icono a los recursos del proyecto y asigne a este icono el **elemento Web**.

8. En **Explorador de soluciones**, en la carpeta **recursos** del proyecto **ExtensiónNodoElementoWeb** , elija *WebPartsNode. ico*.

9. En la ventana **propiedades** , abra la lista **acción de compilación** y, a continuación, elija **recurso incrustado**.

10. Repita los dos últimos pasos para *WebPart. ico*.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Agregue el nodo de la galería de elementos Web a Explorador de servidores
 Cree una clase que agregue el nuevo nodo de la **Galería de elementos Web** a cada nodo del sitio de SharePoint. Para agregar el nuevo nodo, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaz. Implemente esta interfaz siempre que desee ampliar el comportamiento de un nodo existente en **Explorador de servidores**, como agregar un nuevo nodo secundario a un nodo.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Para agregar el nodo Galería de elementos Web a Explorador de servidores

1. Pegue el código siguiente en el archivo de código **SiteNodeExtension** para el proyecto **ExtensiónNodoElementoWeb** .

    > [!NOTE]
    > Tras agregar este código, el proyecto tendrá algunos errores de compilación. Estos errores desaparecerán al agregar código en pasos posteriores.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definir un tipo de nodo que represente un elemento Web
 Cree una clase que defina un nuevo tipo de nodo que representa un elemento Web. Visual Studio usa este nuevo tipo de nodo para mostrar los nodos secundarios en el nodo de la **Galería de elementos Web** . Cada uno de estos nodos secundarios representa un único elemento Web en el sitio de SharePoint.

 Para definir el nuevo tipo de nodo, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaz. Implemente esta interfaz siempre que desee definir un nuevo tipo de nodo en **Explorador de servidores**.

#### <a name="to-define-the-web-part-node-type"></a>Para definir el tipo de nodo de elemento Web

1. Pegue el código siguiente en el archivo de código **WebPartNodeTypeProvider** para el proyecto **ExtensiónNodoElementoWeb** .

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]

## <a name="checkpoint"></a>Punto de control
 En este punto del tutorial, todo el código del nodo **Galería de elementos Web** está ahora en el proyecto. Compile el proyecto **ExtensiónNodoElementoWeb** para asegurarse de que se compila sin errores.

#### <a name="to-build-the-project"></a>Para compilar el proyecto

1. En **Explorador de soluciones**, abra el menú contextual del proyecto **ExtensiónNodoElementoWeb** y, a continuación, elija **compilar**.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Crear un paquete VSIX para implementar la extensión
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX. En primer lugar, configure el paquete VSIX modificando el archivo source. Extension. vsixmanifest incluido en el proyecto. A continuación, cree el paquete VSIX compilando la solución.

#### <a name="to-configure-the-vsix-package"></a>Para configurar el paquete VSIX

1. En **Explorador de soluciones**, en el proyecto **WebPartNode** , abra el archivo **source. Extension. vsixmanifest** en el editor de manifiestos.

     El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que requieren todos los paquetes VSIX. Para obtener más información acerca de este archivo, vea [referencia de esquema de extensión VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. En el cuadro **nombre de producto** , escriba **nodo de la galería de elementos Web para explorador de servidores**.

3. En el cuadro **autor** , escriba **contoso**.

4. En el cuadro **Descripción** , escriba **Agregar un nodo de la galería de elementos web personalizado al nodo conexiones de SharePoint en explorador de servidores**.

5. En la pestaña **activos** del editor, elija el botón **nuevo** .

6. En el cuadro de diálogo **Agregar nuevo activo** , en la lista **tipo** , elija **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest. Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX. Para obtener más información, vea [elemento MEFComponent (esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. En la lista **origen** , elija **un proyecto en la solución actual**.

8. En la lista **proyecto** , elija **ExtensiónNodoElementoWeb**y elija el botón **Aceptar** .

9. En la barra de menús, **Elija compilar compilar**  >  **solución**y, a continuación, asegúrese de que la solución se compila sin errores.

10. Asegúrese de que la carpeta de salida de compilación del proyecto WebPartNode contiene ahora el archivo WebPartNode. vsix.

     De forma predeterminada, la carpeta de salida de la compilación es \bin\Debug, ubicada bajo la carpeta que contiene el archivo de proyecto.

## <a name="test-the-extension"></a>Prueba de la extensión
 Ahora está listo para probar el nuevo nodo de la **Galería de elementos Web** en **Explorador de servidores**. En primer lugar, empiece a depurar el proyecto de extensión en una instancia experimental de Visual Studio. A continuación, use el nuevo nodo **elementos Web** en la instancia experimental de Visual Studio.

#### <a name="to-start-debugging-the-extension"></a>Para comenzar a depurar la extensión

1. Reinicie Visual Studio con credenciales administrativas y, a continuación, abra la solución **WebPartNode** .

2. En el proyecto ExtensiónNodoElementoWeb, abra el archivo de código **SiteNodeExtension** y, a continuación, agregue un punto de interrupción a las primeras líneas de código en los `NodeChildrenRequested` `CreateWebPartNodes` métodos y.

3. Elija la tecla **F5** para iniciar la depuración.

     Visual Studio instala la extensión en la extensión de nodo de la galería de elementos de%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web para el servidor Explorer\1.0 e inicia una instancia experimental de Visual Studio. Probará el elemento de proyecto en esta instancia de Visual Studio.

#### <a name="to-test-the-extension"></a>Para probar la extensión

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **Ver**  >  **Explorador de servidores**.

2. Compruebe que el sitio de SharePoint que desea usar para las pruebas aparece en el nodo **conexiones de SharePoint** en **Explorador de servidores**. Si no aparece, siga estos pasos:

    1. Abra el menú contextual para **las conexiones de SharePoint**y, a continuación, elija **Agregar conexión**.

    2. En el cuadro de diálogo **Agregar conexión de SharePoint** , escriba la dirección URL del sitio de SharePoint al que desea conectarse y, a continuación, elija el botón **Aceptar** .

         Para especificar el sitio de SharePoint en el equipo de desarrollo, escriba **http://localhost** .

3. Expanda el nodo conexión de sitio (que muestra la dirección URL de su sitio) y, a continuación, expanda un nodo de sitio secundario (por ejemplo, **sitio de grupo**).

4. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el `NodeChildrenRequested` método y, a continuación, elija la tecla **F5** para continuar depurando el proyecto.

5. En la instancia experimental de Visual Studio, expanda el nodo **Galería de elementos Web** , que aparece bajo el nodo de sitio de nivel superior.

6. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el `CreateWebPartNodes` método y, a continuación, elija la tecla **F5** para continuar depurando el proyecto.

7. En la instancia experimental de Visual Studio, compruebe que todos los elementos web del sitio conectado aparecen en el nodo **Galería de elementos Web** de **Explorador de servidores**.

8. Abra el menú contextual de un elemento Web y, a continuación, elija **propiedades**.

9. En la ventana **propiedades** , compruebe que aparecen los detalles sobre el elemento Web.

10. En **Explorador de servidores**, abra el menú contextual del mismo elemento Web y, a continuación, elija **Mostrar mensaje**.

     En el cuadro de mensaje que aparece, elija el botón **Aceptar** .

## <a name="uninstall-the-extension-from-visual-studio"></a>Desinstalar la extensión de Visual Studio
 Una vez finalizada la prueba de la extensión, desinstálelo desde Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Para desinstalar la extensión

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **herramientas**  >  **extensiones y actualizaciones**.

     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

2. En la lista de extensiones, elija **nodo de la galería de elementos Web para explorador de servidores**y, a continuación, elija el botón **desinstalar** .

3. En el cuadro de diálogo que aparece, elija el botón **sí** .

4. Elija el botón **reiniciar ahora** para completar la desinstalación.

     También se desinstala el elemento de proyecto.

5. Cierre ambas instancias de Visual Studio (la instancia experimental y la instancia de Visual Studio en la que está abierta la solución WebPartNode).

## <a name="see-also"></a>Consulte también
- [Llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Extender el nodo conexiones de SharePoint en Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Tutorial: extender Explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Editor de imágenes para iconos](/cpp/windows/image-editor-for-icons)
- [Crear un icono u otra imagen &#40;editor de imágenes para iconos&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
