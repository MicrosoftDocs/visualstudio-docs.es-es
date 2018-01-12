---
title: 'Tutorial: Extender un tipo de elemento de proyecto de SharePoint | Documentos de Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e2f39fc15d73b2019e739d7695f40cf0e3fd0940
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-extending-a-sharepoint-project-item-type"></a>Tutorial: Extender un tipo de elemento de proyecto de SharePoint
  Puede usar el **modelo de conectividad a datos empresariales** elemento de proyecto para crear un modelo para el servicio de conectividad de datos profesionales (BDC) en SharePoint. De forma predeterminada, al crear un modelo utilizando este elemento de proyecto, los datos del modelo no se muestran a los usuarios. Por esta razón debe crear una lista externa en SharePoint que permita a los usuarios ver los datos.  
  
 En este tutorial, creará una extensión para el **modelo de conectividad a datos empresariales** elemento de proyecto. Los desarrolladores pueden utilizar la extensión para crear una lista externa en sus proyectos que muestre los datos en el modelo BDC. En este tutorial se muestran las siguientes tareas:  
  
-   Crear una extensión Visual Studio que realiza dos tareas principales:  
  
    -   Genera una lista externa que muestra los datos en un modelo BDC. La extensión utiliza el modelo de objetos para que el sistema de proyectos de SharePoint genere un archivo Elements.xml que defina la lista. También agrega el archivo al proyecto para que se implemente junto con el modelo BDC.  
  
    -   Agrega un elemento de menú contextual para el **modelo de conectividad a datos empresariales** elementos de proyecto en **el Explorador de soluciones**. Los desarrolladores pueden hacer clic en este elemento de menú para generar una lista externa para el modelo BDC.  
  
-   Compilar un paquete de extensión de Visual Studio (VSIX) para implementar el ensamblado de la extensión.  
  
-   Probar la extensión.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows, SharePoint y Visual Studio. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Este tutorial se utiliza la **proyecto VSIX** plantilla en el SDK para crear un paquete VSIX para implementar el elemento de proyecto. Para obtener más información, consulte [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.  
  
-   El servicio BDC de [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]. Para obtener más información, consulte [arquitectura de BDC](http://go.microsoft.com/fwlink/?LinkId=177798).  
  
-   El esquema XML de los modelos BDC. Para obtener más información, consulte [infraestructura del modelo BDC](http://go.microsoft.com/fwlink/?LinkId=177799).  
  
## <a name="creating-the-projects"></a>Crear los proyectos  
 Para completar este tutorial, debe crear dos proyectos:  
  
-   Un proyecto VSIX para crear el paquete VSIX e implementar la extensión de elemento de proyecto.  
  
-   Un proyecto de biblioteca de clases que implemente la extensión de elemento de proyecto.  
  
 Comience el tutorial creando ambos proyectos.  
  
#### <a name="to-create-the-vsix-project"></a>Para crear el proyecto VSIX  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
3.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos y, a continuación, elija la **extensibilidad** nodo.  
  
    > [!NOTE]  
    >  El **extensibilidad** nodo solo está disponible si instala el SDK de Visual Studio. Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.  
  
4.  En la lista en la parte superior de la **nuevo proyecto** diálogo cuadro, elija **.NET Framework 4.5**.  
  
     Las extensiones de herramientas de SharePoint requieren características de esta versión de .NET Framework.  
  
5.  Elija la **proyecto VSIX** plantilla.  
  
6.  En el **nombre** cuadro, escriba **GenerateExternalDataLists**y, a continuación, elija la **Aceptar** botón.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Agrega el **GenerateExternalDataLists** proyecto al **el Explorador de soluciones**.  
  
7.  Si el archivo source.extension.vsixmanifest no se abre automáticamente, abra su menú contextual en el proyecto GenerateExternalDataLists y, a continuación, elija **abrir**  
  
8.  Compruebe que el archivo source.extension.vsixmanifest tenga una entrada que no esté en blanco (escriba Contoso) para el campo Autor, guarde el archivo y ciérrelo.  
  
#### <a name="to-create-the-extension-project"></a>Para crear la extensión de proyecto  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el **GenerateExternalDataLists** nodo de la solución, elija **agregar**y, a continuación, elija **nuevo proyecto**.  
  
2.  En el **Agregar nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos y, a continuación, elija la **Windows** nodo.  
  
3.  En la lista en la parte superior del cuadro de diálogo, elija **.NET Framework 4.5**.  
  
4.  En la lista de plantillas de proyecto, elija **biblioteca de clases**.  
  
5.  En el **nombre** cuadro, escriba **BdcProjectItemExtension**y, a continuación, elija la **Aceptar** botón.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Agrega el **BdcProjectItemExtension** proyecto a la solución y abre el archivo de código predeterminado Class1.  
  
6.  Elimine el archivo de código Class1 del proyecto.  
  
## <a name="configuring-the-extension-project"></a>Configurar el proyecto de extensión  
 Antes de escribir el código para crear la extensión de elemento de proyecto, tiene que agregar los archivos de código y las referencias de ensamblado al proyecto de extensión.  
  
#### <a name="to-configure-the-project"></a>Para configurar el proyecto  
  
1.  En el proyecto BdcProjectItemExtension, agregue dos archivos de código que tienen los siguientes nombres:  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  Elija el proyecto BdcProjectItemExtension y, a continuación, en la barra de menús, elija **proyecto**, **Agregar referencia**.  
  
3.  En el **ensamblados** nodo, elija la **Framework** nodo y seleccione la casilla de verificación para cada uno de los siguientes ensamblados:  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  En el **ensamblados** nodo, elija la **extensiones** nodo y, a continuación, seleccione la casilla de verificación del ensamblado siguiente:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Elija el botón **Aceptar** .  
  
## <a name="defining-the-project-item-extension"></a>Definir la extensión de los elementos de proyecto  
 Cree una clase que defina la extensión para la **modelo de conectividad a datos empresariales** elemento de proyecto. Para definir la extensión, la clase implementa la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>. Implemente esta interfaz para extender un tipo existente de elemento de proyecto todas las veces que desee.  
  
#### <a name="to-define-the-project-item-extension"></a>Para definir la extensión del elemento de proyecto  
  
1.  Pegue el código siguiente en el archivo de código ProjectItemExtension.  
  
    > [!NOTE]  
    >  Tras agregar este código, el proyecto tendrá algunos errores de compilación. Estos errores desaparecerán al agregar código en pasos posteriores.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## <a name="creating-the-external-data-lists"></a>Crear listas de datos externas  
 Agregue una definición parcial de la clase `GenerateExternalDataListsExtension` que cree una lista de datos externa para cada entidad del modelo BDC. Para crear la lista de datos externos, este código lee primero los datos de entidad del modelo BDC mediante el análisis de los datos XML del archivo del modelo BDC. A continuación, crea una instancia de la lista basada en el modelo BDC y la agrega al proyecto.  
  
#### <a name="to-create-the-external-data-lists"></a>Para crear las listas de datos externas  
  
1.  Pegue el código siguiente en el archivo de código GenerateExternalDataLists.  
  
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]  
  
## <a name="checkpoint"></a>Punto de control  
 En este punto del tutorial, todo el código de la extensión del elemento de proyecto está en el proyecto. Compile la solución para asegurarse de que el proyecto se compila sin errores.  
  
#### <a name="to-build-the-solution"></a>Para compilar la solución  
  
1.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item-extension"></a>Crear un paquete VSIX para implementar la extensión de elemento de proyecto  
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX. Primero, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest incluido en el proyecto VSIX. A continuación, cree el paquete VSIX compilando la solución.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Para crear y configurar el paquete VSIX  
  
1.  En **el Explorador de soluciones**, abra el menú contextual del archivo source.extension.vsixmanifest en el proyecto GenerateExternalDataLists y, a continuación, elija **abrir**.  
  
     Visual Studio abre el archivo en el editor de manifiestos. El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que requieren todos los paquetes VSIX. Para obtener más información acerca de este archivo, consulte [referencia de 1.0 de esquema de extensión VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  En el **Product Name** cuadro, escriba **External Data List Generator**.  
  
3.  En el **autor** cuadro, escriba **Contoso**.  
  
4.  En el **descripción** cuadro, escriba **una extensión para los elementos de proyecto de modelo de conectividad a datos empresariales que puede usarse para generar listas de datos externas**.  
  
5.  En el **activos** pestaña del editor, elija la **New** botón.  
  
     El **Agregar nuevo activo** aparece el cuadro de diálogo.  
  
6.  En el **tipo** elija **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest. Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX. Para obtener más información, consulte [elemento MEFComponent (Esquema VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  En el **origen** elija **un proyecto de la solución actual**.  
  
8.  En el **proyecto** elija **BdcProjectItemExtension**y, a continuación, elija la **Aceptar** botón.  
  
9. En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
10. Asegúrese de que el proyecto se compila y se crea sin errores.  
  
11. Asegúrese de que la carpeta de salida de la compilación del proyecto GenerateExternalDataLists contiene ahora el archivo GenerateExternalDataLists.vsix.  
  
     De forma predeterminada, la carpeta de salida de la compilación es \bin\Debug, ubicada bajo la carpeta que contiene el archivo de proyecto.  
  
## <a name="testing-the-project-item-extension"></a>Probar la extensión de elemento de proyecto  
 Ya puede probar la extensión de elemento de proyecto. Primero, empiece a depurar el proyecto de extensión en la instancia experimental de Visual Studio. A continuación, utilice la extensión en la instancia experimental de Visual Studio para generar una lista externa para un modelo BDC. Finalmente, abra la lista externa en el sitio de SharePoint para comprobar que funciona según lo esperado.  
  
#### <a name="to-start-debugging-the-extension"></a>Para comenzar a depurar la extensión  
  
1.  Si es necesario, reinicie Visual Studio con credenciales administrativas y, a continuación, abra la solución GenerateExternalDataLists.  
  
2.  En el proyecto BdcProjectItemExtension, abra el archivo de código ProjectItemExtension y, a continuación, agregue un punto de interrupción a la línea de código en el método `Initialize`.  
  
3.  Abra el archivo de código GenerateExternalDataLists y, a continuación, agregue un punto de interrupción a la primera línea de código en el método `GenerateExternalDataLists_Execute`.  
  
4.  Empiece a depurar eligiendo la tecla F5 o, en la barra de menús, elija **depurar**, **Iniciar depuración**.  
  
     Visual Studio instala la extensión en %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Data List Generator\1 .0 e inicia una instancia experimental de Visual Studio. Probará el elemento de proyecto en esta instancia de Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Para probar la extensión  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **archivo**, **New**, **proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, expanda el **plantillas** nodo, expanda el **Visual C#** nodo, expanda el **SharePoint** nodo y, a continuación, Elija **2010**.  
  
3.  En la lista en la parte superior del cuadro de diálogo, asegúrese de que **.NET Framework 3.5** está seleccionada. Los proyectos de [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] requieren esta versión de .NET Framework.  
  
4.  En la lista de plantillas de proyecto, elija **proyecto de SharePoint 2010**.  
  
5.  En el **nombre** cuadro, escriba **SharePointProjectTestBDC**y, a continuación, elija la **Aceptar** botón.  
  
6.  En el Asistente para la personalización de SharePoint, escriba la dirección URL del sitio que desea usar para la depuración, elija **implementar como solución de granja de servidores**y, a continuación, elija la **finalizar**botón.  
  
7.  Abra el menú contextual para el proyecto SharePointProjectTestBDC, elija **agregar**y, a continuación, elija **nuevo elemento**.  
  
8.  En el **Agregar nuevo elemento-SharePointProjectTestBDC** diálogo cuadro, expanda el nodo de lenguaje instalado, el **SharePoint** nodo.  
  
9. Elija la **2010** nodo y, a continuación, elija la **modelo conectividad a datos profesionales (solución de granja de servidores únicamente)** plantilla.  
  
10. En el **nombre** cuadro, escriba **TestBDCModel**y, a continuación, elija la **agregar** botón.  
  
11. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `Initialize` del archivo de código ProjectItemExtension.  
  
12. En la instancia detenida de Visual Studio, elija la **F5** clave o en la barra de menús, elija **depurar**, **continuar** para continuar depurando el proyecto.  
  
13. En la instancia experimental de Visual Studio, elija la **F5** clave, o bien, en la barra de menús, elija **depurar**, **Iniciar depuración** para compilar, implementar y ejecutar el  **TestBDCModel** proyecto.  
  
     El explorador web se abre en la página predeterminada del sitio de SharePoint que se especifica para la depuración.  
  
14. Compruebe que la **enumera** sección en el área Inicio rápido aún no contiene una lista que se basa en el modelo BDC predeterminado en el proyecto. Primero debe crear una lista de datos externa mediante la interfaz de usuario de SharePoint o la extensión de elemento de proyecto.  
  
15. Cierre el explorador web.  
  
16. En la instancia de Visual Studio que tiene el proyecto TestBDCModel abierto, abra el menú contextual para el **TestBDCModel** nodo **el Explorador de soluciones**y, a continuación, elija **generar datos externos Lista**.  
  
17. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció en el método `GenerateExternalDataLists_Execute`. Elija la **F5** clave, o bien, en la barra de menús, elija **depurar**, **continuar** para continuar depurando el proyecto.  
  
18. La instancia experimental de Visual Studio agrega una instancia de lista que se denomina **Entity1DataList** a TestBDCModel proyecto y genera una característica que se denomina **Feature2** para obtener la lista instancia.  
  
19. Elija la **F5** clave, o bien, en la barra de menús, elija **depurar**, **Iniciar depuración** para compilar, implementar y ejecutar el proyecto TestBDCModel.  
  
     El explorador web se abre en la página predeterminada del sitio de SharePoint que se usa para depurar.  
  
20. En el **enumera** sección del área Inicio rápido, elija la **Entity1DataList** lista.  
  
21. Compruebe que la lista contiene columnas denominadas Identificador1 y Mensaje, además de un elemento con un valor Identificador1 de 0 y un valor Mensaje de Hola a todos.  
  
     El **modelo de conectividad a datos empresariales** plantilla de proyecto genera el modelo BDC predeterminado que proporciona todos estos datos.  
  
22. Cierre el explorador web.  
  
## <a name="cleaning-up-the-development-computer"></a>Limpiar el equipo de desarrollo  
 Después de probar la extensión de elemento de proyecto, quite la lista externa y modelo BDC del sitio de SharePoint y quite la extensión de elemento de proyecto de Visual Studio.  
  
#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Para quitar la lista de datos externa del sitio de SharePoint  
  
1.  En el área Inicio rápido del sitio de SharePoint, elija el **Entity1DataList** lista.  
  
2.  En la cinta de opciones en el sitio de SharePoint, elija el **lista** ficha.  
  
3.  En el **lista** ficha la **configuración** grupo, elija **configuración de la lista**.  
  
4.  En **permisos y administración**, elija **eliminar esta lista**y, a continuación, elija **Aceptar** para confirmar que desea enviar la lista a la Papelera de reciclaje.  
  
5.  Cierre el explorador web.  
  
#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Para quitar el modelo BDC del sitio de SharePoint  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **generar**, **Retract**.  
  
     Visual Studio quita el modelo BDC del sitio de SharePoint.  
  
#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Para quitar la extensión del elemento de proyecto de Visual Studio  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **herramientas**, **extensiones y actualizaciones**.  
  
     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.  
  
2.  En la lista de extensiones, elija **External Data List Generator**y, a continuación, elija la **desinstalar** botón.  
  
3.  En el cuadro de diálogo que aparece, elija **Sí** para confirmar que desea desinstalar la extensión.  
  
4.  Elija **reiniciar ahora** para completar la desinstalación.  
  
5.  Cierre ambas instancias de Visual Studio (la instancia experimental y la instancia en la que se abre la solución GenerateExternalDataLists).  
  
## <a name="see-also"></a>Vea también  
 [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  