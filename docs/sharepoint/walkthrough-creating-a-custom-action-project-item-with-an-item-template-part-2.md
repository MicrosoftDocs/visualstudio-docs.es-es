---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "project items [SharePoint development in Visual Studio], creating template wizards"
  - "SharePoint project items, creating template wizards"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 2d8165d3-4af9-4a5e-bdba-8b2a06b1dc8d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2
  Después de definir un tipo personalizado de elemento de proyecto de SharePoint y asociarlo a una plantilla de elemento en Visual Studio, es posible que desee proporcionar también un asistente para la plantilla.  Puede usar el asistente para recopilar información de los usuarios cuando empleen la plantilla para agregar a un proyecto una nueva instancia del elemento de proyecto.  La información que recopile puede usarse para inicializar el elemento de proyecto.  
  
 En este tutorial, agregará un asistente al elemento de proyecto Acción personalizada que se muestra en [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  Cuando un usuario agrega un elemento de proyecto acción personalizada a un proyecto de SharePoint, el asistente recopila información sobre la acción personalizada \(como su ubicación y la dirección URL para navegar a un usuario final la elige\) y agrega esta información al archivo Elements.xml del nuevo elemento.  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear un asistente para un tipo de elemento de proyecto de SharePoint personalizado asociado a una plantilla de elemento.  
  
-   Definir una interfaz de usuario de asistente personalizada similar a la de los asistentes integrados para los elementos de proyecto de SharePoint en Visual Studio.  
  
-   Usar parámetros reemplazables para inicializar los archivos de proyecto de SharePoint con los datos recopilados en el asistente.  
  
-   Depurar y probar el asistente.  
  
> [!NOTE]  
>  Puede descargar un ejemplo que contiene los proyectos completos, código, y otros archivos para este tutorial de la siguiente ubicación: [Archivos de proyecto para los tutoriales de extensibilidad de herramientas de SharePoint](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Requisitos previos  
 Para realizar este tutorial, debe crear primero la solución CustomActionProjectItem con el tutorial [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 También necesitará los siguientes componentes en el equipo de desarrollo para completar este tutorial:  
  
-   Ediciones compatibles de Windows, SharePoint, y Visual Studio.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK.  En este tutorial se utiliza la plantilla **Proyecto VSIX** del SDK para crear un paquete VSIX e implementar el elemento.  Para obtener más información, vea [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.  
  
-   Asistentes para plantillas de elementos y proyectos de Visual Studio.  Para obtener más información, vea [Cómo: Utilizar los asistentes con las plantillas de proyectos](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md) y la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
-   Acciones personalizadas en SharePoint.  Para obtener más información, vea [Acción personalizada](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
## Crear el proyecto de asistente  
 Para completar este tutorial, debe agregar un proyecto a la solución CustomActionProjectItem que creó en [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  Implementará la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> y definirá la interfaz de usuario del asistente de este proyecto.  
  
#### Para crear el proyecto de asistente  
  
1.  En Visual Studio, abra la solución CustomActionProjectItem  
  
2.  En **Explorador de soluciones**, abra el menú contextual para el nodo de la solución, elija **Agregar**y, a continuación **Nuevo proyecto**.  
  
    > [!NOTE]  
    >  En los proyectos de Visual Basic, el nodo de la solución aparece en el **Explorador de soluciones** solo cuando se activa la casilla **Mostrar solución siempre** en [General, Proyectos y soluciones, Cuadro de diálogo Opciones](http://msdn.microsoft.com/es-es/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
3.  En el cuadro de diálogo **Nuevo proyecto** , expanda los nodos **Visual c\#** o **Visual Basic** y, a continuación el nodo **Windows** .  
  
4.  En la parte superior del cuadro de diálogo **Nuevo proyecto** , asegúrese de que **.NET Framework 4,5** se elige en la lista de versiones de .NET Framework.  
  
5.  Elija la plantilla de proyecto **Biblioteca de controles de usuario de WPF** , asigne al proyecto **ItemTemplateWizard**, y elija el botón **Aceptar** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **ItemTemplateWizard** a la solución.  
  
6.  Elimine el elemento UserControl1 del proyecto.  
  
## Configurar el proyecto de asistente  
 Antes de crear el asistente, debe agregar una ventana de \(WPF\) de Windows Presentation Foundation, un archivo de código, y referencias de ensamblado al proyecto.  
  
#### Para configurar el proyecto de asistente  
  
1.  En **Explorador de soluciones**, abra el menú contextual del nodo del proyecto **ItemTemplateWizard** y, a continuación **Propiedades**.  
  
2.  En **Diseñador de proyectos**, asegúrese de que el marco de destino esté establecido en .NET Framework 4,5.  
  
     Para los proyectos de Visual c\#, puede establecer este valor en la pestaña **Aplicación** .  Para los proyectos de Visual Basic, puede establecer este valor en la pestaña **Compilar** .  Para obtener más información, vea [Cómo: Usar como destino una versión de .NET Framework](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md).  
  
3.  En el proyecto **ItemTemplateWizard** , agregue un elemento **Ventana \(WPF\)** al proyecto, y llame al elemento **WizardWindow**.  
  
4.  Agregue dos archivos de código que se llama CustomActionWizard y cadenas.  
  
5.  Abrir el menú contextual para el proyecto **ItemTemplateWizard** y, a continuación **Agregar referencia**.  
  
6.  En el cuadro de diálogo **Administrador de referencia \- ItemTemplateWizard** , bajo el nodo **Ensamblados** , elija el nodo **Extensiones** .  
  
7.  Active las casillas situadas junto a los siguientes ensamblados, y después elija el botón **Aceptar** :  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  En **Explorador de soluciones**, en la carpeta **Referencias** del proyecto ItemTemplateWizard, elija la referencia **EnvDTE** .  
  
    > [!NOTE]  
    >  En los proyectos de Visual Basic, la carpeta **Referencias** solo aparece cuando está activada la casilla **Mostrar solución siempre** del [General, Proyectos y soluciones, Cuadro de diálogo Opciones](http://msdn.microsoft.com/es-es/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
9. En la ventana **Propiedades** , cambie el valor de la propiedad **Incrustar tipos de interoperabilidad** a **False**.  
  
## Definir las cadenas de identificación y ubicación predeterminadas para las acciones personalizadas  
 Cada acción personalizada tiene una ubicación y un identificador que se especifican en los atributos `Location` y `GroupID` del elemento `CustomAction` en el archivo Elements.xml.  En este paso, va a definir algunas cadenas válidas para estos atributos en el proyecto ItemTemplateWizard.  Al completar este tutorial, estas cadenas se escriben en el archivo Elements.xml del elemento de proyecto acción personalizada cuando los usuarios especifican una ubicación y un identificador en el asistente.  
  
 Para que resulte más sencillo, este ejemplo solo admite un subconjunto de ubicaciones e identificadores predeterminados disponibles.  Para consultar la lista completa, vea [Default Custom Action Locations and IDs](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### Para definir las cadenas de identificación y ubicación predeterminadas  
  
1.  abierto.  
  
2.  En el proyecto **ItemTemplateWizard** , reemplace el código del archivo de código de cadenas con el código siguiente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/strings.vb#6)]  
  
## Crear la interfaz de usuario del asistente  
 Agregue el código XAML que define la interfaz de usuario del asistente y algún otro código que enlace algunos de los controles del asistente con las cadenas de identificación.  El asistente que crea se parece al asistente integrado para los proyectos de SharePoint en Visual Studio.  
  
#### Para crear la interfaz de usuario del asistente  
  
1.  En el proyecto **ItemTemplateWizard** , abra el menú contextual para el archivo **WizardWindow.xaml** y, a continuación **Abrir** para abrir la ventana del diseñador.  
  
2.  En la vista XAML, reemplace el código XAML actual por el siguiente.  El XAML define una interfaz de usuario que incluye un título, controles para especificar el comportamiento de la acción personalizada y los botones de navegación en la parte inferior de la ventana.  
  
    > [!NOTE]  
    >  El proyecto tendrá algunos errores de compilación después de agregar este código.  Estos errores desaparecerán al agregar código en pasos posteriores.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  La ventana que se crea en este XAML se deriva de la clase base <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> .  Cuando se agrega un cuadro de diálogo WPF personalizado en Visual Studio, se recomienda deriva el cuadro de diálogo de esta clase para tener un estilo coherente con otros cuadros de diálogo en Visual Studio y para evitar los problemas que se podrían producir de otra manera con cuadros de diálogo modales.  Para obtener más información, vea [Creación y administración de cuadros de diálogo modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
3.  Si está desarrollando un proyecto de Visual Basic, quite el espacio de nombres `ItemTemplateWizard` class name `WizardWindow` en el atributo `x:Class` de elemento `Window` .  Este elemento es la primera línea del XAML.  Cuando lo haga, la primera línea debe ser similar al código siguiente:  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  En código\- subyacente del archivo WizardWindow.xaml, reemplace el código actual con el código siguiente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml.cs#7)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/wizardwindow.xaml.vb#7)]  
  
## Implementar el asistente  
 Para definir la funcionalidad del asistente, implemente la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
#### Para implementar el asistente  
  
1.  En el proyecto **ItemTemplateWizard** , abra el archivo de código **CustomActionWizard** y, a continuación reemplaza el código actual de este archivo por el código siguiente:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/customactionwizard.vb#8)]  
  
## Punto de control  
 En este punto del tutorial, todo el código del asistente está en el proyecto.  Compile el proyecto para asegurarse de que se compila sin errores.  
  
#### Para compilar el proyecto  
  
1.  En la barra de menú, elija **Generar**, **Compilar solución**.  
  
## Asociar el asistente a la plantilla de elemento  
 Ahora que ha implementado el asistente, debe asociarlo a la plantilla de elementos **acción personalizada** completando tres pasos principales:  
  
1.  Firmar el ensamblado del asistente con un nombre seguro.  
  
2.  Obtener el token de clave pública del ensamblado del asistente.  
  
3.  Agregar una referencia al ensamblado del asistente en el archivo .vstemplate de la plantilla de elemento **Acción personalizada**.  
  
#### Para firmar el ensamblado del asistente con un nombre seguro  
  
1.  En **Explorador de soluciones**, abra el menú contextual del nodo del proyecto **ItemTemplateWizard** y, a continuación **Propiedades**.  
  
2.  En la ficha **Firma**, active la casilla **Firmar el ensamblado**.  
  
3.  En la lista **Elija un archivo de clave de nombre seguro** , elija **\<New...\>**.  
  
4.  En el cuadro de diálogo **Crear clave de nombre seguro** , escriba un nombre, desactive la casilla **Proteger mi archivo de clave mediante contraseña** , y elija el botón **Aceptar** .  
  
5.  En la barra de menú, elija **Generar**, **Compilar solución**.  
  
#### Para obtener el token de clave pública del ensamblado del asistente  
  
1.  En una ventana de símbolo del sistema de Visual Studio, ejecute el comando siguiente, reemplazando *PathToWizardAssembly* con la ruta de acceso completa al ensamblado ItemTemplateWizard.dll integrado del proyecto ItemTemplateWizard en el equipo de desarrollo.  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     El token de clave pública del ensamblado ItemTemplateWizard.dll se escribe en la ventana del símbolo del sistema de Visual Studio.  
  
2.  Mantenga abierta la ventana del símbolo del sistema de Visual Studio.  Necesitará el token de clave pública completar el procedimiento siguiente.  
  
#### Para agregar una referencia al ensamblado del asistente del archivo .vstemplate  
  
1.  En **Explorador de soluciones**, expanda el nodo del proyecto **ItemTemplate** , y abra el archivo ItemTemplate.vstemplate.  
  
2.  Cuando se acerque el final del archivo, agregue el siguiente elemento `WizardExtension` entre las etiquetas `</TemplateContent>` y `</VSTemplate>`.  Reemplace el valor *TheToken*`PublicKeyToken` con el token de clave pública que obtuvo en el procedimiento anterior.  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Para obtener más información sobre el elemento `WizardExtension`, vea [WizardExtension &#40;Elemento, Plantillas de Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).  
  
3.  Guarde y cierre el archivo.  
  
## Agregar parámetros reemplazables al archivo Elements.xml de la plantilla de elemento  
 Agregue varios parámetros reemplazables al archivo Elements.xml del proyecto ItemTemplate.  Estos parámetros se inicializan en el método `PopulateReplacementDictionary` de la clase `CustomActionWizard` que definió anteriormente.  Cuando un usuario agrega un elemento de proyecto Acción personalizada a un proyecto, Visual Studio reemplaza automáticamente estos parámetros en el archivo Elements.xml del nuevo elemento de proyecto por los valores especificados en el asistente.  
  
 Un parámetro reemplazable es un token que empieza y termina por el signo de dólar \($\).  Además de definición poseer parámetros reemplazables, puede usar los parámetros integrados que el sistema de proyectos de SharePoint define y se inicializa.  Para obtener más información, vea [Parámetros reemplazables](../sharepoint/replaceable-parameters.md).  
  
#### Para agregar parámetros reemplazables al archivo Elements.xml  
  
1.  En el proyecto ItemTemplate, reemplace el contenido del archivo Elements.xml con el XML siguiente.  
  
    ```  
  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     El nuevo código XML cambia los valores de los atributos `Id`, `GroupId`, `Location`, `Description` y `Url` por parámetros reemplazables.  
  
2.  Guarde y cierre el archivo.  
  
## Agregar el asistente al paquete VSIX  
 En el archivo source.extension.vsixmanifest del proyecto VSIX, agregue una referencia al proyecto de asistente de modo que haya implementado con el paquete VSIX que contiene el elemento de proyecto.  
  
#### Para agregar el asistente al paquete VSIX  
  
1.  En **Explorador de soluciones**, abra el menú contextual del archivo **source.extension.vsixmanifest** en el proyecto elementoproyectoacciónpersonalizada y, a continuación **Abrir** para abrirlo en el editor de manifiestos.  
  
2.  En el editor de manifiestos, elija la ficha **Activos** , elija el botón **Nuevo** .  
  
     El cuadro de diálogo **Agregar nuevo activo** aparece.  
  
3.  En la lista **Tipo** , elija **Microsoft.VisualStudio.Assembly**.  
  
4.  En la lista **Origen** , elija **Un proyecto de la solución actual**.  
  
5.  En la lista **Proyecto** , elija **ItemTemplateWizard**, y elija el botón **Aceptar** .  
  
6.  En la barra de menú, elija **Generar**, **Compilar solución**, y asegúrese de que la solución se compila sin errores.  
  
## Probar el asistente  
 Ahora está preparado para probar el asistente.  Primero, empiece a depurar la solución CustomActionProjectItem en la instancia experimental de Visual Studio.  A continuación pruebe el asistente del elemento de proyecto acción personalizada en un proyecto de SharePoint en la instancia experimental de Visual Studio.  Por último, compile y ejecute el proyecto SharePoint para comprobar que la acción personalizada funciona del modo esperado.  
  
#### Para empezar a depurar la solución  
  
1.  Reinicie Visual Studio con credenciales administrativas, y vuelva a abrir la solución elementoproyectoacciónpersonalizada.  
  
2.  En el proyecto ItemTemplateWizard, abra el archivo de código CustomActionWizard, y después agregue un punto de interrupción a la primera línea de código en el método `RunStarted` .  
  
3.  En la barra de menú, elija **Depurar**, **Excepciones**.  
  
4.  En el cuadro de diálogo **Excepciones** , asegúrese de que las casillas **Producida** y **No controlada por el usuario** para **Excepciones de Common Language Runtime** están desactivadas, y elija el botón **Aceptar** .  
  
5.  Empiece a depurar eligiendo la tecla F5, o, en la barra de menús, eligiendo **Depurar**, **Iniciar depuración**.  
  
     Visual Studio instala la extensión en %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Custom Action Project Item\\1.0 and starts an experimental instance of Visual Studio.  Probará el elemento de proyecto en esta instancia de Visual Studio.  
  
#### Para probar el asistente en Visual Studio  
  
1.  En la instancia experimental de Visual Studio, en la barra de menú, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  Expanda el nodo **Visual c\#** o **Visual Basic** \(dependiendo del lenguaje que la plantilla de elementos admite\), expanda el nodo **SharePoint** y, a continuación el nodo **2010** .  
  
3.  En la lista de plantillas de proyecto, elija **Proyecto de SharePoint 2010**, asigne al proyecto **CustomActionWizardTest**, y elija el botón **Aceptar** .  
  
4.  En **Asistente para la personalización de SharePoint**, escriba la dirección URL del sitio que desea utilizar para depurar, y elija el botón **Finalizar** .  
  
5.  En **Explorador de soluciones**, abra el menú contextual para el nodo del proyecto, elija **Agregar**y, a continuación **Nuevo elemento**.  
  
6.  En el cuadro de diálogo **Agregar nuevo elemento \- CustomItemWizardTest** , expanda el nodo **SharePoint** , expanda el nodo **2010** .  
  
7.  En la lista de elementos de proyecto, elija el elemento **acción personalizada** , y elija el botón **Agregar** .  
  
8.  Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `RunStarted`.  
  
9. Continuar depurando el proyecto eligiendo la tecla F5 o, en la barra de menús, eligiendo **Depurar**, **Continuar**.  
  
     Aparece el Asistente para la personalización de SharePoint.  
  
10. En **Ubicación**, elija el botón de opción **Edición de lista** .  
  
11. En la lista **Identificador del grupo** , elija **Comunicaciones**.  
  
12. En el cuadro **Título** , entre en **Centro para desarrolladores de SharePoint**.  
  
13. En el cuadro **Descripción** , entre en **Abra el sitio Web del centro para desarrolladores de SharePoint**.  
  
14. En el cuadro **Dirección URL** , entre en **http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx**, y elija el botón **Finalizar** .  
  
     Studio isual agrega un elemento denominado **CustomAction1** al proyecto y abre el archivo Elements.xml en el editor.  Compruebe que Elements.xml contiene los valores especificados en el asistente.  
  
#### Para probar la acción personalizada en SharePoint  
  
1.  En la instancia experimental de Visual Studio, elija la tecla F5 o, en la barra de menú, elija **Depurar**, **Iniciar depuración**.  
  
     La acción personalizada se empaqueta e implementa en el sitio de SharePoint especificado por la propiedad **URL del sitio** de proyecto, y el explorador web se abre en la página predeterminada de este sitio.  
  
    > [!NOTE]  
    >  Si aparece el cuadro de diálogo **Depuración de scripts deshabilitada** , elija el botón **Sí** .  
  
2.  En el área de listas del sitio de SharePoint, elija el vínculo **Tareas** .  
  
     La página **Tareas – todas las tareas** aparece.  
  
3.  En la pestaña **Herramientas de la lista** ribbon, elija la ficha **Lista** y, a continuación, en el grupo **Configuración** , elija **Configuración de la lista**.  
  
     La página **Configuración de la lista** aparece.  
  
4.  En **Comunicaciones** que dirige cerca de la parte superior de la página, elija el vínculo **Centro para desarrolladores de SharePoint** , comprueba que el explorador el sitio Web http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx, y luego cierre el explorador.  
  
## Limpiar el equipo de desarrollo  
 Después de probar el elemento de proyecto, quite la plantilla de elemento de proyecto de la instancia experimental de Visual Studio.  
  
#### para limpiar el equipo de desarrollo  
  
1.  En la instancia experimental de Visual Studio, en la barra de menú, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
     El cuadro de diálogo **Extensiones y actualizaciones** abra.  
  
2.  En la lista de extensiones, elija la extensión **Elemento de proyecto acción personalizada** , y elija el botón **Desinstalar** .  
  
3.  En el cuadro de diálogo que aparece, elija el botón **Sí** para confirmar que desea desinstalar la extensión, y elija el botón **Reiniciar ahora** para completar la desinstalación.  
  
4.  Cierre ambas instancias de Visual Studio \(la instancia experimental y la instancia de Visual Studio en la que la solución CustomActionProjectItem está abierto\).  
  
## Vea también  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Cómo: Utilizar los asistentes con las plantillas de proyectos](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)   
 [Ubicaciones predeterminadas y id. de la acción personalizada](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  