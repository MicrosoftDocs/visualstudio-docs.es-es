---
title: Crear un paso de implementación personalizado para proyectos de SharePoint
description: En este tutorial, creará un paso de implementación personalizado para actualizar las soluciones de proyecto de SharePoint en un servidor que ejecute SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 77c80134ad63346b363c072ef2eff7e49978501f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217936"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint
  Al implementar un proyecto de SharePoint, Visual Studio ejecuta una serie de pasos de implementación en un orden específico. Visual Studio incluye muchos pasos de implementación integrados, pero también puede crear los suyos propios.

 En este tutorial, creará un paso de implementación personalizado para actualizar soluciones en un servidor que ejecuta SharePoint. Visual Studio incluye pasos de implementación integrados para muchas tareas, como retirar o agregar soluciones, pero no incluye un paso de implementación para actualizar las soluciones. De forma predeterminada, al implementar una solución de SharePoint, Visual Studio retrae primero la solución (si ya está implementada) y, a continuación, vuelve a implementar toda la solución. Para obtener más información acerca de los pasos de implementación integrados, vea [implementar, publicar y actualizar paquetes de soluciones de SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

 En este tutorial se muestran las siguientes tareas:

- Crear una extensión Visual Studio que realiza dos tareas principales:

  - La extensión define un paso de implementación personalizado para actualizar las soluciones de SharePoint.

  - La extensión crea una extensión de proyecto que define una nueva configuración de implementación, que es un conjunto de pasos de implementación que se ejecutan para un proyecto determinado. La nueva configuración de implementación incluye el paso de implementación personalizada y varios pasos de implementación integrados.

- Cree dos comandos personalizados de SharePoint a los que llama el ensamblado de extensión. Los comandos de SharePoint son métodos a los que pueden llamar los ensamblados de extensión para usar las API en el modelo de objetos de servidor para SharePoint. Para obtener más información, consulte [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Compilar un paquete de extensión de Visual Studio (VSIX) para implementar ambos ensamblados.

- Prueba del nuevo paso de implementación.

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:

- Ediciones compatibles de Windows, SharePoint y Visual Studio.

- Visual Studio SDK. En este tutorial se usa la plantilla de **Proyecto VSIX** en el SDK para crear un paquete VSIX para implementar la extensión. Para obtener más información, vea [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.

- Usar el modelo de objetos de servidor para SharePoint. Para obtener más información, vea [usar el modelo de objetos de SharePoint Foundation Server-Side](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- Soluciones de SharePoint. Para obtener más información, vea [información general sobre soluciones](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

- Actualizar soluciones de SharePoint. Para obtener más información, vea [actualizar una solución](/previous-versions/office/developer/sharepoint-2010/aa543659(v=office.14)).

## <a name="create-the-projects"></a>Crear los proyectos
 Para completar este tutorial, debe crear tres proyectos:

- Un proyecto VSIX para crear el paquete VSIX para implementar la extensión.

- Proyecto de biblioteca de clases que implementa la extensión. Este proyecto debe tener como destino el .NET Framework 4,5.

- Proyecto de biblioteca de clases que define los comandos de SharePoint personalizados. Este proyecto debe tener como destino el .NET Framework 3,5.

  Comience el tutorial creando ambos proyectos.

#### <a name="to-create-the-vsix-project"></a>Para crear el proyecto VSIX

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

3. En el cuadro de diálogo **nuevo proyecto** , expanda los nodos **Visual C#** o **Visual Basic** y, a continuación, elija el nodo **extensibilidad** .

    > [!NOTE]
    > El nodo **extensibilidad** solo está disponible si instala el SDK de Visual Studio. Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.

4. En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de la .NET Framework.

5. Elija la plantilla de **Proyecto VSIX** , asigne al proyecto el nombre **UpgradeDeploymentStep** y, a continuación, elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **UpgradeDeploymentStep** a **Explorador de soluciones**.

#### <a name="to-create-the-extension-project"></a>Para crear la extensión de proyecto

1. En **Explorador de soluciones**, abra el menú contextual del nodo de la solución UpgradeDeploymentStep, elija **Agregar** y, a continuación, elija **nuevo proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , expanda los nodos **Visual C#** o **Visual Basic** y, a continuación, elija el nodo **Windows** .

3. En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de la .NET Framework.

4. Elija la plantilla de proyecto **biblioteca de clases** , asigne al proyecto el nombre **DeploymentStepExtension** y, a continuación, elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **DeploymentStepExtension** a la solución y abre el archivo de código predeterminado Class1.

5. Elimine el archivo de código Class1 del proyecto.

#### <a name="to-create-the-sharepoint-command-project"></a>Para crear el proyecto de comandos de SharePoint

1. En **Explorador de soluciones**, abra el menú contextual del nodo de la solución UpgradeDeploymentStep, elija **Agregar** y, a continuación, elija **nuevo proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , expanda **Visual C#** o **Visual Basic** y, a continuación, elija el nodo **Windows** .

3. En la parte superior del cuadro de diálogo, elija **.NET Framework 3,5** en la lista de versiones de la .NET Framework.

4. Elija la plantilla de proyecto **biblioteca de clases** , asigne al proyecto el nombre **SharePointCommands** y, a continuación, elija el botón **Aceptar** .

     Visual Studio agrega el proyecto **SharePointCommands** a la solución y abre el archivo de código predeterminado Class1.

5. Elimine el archivo de código Class1 del proyecto.

## <a name="configure-the-projects"></a>Configurar los proyectos
 Antes de escribir código para crear el paso de implementación personalizado, debe agregar los archivos de código y las referencias de ensamblado, y debe configurar los proyectos.

#### <a name="to-configure-the-deploymentstepextension-project"></a>Para configurar el proyecto DeploymentStepExtension

1. En el proyecto **DeploymentStepExtension** , agregue dos archivos de código que tengan los siguientes nombres:

    - UpgradeStep

    - DeploymentConfigurationExtension

2. Abra el menú contextual en el proyecto DeploymentStepExtension y, a continuación, elija **Agregar referencia**.

3. En la pestaña **marco** , active la casilla del ensamblado System. ComponentModel. Composition.

4. En la pestaña **extensiones** , active la casilla del ensamblado Microsoft. VisualStudio. SharePoint y, a continuación, elija el botón **Aceptar** .

#### <a name="to-configure-the-sharepointcommands-project"></a>Para configurar el proyecto SharePointCommands

1. En el proyecto **SharePointCommands** , agregue un archivo de código denominado Commands.

2. En **Explorador de soluciones**, abra el menú contextual en el nodo del proyecto **SharePointCommands** y, a continuación, elija **Agregar referencia**.

3. En la pestaña **extensiones** , active las casillas de verificación de los siguientes ensamblados y, a continuación, haga clic en elegir el botón **Aceptar** .

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

## <a name="define-the-custom-deployment-step"></a>Definir el paso de implementación personalizado
 Cree una clase que defina el paso de implementación de actualización. Para definir el paso de implementación, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfaz. Implemente esta interfaz siempre que desee definir un paso de implementación personalizado.

#### <a name="to-define-the-custom-deployment-step"></a>Para definir el paso de implementación personalizado

1. En el proyecto **DeploymentStepExtension** , abra el archivo de código UpgradeStep y, a continuación, pegue el código siguiente en él.

    > [!NOTE]
    > Después de agregar este código, el proyecto tendrá algunos errores de compilación, pero desaparecerán cuando agregue código en pasos posteriores.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb" id="Snippet1":::

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Crear una configuración de implementación que incluya el paso de implementación personalizado
 Cree una extensión de proyecto para la nueva configuración de implementación, que incluye varios pasos de implementación integrados y el nuevo paso de implementación de actualización. Al crear esta extensión, ayudará a los desarrolladores de SharePoint a usar el paso de implementación de actualización en los proyectos de SharePoint.

 Para crear la configuración de implementación, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaz. Implemente esta interfaz siempre que desee crear una extensión de proyecto de SharePoint.

#### <a name="to-create-the-deployment-configuration"></a>Para crear la configuración de implementación

1. En el proyecto **DeploymentStepExtension** , abra el archivo de código DeploymentConfigurationExtension y, a continuación, pegue el código siguiente en él.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb" id="Snippet2":::

## <a name="create-the-custom-sharepoint-commands"></a>Crear los comandos de SharePoint personalizados
 Cree dos comandos personalizados que llamen al modelo de objetos de servidor para SharePoint. Un comando determina si ya se ha implementado una solución; el otro comando actualiza una solución.

#### <a name="to-define-the-sharepoint-commands"></a>Para definir los comandos de SharePoint

1. En el proyecto **SharePointCommands** , abra el archivo de código de comandos y, a continuación, pegue el código siguiente en él.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs" id="Snippet4":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb" id="Snippet4":::

## <a name="checkpoint"></a>Punto de control
 En este punto del tutorial, todo el código para el paso de implementación personalizado y los comandos de SharePoint se encuentran ahora en los proyectos. Compilarlos para asegurarse de que se compilan sin errores.

#### <a name="to-build-the-projects"></a>Procedimiento para generar los proyectos

1. En **Explorador de soluciones**, abra el menú contextual del proyecto **DeploymentStepExtension** y, a continuación, elija **compilar**.

2. Abra el menú contextual del proyecto **SharePointCommands** y, a continuación, elija **compilar**.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Crear un paquete VSIX para implementar la extensión
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX. En primer lugar, configure el paquete VSIX modificando el archivo source. Extension. vsixmanifest en el Proyecto VSIX. A continuación, cree el paquete VSIX compilando la solución.

#### <a name="to-configure-and-create-the-vsix-package"></a>Para crear y configurar el paquete VSIX

1. En **Explorador de soluciones**, en el proyecto **UpgradeDeploymentStep** , abra el menú contextual del archivo **source. Extension. vsixmanifest** y, a continuación, elija **abrir**.

     Visual Studio abre el archivo en el editor de manifiestos. El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que requieren todos los paquetes VSIX. Para obtener más información acerca de este archivo, vea [referencia de esquema de extensión VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. En el cuadro **nombre de producto** , escriba **paso de implementación de actualización para proyectos de SharePoint**.

3. En el cuadro **autor** , escriba **contoso**.

4. En el cuadro **Descripción** , escriba **proporciona un paso de implementación de actualización personalizado que se puede usar en los proyectos de SharePoint**.

5. En la pestaña **activos** del editor, elija el botón **nuevo** .

     Aparecerá el cuadro de diálogo **Agregar nuevo activo** .

6. En la lista **tipo** , elija **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest. Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX. Para obtener más información, vea [elemento MEFComponent (esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. En la lista **origen** , elija **un proyecto en la solución actual**.

8. En la lista **proyecto** , elija **DeploymentStepExtension** y, a continuación, elija el botón **Aceptar** .

9. En el editor de manifiestos, vuelva a elegir el botón **nuevo** .

     Aparecerá el cuadro de diálogo **Agregar nuevo activo** .

10. En la lista **tipo** , escriba **SharePoint. Commands. V4**.

    > [!NOTE]
    > Este elemento especifica una extensión personalizada que desea incluir en la extensión de Visual Studio. Para obtener más información, vea [elemento asset (esquema VSX)](/previous-versions/dd393737(v=vs.110)).

11. En la lista **origen** , elija **un proyecto en la solución actual**.

12. En la lista **proyecto** , elija **SharePointCommands** y, a continuación, elija el botón **Aceptar** .

13. En la barra de menús, **Elija compilar compilar**  >  **solución** y, a continuación, asegúrese de que la solución se compila sin errores.

14. Asegúrese de que la carpeta de salida de compilación del proyecto UpgradeDeploymentStep contiene ahora el archivo UpgradeDeploymentStep. vsix.

     De forma predeterminada, la carpeta de salida de la compilación es \bin\Debug, ubicada bajo la carpeta que contiene el archivo de proyecto.

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Preparar la prueba del paso de implementación de actualización
 Para probar el paso de implementación de actualización, primero debe implementar una solución de ejemplo en el sitio de SharePoint. Empiece por depurar la extensión en la instancia experimental de Visual Studio. A continuación, cree una definición de lista y una instancia de lista que se usarán para probar el paso de implementación y, a continuación, impleméntela en el sitio de SharePoint. A continuación, modifique la definición de lista y la instancia de lista, y vuelva a implementarlos para demostrar cómo el proceso de implementación predeterminado sobrescribe las soluciones en el sitio de SharePoint.

 Más adelante en este tutorial, modificará la definición de lista y la instancia de lista y, a continuación, los actualizará en el sitio de SharePoint.

#### <a name="to-start-debugging-the-extension"></a>Para comenzar a depurar la extensión

1. Reinicie Visual Studio con credenciales administrativas y, a continuación, abra la solución UpgradeDeploymentStep.

2. En el proyecto DeploymentStepExtension, abra el archivo de código UpgradeStep y, a continuación, agregue un punto de interrupción a la primera línea de código en los `CanExecute` `Execute` métodos y.

3. Para iniciar la depuración, elija la tecla **F5** o, en la barra de menús, elija **depurar**  >  **iniciar depuración**.

4. Visual Studio instala la extensión en el paso de implementación de%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade para SharePoint Projects\1.0 e inicia una instancia experimental de Visual Studio. Probará el paso de implementación de actualización en esta instancia de Visual Studio.

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Para crear un proyecto de SharePoint con una definición de lista y una instancia de lista

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **archivo**  >  **nuevo**  >  **proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , expanda el nodo **Visual C#** o el nodo **Visual Basic** , expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

3. En la parte superior del cuadro de diálogo, asegúrese de que aparece **.NET Framework 3,5** en la lista de versiones de la .NET Framework.

    Los proyectos de [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] requieren esta versión del .NET Framework.

4. En la lista de plantillas de proyecto, elija **proyecto de SharePoint 2010**, asigne al proyecto el nombre **EmployeesListDefinition** y, a continuación, elija el botón **Aceptar** .

5. En el **Asistente para la personalización de SharePoint**, escriba la dirección URL del sitio que desea usar para la depuración.

6. En **¿cuál es el nivel de confianza de esta solución de SharePoint**?, elija el botón de opción **implementar como solución de granja de servidores** .

   > [!NOTE]
   > El paso de implementación de actualización no es compatible con las soluciones en espacio aislado.

7. Elija el botón **Finalizar**.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el proyecto EmployeesListDefinition.

8. Abra el menú contextual del proyecto EmployeesListDefinition, elija **Agregar** y, a continuación, elija **nuevo elemento**.

9. En el cuadro de diálogo **Agregar nuevo elemento-EmployeesListDefinition** , expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

10. Elija la plantilla de elemento de **lista** , asigne un nombre a la **lista de empleados** de elementos y, a continuación, elija el botón **Agregar** .

     Aparece el Asistente para la personalización de SharePoint

11. En la página **elegir la configuración** de la lista, Compruebe la configuración siguiente y, a continuación, elija el botón **Finalizar** :

    1. La **lista empleados** aparece en el cuadro **¿Qué nombre desea mostrar en la lista?**

    2. Se elige el botón de opción **crear una lista personalizable basada en:** .

    3. El **valor predeterminado (en blanco)** se elige en la lista **crear una lista personalizable basada en:** .

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el elemento de la lista de empleados con una columna de título y una única instancia vacía y abre el diseñador de listas.

12. En el diseñador de listas, en la pestaña **columnas** , elija la fila **Escriba un nombre de columna nuevo o existente** y, a continuación, agregue las columnas siguientes en la lista **nombre para mostrar columna** :

    1. Nombre

    2. Compañía

    3. Teléfono del trabajo

    4. Correo electrónico

13. Guarde todos los archivos y, a continuación, cierre el diseñador de listas.

14. En **Explorador de soluciones**, expanda el nodo **lista de empleados** y, a continuación, expanda el nodo secundario instancia de **lista de empleados** .

15. En el archivo de *Elements.xml* , reemplace el XML predeterminado en este archivo por el siguiente código XML. Este XML cambia el nombre de la lista a **Employees** y agrega información para un empleado denominado Jim Hance.

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

16. Guarde y cierre el archivo de *Elements.xml* .

17. Abra el menú contextual del proyecto EmployeesListDefinition y, a continuación, elija **abrir** o **propiedades**.

     Se abre el diseñador de propiedades.

18. En la pestaña **SharePoint** , desactive la casilla **retraer automáticamente después de depurar** y, a continuación, guarde las propiedades.

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Para implementar la definición de lista y la instancia de lista

1. En **Explorador de soluciones**, elija el nodo del proyecto **EmployeesListDefinition** .

2. En la ventana **propiedades** , asegúrese de que la propiedad **configuración de implementación activa** está establecida en **predeterminado**.

3. Elija la tecla **F5** o, en la barra de menús, elija **depurar**  >  **iniciar depuración**.

4. Compruebe que el proyecto se compila correctamente, que el explorador Web se abre en el sitio de SharePoint, que el elemento **listas** de la barra de inicio rápido incluye la lista nuevos **empleados** y que la lista **empleados** incluye la entrada de Jim Hance.

5. Cierre el explorador web.

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Para modificar la definición de lista y la instancia de lista y volver a implementarlos

1. En el proyecto EmployeesListDefinition, abra el archivo *Elements.xml* que es un elemento secundario del elemento de proyecto de instancia de la **lista de empleados** .

2. Quite el `Data` elemento y sus elementos secundarios para quitar de la lista la entrada de Jim Hance.

     Cuando termine, el archivo debe contener el siguiente código XML.

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

3. Guarde y cierre el archivo de *Elements.xml* .

4. Abra el menú contextual del elemento de proyecto de la **lista de empleados** y, a continuación, elija **abrir** o **propiedades**.

5. En el diseñador de listas, elija la pestaña **vistas** .

6. En la lista **columnas seleccionadas** , elija **datos adjuntos** y, a continuación, elija la clave de < para moverla a la lista **columnas disponibles** .

7. Repita el paso anterior para pasar la columna **Business Phone** de la lista **columnas seleccionadas** a la lista **columnas disponibles** .

     Esta acción quita estos campos de la vista predeterminada de la lista de **empleados** en el sitio de SharePoint.

8. Para iniciar la depuración, elija la tecla **F5** o, en la barra de menús, elija **depurar**  >  **iniciar depuración**.

9. Compruebe que aparece el cuadro de diálogo **conflictos de implementación** .

     Este cuadro de diálogo aparece cuando Visual Studio intenta implementar una solución (la instancia de lista) en un sitio de SharePoint en el que ya se ha implementado esa solución. Este cuadro de diálogo no aparecerá al ejecutar el paso de implementación de actualización más adelante en este tutorial.

10. En el cuadro de diálogo **conflictos de implementación** , elija el botón de opción **resolver automáticamente** .

     Visual Studio elimina la instancia de lista en el sitio de SharePoint, implementa el elemento de lista en el proyecto y, a continuación, abre el sitio de SharePoint.

11. En la sección **listas** de la barra Inicio rápido, elija la lista **empleados** y, a continuación, compruebe los detalles siguientes:

    - Las columnas **datos adjuntos** y **teléfono particular** no aparecen en esta vista de la lista.

    - La lista está vacía. Al usar la configuración de implementación **predeterminada** para volver a implementar la solución, la lista de **empleados** se ha reemplazado por la nueva lista vacía en el proyecto.

## <a name="test-the-deployment-step"></a>Probar el paso de implementación
 Ahora está listo para probar el paso de implementación de actualización. En primer lugar, agregue un elemento a la instancia de lista en SharePoint. A continuación, cambie la definición de lista y la instancia de lista, actualícelo en el sitio de SharePoint y confirme que el paso de implementación de actualización no sobrescribe el nuevo elemento.

#### <a name="to-manually-add-an-item-to-the-list"></a>Para agregar manualmente un elemento a la lista

1. En la cinta de opciones del sitio de SharePoint, en la pestaña **herramientas de lista** , elija la pestaña **elementos** .

2. En el **nuevo** grupo, elija **nuevo elemento**.

     Como alternativa, puede elegir el vínculo **Agregar nuevo elemento** en la lista de elementos.

3. En la ventana **empleados-nuevo elemento** , en el cuadro **título** , escriba **jefe de instalaciones**.

4. En el cuadro **First Name (nombre** ), escriba **Andy**.

5. En el cuadro **empresa** , escriba **contoso**.

6. Elija el botón **Guardar** , compruebe que el nuevo elemento aparece en la lista y, a continuación, cierre el explorador Web.

     Más adelante en este tutorial, usará este elemento para comprobar que el paso de implementación de actualización no sobrescribe el contenido de esta lista.

#### <a name="to-test-the-upgrade-deployment-step"></a>Para probar el paso de implementación de actualización

1. En la instancia experimental de Visual Studio, en **Explorador de soluciones**, abra el menú contextual del nodo de proyecto **EmployeesListDefinition** y, a continuación, elija **propiedades**.

    Se abre el editor de propiedades o el diseñador.

2. En la pestaña **SharePoint** , establezca la propiedad **configuración de implementación activa** en **Actualizar**.

    Esta configuración de implementación personalizada incluye el nuevo paso de implementación de actualización.

3. Abra el menú contextual del elemento de proyecto de la **lista de empleados** y, a continuación, elija **propiedades** o **abrir**.

    Se abre el editor de propiedades o el diseñador.

4. En la pestaña **vistas** , elija la columna **correo electrónico** y, a continuación, elija la **<** clave para pasar esa columna de la lista **columnas seleccionadas** a la lista **columnas disponibles** .

    Esta acción quita estos campos de la vista predeterminada de la lista de **empleados** en el sitio de SharePoint.

5. Para iniciar la depuración, elija la tecla **F5** o, en la barra de menús, elija **depurar**  >  **iniciar depuración**.

6. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `CanExecute`.

7. Vuelva a elegir la tecla **F5** o, en la barra de menús, elija **depurar**  >  **continuar**.

8. Compruebe que el código se detiene en el punto de interrupción que estableció anteriormente en el `Execute` método.

9. Elija la tecla **F5** o, en la barra de menús, elija **depurar**  >  **continuar** una hora final.

     El explorador Web abre el sitio de SharePoint.

10. En la sección **listas** del área Inicio rápido, elija la lista **empleados** y, a continuación, compruebe los detalles siguientes:

    - El elemento que agregó manualmente anteriormente (para Andy, el administrador de instalaciones) todavía está en la lista.

    - Las columnas **teléfono del trabajo** y dirección de **correo electrónico** no aparecen en esta vista de la lista.

      La configuración de implementación de **actualización** modifica la instancia de la lista de **empleados** existente en el sitio de SharePoint. Si usó la configuración de implementación **predeterminada** en lugar de la configuración de **actualización** , se produciría un conflicto de implementación. Visual Studio resolverá el conflicto reemplazando la lista de **empleados** y se eliminará el elemento de Andy, Director de instalaciones.

## <a name="clean-up-the-development-computer"></a>Limpiar el equipo de desarrollo
 Cuando termine de probar el paso de implementación de actualización, quite la instancia de lista y la definición de lista del sitio de SharePoint y quite la extensión de paso de implementación de Visual Studio.

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Para quitar la instancia de lista del sitio de SharePoint

1. Abra la lista de **empleados** en el sitio de SharePoint, si la lista no está abierta.

2. En la cinta de opciones del sitio de SharePoint, elija la pestaña **herramientas de lista** y, a continuación, elija la pestaña **lista** .

3. En el grupo **configuración** , elija el elemento configuración de la **lista** .

4. En **permisos y administración**, elija el comando **eliminar esta lista** , haga clic en **Aceptar** para confirmar que desea enviar la lista a la papelera de reciclaje y, a continuación, cierre el explorador Web.

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Para quitar la definición de lista del sitio de SharePoint

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **compilar**  >  **retraer**.

     Visual Studio retira la definición de lista del sitio de SharePoint.

#### <a name="to-uninstall-the-extension"></a>Para desinstalar la extensión

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **herramientas**  >  **extensiones y actualizaciones**.

     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

2. En la lista de extensiones, elija **Actualizar paso de implementación para proyectos de SharePoint** y, a continuación, elija el comando **desinstalar** .

3. En el cuadro de diálogo que aparece, elija **sí** para confirmar que desea desinstalar la extensión y, a continuación, elija **reiniciar ahora** para completar la desinstalación.

4. Cierre ambas instancias de Visual Studio (la instancia experimental y la instancia de Visual Studio en la que está abierta la solución UpgradeDeploymentStep).

## <a name="see-also"></a>Consulte también
- [Extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)