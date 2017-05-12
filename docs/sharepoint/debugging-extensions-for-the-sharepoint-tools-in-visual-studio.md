---
title: "Debugging Extensions for the SharePoint Tools in Visual Studio"
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
  - "SharePoint development in Visual Studio, debugging extensions"
ms.assetid: 7cee8ce0-d07b-41f6-8ce1-b18e4be3b50c
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Debugging Extensions for the SharePoint Tools in Visual Studio
  Puede depurar las extensiones de las herramientas de SharePoint en la instancia experimental o en la instancia normal de Visual Studio.  Si necesita solucionar problemas relacionados con el comportamiento de una extensión, también puede modificar los valores del Registro para mostrar información adicional sobre los errores y configurar el modo en que Visual Studio ejecuta los comandos de SharePoint.  
  
## Depurar extensiones en la instancia experimental de Visual Studio  
 Para evitar que se produzcan daños en el entorno de desarrollo de Visual Studio por extensiones que no se han comprobado, Visual Studio SDK proporciona una instancia de Visual Studio alternativa llamada *instancia experimental*, que se puede usar para instalar y probar extensiones.  Las extensiones nuevas se desarrollan usando la instancia normal de Visual Studio, pero se depuran y ejecutan en la instancia experimental.  Para obtener más información, vea [La instancia Experimental](../extensibility/the-experimental-instance.md).  
  
 Si para implementar la extensión se usa un proyecto de VSIX que es el proyecto de inicio de la solución, cuando se depura la solución, Visual Studio instala y ejecuta la extensión automáticamente en la instancia experimental.  El proyecto de inicio es el proyecto que se inicia cuando se depura una solución que contiene varios proyectos.  Para obtener más información acerca de cómo se usa un proyecto de VSIX para implementar la extensión, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  Para obtener más información acerca de los proyectos de inicio, vea [Cómo: Establecer proyectos de inicio](http://msdn.microsoft.com/es-es/31465836-0911-48db-a5d9-e456b635e970).  
  
 Para obtener ejemplos en los que se muestra cómo depurar diversos tipos de extensiones en la instancia experimental de Visual Studio, vea los siguientes tutoriales:  
  
-   [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## Depurar extensiones en la instancia normal de Visual Studio  
 Si desea depurar el proyecto de extensión en la instancia normal de Visual Studio, instale primero la extensión en la instancia normal.  A continuación, adjunte el depurador a un segundo proceso de Visual Studio.  Una vez finalizados, puede quitar la extensión para que no vuelva a cargarse en el equipo de desarrollo.  
  
#### Para instalar la extensión  
  
1.  Cierre todas las instancias de Visual Studio.  
  
2.  En la carpeta de salida de la compilación del proyecto de extensión, abra el archivo .vsix. Para ello, haga doble clic o abra el menú contextual y elija **Abrir**:  
  
3.  En el cuadro de diálogo **Instalador de extensiones de Visual Studio**, elija la edición de Visual Studio en la que desea instalar la extensión y, a continuación, elija el botón **Instalar**.  
  
     Visual Studio instala los archivos de extensión en %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions\\*author name*\\*extension name*\\*version*.  Las tres últimas carpetas de esta ruta de acceso se crean a partir de los elementos `Author`, `Name` y `Version` del archivo extension.vsixmanifest de la extensión.  
  
4.  Cuando Visual Studio haya instalado la extensión, elija el botón **Cerrar**.  
  
#### Para depurar la extensión  
  
1.  Inicie Visual Studio con privilegios de administrador y abra el proyecto de extensión.  En los pasos siguientes, esta instancia de Visual Studio se va a denominar *primera instancia*.  
  
2.  Inicie otra instancia de Visual Studio con privilegios de administrador.  En los pasos siguientes, esta instancia de Visual Studio se va a denominar *segunda instancia*.  
  
3.  Cambie a la primera instancia de Visual Studio.  
  
4.  En la barra de menús, elija **Depurar**, **Asociar al proceso**.  
  
5.  En la lista **Procesos disponibles**, elija devenv.exe.  Esta entrada hace referencia a la segunda instancia de Visual Studio; esta es la instancia en la que desea depurar la extensión del proyecto.  
  
6.  Elija el botón **Asociar**.  
  
     Visual Studio ejecuta el proyecto de extensión en modo de depuración.  
  
7.  Cambie a la segunda instancia de Visual Studio.  
  
8.  Cree un nuevo proyecto de SharePoint que cargue la extensión.  Por ejemplo, si está depurando una extensión de elementos de proyecto de definición de lista, cree un proyecto **Definición de lista**.  
  
9. Realice los pasos que sean necesarios para probar el código de la extensión.  
  
10. Cuando finalice la depuración de la extensión, cierre la segunda instancia de Visual Studio.  
  
#### Para quitar la extensión  
  
1.  En Visual Studio, en la barra de menús, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.  
  
2.  En la lista de extensiones, elija el nombre de la extensión y, a continuación, el botón **Desinstalar**.  
  
3.  En el cuadro de diálogo que aparece, elija el botón **Sí** para confirmar la desinstalación.  
  
4.  Elija el botón **Reiniciar ahora** para completar la desinstalación.  
  
## Depurar comandos de SharePoint  
 Si desea depurar un comando de SharePoint que forma parte de una extensión de herramientas de SharePoint, debe asociar el depurador al proceso vssphost4.exe.  Se trata del proceso del host de 64 bits que ejecuta los comandos de SharePoint.  Para obtener más información sobre los comandos de SharePoint y vssphost4.exe, vea [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
#### Para asociar el depurador al proceso vssphost4.exe  
  
1.  Inicie la depuración de la extensión en la instancia experimental de Visual Studio o en la instancia normal de Visual Studio; siga las instrucciones mencionadas anteriormente.  
  
2.  En la instancia de Visual Studio en la que se está ejecutando el depurador, en la barra de menús, elija **Depurar**, **Asociar al proceso**.  
  
3.  En la lista **Procesos disponibles**, elija vssphost.exe.  
  
    > [!NOTE]  
    >  Si vssphost.exe no aparece en la lista, debe iniciar el proceso de vssphost4.exe en la instancia de Visual Studio en la que se está ejecutando la extensión.  Normalmente, para ello, realizara una acción que haga que Visual Studio se conecte al sitio de SharePoint del equipo de desarrollo.  Por ejemplo, Visual Studio inicia vssphost4.exe cuando se expande un nodo de conexión del sitio \(un nodo en el que aparece la dirección URL del sitio\) bajo el nodo **Conexiones de SharePoint** de la ventana **Explorador de servidores**, o cuando se agregan ciertos elementos de proyecto de SharePoint, como **Instancia de lista** o **Receptor de eventos** a un proyecto de SharePoint.  
  
4.  Elija el botón **Asociar**.  
  
5.  En la instancia de Visual Studio que se está depurando, siga los pasos necesarios para ejecutar el comando.  
  
## Modificar los valores del Registro para facilitar la depuración de extensiones de herramientas de SharePoint  
 Cuando depure una extensión de herramientas de SharePoint en Visual Studio, puede modificar los valores del Registro para que le resulte más fácil solucionar los problemas relacionados con la extensión.  Los valores se encuentran en la clave HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools.  Estos valores no existen de forma predeterminada.  
  
 Para que le resulte más fácil solucionar los problemas relacionados con las extensiones de herramientas de SharePoint, puede crear y establecer el valor EnableDiagnostics.  En la siguiente tabla se describe este valor.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|EnableDiagnostics|REG\_DWORD que especifica si los mensajes de diagnóstico se muestran en la **Ventana de salida**.<br /><br /> Para mostrar los mensajes de diagnóstico, establezca este valor en 1.  Para dejar de mostrar los mensajes, establezca este valor en 0 o elimínelo.<br /><br /> Para escribir mensajes en la **Ventana de salida** de una extensión de herramientas de SharePoint, use el servicio del proyecto de SharePoint.  Para obtener más información, vea [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).|  
  
 Si la extensión contiene un comando de SharePoint, puede crear y establecer valores adicionales para que le resulte más fácil solucionar los problemas relacionados con el comando.  En la siguiente tabla se describen estos valores.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|AttachDebuggerToHostProcess|REG\_DWORD que especifica si se va a mostrar un cuadro de diálogo que permita asociar el depurador a vssphost4.exe tan pronto como se inicie.  Resulta útil si vssphost.exe ejecuta el comando que se desea depurar inmediatamente después de iniciarse y no hay suficiente tiempo para asociar manualmente el depurador antes de que se ejecute el comando.  Para mostrar el cuadro de diálogo, vssphost4.exe llama al método <xref:System.Diagnostics.Debugger.Break%2A> cuando se inicia.<br /><br /> Para habilitar este comportamiento, establezca este valor en 1.  Para deshabilitar este comportamiento, establezca este valor en 0 o elimínelo.<br /><br /> Si establece este valor en 1, quizás desee también aumentar el valor HostProcessStartupTimeout a fin de disponer de tiempo suficiente para asociar el depurador antes de que Visual Studio espere a que vssphost4.exe indique que se inició correctamente.|  
|ChannelOperationTimeout|REG\_DWORD que especifica el tiempo, en segundos, que Visual Studio espera a que se ejecute un comando de SharePoint.  Si el comando no se ejecuta a tiempo, se produce una excepción <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>.<br /><br /> El valor predeterminado es 120 segundos.|  
|HostProcessStartupTimeout|REG\_DWORD que especifica el tiempo, en segundos, que Visual Studio espera a que vssphost4.exe indique que se ha iniciado correctamente.  Si vssphost4.exe no indica un inicio correcto a tiempo, se produce una excepción <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>.<br /><br /> El valor predeterminado es 60 segundos.|  
|MaxReceivedMessageSize|REG\_DWORD que especifica el tamaño máximo permitido, en bytes, de los mensajes de WCF que se pasan entre Visual Studio y vssphost4.exe.<br /><br /> El valor predeterminado es 1.048.576 \(1 MB\).|  
|MaxStringContentLength|REG\_DWORD que especifica el tamaño máximo permitido, en bytes, de las cadenas que se pasan entre Visual Studio y vssphost4.exe.<br /><br /> El valor predeterminado es 1.048.576 \(1 MB\).|  
  
## Vea también  
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  