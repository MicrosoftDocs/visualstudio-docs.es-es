---
title: "Tutorial: Publicar una plantilla de proyecto de control web | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plantillas, controles web"
  - "Plantillas de control web"
ms.assetid: b56490f8-38bd-4220-a17e-5ebb30d3ac78
caps.latest.revision: 22
caps.handback.revision: 22
manager: "douge"
---
# Tutorial: Publicar una plantilla de proyecto de control web
Puede crear una plantilla de proyecto de control web para usarla como base para otros proyectos de control web. También puede distribuir la plantilla como una extensión VSIX.  
  
 Para distribuir una extensión VSIX, recomendamos que la agregue al sitio web de la Galería de Visual Studio, ya que los desarrolladores pueden usar el Administrador de extensiones para buscar allí extensiones nuevas y actualizadas. También puede distribuir una extensión colocándola en otro servidor distinto o grabándola en un CD u otros recursos multimedia.  
  
 En este tutorial, que es uno de los dos tutoriales relacionados, se enseña cómo crear una plantilla de proyecto de control de web y luego distribuirlo. El otro tutorial, [Tutorial: Publicar una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md), enseña a crear y distribuir un control web.  
  
 Este tutorial contiene las siguientes secciones:  
  
-   Crear una plantilla de proyecto de control web en una extensión VSIX  
  
-   Publicar la plantilla en la Galería de Visual Studio  
  
-   Instalar la plantilla de la Galería de Visual Studio  
  
-   Probar la plantilla instalada  
  
-   Agregar un Asistente para acciones de depuración a la plantilla  
  
## Requisitos previos  
 Para completar este tutorial, debe comprender los controles web y saber cómo crear proyectos, establecer propiedades del proyecto y usar la instancia experimental de Visual Studio. Visual Studio y el SDK de Visual Studio deben instalarse en el equipo. Antes de empezar este tutorial, debe completar [Tutorial: Publicar una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## Crear una plantilla de proyecto de control web en una extensión VSIX  
 Para crear una plantilla de proyecto de control web, cree primero un proyecto de control web. Para este tutorial, empiece con el proyecto de control web ColorTextControl que creó en [Tutorial: Publicar una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
 Antes de publicar una plantilla de proyecto en la Galería de Visual Studio, use el asistente para **Exportar plantilla como VSIX** para exportar la plantilla como una extensión VSIX y asignarle un icono para ayudar a identificarla en el **Administrador de extensiones** y una imagen para mostrar lo que hace.  
  
#### Para preparar un proyecto de control web para su distribución  
  
1.  En Visual Studio, abra el proyecto MyWebControls.  
  
2.  Use el **Administrador de extensiones** para descargar el **Asistente para exportar plantillas** del sitio web de la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329).  
  
     Después de instalar el asistente, cuando se abre un proyecto, aparece **Exportar plantilla como VSIX** en el menú **Archivo**.  
  
3.  En el menú **Archivo**, haga clic en **Exportar plantilla como VSIX**.  
  
     ![File menu Export Project as VSIX](../misc/media/pcwc_exportasvsix.png "PCWC\_ExportAsVsix")  
  
4.  En la página **Elegir tipo de plantilla**, seleccione **Plantilla de proyecto** y, a continuación, seleccione MyWebControls.csproj. Haga clic en **Siguiente**.  
  
     ![Elegir una plantilla de proyecto](../misc/media/pcwc_choosetemplate.png "PCWC\_ChooseTemplate")  
  
5.  En la página **Seleccionar opciones de plantilla**, establezca **Nombre de plantilla** en `Extensibility Color Text Web Toolbox Control` y **Descripción de plantilla** en `Color text web control project that produces a VSIX extension.`  
  
6.  Junto al cuadro **Imagen del icono**, haga clic en **Examinar**. En el cuadro **Nombre de archivo**, escriba `*.*`. Busque Color.bmp y haga clic en **Abrir**.  
  
7.  Junto al cuadro **Imagen de vista previa**, haga clic en **Examinar**. En el cuadro **Nombre de archivo**, escriba `*.*`. Busque ScreenShot.bmp y haga clic en **Abrir**. Haga clic en **Siguiente**.  
  
     ![Seleccionar opciones de plantilla](../misc/media/pcwc_selecttemplateoptions2.png "PCWC\_SelectTemplateOptions2")  
  
8.  En la página **Seleccionar opciones de VSIX**, cambie **Nombre de producto** a `Extensibility Color Text Web Control Template`.  
  
9. Si quiere, puede cambiar **Nombre de la compañía**, **Versión**, **Licencia** y **URL de la guía de introducción**.  
  
10. Desactive la opción **Importar la plantilla automáticamente en Visual Studio** Haga clic en **Finalizar**.  
  
     ![Desactivar Importar la plantilla automáticamente](../misc/media/pcwc_.png "PCWC\_")  
  
     En el Explorador de Windows, en la carpeta ..\\Mis documentos\\Visual Studio *\<versión\>*\\My Exported Templates\\, se muestra Extensibility Color Text Web Control Template.vsix.  
  
## Publicar la plantilla en la Galería de Visual Studio  
 La plantilla de proyecto está lista ahora para publicarse en la Galería de Visual Studio.  
  
#### Para publicar la plantilla en la Galería de Visual Studio  
  
1.  En el explorador web, abra el sitio web de la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329).  
  
2.  En la esquina superior derecha, haga clic en **iniciar sesión**.  
  
3.  Para ello, use la cuenta de Microsoft. Si no tiene una cuenta de Microsoft, puede crear una aquí.  
  
4.  Haga clic en **Cargar**.  
  
5.  En el **Paso 1: Tipo de extensión**, seleccione **Plantilla de proyecto o de elemento** y, a continuación, haga clic en **Siguiente**.  
  
6.  En **paso 2: Cargar**, haga clic en **Examinar**. En la carpeta \\My Exported Templates\\, seleccione Extensibility Color Text Web Control Template.vsix. Haga clic en **Siguiente**.  
  
7.  En **Paso 3: Información básica**, se muestra la información del **Asistente para exportar plantillas como VSIX**.  
  
8.  Establezca **Categoría** en `ASP.NET` y **Etiquetas** en `toolbox, web control, templates`.  
  
9. Lea el acuerdo de contribución, acéptelo y, a continuación, en el cuadro, escriba el texto que se muestra.  
  
10. Haga clic en **Crear contribución** y, a continuación, en **Publicar**.  
  
11. Busque la plantilla Extensibility Color Text Web Control Template en la Galería de Visual Studio. Debe aparecer la lista de la plantilla.  
  
     ![La lista de la nueva plantilla de control web](../misc/media/pcwc_templatelisting.png "PCWC\_TemplateListing")  
  
## Instalar la plantilla de la Galería de Visual Studio  
 Ahora que se ha publicado la plantilla de proyecto de control web, instálela en Visual Studio y pruébela.  
  
#### Para instalar la plantilla de proyecto de control web en Visual Studio  
  
1.  En el menú **Herramientas** de Visual Studio, haga clic en **Administrador de extensiones**.  
  
2.  Haga clic en **Galería en línea** y busque la plantilla Extensibility Color Text Web Control Template. Debe aparecer la lista de la plantilla.  
  
3.  Haga clic en **Descargar**. Después de descargar la extensión, haga clic en **Instalar**.  
  
## Probar la plantilla instalada  
 Ahora, puede usar la plantilla Extensibility Color Text Web Control Project Template para crear controles web personalizados. No es necesario crear cada uno de ellos a mano. En esta sección se muestra cómo usar la plantilla para crear un control web BlueColorTextControl.  
  
#### Para crear un control web basado en la plantilla  
  
1.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
2.  En el panel izquierdo, haga clic en **Plantillas en línea**, expanda **Plantillas**, y, a continuación, haga clic en **ASP.NET**. En el panel central, haga clic en **Extensibility Color Text Web Control Template**.  
  
     ![Seleccionar la plantilla Extensibility Color Text Web Template](../misc/media/pcwc_newprojecttemplate.png "PCWC\_NewProjectTemplate")  
  
3.  Establezca **Nombre** en `MoreWebControls`. Haga clic en **Aceptar**.  
  
4.  En **el Explorador de soluciones**, cambie el nombre de ColorTextControl.cs a BlueColorTextControl.cs.  
  
5.  Haga doble clic en BlueColorTextControl.cs para abrirlo en el editor.  
  
6.  En el atributo `ToolboxData`, reemplace ambas apariciones de `ColorTextControl` por `BlueColorTextControl`.  
  
     Estos valores especifican etiquetas de apertura y cierre que se generan para el control cuando se arrastra desde el **Cuadro de herramientas** a una página web en tiempo de diseño.  Deben coincidir con el nombre de la clase de control, que también es el nombre del control que aparecerá en el **Cuadro de herramientas**.  
  
     El principio del código fuente de la clase de control debe ser ahora similar al siguiente código.  
  
    ```  
    namespace MoreWebControls { [DefaultProperty("Text")] [ToolboxData("<{0}:BlueColorTextControl runat=server> </{0}:BlueColorTextControl>")] [ProvideToolboxControl("MoreWebControls", false)] public class BlueColorTextControl : WebControl {  
  
    ```  
  
7.  En el método `get`, cambie `color:green` a `color:blue`.  
  
    ```  
    get { String s = (String)ViewState["Text"]; return "<span style='color:blue'>" + s + "</span>"; }  
    ```  
  
     El texto se ajusta en una etiqueta de extensión que lo colorea de azul.  
  
8.  Compile el proyecto MoreWebControls.  
  
## Probar el nuevo control web  
 Ahora, puede probar si el nuevo control web está disponible en el **Cuadro de herramientas**. Sin embargo, aunque el proyecto MoreWebControls está abierto, al presionar la tecla F5 no se inicia una instancia experimental de Visual Studio en la que se pueda probar el control. Esto sucede porque el proyecto está basado en la plantilla Extensibility Color Text Web Control Template, que todavía no puede establecer una acción de depuración. \(En la sección siguiente se muestra cómo agregar a la plantilla un asistente que establece la acción de depuración\). Por ahora, para probar el control, siga estos pasos.  
  
#### Para probar el nuevo control web  
  
1.  Para abrir una instancia experimental de Visual Studio, inicie la instancia experimental.  
  
    1.  En [!INCLUDE[win7](../debugger/includes/win7_md.md)], use el menú **Inicio** \(**Inicio\/Todos los programas, Microsoft Visual Studio \<versión\> SDK\/Herramientas\/Iniciar la instancia experimental de Visual Studio \<versión\>**.  
  
    2.  En [!INCLUDE[win81](../debugger/includes/win81_md.md)], en la pantalla **Inicio** escriba **Iniciar la instancia experimental de Visual Studio \<versión\>**.  
  
2.  Cree un proyecto de aplicación web.  
  
3.  En el proyecto, abra el archivo default.aspx. Asegúrese de que se muestra la vista **Origen**.  
  
4.  En el **Cuadro de herramientas**, en la categoría **MoreWebControls**, debe mostrarse **BlueColorTextControl**.  
  
     ![Control BlueColorTextControl de la categoría MoreWebControls](../misc/media/pcwc_toolbox2.png "PCWC\_Toolbox2")  
  
5.  Arrastre un control BlueColorTextControl a algún lugar de la etiqueta `body` en la página web.  
  
6.  En la etiqueta `ColorTextControl`, agregue un atributo `Text` y especifique `Think Blue!` como valor. La etiqueta resultante debería ser similar a la siguiente.  
  
    ```  
    <cc1:BlueColorTextControl ID="BlueColorTextControl1" Text="Think Blue!" runat="server" />  
  
    ```  
  
7.  Presione F5 para iniciar el servidor de desarrollo de ASP.NET.  
  
     La pantalla de BlueColorTextControl debe parecerse a la imagen siguiente.  
  
     ![BlueColorTextControl presenta Think Blue](../misc/media/pcwc_thinkblue.png "PCWC\_ThinkBlue")  
  
8.  Cierre el servidor de desarrollo de ASP.NET.  
  
9. Cierre la instancia experimental de Visual Studio.  
  
## Agregar un Asistente para acciones de depuración a la plantilla  
 Como se indicó en la sección anterior, si presiona F5 cuando el proyecto MoreWebControls está abierto, no se abre una instancia experimental de Visual Studio. En su lugar, se muestra este mensaje: "No se puede iniciar directamente un proyecto con un tipo de resultado de biblioteca de clases". Esto sucede cuando la ubicación de la instancia experimental es desconocida para un proyecto. Sin embargo, puede habilitar una plantilla para determinar la ubicación de la instancia experimental en un equipo de destino y establecer la acción de depuración adecuada. Después de esto, todos los proyectos del equipo que se basan en esa plantilla responderán a F5 según lo esperado.  
  
 Todas las plantillas de proyecto de extensibilidad que se incluyen en el SDK de Visual Studio contienen un asistente que se ejecuta durante la instalación, busca la instancia experimental en el equipo de destino y establece la acción de depuración. Puede crear su propio asistente para hacer esto, y puede incluirlo en cada plantilla que distribuya.  
  
 Para agregar un Asistente para acciones de depuración a la plantilla Extensibility Color Text Web Control Template, debe eliminar la primera versión de la plantilla, agregarle el asistente y, a continuación, volver a crearla.  
  
#### Para eliminar la primera versión de la plantilla  
  
1.  En el sitio web de la Galería de Visual Studio, en la esquina superior izquierda, haga clic en **Mis contribuciones**. Aparece el listado de **Extensibility Color Text Web Control Template**.  
  
2.  Para quitar permanentemente la plantilla de proyecto de la Galería de Visual Studio, haga clic en **Eliminar**.  
  
3.  En el menú **Herramientas** de Visual Studio, haga clic en **Administrador de extensiones**.  
  
4.  Seleccione **Extensibility Color Text Web Control Template**, y, a continuación, haga clic en **Desinstalar**.  
  
5.  Cierre el **Administrador de extensiones**.  
  
6.  Cierre la solución MoreWebControls.  
  
7.  Cierre Visual Studio.  
  
8.  Elimine la carpeta de soluciones MoreWebControls.  
  
9. Para completar el proceso de desinstalación, reinicie Visual Studio.  
  
 El Asistente para acciones de depuración debe tener una implementación pública de `Microsoft.VisualStudio.TemplateWizard.IWizard`, y debe estar firmado con un nombre seguro de ensamblado.  
  
#### Para crear el Asistente para acciones de depuración  
  
1.  En el cuadro de diálogo **Nuevo proyecto**, cree un proyecto de **Visual C\#**, **Windows**, **Biblioteca de clases** y asígnele el nombre `MyWizard`.  
  
2.  En el nuevo proyecto, cambie el nombre de class1.cs a MyWizard.cs.  
  
3.  Reemplace el contenido de MyWizard.cs por el código siguiente.  
  
    ```  
    using System; using System.Collections.Generic; using System.Linq; using System.Text; using Microsoft.VisualStudio.TemplateWizard; using System.Globalization; using EnvDTE; namespace MyWizard { public class MyWizard : IWizard { public void BeforeOpeningFile(ProjectItem projectItem) { } public void ProjectFinishedGenerating(Project project) { foreach (Configuration config in project.ConfigurationManager) { //Set up the debug options to run "devenv /rootsuffix Exp"; config.Properties.Item("StartAction").Value = 1; //Get the full path to devenv.exe through DTE.FullName config.Properties.Item("StartProgram").Value = project.DTE.FullName; config.Properties.Item("StartArguments").Value = "/rootsuffix Exp"; } } public void ProjectItemFinishedGenerating(ProjectItem projectItem) { } public void RunFinished() { } public void RunStarted(object automationObject, Dictionary<string, string> replacementsDictionary, WizardRunKind runKind, object[] customParams) { } public bool ShouldAddProjectItem(string filePath) { return true; } } }  
  
    ```  
  
4.  Agregue las siguientes referencias al proyecto. Si hay más de una opción, seleccione la referencia que tenga una ruta de acceso a [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
5.  Haga clic con el botón derecho en el proyecto MyWizard y, a continuación, haga clic en **Propiedades**. En la pestaña **Firma**, seleccione la opción **Firmar el ensamblado**.  
  
6.  En la lista **Elija un archivo de clave de nombre seguro**, seleccione **\<Nuevo...\>**. Aparece el cuadro de diálogo **Crear clave de nombre seguro**.  
  
7.  Establezca **Nombre del archivo de clave** en `key.snk` y desactive la opción **Proteger mi archivo de clave mediante contraseña**.  
  
     ![Especifique un archivo de clave](../misc/media/pcwc_strongname.png "PCWC\_StrongName")  
  
8.  Haga clic en **Aceptar** para agregar key.snk al proyecto.  
  
9. Compile el proyecto MyWizard como una compilación de versión. El asistente está listo para usarse.  
  
10. Cierre la solución MyWizard.  
  
#### Para incorporar el asistente y volver a crear la plantilla  
  
1.  Siga los pasos de la sección anterior, Crear una plantilla de proyecto de control web en una extensión VSIX, pero realice estos cambios y adiciones:  
  
    -   No es necesario descargar el asistente para **Exportar plantilla como VSIX** de nuevo.  
  
    -   En el asistente para **Exportar plantilla como VSIX**, en la página **Select VSIX Options**, en el cuadro **Asistente**, busque el archivo \\bin\\Release\\MyWizard.dll que creó en los pasos anteriores y selecciónelo.  
  
         ![Especificar el ensamblado del asistente](../misc/media/pcwc_wizardassembly.png "PCWC\_WizardAssembly")  
  
    -   Cuando se le pida si quiere sobrescribir el archivo de salida de extensión VSIX existente, haga clic en **Sí**.  
  
2.  Cuando llegue a la sección Probar el nuevo control web, presione F5. Se debe iniciar una instancia experimental de Visual Studio.  
  
## Pasos siguientes  
 Este tutorial ha mostrado cómo usar el asistente para **Exportar plantilla como VSIX** para crear y distribuir una plantilla de proyecto. Si necesita más control de la plantilla de proyecto, por ejemplo, para elegir el icono que aparece en el cuadro de diálogo **Nuevo proyecto**, debe crear explícitamente la plantilla de proyecto y encapsularla en una extensión VSIX. Para obtener más información, consulte [Creating and Sharing Project & Item Templates](http://go.microsoft.com/fwlink/?LinkId=194551) \(Creación y uso compartido de plantillas de proyectos y elementos\) en el sitio web The Visual Studio Blog.  
  
## Vea también  
 [Envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)