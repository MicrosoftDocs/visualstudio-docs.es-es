---
title: "Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
ms.assetid: 897d3798-42c1-4fff-b280-8b84b53d80c6
caps.latest.revision: 100
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 96
---
# Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension
  En este tutorial se muestra cómo llamar al modelo de objetos de cliente de SharePoint desde una extensión del nodo **Conexiones de SharePoint** en el **Explorador de servidores**.  Para obtener más información sobre cómo utilizar el modelo de objetos de cliente de SharePoint, vea [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear una extensión [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que extiende el nodo **Conexiones de SharePoint** del **Explorador de servidores** de las maneras siguientes:  
  
    -   La extensión agrega un nodo **Galería de elementos web** bajo cada nodo de sitio de SharePoint en **Explorador de servidores**.  Este nuevo nodo contiene nodos secundarios que representan cada elemento web en la galería de elementos web del sitio.  
  
    -   La extensión define un nuevo tipo de nodo que representa una instancia del elemento web.  Este nuevo tipo de nodo es la base de los nodos secundarios bajo el nuevo nodo **Galería de elementos web**.  El nuevo tipo de nodo elemento web muestra información en la ventana **Propiedades** sobre el elemento web que representa el nodo.  
  
-   Compilar un paquete de extensión de Visual Studio \(VSIX\) para implementar la extensión.  
  
-   Depurar y probar la extensión.  
  
> [!NOTE]  
>  La extensión que se crea en este tutorial se parece a la extensión que se crea en [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  Que el tutorial utiliza el modelo de objetos de servidor de SharePoint, pero este tutorial realiza las mismas tareas con el modelo de objetos de cliente.  
  
## Requisitos previos  
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:  
  
-   Ediciones compatibles de Windows, SharePoint, y Visual Studio.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK.  En este tutorial se utiliza la plantilla **Proyecto VSIX** del SDK para crear un paquete VSIX para implementar la extensión.  Para obtener más información, vea [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.  
  
-   Utilizar el modelo de objetos de cliente de SharePoint.  Para obtener más información, vea [Modelo de objetos de cliente administrado](http://go.microsoft.com/fwlink/?LinkId=177797).  
  
-   Elementos web en SharePoint.  Para obtener más información, vea [Información general sobre elementos web](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## Crear los proyectos  
 Para completar este tutorial, debe crear dos proyectos:  
  
-   Un proyecto VSIX para crear el paquete VSIX para implementar la extensión **Explorador de servidores** .  
  
-   Un proyecto de biblioteca de clases que implemente la extensión **Explorador de servidores** .  
  
 Comience el tutorial creando ambos proyectos.  
  
#### Para crear el proyecto VSIX  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menú, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
3.  En el cuadro de diálogo **Nuevo proyecto** , expanda los nodos **Visual c\#** o **Visual Basic** y, a continuación **Extensibilidad**.  
  
    > [!NOTE]  
    >  El nodo **Extensibilidad** solo está disponible si instala Visual Studio SDK.  Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.  
  
4.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de .NET Framework.  
  
     Las extensiones de herramientas de SharePoint requieren características de esta versión de .NET Framework.  
  
5.  Elija la plantilla **Proyecto VSIX** .  
  
6.  En el cuadro **Nombre** , **WebPartNode**escrito, y elija el botón **Aceptar** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **NodoElementoWeb** al **Explorador de soluciones**.  
  
#### Para crear la extensión de proyecto  
  
1.  En **Explorador de soluciones**, abra el menú contextual para el nodo de la solución, elija **Agregar**y, a continuación **Nuevo proyecto**.  
  
    > [!NOTE]  
    >  En los proyectos de Visual Basic, el nodo de la solución aparece en el **Explorador de soluciones** solo cuando se activa la casilla **Mostrar solución siempre** en [General, Proyectos y soluciones, Cuadro de diálogo Opciones](http://msdn.microsoft.com/es-es/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  En el cuadro de diálogo  **Nuevo proyecto** , expanda los nodos **Visual c\#** o **Visual Basic** y, a continuación **Windows**.  
  
3.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de .NET Framework.  
  
4.  En la lista de plantillas de proyecto, elija **Biblioteca de clases**.  
  
5.  En el cuadro **Nombre** , entre en **WebPartNodeExtension**, y elija el botón **Aceptar** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **ExtensiónNodoElementoWeb** a la solución y abre el archivo de código predeterminado Class1.  
  
6.  Elimine el archivo de código Class1 del proyecto.  
  
## Configurar el proyecto de extensión  
 Antes de escribir el código para crear la extensión, debe agregar los archivos de código y las referencias de ensamblado al proyecto, y debe actualizar el espacio de nombres predeterminado.  
  
#### Para configurar el proyecto  
  
1.  En el proyecto **WebPartNodeExtension** , agregue dos archivos de código que se llama SiteNodeExtension y WebPartNodeTypeProvider.  
  
2.  Abrir el menú contextual del proyecto extensiónnodoelementoweb y, a continuación **Agregar referencia**.  
  
3.  En el cuadro de diálogo **Administrador de referencia – WebPartNodeExtension** , elija el nodo **Framework** , y seleccione las casillas de los ensamblados System.ComponentModel.Composition y System.Windows.Forms.  
  
4.  Elija el nodo **Extensiones** , active la casilla para cada uno de los siguientes ensamblados, y después elija el botón **Aceptar** :  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Abrir el menú contextual para el proyecto **WebPartNodeExtension** y, a continuación **Propiedades**.  
  
     Se abrirá el **Diseñador de proyectos**.  
  
6.  Elija la ficha **Aplicación** .  
  
7.  En el cuadro **Espacio de nombres predeterminado** \(C\#\) o el cuadro **Espacio de nombres de la raíz** \(Visual Basic\), escriba en **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## Crear iconos para los nuevos nodos  
 Cree dos iconos para la extensión **Explorador de servidores** : un icono para el nuevo nodo **Galería de elementos web** y otro icono para cada nodo secundario del elemento web bajo el nodo **Galería de elementos web** .  Más adelante en este tutorial, escribirá código que asocie estos iconos a los nodos.  
  
#### Para crear iconos para los nodos  
  
1.  En **Diseñador de proyectos** para el proyecto extensiónnodoelementoweb, elija la ficha **RECURSOS** .  
  
2.  Elija el vínculo **De que el proyecto no contiene un archivo de recursos predeterminado. Haga clic aquí para crear uno.**  
  
     Visual Studio crea un archivo de recursos y lo abre en el diseñador.  
  
3.  En la parte superior del diseñador, elija la flecha en el comando de menú **Agregar recurso** , y elija **Agregar nuevo icono**.  
  
4.  Escriba en **WebPartsNode** para el nuevo icono, y elija el botón **Agregar** .  
  
     El nuevo icono se abre en el **Editor de imágenes**.  
  
5.  Modifique la versión 16x16 del icono para que tenga un diseño que pueda fácilmente reconocer.  
  
6.  Abrir el menú contextual para la versión 32x32 del icono y, a continuación **Eliminar tipo de imagen**.  
  
7.  Repita los pasos 3 a 7 para agregar un segundo icono a los recursos del proyecto, y llame a este icono **WebPart**.  
  
8.  En **Explorador de soluciones**, en la carpeta **RECURSOS** para el proyecto **WebPartNodeExtension** , elija **WebPartsNode.ico**.  
  
9. En la ventana **Propiedades** , abra la lista **Acción de compilación** y, a continuación **Recurso incrustado**.  
  
10. Repita los últimos dos pasos con **ElementoWeb.ico**.  
  
## Agregar el nodo Galería de elementos web al Explorador de servidores  
 Cree una clase que agregue el nuevo nodo **Galería de elementos web** a cada nodo del sitio de SharePoint.  Para agregarlo, la clase implementa la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Implemente esta interfaz para extender el comportamiento de un nodo existente en el **Explorador de servidores**, como agregar un nuevo nodo secundario a un nodo.  
  
#### Para agregar el nodo Galería de elementos web al Explorador de servidores  
  
1.  Pegue el código siguiente en el archivo de código **SiteNodeExtension** para el proyecto **WebPartNodeExtension** .  
  
    > [!NOTE]  
    >  Después de agregar este código, el proyecto tendrá algunos errores de compilación.  Estos errores desaparecerán al agregar código en pasos posteriores.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## Definir un tipo de nodo que represente un elemento web  
 Cree una clase que defina un nuevo tipo de nodo que represente un elemento web.  Visual Studio utiliza este nuevo tipo de nodo para mostrar los nodos secundarios del nodo **Galería de elementos web** .  Cada uno de estos nodos secundarios representa un elemento web único en el sitio de SharePoint.  
  
 Para definir el nuevo tipo de nodo, la clase implementa la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Implemente esta interfaz para definir un nuevo tipo de nodo en el **Explorador de servidores** todas las veces que desee.  
  
#### Para definir el tipo de nodo Elemento web  
  
1.  Pegue el código siguiente en el archivo de código **WebPartNodeTypeProvider** para el proyecto **WebPartNodeExtension** .  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## Punto de control  
 En este punto del tutorial, todo el código del nodo **Galería de elementos web** está en el proyecto.  Compile el proyecto **WebPartNodeExtension** para asegurarse de que se compila sin errores.  
  
#### Para compilar el proyecto  
  
1.  En **Explorador de soluciones**, abra el menú contextual para el proyecto **WebPartNodeExtension** y, a continuación **Generar**.  
  
## Crear un paquete VSIX para implementar la extensión  
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX.  Primero, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest incluido en el proyecto.  A continuación cree el paquete VSIX compilando la solución.  
  
#### Para configurar el paquete VSIX  
  
1.  En **Explorador de soluciones**, en el proyecto **WebPartNode** , abra el archivo **source.extension.vsixmanifest** en el editor de manifiestos.  
  
     El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que todos los paquetes VSIX requieren.  Para obtener más información sobre este archivo, vea [Referencia de esquema de extensión VSIX](http://msdn.microsoft.com/es-es/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  En el cuadro **Nombre de producto** , entre en **Nodo galería de elementos web para el Explorador de servidores**.  
  
3.  En el cuadro **Autor** , entre en **Contoso**.  
  
4.  En el cuadro **Descripción** , entre en **Agrega un nodo galería de elementos web personalizado al nodo conexiones de SharePoint en el Explorador de servidores**.  
  
5.  En la pestaña **Activos** de editor, elija el botón **Nuevo** .  
  
6.  En el cuadro de diálogo **Agregar nuevo activo** , en la lista **Tipo** , elija **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest.  Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX.  Para obtener más información, vea [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/es-es/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  En la lista **Origen** , elija **Un proyecto de la solución actual**.  
  
8.  En la lista **Proyecto** , elija **WebPartNodeExtension**, y elija el botón **Aceptar** .  
  
9. En la barra de menú, elija **Generar**, **Compilar solución**, y asegúrese de que la solución se compila sin errores.  
  
10. Asegúrese de que la carpeta de salida de la compilación del proyecto nodoelementoweb ahora contiene el archivo nodoelementoweb.vsix.  
  
     De forma predeterminada, la carpeta de resultado de compilación es ..  \\bin\\Debug, que se encuentra bajo la carpeta que contiene el archivo de proyecto.  
  
## Probar la extensión  
 Ya puede probar el nuevo nodo **Galería de elementos web** en el **Explorador de servidores**.  Primero, empiece a depurar el proyecto de extensión en una instancia experimental de Visual Studio.  Después utilice el nuevo nodo **Elementos web** en la instancia experimental de Visual Studio.  
  
#### Para comenzar a depurar la extensión  
  
1.  Reinicie Visual Studio con credenciales administrativas, y vuelva a abrir la solución **WebPartNode** .  
  
2.  En el proyecto extensiónnodoelementoweb, abra el archivo de código **SiteNodeExtension** , y después agregue un punto de interrupción a las primeras líneas de código en los métodos `NodeChildrenRequested` y `CreateWebPartNodes` .  
  
3.  Elija la tecla F5 para iniciar la depuración.  
  
     Visual Studio instala la extensión en %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Web Part Gallery Node Extension for Server Explorer\\1.0 and starts an experimental instance of Visual Studio.  Probará el elemento de proyecto en esta instancia de Visual Studio.  
  
#### Para probar la extensión  
  
1.  En la instancia experimental de Visual Studio, en la barra de menú, elija **Ver**, **Explorador de servidores**.  
  
2.  Compruebe que el sitio de SharePoint que desea utilizar para probar aparece bajo el nodo **Conexiones de SharePoint** en el **Explorador de servidores**.  Si no aparece, siga estos pasos:  
  
    1.  Abrir el menú contextual para **Conexiones de SharePoint**y, a continuación **Agregar conexión**.  
  
    2.  En el cuadro de diálogo **Agregar conexión a SharePoint** , escriba la dirección URL para el sitio de SharePoint al que desea conectarse, y elija el botón **Aceptar** .  
  
         Para especificar el sitio de SharePoint en el equipo de desarrollo, tipo **http:\/\/localhost**.  
  
3.  Expanda el nodo de conexión del sitio \(que muestra la dirección URL del sitio\) y, a continuación expanda un nodo de sitio secundario \(por ejemplo, **Sitio del equipo**\).  
  
4.  Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `NodeChildrenRequested` , y elija la tecla F5 para continuar y depurar el proyecto.  
  
5.  En la instancia experimental de Visual Studio, expanda el nodo **Galería de elementos web** , que aparece bajo el nodo del sitio de nivel superior.  
  
6.  Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `CreateWebPartNodes` , y elija la tecla F5 para continuar y depurar el proyecto.  
  
7.  En la instancia experimental de Visual Studio, compruebe que todos los elementos web del sitio conectado aparecen bajo el nodo **Galería de elementos web** en el **Explorador de servidores**.  
  
8.  Abrir el menú contextual para un elemento web y, a continuación **Propiedades**.  
  
9. En la ventana **Propiedades** , compruebe que aparecen los detalles sobre el elemento web.  
  
10. En **Explorador de servidores**, abra el menú contextual para el mismo elemento web y, a continuación **Mensaje de la pantalla**.  
  
     En el cuadro de mensaje que aparece, elija el botón **Aceptar** .  
  
## Desinstalar la extensión de Visual Studio  
 Después de probar la extensión, desinstalela de Visual Studio.  
  
#### Para desinstalar la extensión  
  
1.  En la instancia experimental de Visual Studio, en la barra de menú, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
     El cuadro de diálogo **Extensiones y actualizaciones** abra.  
  
2.  En la lista de extensiones, elija **Nodo galería de elementos web para el Explorador de servidores**, y elija el botón **Desinstalar** .  
  
3.  En el cuadro de diálogo que aparece, elija el botón **Sí** .  
  
4.  Elija el botón **Reiniciar ahora** para completar la desinstalación.  
  
     También se desinstala el elemento de proyecto.  
  
5.  Cierre ambas instancias de Visual Studio \(la instancia experimental y la instancia de Visual Studio en la que la solución nodoelementoweb está abierto\).  
  
## Vea también  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  