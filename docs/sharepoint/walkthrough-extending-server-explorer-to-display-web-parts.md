---
title: "Walkthrough: Extending Server Explorer to Display Web Parts"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 5b1f104a-0eaf-4929-9f1f-d7afcfc8b707
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Walkthrough: Extending Server Explorer to Display Web Parts
  En Visual Studio, puede utilizar el nodo **Conexiones de SharePointExplorador de servidores** para ver componentes en sitios de SharePoint.  Sin embargo, **Explorador de servidores** no muestra algunos componentes de forma predeterminada.  En este tutorial, ampliará **Explorador de servidores** de modo que muestre la galería de elementos web en cada sitio de SharePoint conectado.  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear una extensión de Visual Studio que extiende el **Explorador de servidores** de las maneras siguientes:  
  
    -   La extensión agrega un nodo **Galería de elementos web** bajo cada nodo de sitio de SharePoint en **Explorador de servidores**.  Este nuevo nodo contiene nodos secundarios que representan cada elemento web en la galería de elementos web del sitio.  
  
    -   La extensión define un nuevo tipo de nodo que representa una instancia del elemento web.  Este nuevo tipo de nodo es la base de los nodos secundarios bajo el nuevo nodo **Galería de elementos web**.  El nuevo tipo de nodo Elemento web muestra información en la ventana **Propiedades** sobre el elemento web que representa.  El tipo de nodo también incluye un elemento de menú contextual personalizado que puede utilizar como punto de partida para realizar otras tareas relacionadas con el elemento web.  
  
-   Crear dos comandos de SharePoint personalizados que el ensamblado de la extensión llama.  Los comandos de SharePoint son métodos que se pueden llamar a los ensamblados de la extensión para utilizar las API del modelo de objetos de servidor de SharePoint.  En este tutorial, creará comandos que recuperan información del elemento web del sitio de SharePoint local en el equipo de desarrollo.  Para obtener más información, vea [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Compilar un paquete de extensión de Visual Studio \(VSIX\) para implementar la extensión.  
  
-   Depurar y probar la extensión.  
  
> [!NOTE]  
>  Para obtener una versión alternativa de este tutorial que utiliza el modelo de objetos de cliente de SharePoint en lugar del modelo de objetos de servidor, vea [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## Requisitos previos  
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:  
  
-   Ediciones compatibles de Windows, SharePoint y Visual Studio.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK.  En este tutorial se utiliza la plantilla **Proyecto VSIX** del SDK para crear un paquete VSIX e implementar el elemento.  Para obtener más información, vea [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.  
  
-   Utilizar el modelo de objetos de servidor de SharePoint.  Para obtener más información, vea [Utilizar el modelo de objetos de servidor de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Elementos web en soluciones de SharePoint.  Para obtener más información, vea [Información general sobre elementos web](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## Crear los proyectos  
 Para completar este tutorial, debe crear tres proyectos:  
  
-   Un proyecto VSIX para crear el paquete VSIX e implementar la extensión.  
  
-   Un proyecto de biblioteca de clases que implemente la extensión.  Este proyecto debe tener como destino .NET Framework 4,5.  
  
-   Un proyecto de biblioteca de clases que define los comandos de SharePoint personalizados.  Este proyecto debe tener como destino .NET Framework 3.5.  
  
 Comience el tutorial creando ambos proyectos.  
  
#### Para crear el proyecto VSIX  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menú, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
3.  En el cuadro de diálogo  **Nuevo proyecto** , expanda los nodos **Visual c\#** o **Visual Basic** y, a continuación el nodo **Extensibilidad** .  
  
    > [!NOTE]  
    >  El nodo **Extensibilidad** solo está disponible si instala Visual Studio SDK.  Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.  
  
4.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de .NET Framework.  
  
5.  Elija la plantilla **Proyecto VSIX** , asigne al proyecto **WebPartNode**, y elija el botón **Aceptar** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **NodoElementoWeb** al **Explorador de soluciones**.  
  
#### Para crear la extensión de proyecto  
  
1.  En **Explorador de soluciones**, abra el menú contextual para el nodo de la solución, elija **Agregar**y, a continuación **Nuevo proyecto**.  
  
    > [!NOTE]  
    >  En los proyectos de Visual Basic, el nodo de la solución aparece en el **Explorador de soluciones** solo cuando se activa la casilla **Mostrar solución siempre** en [General, Proyectos y soluciones, Cuadro de diálogo Opciones](http://msdn.microsoft.com/es-es/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  En el cuadro de diálogo **Nuevo proyecto** , expanda el nodo **Visual c\#** o el nodo **Visual Basic** , y el nodo **Windows** choose.  
  
3.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de .NET Framework.  
  
4.  En la lista de plantillas de proyecto, elija **Biblioteca de clases**, asigne al proyecto **WebPartNodeExtension**, y elija el botón **Aceptar** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **ExtensiónNodoElementoWeb** a la solución y abre el archivo de código predeterminado Class1.  
  
5.  Elimine el archivo de código Class1 del proyecto.  
  
#### Para crear el proyecto Comandos de SharePoint  
  
1.  En **Explorador de soluciones**, abra el menú contextual para el nodo de la solución, elija **Agregar**y, a continuación **Nuevo proyecto**.  
  
    > [!NOTE]  
    >  En los proyectos de Visual Basic, el nodo de la solución aparece en el **Explorador de soluciones** solo cuando se activa la casilla **Mostrar solución siempre** en [General, Proyectos y soluciones, Cuadro de diálogo Opciones](http://msdn.microsoft.com/es-es/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  En el cuadro de diálogo  **Nuevo proyecto** , expanda el nodo **Visual c\#** o el nodo **Visual Basic** y, a continuación el nodo **Windows** .  
  
3.  En la parte superior del cuadro de diálogo, elija **.NET Framework 3.5** en la lista de versiones de .NET Framework.  
  
4.  En la lista de plantillas de proyecto, elija **Biblioteca de clases**, asigne al proyecto **WebPartCommands**, y elija el botón **Aceptar** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **WebPartCommands** a la solución y abre el archivo de clase predeterminado Class1.  
  
5.  Elimine el archivo de código Class1 del proyecto.  
  
## Configurar los proyectos  
 Antes de escribir el código para crear la extensión, debe agregar los archivos de código y las referencias de ensamblado, y establece la configuración del proyecto.  
  
#### Para configurar el proyecto ExtensiónNodoElementoWeb  
  
1.  En el proyecto extensiónnodoelementoweb, agregue cuatro archivos de código que tienen los nombres siguientes:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Abrir el menú contextual para el proyecto **WebPartNodeExtension** y, a continuación **Agregar referencia**.  
  
3.  En el cuadro de diálogo **Administrador de referencia – WebPartNodeExtension** , elija la ficha **Framework** , y seleccione la casilla para cada uno de los siguientes ensamblados:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  Elija la ficha **Extensiones** , active la casilla para el ensamblado Microsoft.VisualStudio.SharePoint, y después elija el botón **Aceptar** .  
  
5.  En **Explorador de soluciones**, abra el menú contextual para el nodo del proyecto **WebPartNodeExtension** y, a continuación **Propiedades**.  
  
     Se abrirá el **Diseñador de proyectos**.  
  
6.  Elija la ficha **Aplicación** .  
  
7.  En el cuadro **Espacio de nombres predeterminado** \(C\#\) o el cuadro **Espacio de nombres de la raíz** \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\), escriba en **ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### Para configurar el proyecto WebPartCommands  
  
1.  En el proyecto WebPartCommands, agregue un archivo de código denominado WebPartCommands.  
  
2.  En **Explorador de soluciones**, abra el menú contextual para el nodo del proyecto **WebPartCommands** , elija **Agregar**y, a continuación **Elemento existente**.  
  
3.  En el cuadro de diálogo **Agregar elemento existente** , vaya a la carpeta que contiene los archivos de código del proyecto extensiónnodoelementoweb, elija y luego los archivos de código WebPartCommandIds y WebPartNodeInfo.  
  
4.  Elija la flecha situada junto al botón **Agregar** , y elija **Agregar como vínculo** en el menú que aparece.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega los archivos de código al proyecto WebPartCommands como vínculos.  Como resultado, los archivos de código se encuentran en el proyecto extensiónnodoelementoweb, pero el código en los archivos también se compila en el proyecto WebPartCommands.  
  
5.  Abrir el menú contextual para el proyecto **WebPartCommands** de nuevo, y elija **Agregar referencia**.  
  
6.  En el cuadro de diálogo **Administrador de referencia – WebPartCommands** , elija la ficha **Extensiones** , active la casilla para cada uno de los siguientes ensamblados, y después elija el botón **Aceptar** :  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  En **Explorador de soluciones**, abra el menú contextual para el proyecto **WebPartCommands** de nuevo y, a continuación **Propiedades**.  
  
     Se abrirá el **Diseñador de proyectos**.  
  
8.  Elija la ficha de **Aplicación** .  
  
9. En el cuadro **Espacio de nombres predeterminado** \(C\#\) o el cuadro **Espacio de nombres de la raíz** \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\), escriba en **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## Crear iconos para los nuevos nodos  
 Cree dos iconos para la extensión **Explorador de servidores**: uno para el nuevo nodo **Galería de elementos web** y otro para cada nodo secundario bajo el nodo **Galería de elementos web**.  Más adelante en este tutorial, escribirá código que asocie estos iconos a los nodos.  
  
#### Para crear iconos para los nodos  
  
1.  En **Explorador de soluciones**, abra el menú contextual para el proyecto **WebPartNodeExtension** y, a continuación **Propiedades**.  
  
2.  Se abrirá el **Diseñador de proyectos**.  
  
3.  Elija **la ficha resources**, y después elija **el This que el proyecto no contiene un archivo de recursos predeterminado. Haga clic aquí para establecer una** relaciones.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea un archivo de recursos y lo abre en el diseñador.  
  
4.  En la parte superior del diseñador, elija la flecha situada junto al comando de menú **Agregar recurso** , y elija **Agregar nuevo icono** en el menú que aparece.  
  
5.  En el cuadro de diálogo **Agregar nuevo recurso** , llame al nuevo icono **WebPartsNode**, y elija el botón **Agregar** .  
  
     El nuevo icono se abre en el **Editor de imágenes**.  
  
6.  Modifique la versión 16x16 del icono para que tenga un diseño que pueda fácilmente reconocer.  
  
7.  Abrir el menú contextual para la versión 32x32 del icono y, a continuación **Eliminar tipo de imagen**.  
  
8.  Repita los pasos 5 a 8 para agregar un segundo icono a los recursos del proyecto, y llame a este icono **WebPart**.  
  
9. En **Explorador de soluciones**, bajo la carpeta **RECURSOS** para el proyecto **WebPartNodeExtension** , abra el menú contextual para **WebPartsNode.ico**.  
  
10. En la ventana **Propiedades** , elija la flecha situada junto a **Acción de compilación**, y elija **Recurso incrustado** en el menú que aparece.  
  
11. Repita los últimos dos pasos con **ElementoWeb.ico**.  
  
## Agregar el nodo Galería de elementos web al Explorador de servidores  
 Cree una clase que agregue el nuevo nodo **Galería de elementos web** a cada nodo del sitio de SharePoint.  Para agregarlo, la clase implementa la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Implemente esta interfaz para extender el comportamiento de un nodo existente en **Explorador de servidores**, como agregar un nodo secundario a un nodo.  
  
#### Para agregar el nodo Galería de elementos web al Explorador de servidores  
  
1.  En el proyecto extensiónnodoelementoweb, abra el archivo de código SiteNodeExtension y, a continuación pegue el siguiente código en él.  
  
    > [!NOTE]  
    >  Después de agregar este código, el proyecto tendrá algunos errores de compilación, pero desaparecerán al agregar código en pasos posteriores.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## Definir un tipo de nodo que represente un elemento web  
 Cree una clase que defina un nuevo tipo de nodo que represente un elemento web.  Visual Studio utiliza este nuevo tipo de nodo para mostrar los nodos secundarios del nodo **Galería de elementos web** .  Cada nodo secundario representa un elemento web único en el sitio de SharePoint.  
  
 Para definir el nuevo tipo de nodo, la clase implementa la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Implemente esta interfaz para definir un nuevo tipo de nodo en el **Explorador de servidores** todas las veces que desee.  
  
#### Para definir el tipo de nodo Elemento web  
  
1.  En el proyecto extensiónnodoelementoweb, abra el archivo de código WebPartNodeTypeProvder y, a continuación pegue el siguiente código en él.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## Definir la clase Web Part Data  
 Defina una clase que contenga los datos de un elemento web único del sitio de SharePoint.  Más adelante en este tutorial, creará un comando de SharePoint personalizado que recupera datos de cada elemento web del sitio y después asigne los datos a instancia de esta clase.  
  
#### Para definir la clase Web Part Data  
  
1.  En el proyecto extensiónnodoelementoweb, abra el archivo de código WebPartNodeInfo y, a continuación pegue el siguiente código en él.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodeinfo.cs#3)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodeinfo.vb#3)]  
  
## Definir los identificadores del comando de SharePoint  
 Defina varias cadenas que identifican los comandos de SharePoint personalizados.  Implementará estos comandos más adelante en este tutorial.  
  
#### Para definir los identificadores de comando  
  
1.  En el proyecto extensiónnodoelementoweb, abra el archivo de código WebPartCommandIds y, a continuación pegue el siguiente código en él.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartcommandids.vb#4)]  
  
## Crear los comandos de SharePoint personalizados  
 Cree comandos personalizados que llamen al modelo de objetos de servidor de SharePoint para recuperar datos de los elementos web del sitio de SharePoint.  Cada comando es un método que tiene el <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> aplicado.  
  
#### Para definir los comandos de SharePoint  
  
1.  En el proyecto WebPartCommands, abra el archivo de código WebPartCommands, y luego pegue el siguiente código en él.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartcommands/webpartcommands.vb#6)]  
  
## Punto de control  
 En este punto del tutorial, todo el código del nodo **Galería de elementos web** y los comandos de SharePoint es en los proyectos.  Compile la solución para asegurarse de que ambos proyectos se compilan sin errores.  
  
#### Para compilar la solución  
  
1.  En la barra de menú, elija **Generar**, **Compilar solución**.  
  
    > [!WARNING]  
    >  En este punto, el proyecto nodoelementoweb puede tener un error de compilación porque el archivo de manifiesto VSIX no tiene un valor para el autor.  Este error saldrá cuando se agrega un valor en pasos posteriores.  
  
## Crear un paquete VSIX para implementar la extensión  
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX.  Primero, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest del proyecto VSIX.  A continuación, cree el paquete VSIX compilando la solución.  
  
#### Para configurar el paquete VSIX  
  
1.  En **Explorador de soluciones**, bajo el proyecto nodoelementoweb, abra el archivo **source.extension.vsixmanifest** en el editor de manifiestos.  
  
     El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que todos los paquetes VSIX requieren.  Para obtener más información sobre este archivo, vea [Referencia de esquema de extensión VSIX](http://msdn.microsoft.com/es-es/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  En el cuadro **Nombre de producto** , entre en **Nodo galería de elementos web para el Explorador de servidores**.  
  
3.  En el cuadro **Autor** , entre en **Contoso**.  
  
4.  En **el cuadro** de descripción, entre **agrega un nodo galería de elementos web personalizado al nodo conexiones de SharePoint en el Explorador de servidores. Esta extensión utiliza un comando de SharePoint personalizado para llamar al modelo de objetos de servidor.**  
  
5.  Elija la ficha **Activos** del editor, y elija el botón **Nuevo** .  
  
     El cuadro de diálogo **Agregar nuevo activo** aparece.  
  
6.  En la lista **Tipo** , elija **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest.  Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX.  Para obtener más información, vea [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/es-es/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  En la lista **Origen** , elija **Un proyecto de la solución actual**.  
  
8.  En la lista **Proyecto** , elija **WebPartNodeExtension** y elija el botón **Aceptar** .  
  
9. En el editor de manifiestos, elija el botón **Nuevo** de nuevo.  
  
     El cuadro de diálogo **Agregar nuevo activo** aparece.  
  
10. En el cuadro **Tipo** , entre en **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Este elemento especifica una extensión personalizada que desea incluir en la extensión de Visual Studio.  Para obtener más información, vea [Elemento de activo \(esquema VSX\)](http://msdn.microsoft.com/es-es/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. En la lista **Origen** , elija el elemento de lista **Un proyecto de la solución actual** .  
  
12. En la lista **Proyecto** , elija **WebPartCommands**, y elija el botón **Aceptar** .  
  
13. En la barra de menú, elija **Generar**, **Compilar solución**, y asegúrese de que la solución se compila sin errores.  
  
14. Asegúrese de que la carpeta de salida de la compilación del proyecto nodoelementoweb ahora contiene el archivo nodoelementoweb.vsix.  
  
     De forma predeterminada, la carpeta de resultado de compilación es ..  \\bin\\Debug, que se encuentra bajo la carpeta que contiene el archivo de proyecto.  
  
## Probar la extensión  
 Ya puede probar el nuevo nodo **Galería de elementos web** en **Explorador de servidores**.  Primero, empiece a depurar la extensión en una instancia experimental de Visual Studio.  A continuación, utilice el nuevo nodo **Elementos web** en la instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### Para comenzar a depurar la extensión  
  
1.  Reinicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenciales administrativas, y vuelva a abrir la solución nodoelementoweb.  
  
2.  En el proyecto extensiónnodoelementoweb, abra el archivo de código SiteNodeExtension, y después agregue un punto de interrupción a la primera línea de código en los métodos `NodeChildrenRequested` y `CreateWebPartNodes` .  
  
3.  Elija la tecla F5 para iniciar la depuración.  
  
     Visual Studio instala la extensión en %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Web Part Gallery Node Extension for Server Explorer\\1.0 and starts an experimental instance of Visual Studio.  Probará el elemento de proyecto en esta instancia de Visual Studio.  
  
#### Para probar la extensión  
  
1.  En la instancia experimental [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], en la barra de menú, elija **Ver**, **Explorador de servidores**.  
  
2.  Realice los pasos siguientes si el sitio de SharePoint que desea utilizar para probar no aparece bajo el nodo **Conexiones de SharePoint** en **Explorador de servidores**:  
  
    1.  En **Explorador de servidores**, abra el menú contextual para **Conexiones de SharePoint**y, a continuación **Agregar conexión**.  
  
    2.  En el cuadro de diálogo **Agregar conexión a SharePoint** , escriba la dirección URL para el sitio de SharePoint al que desea conectarse, y elija el botón **Aceptar** .  
  
         Para especificar el sitio de SharePoint en el equipo de desarrollo, entre en **http:\/\/localhost**.  
  
3.  Expanda el nodo de conexión del sitio \(que muestra la dirección URL del sitio\) y, a continuación expanda un nodo de sitio secundario \(por ejemplo, **Sitio del equipo**\).  
  
4.  Compruebe que el código de la otra instancia [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] detiene en el punto de interrupción que estableció anteriormente en el método `NodeChildrenRequested` , elija y luego F5 para continuar y depurar el proyecto.  
  
5.  En la instancia experimental de Visual Studio, compruebe que un nuevo nodo denominado **Galería de elementos web** aparece bajo el nodo del sitio de nivel superior, y expanda el nodo **Galería de elementos web** .  
  
6.  Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `CreateWebPartNodes` , y elija la tecla F5 para continuar y depurar el proyecto.  
  
7.  En la instancia experimental de Visual Studio, compruebe que todos los elementos web del sitio conectado aparecen bajo el nodo **Galería de elementos web** en **Explorador de servidores**.  
  
8.  En **Explorador de servidores**, abra el menú contextual para uno de los elementos web y, a continuación **Propiedades**.  
  
9. En la instancia [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que está depurando, compruebe que los detalles sobre el elemento web aparecen en la ventana **Propiedades** .  
  
## Desinstalar la extensión de Visual Studio  
 Después de terminar de probar la extensión, desinstale la extensión de Visual Studio.  
  
#### Para desinstalar la extensión  
  
1.  En la instancia experimental [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], en la barra de menú, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
     El cuadro de diálogo **Extensiones y actualizaciones** abra.  
  
2.  En la lista de extensiones, elija **Extensión de Nodos de la galería de elementos web para el Explorador de servidores**, y elija el botón **Desinstalar** .  
  
3.  En el cuadro de diálogo que aparece, elija el botón **Sí** para confirmar que desea desinstalar la extensión, y elija el botón **Reiniciar ahora** para completar la desinstalación.  
  
4.  Cierre ambas instancias de Visual Studio \(la instancia experimental y la instancia de Visual Studio en la que la solución nodoelementoweb está abierto\).  
  
## Vea también  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  