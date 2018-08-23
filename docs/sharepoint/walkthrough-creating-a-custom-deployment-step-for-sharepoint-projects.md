---
title: 'Tutorial: Crear un paso de implementación personalizado para proyectos de SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1e5c5856217951d15042f07edb97a918e09ba777
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42635031"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Tutorial: Crear un paso de implementación personalizado para proyectos de SharePoint
  Al implementar un proyecto de SharePoint, Visual Studio ejecuta una serie de pasos de implementación en un orden específico. Visual Studio incluye muchos pasos de implementación integrados, pero también puede crear sus propios.  
  
 En este tutorial, creará un paso de implementación personalizado para actualizar una solución en un servidor que ejecuta SharePoint. Visual Studio incluye pasos de implementación integrados para muchas tareas, tales retiro o incorporación de soluciones, pero no incluye un paso de implementación de actualización de soluciones. De forma predeterminada, al implementar una solución de SharePoint, Visual Studio en primer lugar se retrae la solución (si ya está implementada) y, a continuación, vuelve a implementar toda la solución. Para obtener más información acerca de los pasos de implementación integradas, consulte [implementar, publicar y actualizar paquetes de solución SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear una extensión Visual Studio que realiza dos tareas principales:  
  
    -   La extensión define un paso de implementación personalizado para actualizar las soluciones de SharePoint.  
  
    -   La extensión crea una extensión de proyecto que define una nueva configuración de implementación, que es un conjunto de pasos de implementación que se ejecutan para un proyecto determinado. La nueva configuración de implementación incluye el paso de implementación personalizado y varios pasos de implementación integrados.  
  
-   Cree dos comandos de SharePoint personalizados que llama el ensamblado de extensión. Comandos de SharePoint son métodos que pueden llamarse mediante ensamblados de extensión para usar las API en el modelo de objetos de servidor de SharePoint. Para obtener más información, consulte [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Creación de un paquete de extensión de Visual Studio (VSIX) para implementar los dos ensamblados.  
  
-   Probar el nuevo paso de implementación.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:  
  
-   Ediciones compatibles de Windows, SharePoint y Visual Studio.
  
-   Visual Studio SDK. Este tutorial utiliza el **proyecto VSIX** plantilla en el SDK para crear un paquete VSIX para implementar la extensión. Para obtener más información, consulte [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.  
  
-   Mediante el modelo de objetos de servidor para SharePoint. Para obtener más información, consulte [mediante el modelo de objetos de servidor de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Soluciones de SharePoint. Para obtener más información, consulte [información general sobre soluciones](http://go.microsoft.com/fwlink/?LinkId=169422).  
  
-   Actualizar soluciones SharePoint. Para obtener más información, consulte [actualización de una solución](http://go.microsoft.com/fwlink/?LinkId=177802).  
  
## <a name="create-the-projects"></a>Crear los proyectos
 Para completar este tutorial, debe crear tres proyectos:  
  
-   Un proyecto VSIX para crear el paquete VSIX para implementar la extensión.  
  
-   Un proyecto de biblioteca de clases que implementa la extensión. Este proyecto debe tener como destino .NET Framework 4.5.  
  
-   Un proyecto de biblioteca de clases que define los comandos de SharePoint personalizados. Este proyecto debe tener como destino .NET Framework 3.5.  
  
 Comience el tutorial creando ambos proyectos.  
  
#### <a name="to-create-the-vsix-project"></a>Para crear el proyecto VSIX  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.  
  
3.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos y, a continuación, elija el **extensibilidad** nodo.  
  
    > [!NOTE]  
    >  El **extensibilidad** nodo está disponible solo si instala el SDK de Visual Studio. Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.  
  
4.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4.5** en la lista de versiones de .NET Framework.  
  
5.  Elija la **proyecto VSIX** plantilla, el nombre del proyecto **PasoImplementarActualización**y, a continuación, elija el **Aceptar** botón.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **PasoImplementarActualización** proyecto a **el Explorador de soluciones**.  
  
#### <a name="to-create-the-extension-project"></a>Para crear la extensión de proyecto  
  
1.  En **el Explorador de soluciones**, abra el menú contextual del nodo de solución PasoImplementarActualización, elija **agregar**y, a continuación, elija **nuevo proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos y, a continuación, elija el **Windows** nodo.  
  
3.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4.5** en la lista de versiones de .NET Framework.  
  
4.  Elija la **biblioteca de clases** plantilla de proyecto, asigne al proyecto **ExtensiónPasoImplementación**y, a continuación, elija el **Aceptar** botón.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **ExtensiónPasoImplementación** proyecto a la solución y abre el archivo de código predeterminado Class1.  
  
5.  Elimine el archivo de código Class1 del proyecto.  
  
#### <a name="to-create-the-sharepoint-command-project"></a>Para crear el proyecto de comando de SharePoint  
  
1.  En **el Explorador de soluciones**, abra el menú contextual del nodo de solución PasoImplementarActualización, elija **agregar**y, a continuación, elija **nuevo proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, expanda **Visual C#** o **Visual Basic**y, a continuación, elija el **Windows** nodo.  
  
3.  En la parte superior del cuadro de diálogo, elija **.NET Framework 3.5** en la lista de versiones de .NET Framework.  
  
4.  Elija la **biblioteca de clases** plantilla de proyecto, asigne al proyecto **SharePointCommands**y, a continuación, elija el **Aceptar** botón.  
  
     Visual Studio agrega el **SharePointCommands** proyecto a la solución y abre el archivo de código predeterminado Class1.  
  
5.  Elimine el archivo de código Class1 del proyecto.  
  
## <a name="configure-the-projects"></a>Configurar los proyectos
 Antes de escribir código para crear el paso de implementación personalizado, debe agregar referencias a ensamblados y archivos de código, y debe configurar los proyectos.  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>Para configurar el proyecto ExtensiónPasoImplementación
  
1.  En el **ExtensiónPasoImplementación** del proyecto, agregue dos archivos de código que tienen los nombres siguientes:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Abra el menú contextual en el proyecto ExtensiónPasoImplementación y, a continuación, elija **Agregar referencia**.  
  
3.  En el **Framework** ficha, active la casilla de verificación para el ensamblado System.ComponentModel.Composition.  
  
4.  En el **extensiones** , seleccione la casilla de verificación para el ensamblado Microsoft.VisualStudio.SharePoint y, a continuación, elija el **Aceptar** botón.  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Para configurar el proyecto SharePointCommands
  
1.  En el **SharePointCommands** proyecto, agregue un archivo de código llamado Commands.  
  
2.  En **el Explorador de soluciones**, abra el menú contextual en el **SharePointCommands** nodo de proyecto y, a continuación, elija **Agregar referencia**.  
  
3.  En el **extensiones** ficha, active las casillas para los ensamblados siguientes y, a continuación, haga clic en elegir la **Aceptar** botón  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="define-the-custom-deployment-step"></a>Definir el paso de implementación personalizado
 Cree una clase que define el paso de implementación de actualización. Para definir el paso de implementación, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfaz. Implemente esta interfaz siempre que desee definir un paso de implementación personalizado.  
  
#### <a name="to-define-the-custom-deployment-step"></a>Para definir el paso de implementación personalizado  
  
1.  En el **ExtensiónPasoImplementación** del proyecto, abra el archivo de código UpgradeStep y, a continuación, pegue el código siguiente en él.  
  
    > [!NOTE]  
    >  Después de agregar este código, el proyecto tendrá algunos errores de compilación, pero desaparecerán cuando agregue código en pasos posteriores.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Crear una configuración de implementación que incluye el paso de implementación personalizado
 Crear una extensión de proyecto para la nueva configuración de implementación, que incluye varios pasos de implementación integrados y el nuevo paso de implementación de actualización. Mediante la creación de esta extensión, ayudan a los desarrolladores de SharePoint para usar el paso de implementación de actualización en los proyectos de SharePoint.  
  
 Para crear la configuración de implementación, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaz. Implemente esta interfaz cuando quiera crear una extensión de proyecto de SharePoint.  
  
#### <a name="to-create-the-deployment-configuration"></a>Para crear la configuración de implementación  
  
1.  En el **ExtensiónPasoImplementación** del proyecto, abra el archivo de código DeploymentConfigurationExtension y, a continuación, pegue el código siguiente en él.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="create-the-custom-sharepoint-commands"></a>Crear los comandos de SharePoint personalizados
 Cree dos comandos personalizados que llamen al modelo de objetos de servidor de SharePoint. Un comando determina si ya se implementó una solución; el otro comando actualiza una solución.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Para definir los comandos de SharePoint  
  
1.  En el **SharePointCommands** del proyecto, abra el archivo de código de comandos y, a continuación, pegue el código siguiente en él.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>Punto de control  
 En este punto del tutorial, todo el código para el paso de implementación personalizado y los comandos de SharePoint están en los proyectos. Compilar, para asegurarse de que compila sin errores.  
  
#### <a name="to-build-the-projects"></a>Para compilar los proyectos  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el **ExtensiónPasoImplementación** del proyecto y, a continuación, elija **compilar**.  
  
2.  Abra el menú contextual para el **SharePointCommands** del proyecto y, a continuación, elija **compilar**.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Crear un paquete VSIX para implementar la extensión
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX. En primer lugar, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest del proyecto VSIX. A continuación, crear el paquete VSIX compilando la solución.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Para crear y configurar el paquete VSIX  
  
1.  En **el Explorador de soluciones**, en el **PasoImplementarActualización** de proyecto, abra el menú contextual para el **source.extension.vsixmanifest** de archivo y, a continuación, elija  **Abra**.  
  
     Visual Studio abre el archivo en el editor de manifiestos. El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que requieren todos los paquetes VSIX. Para obtener más información acerca de este archivo, consulte [referencia de 1.0 del esquema de extensión de VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  En el **Product Name** , escriba **actualizar el paso de implementación para proyectos de SharePoint**.  
  
3.  En el **autor** , escriba **Contoso**.  
  
4.  En el **descripción** , escriba **proporciona un paso de implementación de actualización personalizada que se puede usar en proyectos de SharePoint**.  
  
5.  En el **activos** pestaña del editor, elija la **New** botón.  
  
     El **Agregar nuevo activo** aparece el cuadro de diálogo.  
  
6.  En el **tipo** elija **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest. Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX. Para obtener más información, consulte [elemento MEFComponent (Esquema VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  En el **origen** elija **un proyecto de la solución actual**.  
  
8.  En el **proyecto** elija **ExtensiónPasoImplementación**y, a continuación, elija el **Aceptar** botón.  
  
9. En el editor de manifiestos, elija el **New** nuevamente en el botón.  
  
     El **Agregar nuevo activo** aparece el cuadro de diálogo.  
  
10. En el **tipo** lista, escriba **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Este elemento especifica una extensión personalizada que se va a incluir en la extensión de Visual Studio. Para obtener más información, consulte [elemento activo (Esquema VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. En el **origen** elija **un proyecto de la solución actual**.  
  
12. En el **proyecto** elija **SharePointCommands**y, a continuación, elija el **Aceptar** botón.  
  
13. En la barra de menús, elija **compilar** > **compilar solución**y, a continuación, asegúrese de que la solución se compila sin errores.  
  
14. Asegúrese de que la carpeta de salida de compilación del proyecto PasoImplementarActualización contiene ahora el archivo PasoImplementarActualización.vsix.  
  
     De forma predeterminada, la carpeta de salida de la compilación es \bin\Debug, ubicada bajo la carpeta que contiene el archivo de proyecto.  
  
## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Prepararse para probar el paso de implementación de actualización
 Para probar el paso de implementación de actualización, primero debe implementar una solución de ejemplo en el sitio de SharePoint. Comience por depurar la extensión en la instancia experimental de Visual Studio. A continuación, cree una definición de lista y una instancia de lista para usar para probar el paso de implementación y, a continuación, implementarlos en el sitio de SharePoint. A continuación, modifique la definición y la instancia de la lista y volver a implementarlos para demostrar cómo el proceso de implementación predeterminado sobrescribe las soluciones en el sitio de SharePoint.  
  
 Más adelante en este tutorial, modificará la definición y la instancia de la lista y, a continuación, se actualizará en el sitio de SharePoint.  
  
#### <a name="to-start-debugging-the-extension"></a>Para comenzar a depurar la extensión  
  
1.  Reinicie Visual Studio con credenciales administrativas y, a continuación, abra la solución PasoImplementarActualización.  
  
2.  En el proyecto ExtensiónPasoImplementación, abra el archivo de código UpgradeStep y, a continuación, agregue un punto de interrupción a la primera línea de código en el `CanExecute` y `Execute` métodos.  
  
3.  Iniciar la depuración eligiendo el **F5** clave o, en la barra de menús, elija **depurar** > **Iniciar depuración**.  
  
4.  Visual Studio instala la extensión a %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade paso de implementación de SharePoint Projects\1.0 e inicia una instancia experimental de Visual Studio. Probará el paso de implementación de actualización en esta instancia de Visual Studio.  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Para crear un proyecto de SharePoint con una definición de lista y una instancia de lista  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **archivo** > **New** > **proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** nodo o la **Visual Basic** nodo, expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.  
  
3.  En la parte superior del cuadro de diálogo, asegúrese de que **.NET Framework 3.5** aparece en la lista de versiones de .NET Framework.  
  
     Proyectos para [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] requieren esta versión de .NET Framework.  
  
4.  En la lista de plantillas de proyecto, elija **proyecto de SharePoint 2010**, denomine el proyecto **DefiniciónListaEmpleados**y, a continuación, elija el **Aceptar** botón.  
  
5.  En el **Asistente de personalización de SharePoint**, escriba la dirección URL del sitio que desea usar para la depuración.  
  
6.  En **¿qué es el nivel de confianza para esta solución de SharePoint**, elija el **implementar como solución de granja de servidores** botón de opción.  
  
    > [!NOTE]  
    >  El paso de implementación de actualización no es compatible con soluciones en espacio aislado.  
  
7.  Elija la **finalizar** botón.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el proyecto DefiniciónListaEmpleados.  
  
8.  Abra el menú contextual para el proyecto DefiniciónListaEmpleados, elija **agregar**y, a continuación, elija **nuevo elemento**.  
  
9. En el **Agregar nuevo elemento - DefiniciónListaEmpleados** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.  
  
10. Elija la **lista** plantilla de elemento, nombre del elemento **lista de los empleados**y, a continuación, elija el **agregar** botón.  
  
     Aparece el Asistente de personalización de SharePoint  
  
11. En el **elegir configuración de la lista** página, compruebe la siguiente configuración y, a continuación, elija el **finalizar** botón:  
  
    1.  **Lista de los empleados** aparece en el **qué nombre desea mostrar para la lista?** cuadro.  
  
    2.  El **crear una lista personalizable basada en:** se elige el botón de opción.  
  
    3.  **Predeterminado (en blanco)** se elige en la **crear una lista personalizable basada en:** lista.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el elemento de lista de los empleados con una columna de título y una única instancia vacía y se abre el Diseñador de la lista.  
  
12. En el Diseñador de la lista, en el **columnas** ficha, elija la **escriba un nombre de columna nuevo o existente** fila y, a continuación, agregue las siguientes columnas de la **nombre para mostrar columna** lista:  
  
    1.  Nombre  
  
    2.  Organización  
  
    3.  Teléfono del trabajo  
  
    4.  Correo electrónico  
  
13. Guarde todos los archivos y, a continuación, cierre el Diseñador de la lista.  
  
14. En **el Explorador de soluciones**, expanda el **lista de los empleados** nodo y, a continuación, expanda el **instancia de la lista de los empleados** nodo secundario.  
  
15. En el *Elements.xml* de archivo, reemplace el XML predeterminado de este archivo con el siguiente código XML. Este código XML cambia el nombre de la lista para **empleados** y agrega información de un empleado que tiene con Jim Hance.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. Guarde y cierre el *Elements.xml* archivo.  
  
17. Abra el menú contextual para el proyecto DefiniciónListaEmpleados y, a continuación, elija **abierto** o **propiedades**.  
  
     Se abre el Diseñador de propiedades.  
  
18. En el **SharePoint** ficha, desactive la **retraer automáticamente después de depurar** casilla de verificación y, a continuación, guardar las propiedades.  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Para implementar la definición de lista y la instancia de lista  
  
1.  En **el Explorador de soluciones**, elija el **DefiniciónListaEmpleados** nodo del proyecto.  
  
2.  En el **propiedades** ventana, asegúrese de que el **Active Deployment Configuration** propiedad está establecida en **predeterminado**.  
  
3.  Elija la **F5** clave o, en la barra de menús, elija **depurar** > **Iniciar depuración**.  
  
4.  Compruebe que el proyecto se compila correctamente, que se abre el explorador web en el sitio de SharePoint, que el **enumera** incluye el nuevo elemento en la barra Inicio rápido **empleados** lista y que la  **Los empleados** lista incluye la entrada de Jim Hance.  
  
5.  Cierre el explorador web.  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Para modificar la definición y la instancia de la lista y volver a implementarlos  
  
1.  En el proyecto DefiniciónListaEmpleados, abra el *Elements.xml* archivo que es un elemento secundario de la **instancia de la lista de empleados** elemento de proyecto.  
  
2.  Quitar el `Data` elemento y sus elementos secundarios para quitar la entrada de Jim Hance de la lista.  
  
     Cuando haya terminado, el archivo debe contener el siguiente código XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Guarde y cierre el *Elements.xml* archivo.  
  
4.  Abra el menú contextual para el **lista de los empleados** de elemento de proyecto y, a continuación, elija **abierto** o **propiedades**.  
  
5.  En el Diseñador de la lista, elija el **vistas** ficha.  
  
6.  En el **columnas seleccionadas** elija **datos adjuntos**y, a continuación, elija el < clave para mover dicha columna a la **columnas disponibles** lista.  
  
7.  Repita el paso anterior para mover el **teléfono** columna desde la **columnas seleccionadas** lista para la **columnas disponibles** lista.  
  
     Esta acción quita estos campos de la vista predeterminada de la **empleados** lista en el sitio de SharePoint.  
  
8.  Iniciar la depuración eligiendo el **F5** clave o, en la barra de menús, elija **depurar** > **Iniciar depuración**.  
  
9. Compruebe que la **conflictos de implementación** aparece el cuadro de diálogo.  
  
     Este cuadro de diálogo aparece cuando Visual Studio intenta implementar una solución (la instancia de lista) en un sitio de SharePoint a la que ya se ha implementado esa solución. Este cuadro de diálogo no aparecerá cuando se ejecuta el paso de implementación de actualización más adelante en este tutorial.  
  
10. En el **conflictos de implementación** diálogo cuadro, elija el **resolver automáticamente** botón de opción.  
  
     Visual Studio elimina la instancia de lista en el sitio de SharePoint, implementa el elemento de lista en el proyecto y, a continuación, abre el sitio de SharePoint.  
  
11. En el **enumera** sección de la barra Inicio rápido, elija el **empleados** lista y, a continuación, compruebe los detalles siguientes:  
  
    -   El **datos adjuntos** y **Home Phone** columnas no aparecen en esta vista de la lista.  
  
    -   La lista está vacía. Si usa el **predeterminado** configuración de implementación para volver a implementar la solución, el **empleados** lista se ha reemplazado por la nueva lista vacía en el proyecto.  
  
## <a name="test-the-deployment-step"></a>Probar el paso de implementación
 Ahora está listo para probar el paso de implementación de actualización. En primer lugar, agregue un elemento a la instancia de lista en SharePoint. A continuación, cambie la definición de lista y la instancia de lista, actualizarlos en el sitio de SharePoint y confirme que el paso de implementación de actualización no sobrescribe el nuevo elemento.  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>Para agregar manualmente un elemento a la lista  
  
1.  En la cinta de opciones en el sitio de SharePoint, en la **herramientas de lista** ficha, elija la **elementos** ficha.  
  
2.  En el **New** grupo, elija **nuevo elemento**.  
  
     Como alternativa, puede elegir el **Agregar nuevo elemento** en la lista de elementos en el propio vínculo.  
  
3.  En el **empleados - nuevo elemento** ventana, en el **título** , escriba **instalaciones Manager**.  
  
4.  En el **nombre** , escriba **Andy**.  
  
5.  En el **empresa** , escriba **Contoso**.  
  
6.  Elija la **guardar** botón, compruebe que el nuevo elemento aparece en la lista y, a continuación, cierre el explorador web.  
  
     Más adelante en este tutorial, usará este elemento para comprobar que el paso de implementación de actualización no sobrescribe el contenido de esta lista.  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>Para probar el paso de implementación de actualización  
  
1.  En la instancia experimental de Visual Studio, en **el Explorador de soluciones**, abra el menú contextual para el **DefiniciónListaEmpleados** nodo de proyecto y, a continuación, elija **propiedades**.  
  
     Se abre el diseñador/Editor de propiedades.  
  
2.  En el **SharePoint** pestaña, establezca el **Active Deployment Configuration** propiedad **actualizar**.  
  
     Esta configuración de implementación personalizado incluye el nuevo paso de implementación de actualización.  
  
3.  Abra el menú contextual para el **lista de los empleados** de elemento de proyecto y, a continuación, elija **propiedades** o **abierto**.  
  
     Se abre el diseñador/Editor de propiedades.  
  
4.  En el **vistas** ficha, elija la **correo electrónico** columna y, a continuación, elija el **<** clave para mover dicha columna desde la **seleccionado columnas**lista para la **columnas disponibles** lista.  
  
     Esta acción quita estos campos de la vista predeterminada de la **empleados** lista en el sitio de SharePoint.  
  
5.  Iniciar la depuración eligiendo el **F5** clave o, en la barra de menús, elija **depurar** > **Iniciar depuración**.  
  
6.  Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `CanExecute`.  
  
7.  Elija la **F5** clave nuevo o, en la barra de menús, elija **depurar** > **continuar**.  
  
8.  Compruebe que el código se detiene en el punto de interrupción que estableció anteriormente en el `Execute` método.  
  
9. Elija la **F5** clave o, en la barra de menús, elija **depurar** > **continuar** una última vez.  
  
     El explorador web abrirá el sitio de SharePoint.  
  
10. En el **enumera** sección del área Inicio rápido, elija el **empleados** lista y, a continuación, compruebe los detalles siguientes:  
  
    -   El elemento que ha agregado manualmente anteriormente (por Andy, el Administrador de servicios) todavía está en la lista.  
  
    -   El **teléfono** y **dirección de correo electrónico** columnas no aparecen en esta vista de la lista.  
  
     El **actualizar** modifica de configuración de implementación existente **empleados** instancia de lista en el sitio de SharePoint. Si ha usado el **predeterminado** configuración de implementación en lugar de la **actualizar** configuración, podría producirse un conflicto de implementación. Visual Studio podría resolver el conflicto si se reemplaza el **empleados** lista y el elemento de Andy, el Administrador de instalaciones, se eliminarán.  
  
## <a name="clean-up-the-development-computer"></a>Limpiar el equipo de desarrollo
 Cuando termine de probar el paso de implementación de actualización, quite la instancia de lista y la definición de lista del sitio de SharePoint y quitar la extensión de paso de implementación de Visual Studio.  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Para quitar la instancia de lista del sitio de SharePoint  
  
1.  Abra el **empleados** lista en el sitio de SharePoint, si la lista no está abierta.  
  
2.  En la cinta de opciones en el sitio de SharePoint, elija el **herramientas de lista** pestaña y, a continuación, elija el **lista** ficha.  
  
3.  En el **configuración** grupo, elija la **configuración de la lista** elemento.  
  
4.  En **permisos y administración**, elija el **eliminar esta lista** de comandos, elija **Aceptar** para confirmar que desea enviar la lista a la Papelera de reciclaje y, a continuación, cierre la web Explorador.  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Para quitar la definición de lista del sitio de SharePoint  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **compilar** > **Retract**.  
  
     Visual Studio retira la definición de lista del sitio de SharePoint.  
  
#### <a name="to-uninstall-the-extension"></a>Para desinstalar la extensión  
  
1.  En la instancia experimental de Visual Studio, en la barra de menús, elija **herramientas** > **extensiones y actualizaciones**.  
  
     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.  
  
2.  En la lista de extensiones, elija **actualizar el paso de implementación para proyectos de SharePoint**y, a continuación, elija el **desinstalar** comando.  
  
3.  En el cuadro de diálogo que aparece, elija **Sí** para confirmar que desea desinstalar la extensión y, a continuación, elija **reiniciar ahora** para completar la desinstalación.  
  
4.  Cierre ambas instancias de Visual Studio (la instancia experimental y la instancia de Visual Studio en el que está abierta la solución PasoImplementarActualización).  
  
## <a name="see-also"></a>Vea también
 [Ampliar la implementación y empaquetado de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
