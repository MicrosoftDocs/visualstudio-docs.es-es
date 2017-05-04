---
title: "Walkthrough: Extending a SharePoint Project Item Type | Microsoft Docs"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 1cea4e0f-ce33-4cd7-a664-800184865456
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Walkthrough: Extending a SharePoint Project Item Type
  Puede utilizar el elemento de proyecto **Modelo de catálogo de datos profesionales** para crear un modelo para el servicio Conectividad a datos profesionales \(BDC\) en SharePoint.  De forma predeterminada, al crear un modelo utilizando este elemento de proyecto, los datos del modelo no se muestran a los usuarios.  Por esta razón debe crear una lista externa en SharePoint que permita a los usuarios ver los datos.  
  
 En este tutorial, creará una extensión para el elemento de proyecto **Modelo de conectividad a datos profesionales**.  Los desarrolladores pueden utilizar la extensión para crear una lista externa en sus proyectos que muestre los datos en el modelo BDC.  En este tutorial se muestran las siguientes tareas:  
  
-   Crear una extensión Visual Studio que realiza dos tareas principales:  
  
    -   Genera una lista externa que muestra los datos en un modelo BDC.  La extensión utiliza el modelo de objetos para que el sistema de proyectos de SharePoint genere un archivo Elements.xml que defina la lista.  También agrega el archivo al proyecto para que se implemente junto con el modelo BDC.  
  
    -   Agrega un elemento de menú contextual a los elementos de proyecto **Modelo de conectividad a datos profesionales** en el **Explorador de soluciones**.  Los desarrolladores pueden hacer clic en este elemento de menú para generar una lista externa para el modelo BDC.  
  
-   Compilar un paquete de extensión de Visual Studio \(VSIX\) para implementar el ensamblado de la extensión.  
  
-   Probar la extensión.  
  
## Requisitos previos  
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows, SharePoint y Visual Studio.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  En este tutorial se utiliza la plantilla **Proyecto VSIX** del SDK para crear un paquete VSIX e implementar el elemento.  Para obtener más información, vea [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.  
  
-   El servicio BDC de [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)].  Para obtener más información, vea el tema sobre la [arquitectura de BDC](http://go.microsoft.com/fwlink/?LinkId=177798).  
  
-   El esquema XML de los modelos BDC.  Para obtener más información, vea el tema sobre la [infraestructura del modelo BDC](http://go.microsoft.com/fwlink/?LinkId=177799).  
  
## Crear los proyectos  
 Para completar este tutorial, debe crear dos proyectos:  
  
-   Un proyecto VSIX para crear el paquete VSIX e implementar la extensión de elemento de proyecto.  
  
-   Un proyecto de biblioteca de clases que implemente la extensión de elemento de proyecto.  
  
 Comience el tutorial creando ambos proyectos.  
  
#### Para crear el proyecto VSIX  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
3.  En el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Visual C\#** o **Visual Basic** y, a continuación, elija el nodo **Extensibilidad**.  
  
    > [!NOTE]  
    >  El nodo **Extensibilidad** solo está disponible si se instala Visual Studio SDK.  Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.  
  
4.  En la lista de la parte superior del cuadro de diálogo **Nuevo proyecto**, elija **.NET Framework 4.5**.  
  
     Las extensiones de herramientas de SharePoint requieren características de esta versión de .NET Framework.  
  
5.  Elija la plantilla **Proyecto VSIX**.  
  
6.  En el cuadro **Nombre**, escriba **GenerateExternalDataLists** y elija el botón **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **GenerateExternalDataLists** al **Explorador de soluciones**.  
  
7.  Si el archivo source.extension.vsixmanifest no se abre automáticamente, abra su menú contextual en el proyecto GenerateExternalDataLists y, a continuación, elija **Abrir**.  
  
8.  Compruebe que el archivo source.extension.vsixmanifest tenga una entrada que no esté en blanco \(escriba Contoso\) para el campo Autor, guarde el archivo y ciérrelo.  
  
#### Para crear la extensión de proyecto  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del nodo de la solución **GenerateExternalDataLists**, elija **Agregar** y después **Nuevo proyecto**.  
  
    > [!NOTE]  
    >  En los proyectos de Visual Basic, el nodo de la solución aparece en el **Explorador de soluciones** solo cuando se activa la casilla **Mostrar solución siempre** en [General, Proyectos y soluciones, Cuadro de diálogo Opciones](http://msdn.microsoft.com/es-es/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  En el cuadro de diálogo **Agregar nuevo proyecto**, expanda el nodo **Visual C\#** o **Visual Basic** y, a continuación, elija el nodo **Windows**.  
  
3.  En la lista que aparece en la parte superior del cuadro de diálogo, elija **.NET Framework 4.5**.  
  
4.  En la lista de plantillas de proyecto, elija **Biblioteca de clases**.  
  
5.  En el cuadro **Nombre**, escriba **BdcProjectItemExtension** y elija el botón **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **BdcProjectItemExtension** a la solución y abre el archivo de código predeterminado Class1.  
  
6.  Elimine el archivo de código Class1 del proyecto.  
  
## Configurar el proyecto de extensión  
 Antes de escribir el código para crear la extensión de elemento de proyecto, tiene que agregar los archivos de código y las referencias de ensamblado al proyecto de extensión.  
  
#### Para configurar el proyecto  
  
1.  En el proyecto BdcProjectItemExtension, agregue dos archivos de código que tienen los siguientes nombres:  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  Elija el proyecto BdcProjectItemExtension y, a continuación, en la barra de menús, elija **Proyecto**, **Agregar referencia**.  
  
3.  En el nodo **Ensamblados**, elija el nodo **Framework** y active las casillas de cada uno de los siguientes ensamblados:  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  En el nodo **Ensamblados**, elija el nodo **Extensiones** y active la casilla del ensamblado siguiente:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Elija el botón **Aceptar**.  
  
## Definir la extensión de los elementos de proyecto  
 Cree una clase que defina la extensión del elemento de proyecto **Modelo de conectividad a datos profesionales**.  Para definir la extensión, la clase implementa la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  Implemente esta interfaz para extender un tipo existente de elemento de proyecto todas las veces que desee.  
  
#### Para definir la extensión del elemento de proyecto  
  
1.  Pegue el código siguiente en el archivo de código ProjectItemExtension.  
  
    > [!NOTE]  
    >  Tras agregar este código, el proyecto tendrá algunos errores de compilación.  Estos errores desaparecerán al agregar código en pasos posteriores.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/cs/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/vb/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## Crear listas de datos externas  
 Agregue una definición parcial de la clase `GenerateExternalDataListsExtension` que cree una lista de datos externa para cada entidad del modelo BDC.  Para crear la lista de datos externos, este código lee primero los datos de entidad del modelo BDC mediante el análisis de los datos XML del archivo del modelo BDC.  A continuación, crea una instancia de la lista basada en el modelo BDC y la agrega al proyecto.  
  
#### Para crear las listas de datos externas  
  
1.  Pegue el código siguiente en el archivo de código GenerateExternalDataLists.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/cs/bdcprojectitemextension/generateexternaldatalists.cs#2)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/vb/bdcprojectitemextension/generateexternaldatalists.vb#2)]  
  
## Punto de control  
 En este punto del tutorial, todo el código de la extensión del elemento de proyecto está en el proyecto.  Compile la solución para asegurarse de que el proyecto se compila sin errores.  
  
#### Para compilar la solución  
  
1.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
## Crear un paquete VSIX para implementar la extensión de elemento de proyecto  
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX.  Primero, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest incluido en el proyecto VSIX.  A continuación, cree el paquete VSIX compilando la solución.  
  
#### Para crear y configurar el paquete VSIX  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del archivo source.extension.vsixmanifest en el proyecto GenerateExternalDataLists y, a continuación, elija **Abrir**.  
  
     Visual Studio abre el archivo en el editor de manifiestos.  El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que requieren todos los paquetes VSIX.  Para obtener más información sobre este archivo, vea [Referencia de esquema de extensión VSIX](http://msdn.microsoft.com/es-es/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  En el cuadro **Nombre de producto**, escriba **External Data List Generator**.  
  
3.  En el cuadro **Autor**, escriba **Contoso**.  
  
4.  En el cuadro **Descripción**, escriba **Extensión para los elementos de proyecto de Modelo de conectividad a datos profesionales que se puede utilizar para generar listas de datos externas**.  
  
5.  En la pestaña **Activos** del editor, elija el botón **Nuevo**.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo activo**.  
  
6.  En la lista **Tipo**, elija **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest.  Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX.  Para obtener más información, vea [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/es-es/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  En la lista **Origen**, elija **Un proyecto de la solución actual**.  
  
8.  En la lista **Proyecto**, elija **BdcProjectItemExtension** y, después, elija el botón **Aceptar**.  
  
9. En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
10. Asegúrese de que el proyecto se compila y se crea sin errores.  
  
11. Asegúrese de que la carpeta de salida de la compilación del proyecto GenerateExternalDataLists contiene ahora el archivo GenerateExternalDataLists.vsix.  
  
     De forma predeterminada, la carpeta de salida de la compilación es \\bin\\Debug, ubicada bajo la carpeta que contiene el archivo de proyecto.  
  
## Probar la extensión de elemento de proyecto  
 Ya puede probar la extensión de elemento de proyecto.  Primero, empiece a depurar el proyecto de extensión en la instancia experimental de Visual Studio.  A continuación, utilice la extensión en la instancia experimental de Visual Studio para generar una lista externa para un modelo BDC.  Finalmente, abra la lista externa en el sitio de SharePoint para comprobar que funciona según lo esperado.  
  
#### Para comenzar a depurar la extensión  
  
1.  Si es necesario, reinicie Visual Studio con credenciales administrativas y, a continuación, abra la solución GenerateExternalDataLists.  
  
2.  En el proyecto BdcProjectItemExtension, abra el archivo de código ProjectItemExtension y, a continuación, agregue un punto de interrupción a la línea de código en el método `Initialize`.  
  
3.  Abra el archivo de código GenerateExternalDataLists y, a continuación, agregue un punto de interrupción a la primera línea de código en el método `GenerateExternalDataLists_Execute`.  
  
4.  Empiece a depurar; para ello, elija la tecla F5 o, en la barra de menús, elija **Depurar**, **Iniciar depuración**.  
  
     Visual Studio instala la extensión en %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\External Data List Generator\\1 .0 e inicia una instancia experimental de Visual Studio.  Probará el elemento de proyecto en esta instancia de Visual Studio.  
  
#### Para probar la extensión  
  
1.  En la barra de menús de la instancia experimental de Visual Studio, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, expanda los nodos **Plantillas**, **Visual C\#** y **SharePoint** y, a continuación, elija **2010**.  
  
3.  En la lista que aparece en la parte superior del cuadro de diálogo, asegúrese de que **.NET Framework 3.5** esté seleccionado.  Los proyectos de [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] requieren esta versión de .NET Framework.  
  
4.  En la lista de plantillas de proyecto, elija **Proyecto de SharePoint 2010**.  
  
5.  En el cuadro **Nombre**, escriba **SharePointProjectTestBDC** y elija el botón **Aceptar**.  
  
6.  En el Asistente para personalización de SharePoint, escriba la dirección URL del sitio que desea usar para la depuración, elija **Implementar como solución de granja de servidores** y después elija el botón **Finalizar**.  
  
7.  Abra el menú contextual para el proyecto SharePointProjectTestBDC, elija **Agregar** y, a continuación, **Nuevo elemento**.  
  
8.  En el cuadro de diálogo **Agregar nuevo elemento – SharePointProjectTestBDC**, expanda el nodo de lenguaje instalado y el nodo **SharePoint**.  
  
9. Elija el nodo **2010** y, a continuación, la plantilla **Modelo de conectividad a datos profesionales \(solo en una solución de granja de servidores\)**.  
  
10. En el cuadro **Nombre**, escriba **TestBDCModel** y elija el botón **Agregar**.  
  
11. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `Initialize` del archivo de código ProjectItemExtension.  
  
12. En la instancia detenida de Visual Studio, elija la tecla **F5** o, en la barra de menús, elija **Depurar**, **Continuar** para continuar depurando el proyecto.  
  
13. En la instancia experimental de Visual Studio, elija la tecla **F5** o, en la barra de menús, elija **Depurar**, **Iniciar depuración** para compilar, implementar y ejecutar el proyecto **TestBDCModel**.  
  
     El explorador web se abre en la página predeterminada del sitio de SharePoint que se especifica para la depuración.  
  
14. Compruebe que la sección **Listas** del área Inicio rápido no contiene aún una lista basada en el modelo BDC predeterminado del proyecto.  Primero debe crear una lista de datos externa mediante la interfaz de usuario de SharePoint o la extensión de elemento de proyecto.  
  
15. Cierre el explorador web.  
  
16. En la instancia de Visual Studio que tiene el proyecto TestBDCModel abierto, abra el menú contextual del nodo **TestBDCModel** en el **Explorador de soluciones** y, a continuación, elija **Generate External Data List**.  
  
17. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció en el método `GenerateExternalDataLists_Execute`.  Elija la tecla **F5** o, en la barra de menús, elija **Depurar** y **Continuar** para continuar depurando el proyecto.  
  
18. La instancia experimental de Visual Studio agrega una instancia de la lista denominada **Entity1DataList** al proyecto TestBDCModel, y también genera una característica denominada **Feature2** para la instancia de la lista.  
  
19. Elija la tecla **F5**, o, en la barra de menús, elija **Depurar**, **Iniciar depuración** para compilar, implementar y ejecutar el proyecto TestBDCModel.  
  
     El explorador web se abre en la página predeterminada del sitio de SharePoint que se usa para depurar.  
  
20. En la sección **Listas** del área Inicio rápido, elija la lista **Entity1DataList**.  
  
21. Compruebe que la lista contiene columnas denominadas Identificador1 y Mensaje, además de un elemento con un valor Identificador1 de 0 y un valor Mensaje de Hola a todos.  
  
     La plantilla de proyecto **Modelo de conectividad a datos profesionales** genera el modelo BDC predeterminado que proporciona todos estos datos.  
  
22. Cierre el explorador web.  
  
## Limpiar el equipo de desarrollo  
 Después de probar la extensión de elemento de proyecto, quite la lista externa y modelo BDC del sitio de SharePoint y quite la extensión de elemento de proyecto de Visual Studio.  
  
#### Para quitar la lista de datos externa del sitio de SharePoint  
  
1.  En el área Inicio rápido del sitio de SharePoint, elija la lista **Entity1DataList**.  
  
2.  En la cinta del sitio de SharePoint, elija la pestaña **Lista**.  
  
3.  En la pestaña **Lista**, en el grupo **Configuración**, elija **Configuración de lista**.  
  
4.  En **Permisos y administración**, elija **Eliminar esta lista** y, a continuación, **Aceptar** para confirmar que desea enviar la lista a la Papelera de reciclaje.  
  
5.  Cierre el explorador web.  
  
#### Para quitar el modelo BDC del sitio de SharePoint  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **Compilar**, **Retirar**.  
  
     Visual Studio quita el modelo BDC del sitio de SharePoint.  
  
#### Para quitar la extensión del elemento de proyecto de Visual Studio  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.  
  
2.  En la lista de extensiones, elija **External Data List Generator** y, a continuación, el botón **Desinstalar**.  
  
3.  En el cuadro de diálogo que aparece, elija **Sí** para confirmar que desea desinstalar la extensión.  
  
4.  Elija **Reiniciar ahora** para completar la desinstalación.  
  
5.  Cierre ambas instancias de Visual Studio \(la instancia experimental y la instancia en la que se abre la solución GenerateExternalDataLists\).  
  
## Vea también  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  