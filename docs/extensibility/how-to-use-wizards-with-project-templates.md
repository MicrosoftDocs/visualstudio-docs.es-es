---
title: "C&#243;mo: Utilizar los asistentes con las plantillas de proyectos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IWizard (interfaz)"
  - "plantillas de proyecto [Visual Studio], controles wizard"
  - "plantillas [Visual Studio], controles wizard"
  - "plantillas de Visual Studio, controles wizard"
  - "asistentes [Visual Studio], plantillas de proyecto"
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# C&#243;mo: Utilizar los asistentes con las plantillas de proyectos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio proporciona la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> que, cuando se implementa, permite ejecutar código personalizado cuando un usuario crea un proyecto a partir de una plantilla.  
  
 La personalización de la plantilla de proyecto se puede utilizar para:  
  
-   Mostrar una interfaz de usuario personalizada que acepte los datos proporcionados por el usuario para parametrizar la plantilla.  
  
-   Agregue valores de parámetro para utilizar en la plantilla.  
  
-   Agregue archivos adicionales a la plantilla.  
  
-   Realice virtualmente cualquier acción permitida por el modelo de objetos de automatización de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en un proyecto.  
  
 Mientras se crea el proyecto, se llama varias veces a los métodos de la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>, tan pronto como el usuario hace clic en **Aceptar** en el cuadro de diálogo **Nuevo proyecto**.  Cada método de la interfaz se denomina de modo que describa el punto en el que se llama.  Por ejemplo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] llama a <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> inmediatamente cuando empieza a crear el proyecto, lo que lo convierte en un buen lugar para escribir código personalizado para aceptar los datos proporcionados por el usuario.  
  
 La mayor parte del código que se escribe para los asistentes personalizados utiliza el objeto <xref:EnvDTE.DTE>, que es el objeto principal del modelo de objetos de automatización [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], para personalizar el proyecto.  Para obtener más información sobre el modelo de objetos de automatización, consulte [Ampliar el entorno de Visual Studio](../Topic/Extending%20the%20Visual%20Studio%20Environment.md) y [Referencia de automatización y extensibilidad](../Topic/Automation%20and%20Extensibility%20Reference.md).  
  
## Crear un asistente de plantilla personalizado  
 Este tema muestra cómo crear un asistente personalizado que abre un Windows Form antes de que se cree el proyecto.  El formulario permite al usuario agregar un valor de parámetro personalizado que se agregará a continuación al código fuente durante la creación del proyecto.  Los pasos principales, cada uno de los cuales se explica en detalle, son los siguientes.  
  
#### Para crear un asistente de plantilla personalizado  
  
1.  Cree un ensamblado que implemente la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
2.  Instala el ensamblado en la caché global de ensamblados.  
  
3.  Cree un proyecto y utilice el asistente **Exportar plantilla** para crear una plantilla a partir del proyecto.  
  
4.  Modifique la plantilla agregando un elemento `WizardExtension` en el archivo .vstemplate para vincular la plantilla al ensamblado que implementa <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
5.  Cree un nuevo proyecto mediante el asistente personalizado.  
  
## Implementar IWizard  
 El primer paso del proceso es crear un ensamblado que implemente <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Este ensamblado utiliza el método <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> para mostrar un Windows Form que permita al usuario agregar un valor de parámetro personalizado que, a continuación, se utilizará durante la creación del proyecto.  
  
> [!NOTE]
>  En este ejemplo se usa [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] para implementar <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>, aunque también podría usar [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
#### Para implementar IWizard  
  
1.  Cree un nuevo proyecto de biblioteca de clases.  
  
2.  Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Vea el código siguiente para ver un ejemplo de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] de una interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> totalmente implementada.  
  
 Este ejemplo contiene dos archivos de código: `IWizardImplementation`, una clase que implementa la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> y `UserInputForm`, el formulario Windows Forms para los datos proporcionados por el usuario.  
  
### Clase IWizardImplementation  
 La clase `IWizardImplementation` contiene las implementaciones de método para cada miembro de <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  En este ejemplo, solo el método <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> realiza una tarea.  Los demás métodos no hacen nada o devuelven `true`.  
  
 El método <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> acepta cuatro parámetros:  
  
-   Un parámetro <xref:System.Object> que se puede convertir en el objeto <xref:EnvDTE._DTE> raíz, para permitirle personalizar el proyecto.  
  
-   Un parámetro <xref:System.Collections.Generic.Dictionary%602> que contiene una colección de todos los parámetros predefinidos en la plantilla.  Para obtener más información sobre los parámetros de plantilla, vea [Parámetros de plantilla](../ide/template-parameters.md).  
  
-   Un parámetro <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> que contiene información sobre qué tipo de plantilla se utiliza.  
  
-   Una matriz <xref:System.Object> que contiene un conjunto de parámetros que se pasa al asistente a través de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Este ejemplo agrega un valor de parámetro del formulario de entrada de datos al parámetro <xref:System.Collections.Generic.Dictionary%602>.  Cada instancia del parámetro `$custommessage$` del proyecto se reemplazará por el texto escrito por el usuario.  Debe agregar los ensamblados siguientes al proyecto:  
  
1.  EnvDTE.dll  
  
2.  Microsoft.VisualStudio.TemplateWizardInterface.dll  
  
3.  System.Windows.Forms.dll  
  
> [!IMPORTANT]
>  El UserInputForm utilizado en este ejemplo se define en la sección siguiente.  
  
```c#  
using System;  
using System.Collections.Generic;  
using Microsoft.VisualStudio.TemplateWizard;  
using System.Windows.Forms;  
using EnvDTE;  
  
namespace CustomWizard  
{  
    public class IWizardImplementation:IWizard  
    {  
        private UserInputForm inputForm;  
        private string customMessage;  
  
        // This method is called before opening any item that   
        // has the OpenInEditor attribute.  
        public void BeforeOpeningFile(ProjectItem projectItem)  
        {  
        }  
  
        public void ProjectFinishedGenerating(Project project)  
        {  
        }  
  
        // This method is only called for item templates,  
        // not for project templates.  
        public void ProjectItemFinishedGenerating(ProjectItem   
            projectItem)  
        {  
        }  
  
        // This method is called after the project is created.  
        public void RunFinished()  
        {  
        }  
  
        public void RunStarted(object automationObject,  
            Dictionary<string, string> replacementsDictionary,  
            WizardRunKind runKind, object[] customParams)  
        {  
            try  
            {  
                // Display a form to the user. The form collects   
                // input for the custom message.  
                inputForm = new UserInputForm();  
                inputForm.ShowDialog();  
  
                customMessage = inputForm.get_CustomMessage();  
  
                // Add custom parameters.  
                replacementsDictionary.Add("$custommessage$",   
                    customMessage);  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.ToString());  
            }  
        }  
  
        // This method is only called for item templates,  
        // not for project templates.  
        public bool ShouldAddProjectItem(string filePath)  
        {  
            return true;  
        }          
    }  
}  
```  
  
### Formulario de datos proporcionados por el usuario  
 El formulario de datos proporcionados por el usuario proporciona un formulario simple para escribir un parámetro personalizado.  El formulario contiene un cuadro de texto denominado `textBox1` y un botón denominado `button1`.  Cuando se hace clic en el botón, el texto del cuadro de texto se almacena en el parámetro `customMessage`.  
  
##### Para agregar un Windows Form a la solución  
  
1.  Agregue el código siguiente al archivo que contiene la implementación del asistente.  
  
```c#  
public partial class UserInputForm : Form  
{  
    private string customMessage;  
    private TextBox textBox1;  
  
    public UserInputForm()  
    {   
        textBox1 = new TextBox();  
        this.Controls.Add(textBox1);  
    }  
  
    public string get_CustomMessage()  
    {  
        return customMessage;  
    }  
  
    private void textBox1_TextChanged(object sender, EventArgs e)  
    {  
        customMessage = textBox1.Text;  
        this.Dispose();  
    }  
}  
```  
  
## Instalar el ensamblado en la caché global de ensamblados  
 El ensamblado que implementa <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> se debe firmar con un nombre seguro e instalarse en la caché global de ensamblados.  
  
#### Para instalar el ensamblado en la caché global de ensamblados.  
  
1.  Firmar un ensamblado con un nombre seguro.  Para obtener más información, vea [Cómo: Firmar un ensamblado con un nombre seguro](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md) o [How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/es-es/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
2.  Instala el ensamblado con nombre seguro en la caché global de ensamblados.  Para obtener más información, vea [Cómo: Instalar un ensamblado en la memoria caché global de ensamblados](../Topic/How%20to:%20Install%20an%20Assembly%20into%20the%20Global%20Assembly%20Cache.md).  
  
## Crear un proyecto para utilizarlo como plantilla  
 En este ejemplo, el proyecto que se utiliza como plantilla es una aplicación de consola que muestra el mensaje especificado en el formulario de datos proporcionados por el usuario del asistente personalizado.  
  
#### Para crear el proyecto de ejemplo  
  
1.  Cree una nueva aplicación de consola [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
2.  En el método `Main` de la aplicación, agregue la siguiente línea de código.  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     El parámetro `$custommessage$` se reemplaza por el texto escrito en el formulario de datos proporcionados por el usuario cuando se crea un proyecto a partir de la plantilla.  
  
3.  En el menú **Archivo**, haga clic en **Exportar plantilla**.  
  
4.  En el asistente **Exportar plantilla** asistente, haga clic en **Plantilla de proyecto**, seleccione el proyecto correcto y haga clic en **Siguiente**.  
  
5.  En el asistente **Exportar plantilla**, escriba la descripción de la plantilla, active la casilla **Importar la plantilla automáticamente en Visual Studio** y haga clic en **Finalizar**.  
  
     La plantilla aparece ahora en el cuadro de diálogo **Nuevo proyecto**, pero no utiliza el asistente personalizado.  
  
 El ejemplo siguiente muestra el archivo de código completo antes de haberse exportado a una plantilla.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
namespace TemplateProject  
{  
    class WriteMessage  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("$custommessage$");  
        }  
    }  
}  
```  
  
## Modificar la plantilla  
 Ahora que la plantilla está creada y aparece en el cuadro de diálogo **Nuevo proyecto**, debe modificarla para que utilice el ensamblado creado en los pasos anteriores.  
  
#### Para agregar el asistente personalizado a la plantilla  
  
1.  Busque el archivo .zip que contiene la plantilla.  
  
    1.  En el menú **Herramientas**, haga clic en **Opciones**.  
  
    2.  Haga clic en **Proyectos y soluciones**.  
  
    3.  Lea el cuadro de texto **Ubicación de plantillas de proyecto de usuario de Visual Studio**.  
  
     De forma predeterminada, esta ubicación es Mis documentos\\Visual Studio *Version*\\Templates\\ProjectTemplates.  
  
2.  Extraiga el archivo .zip.  
  
3.  Abra el archivo .vstemplate en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Después del elemento `TemplateContent`, agregue un elemento [WizardExtension \(Elemento, Plantillas de Visual Studio\)](../extensibility/wizardextension-element-visual-studio-templates.md) con el nombre seguro del ensamblado de asistente personalizado.  Para obtener más información sobre cómo encontrar el nombre seguro del ensamblado, vea [Cómo: Consultar el contenido de la memoria caché global de ensamblados](../Topic/How%20to:%20View%20the%20Contents%20of%20the%20Global%20Assembly%20Cache.md)y [Cómo: Hacer referencia a un ensamblado con nombre seguro](../Topic/How%20to:%20Reference%20a%20Strong-Named%20Assembly.md).  
  
     El ejemplo siguiente muestra un elemento `WizardExtension`.  
  
    ```  
    <WizardExtension>  
        <Assembly>CustomWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=fa3902f409bb6a3b</Assembly>  
        <FullClassName>CustomWizard.IWizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
## Utilizar el asistente personalizado  
 Ahora puede crear un proyecto a partir de la plantilla y utilizar el asistente personalizado.  
  
#### Para utilizar el asistente personalizado  
  
1.  En el menú **Archivo**, haga clic en **Nuevo proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, busque la plantilla, escriba un nombre y haga clic en **Aceptar**.  
  
     Se abrirá el formulario de datos proporcionados por el usuario.  
  
3.  Escriba un valor para el parámetro personalizado y haga clic en el botón.  
  
     El formulario de datos proporcionados por el usuario del asistente se cierra y se crea un proyecto a partir de la plantilla.  
  
4.  En el **Explorador de soluciones**, haga clic con el botón secundario en el archivo de código fuente y haga clic en **Ver código**.  
  
     Observe que `$custommessage$` se ha reemplazado con el texto escrito en el formulario de datos proporcionados por el usuario del asistente.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)   
 [WizardExtension \(Elemento, Plantillas de Visual Studio\)](../extensibility/wizardextension-element-visual-studio-templates.md)