---
title: "Walkthrough: Creating a Custom Deployment Step for SharePoint Projects"
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
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 4ba2d120-06b8-4ef3-84eb-c6c50ced9d82
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Walkthrough: Creating a Custom Deployment Step for SharePoint Projects
  Al implementar un proyecto de SharePoint, Visual Studio ejecuta una serie de pasos de implementación en un orden concreto.  Visual Studio incluye muchos pasos de implementación integrados, pero también puede crear los suyos propios.  
  
 En este tutorial, creará un paso de implementación personalizado para actualizar soluciones en un servidor que ejecute SharePoint.  Visual Studio incluye los pasos de implementación integrados para muchas tareas, como retirar o agregar soluciones, pero no incluye un paso de implementación para actualizar soluciones.  De forma predeterminada, al implementar una solución de SharePoint, Visual Studio retira primero la solución \(si está implementada\) y después implementar de nuevo la solución completa.  Para obtener más información acerca de los pasos de implementación integrados, vea [Implementar, publicar y actualizar paquetes de soluciones de  
SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear una extensión Visual Studio que realiza dos tareas principales:  
  
    -   La extensión define un paso de implementación personalizado para actualizar las soluciones de SharePoint.  
  
    -   La extensión crea una extensión de proyecto que define una nueva configuración de implementación, que es un conjunto de pasos de implementación que se ejecuta para un proyecto determinado.  La nueva configuración de implementación incluye el paso de implementación personalizado y varios pasos de implementación integrados.  
  
-   Crear dos comandos de SharePoint personalizados que el ensamblado de la extensión llama.  Los comandos de SharePoint son métodos que se pueden llamar a los ensamblados de la extensión para utilizar las API del modelo de objetos de servidor de SharePoint.  Para obtener más información, vea [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Compilar un paquete de extensión de Visual Studio \(VSIX\) para implementar ambos ensamblados.  
  
-   Probar el nuevo paso de implementación.  
  
## Requisitos previos  
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:  
  
-   Ediciones compatibles de Windows, SharePoint, y Visual Studio.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK.  En este tutorial se utiliza la plantilla **Proyecto VSIX** del SDK para crear un paquete VSIX para implementar la extensión.  Para obtener más información, vea [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.  
  
-   Utilizar el modelo de objetos de servidor de SharePoint.  Para obtener más información, vea [Utilizar el modelo de objetos de servidor de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Soluciones de SharePoint.  Para obtener más información, vea [Información general sobre soluciones](http://go.microsoft.com/fwlink/?LinkId=169422).  
  
-   Actualizar las soluciones de SharePoint.  Para obtener más información, vea [Actualizar una solución](http://go.microsoft.com/fwlink/?LinkId=177802).  
  
## Crear los proyectos  
 Para completar este tutorial, debe crear tres proyectos:  
  
-   Un proyecto VSIX para crear el paquete VSIX e implementar la extensión.  
  
-   Un proyecto de biblioteca de clases que implemente la extensión.  Este proyecto debe tener como destino .NET Framework 4,5.  
  
-   Un proyecto de biblioteca de clases que define los comandos de SharePoint personalizados.  Este proyecto debe tener como destino .NET Framework 3.5.  
  
 Comience el tutorial creando ambos proyectos.  
  
#### Para crear el proyecto VSIX  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menú, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
3.  En el cuadro de diálogo **Nuevo proyecto** , expanda los nodos **Visual c\#** o **Visual Basic** y, a continuación el nodo **Extensibilidad** .  
  
    > [!NOTE]  
    >  El nodo **Extensibilidad** solo está disponible si instala Visual Studio SDK.  Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.  
  
4.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de .NET Framework.  
  
5.  Elija la plantilla **Proyecto VSIX** , asigne al proyecto **UpgradeDeploymentStep**, y elija el botón **Aceptar** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **PasoImplementarActualización** al **Explorador de soluciones**.  
  
#### Para crear la extensión de proyecto  
  
1.  En **Explorador de soluciones**, abra el menú contextual para el nodo de la solución pasoimplementaractualización, elija **Agregar**y, a continuación **Nuevo proyecto**.  
  
    > [!NOTE]  
    >  En los proyectos de Visual Basic, el nodo de la solución aparece en el **Explorador de soluciones** solo cuando se activa la casilla **Mostrar solución siempre** en [General, Proyectos y soluciones, Cuadro de diálogo Opciones](http://msdn.microsoft.com/es-es/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  En el cuadro de diálogo **Nuevo proyecto** , expanda los nodos **Visual c\#** o **Visual Basic** y, a continuación el nodo **Windows** .  
  
3.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de .NET Framework.  
  
4.  Elija la plantilla de proyecto **Biblioteca de clases** , asigne al proyecto **DeploymentStepExtension**, y elija el botón **Aceptar** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **ExtensiónPasoImplementación** a la solución y abre el archivo de código predeterminado Class1.  
  
5.  Elimine el archivo de código Class1 del proyecto.  
  
#### Para crear el proyecto Comandos de SharePoint  
  
1.  En **Explorador de soluciones**, abra el menú contextual para el nodo de la solución pasoimplementaractualización, elija **Agregar**y, a continuación **Nuevo proyecto**.  
  
    > [!NOTE]  
    >  En los proyectos de Visual Basic, el nodo de la solución aparece en el **Explorador de soluciones** solo cuando se activa la casilla **Mostrar solución siempre** en [General, Proyectos y soluciones, Cuadro de diálogo Opciones](http://msdn.microsoft.com/es-es/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  En el cuadro de diálogo **Nuevo proyecto** , expanda **Visual c\#** o **Visual Basic**y, a continuación el nodo **Windows** .  
  
3.  En la parte superior del cuadro de diálogo, elija **.NET Framework 3.5** en la lista de versiones de .NET Framework.  
  
4.  Elija la plantilla de proyecto **Biblioteca de clases** , asigne al proyecto **SharePointCommands**, y elija el botón **Aceptar** .  
  
     Visual Studio agrega el proyecto **ComandosSharePoint** a la solución y abre el archivo de código predeterminado Class1.  
  
5.  Elimine el archivo de código Class1 del proyecto.  
  
## Configurar los proyectos  
 Antes de escribir el código para crear el paso de implementación personalizado, debe agregar los archivos de código y las referencias de ensamblado, y debe configurar los proyectos.  
  
#### Para configurar el proyecto ExtensiónPasoImplementación  
  
1.  En el proyecto **DeploymentStepExtension** , agregue dos archivos de código que tienen los nombres siguientes:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Abra el menú contextual del proyecto extensiónpasoimplementación y, a continuación **Agregar referencia**.  
  
3.  En la pestaña **Framework** , active la casilla para el ensamblado System.ComponentModel.Composition.  
  
4.  En la pestaña **Extensiones** , active la casilla para el ensamblado Microsoft.VisualStudio.SharePoint, y después elija el botón **Aceptar** .  
  
#### Para configurar el proyecto ComandosSharePoint  
  
1.  En el proyecto **SharePointCommands** , agregue un archivo de código denominado Commands.  
  
2.  En **Explorador de soluciones**, abra el menú contextual del nodo del proyecto **SharePointCommands** y, a continuación **Agregar referencia**.  
  
3.  En la pestaña **Extensiones** , active las casillas de los siguientes ensamblados, y seleccione elija el botón **Aceptar**  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## Definir el paso de implementación personalizado  
 Cree una clase que defina el paso de implementación de actualización.  Para definir el paso de implementación, la clase implementa la interfaz <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>.  Implemente esta interfaz para definir un paso de implementación personalizado todas las veces que desee.  
  
#### Para definir el paso de implementación personalizado  
  
1.  En el proyecto **DeploymentStepExtension** , abra el archivo de código UpgradeStep y, a continuación pegue el siguiente código en él.  
  
    > [!NOTE]  
    >  Después de agregar este código, el proyecto tendrá algunos errores de compilación, pero desaparecerán al agregar código en pasos posteriores.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#1)]  
  
## Crear una configuración de implementación que incluya el paso de implementación personalizado  
 Cree una extensión de proyecto para la nueva configuración de implementación, que incluye varios pasos de implementación integrados y el nuevo paso de implementación de actualización.  Crear esta extensión, ayuda a los desarrolladores de SharePoint a utilizar el paso de implementación de actualización en los proyectos de SharePoint.  
  
 Para crear la configuración de implementación, la clase implementa la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Implemente esta interfaz para crear una extensión de proyecto de SharePoint todas las veces que desee.  
  
#### Para crear la configuración de implementación  
  
1.  En el proyecto **DeploymentStepExtension** , abra el archivo de código DeploymentConfigurationExtension y, a continuación pegue el siguiente código en él.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## Crear los comandos de SharePoint personalizados  
 Cree dos comandos personalizados que llamen al modelo de objetos de servidor de SharePoint.  Un comando determina si ya hay implementada una solución; el otro actualiza una solución.  
  
#### Para definir los comandos de SharePoint  
  
1.  En el proyecto **SharePointCommands** , abra el archivo de código commands, y luego pegue el siguiente código en él.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#4)]  
  
## Punto de control  
 En este punto del tutorial, todo el código para el paso de implementación personalizado y los comandos de SharePoint están en los proyectos.  Compilelos para asegurarse de que se compilan sin errores.  
  
#### Para compilar los proyectos  
  
1.  En **Explorador de soluciones**, abra el menú contextual para el proyecto **DeploymentStepExtension** y, a continuación **Generar**.  
  
2.  Abrir el menú contextual para el proyecto **SharePointCommands** y, a continuación **Generar**.  
  
## Crear un paquete VSIX para implementar la extensión  
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX.  Primero, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest del proyecto VSIX.  A continuación cree el paquete VSIX compilando la solución.  
  
#### Para crear y configurar el paquete VSIX  
  
1.  En **Explorador de soluciones**, bajo el proyecto **UpgradeDeploymentStep** , abra el menú contextual para el archivo **source.extension.vsixmanifest** y, a continuación **Abrir**.  
  
     Visual Studio abre el archivo en el editor de manifiestos.  El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que todos los paquetes VSIX requieren.  Para obtener más información sobre este archivo, vea [Referencia de esquema de extensión VSIX](http://msdn.microsoft.com/es-es/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  En el cuadro **Nombre de producto** , entre en **Paso de implementación de actualización para los proyectos de SharePoint**.  
  
3.  En el cuadro **Autor** , entre en **Contoso**.  
  
4.  En el cuadro **Descripción** , entre en **Proporciona un paso de implementación personalizado de actualización que se puede usar en los proyectos de SharePoint**.  
  
5.  En la pestaña **Activos** de editor, elija el botón **Nuevo** .  
  
     El cuadro de diálogo **Agregar nuevo activo** aparece.  
  
6.  En la lista **Tipo** , elija **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest.  Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX.  Para obtener más información, vea [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/es-es/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  En la lista **Origen** , elija **Un proyecto de la solución actual**.  
  
8.  En la lista **Proyecto** , elija **DeploymentStepExtension**, y elija el botón **Aceptar** .  
  
9. En el editor de manifiestos, elija el botón **Nuevo** de nuevo.  
  
     El cuadro de diálogo **Agregar nuevo activo** aparece.  
  
10. En la lista **Tipo** , entre en **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Este elemento especifica una extensión personalizada que desea incluir en la extensión de Visual Studio.  Para obtener más información, vea [Elemento de activo \(esquema VSX\)](http://msdn.microsoft.com/es-es/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. En la lista **Origen** , elija **Un proyecto de la solución actual**.  
  
12. En la lista **Proyecto** , elija **SharePointCommands**, y elija el botón **Aceptar** .  
  
13. En la barra de menú, elija **Generar**, **Compilar solución**, y asegúrese de que la solución se compila sin errores.  
  
14. Asegúrese de que la carpeta de salida de la compilación del proyecto pasoimplementaractualización ahora contiene el archivo pasoimplementaractualización.vsix.  
  
     De forma predeterminada, la carpeta de resultado de compilación es ..  \\bin\\Debug, que se encuentra bajo la carpeta que contiene el archivo de proyecto.  
  
## Preparar la prueba del paso de implementación de actualización  
 Para probar el paso de implementación de actualización, debe implementar primero una solución de ejemplo en el sitio de SharePoint.  Empiece por depurar la extensión en la instancia experimental de Visual Studio.  Cree una definición de lista y una instancia de utilizar para probar el paso de implementación, y después impleméntelas en el sitio de SharePoint.  A continuación, modifique la definición de lista y enumera la instancia y los cambia de nuevo para mostrar cómo el proceso de implementación predeterminado sobrescribe las soluciones en el sitio de SharePoint.  
  
 Más adelante en este tutorial, modificará la definición y mostrará la instancia y, a continuación se actualizará en el sitio de SharePoint.  
  
#### Para comenzar a depurar la extensión  
  
1.  Reinicie Visual Studio con credenciales administrativas, y vuelva a abrir la solución pasoimplementaractualización.  
  
2.  En el proyecto extensiónpasoimplementación, abra el archivo de código UpgradeStep, y después agregue un punto de interrupción a la primera línea de código en los métodos `CanExecute` y `Execute` .  
  
3.  Empiece a depurar eligiendo la tecla F5 o, en la barra de menús, eligiendo **Depurar**, **Iniciar depuración**.  
  
4.  Visual Studio instala la extensión en %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Upgrade Deployment Step for SharePoint Projects\\1.0 and starts an experimental instance of Visual Studio.  Probará el paso de implementación de actualización en esta instancia de Visual Studio.  
  
#### Para crear un proyecto de SharePoint con una definición de lista y una instancia de lista  
  
1.  En la instancia experimental de Visual Studio, en la barra de menú, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto** , expanda el nodo **Visual c\#** o el nodo **Visual Basic** , expanda el nodo **SharePoint** y, a continuación el nodo **2010** .  
  
3.  En la parte superior del cuadro de diálogo, asegúrese de que **.NET Framework 3.5** aparece en la lista de versiones de .NET Framework.  
  
     Los proyectos de [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] requieren esta versión de .NET Framework.  
  
4.  En la lista de plantillas de proyecto, elija **Proyecto de SharePoint 2010**, asigne al proyecto **EmployeesListDefinition**, y elija el botón **Aceptar** .  
  
5.  En **Asistente para la personalización de SharePoint**, escriba la dirección URL del sitio que desea utilizar para depurar.  
  
6.  En **Cuál es el nivel de confianza para la solución de SharePoint**, elija el botón de opción **Implementar como solución de granja de servidores** .  
  
    > [!NOTE]  
    >  El paso de implementación de actualización no admite soluciones en espacio aislado.  
  
7.  Elija el botón **Finalizar** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el proyecto definiciónlistaempleados.  
  
8.  Abrir el menú contextual para el proyecto definiciónlistaempleados, elija **Agregar**y, a continuación **Nuevo elemento**.  
  
9. En el cuadro de diálogo **Agregar nuevo elemento – EmployeesListDefinition** , expanda el nodo **SharePoint** y, a continuación el nodo **2010** .  
  
10. Elija la plantilla de elementos **Lista** , llame al elemento **Lista de empleados**, y elija el botón **Agregar** .  
  
     El Asistente para la personalización de SharePoint aparece  
  
11. En la página **Elegir configuración de la lista** , compruebe los siguientes valores, y elija el botón **Finalizar** :  
  
    1.  **Lista de empleados** aparece en el cuadro **¿Qué nombre desea mostrar en la lista?** .  
  
    2.  Se elige el botón de opción **Cree una lista personalizable basada en:** .  
  
    3.  **Valor predeterminado \(en blanco\)** se elige en la lista **Cree una lista personalizable basada en:** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el elemento de lista de empleados con una columna título y una única instancia vacía y abra la lista Designer.  
  
12. En la lista Designer, en la ficha **Columnas** , elija la fila **Escriba un nombre de columna nuevo o existente** , y agregue las columnas siguientes en **Nombre para mostrar de la columna** muestran:  
  
    1.  Nombre  
  
    2.  Compañía  
  
    3.  Teléfono de negocio  
  
    4.  Correo electrónico  
  
13. Guarde todos los archivos, y luego cierre la lista Designer.  
  
14. En **Explorador de soluciones**, expanda el nodo **Lista de empleados** , expanda el nodo secundario **Instancia de la lista de empleados** .  
  
15. En el archivo Elements.xml, reemplace el XML predeterminado de este archivo por el siguiente.  Este código XML cambia el nombre de la lista a **Empleados** y agrega información para un empleado que ha llamado a Jim Hance.  
  
    ```  
  
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
  
16. Guarde y cierre el archivo Elements.xml.  
  
17. Abrir el menú contextual para el proyecto definiciónlistaempleados y, a continuación **Abrir** o **Propiedades**.  
  
     Las propiedades se abre el diseñador.  
  
18. En la pestaña **SharePoint** , desactive la casilla **Retraer automáticamente después de depurar** , y guarde las propiedades.  
  
#### Para implementar la definición y la instancia de lista  
  
1.  En **Explorador de soluciones**, elija el nodo del proyecto **EmployeesListDefinition** .  
  
2.  En la ventana **Propiedades**, asegúrese de que la propiedad **Active Deployment Configuration** está establecida en **True** \(este es el valor predeterminado\).  
  
3.  Elija la tecla F5 o, en la barra de menú, elija **Depurar**, **Iniciar depuración**.  
  
4.  Compruebe que el proyecto se compila correctamente, que el explorador web se abre el sitio de SharePoint, que el elemento **Listas** en la barra de Inicio rápido incluye la nueva lista **Empleados** , y que la lista **Empleados** incluye la entrada para Jim Hance.  
  
5.  Cierre el explorador web.  
  
#### Modificar la definición y la instancia de lista e implementarlas de nuevo  
  
1.  En el proyecto definiciónlistaempleados, abra el archivo Elements.xml que es un elemento secundario del elemento de proyecto **Instancia de la lista de empleados** .  
  
2.  Quite el elemento `Data` y sus elementos secundarios para quitar la entrada de Jim Hance de la lista.  
  
     Cuando termine, el archivo debe contener el XML siguiente.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Guarde y cierre el archivo Elements.xml.  
  
4.  Abrir el menú contextual para el elemento de proyecto **Lista de empleados** y, a continuación **Abrir** o **Propiedades**.  
  
5.  En la lista Designer, elija la ficha **Vistas** .  
  
6.  En la lista **Columnas seleccionadas** , elija **Datos adjuntos**, y elija la clave \< para desplazarse que columna a la lista **Columnas disponibles** .  
  
7.  Repita el paso anterior para mover la columna **Teléfono de negocio** de la lista **Columnas seleccionadas** a la lista **Columnas disponibles** .  
  
     Esta acción quita estos campos de la vista predeterminada de la lista **Employees** del sitio de SharePoint.  
  
8.  Empiece a depurar eligiendo la tecla F5 o, en la barra de menús, eligiendo **Depurar**, **Iniciar depuración**.  
  
9. Compruebe que aparece el cuadro de diálogo **Conflictos de implementación**.  
  
     Este cuadro de diálogo aparece cuando Visual Studio intenta implementar una solución \(la instancia de lista\) en un sitio de SharePoint al que la solución se ha implementado.  Este cuadro de diálogo no aparecerá cuando se ejecuta el paso de implementación de actualización más adelante en este tutorial.  
  
10. En el cuadro de diálogo **Conflictos de implementación** , elija el botón de opción **Resolver automáticamente** .  
  
     Visual Studio elimina la instancia de lista en el sitio de SharePoint, implementa el elemento de lista en el proyecto, y abra el sitio de SharePoint.  
  
11. En la sección **Listas** de la barra de Inicio rápido, elija la lista **Empleados** , y compruebe los siguientes:  
  
    -   Las columnas **Datos adjuntos** y **Teléfono doméstico** no aparecen en esta vista de lista.  
  
    -   La lista está vacía.  Cuando utilizó la configuración de implementación **Predeterminada** para implementar de nuevo la solución, la lista **Employees** se reemplazó con la nueva lista vacía de su proyecto.  
  
## Probar el paso de implementación  
 Ahora ya puede probar el paso de implementación de actualización.  Primero, agregue un elemento a la instancia de lista en SharePoint.  Después cambie la definición de lista y una instancia de, actualicelas en el sitio de SharePoint, y confirme que el paso de implementación de actualización no sobrescribe el nuevo elemento.  
  
#### Para agregar manualmente un elemento a la lista  
  
1.  En la cinta del sitio de SharePoint, en la pestaña **Enumera las herramientas** , elija la ficha **Elementos** .  
  
2.  En el grupo **Nuevo** , elija **Nuevo elemento**.  
  
     Como alternativa, puede elegir el vínculo en la lista de elementos propio **Agregar nuevo elemento** .  
  
3.  En la ventana **Empleados – nuevo elemento** , en el cuadro **Título** , entre en **Administrador de funciones**.  
  
4.  En el cuadro **Nombre** , entre en **Andy**.  
  
5.  En el cuadro **compañía** , **Contoso**escrito.  
  
6.  Elija el botón **Guardar** , compruebe que el nuevo elemento aparece en la lista, y luego cierre el explorador web.  
  
     Más adelante en este tutorial, utilizará este elemento para comprobar que el paso de implementación de actualización no sobrescribe el contenido de esta lista.  
  
#### Para probar el paso de implementación de actualización  
  
1.  En la instancia experimental de Visual Studio, en **Explorador de soluciones**, abra el menú contextual para el nodo del proyecto **EmployeesListDefinition** y, a continuación **Propiedades**.  
  
     El editor o el Diseñador de las propiedades.  
  
2.  En la pestaña **SharePoint** , establezca la propiedad **Configuración de implementación activa** a **Actualizar**.  
  
     Esta configuración de implementación personalizada incluye el nuevo paso de implementación de actualización.  
  
3.  Abrir el menú contextual para el elemento de proyecto **Lista de empleados** y, a continuación **Propiedades** o **Abrir**.  
  
     El editor o el Diseñador de las propiedades.  
  
4.  En la pestaña **Vistas** , elija la columna **Correo electrónico** , y elija la clave **\<** para desplazarse que la columna de la lista **Columnas seleccionadas** a la lista **Columnas disponibles** .  
  
     Esta acción quita estos campos de la vista predeterminada de la lista **Employees** del sitio de SharePoint.  
  
5.  Empiece a depurar eligiendo la tecla F5 o, en la barra de menús, eligiendo **Depurar**, **Iniciar depuración**.  
  
6.  Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `CanExecute`.  
  
7.  Elija la tecla F5 de nuevo o, en la barra de menú, elija **Depurar**, **Continuar**.  
  
8.  Compruebe que el código se detiene en el punto de interrupción que estableció anteriormente en el método `Execute`.  
  
9. Elija la tecla F5 o, en la barra de menú, elija **Depurar**, **Continuar** una hora final.  
  
     El explorador web abre el sitio de SharePoint.  
  
10. En la sección **Listas** del área de inicio rápido, elija la lista **Empleados** , y compruebe los siguientes:  
  
    -   El elemento que agregó manualmente anterior \(para Andy, el administrador de funciones\) todavía está en la lista.  
  
    -   Las columnas **Teléfono de negocio** y **Dirección de correo electrónico** no aparecen en esta vista de lista.  
  
     La configuración de implementación **Actualizar** modifica la instancia de la lista **Employees** existente en el sitio de SharePoint.  Si se utiliza la configuración de implementación **Predeterminada** en lugar de **Actualizar**, se produce un conflicto de implementación.  Visual Studio lo resolvería reemplazando la lista **Empleados** , y el elemento para Andy, el administrador de funciones, sería eliminado.  
  
## Limpiar el equipo de desarrollo  
 Después de probar el paso de implementación de actualización, quite la instancia y la definición de lista del sitio de SharePoint, y quita la extensión de paso de implementación de Visual Studio.  
  
#### Para quitar la instancia de lista del sitio de SharePoint  
  
1.  Abra **Empleados** enumerado en el sitio de SharePoint, si la lista no está abierto.  
  
2.  En la cinta del sitio de SharePoint, elija la ficha **Herramientas de la lista** , y después elija la ficha **Lista** .  
  
3.  En el grupo **Configuración** , elija el elemento **Configuración de la lista** .  
  
4.  En **Permisos y administración**, elija el comando **Eliminar esta lista** , elija **Aceptar** para confirmar que desea enviar la lista a la papelera de reciclaje, y luego cierre el explorador web.  
  
#### Para quitar la definición de lista del sitio de SharePoint  
  
1.  En la instancia experimental de Visual Studio, en la barra de menú, elija **Generar**, **Retirar**.  
  
     Visual Studio retira la definición de lista del sitio de SharePoint.  
  
#### Para desinstalar la extensión  
  
1.  En la instancia experimental de Visual Studio, en la barra de menú, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
     El cuadro de diálogo **Extensiones y actualizaciones** abra.  
  
2.  En la lista de extensiones, elija **Actualice el paso de implementación de los proyectos de SharePoint**, y elija el comando **Desinstalar** .  
  
3.  En el cuadro de diálogo que aparece, elija **Sí** para confirmar que desea desinstalar la extensión, y elija **Reiniciar ahora** para completar la desinstalación.  
  
4.  Cierre ambas instancias de Visual Studio \(la instancia experimental y la instancia de Visual Studio en la que la solución pasoimplementaractualización está abierto\).  
  
## Vea también  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  