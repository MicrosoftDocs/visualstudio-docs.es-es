---
title: Procedimiento Usar asistentes con plantillas de proyectos
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51c89fb82985d37b106f352047bfce74503f3c48
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913111"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Procedimiento Usar asistentes con plantillas de proyecto

Visual Studio proporciona la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> que, cuando se implementa, permite ejecutar código personalizado cuando un usuario crea un proyecto a partir de una plantilla.

La personalización de la plantilla de proyecto se puede usar para mostrar la interfaz de usuario personalizada que recopila los datos proporcionados por el usuario para personalizar la plantilla, agregar archivos adicionales a la plantilla o cualquier otra acción permitida en un proyecto.

Se <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> llama a los métodos de interfaz en varias ocasiones mientras se crea el proyecto, comenzando en cuanto un usuario haga clic en **Aceptar** en el cuadro de diálogo **nuevo proyecto** . Cada método de la interfaz se denomina de modo que describa el punto en el que se llama. Por ejemplo, Visual Studio llama <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> inmediatamente a cuando empieza a crear el proyecto, convirtiéndolo en una buena ubicación para escribir código personalizado para recopilar datos proporcionados por el usuario.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Crear un proyecto de plantilla de proyecto con un proyecto VSIX

Empiece a crear una plantilla personalizada con el proyecto de plantilla de proyecto, que forma parte del SDK de Visual Studio. En este procedimiento, usaremos un C# proyecto de plantilla de proyecto, pero también hay un proyecto de plantilla de proyecto Visual Basic. A continuación, agregue un proyecto VSIX a la solución que contiene el proyecto de plantilla de proyecto.

1. Cree un C# proyecto de plantilla de proyecto (en Visual Studio, seleccione **archivo** > **nuevo** > **proyecto** y busque "plantilla de proyecto"). Asígnele el nombre **MyProjectTemplate**.

   > [!NOTE]
   > Es posible que se le pida que instale el SDK de Visual Studio. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

2. Agregue un nuevo proyecto de VSIX en la misma solución que el proyecto de plantilla de proyecto (en **Explorador de soluciones**, seleccione el nodo de la solución, haga clic con el botón derecho y seleccione **Agregar** > **nuevo proyecto** y busque "VSIX"). Asígnele el nombre **MyProjectWizard.**

3. Establezca el Proyecto VSIX como proyecto de inicio. En **Explorador de soluciones**, seleccione el nodo del Proyecto VSIX, haga clic con el botón derecho y seleccione **establecer como proyecto de inicio**.

4. Agregue el proyecto de plantilla como un recurso del Proyecto VSIX. En **Explorador de soluciones**, en el nodo del Proyecto VSIX, busque el archivo *source. Extension. vsixmanifest* . Haga doble clic en él para abrirlo en el editor de manifiestos.

5. En el editor de manifiestos, seleccione la pestaña **activos** en el lado izquierdo de la ventana.

6. En la pestaña **activos** , seleccione **nuevo**. En la ventana **Agregar nuevo recurso** , en el campo tipo, seleccione **Microsoft. VisualStudio. ProjectTemplate**. En el campo **origen** , seleccione **un proyecto en la solución actual**. En el campo **proyecto** , seleccione **MyProjectTemplate**. A continuación, haga clic en **Aceptar**.

7. Compile la solución y comience la depuración. Se muestra una segunda instancia de Visual Studio. (Esto puede tardar unos minutos).

8. En la segunda instancia de Visual Studio, intente crear un nuevo proyecto con la nueva plantilla (**archivo** > **nuevo** > **proyecto**, busque "mi proyecto"). El nuevo proyecto debe aparecer con una clase denominada **Class1**. Ahora ha creado una plantilla de proyecto personalizada. Detener la depuración ahora.

## <a name="create-a-custom-template-wizard"></a>Asistente para crear plantillas personalizadas

En este procedimiento se muestra cómo crear un asistente personalizado que abra un Windows Form antes de crear el proyecto. El formulario permite a los usuarios agregar un valor de parámetro personalizado que se agrega al código fuente durante la creación del proyecto.

1. Configure el Proyecto VSIX para permitirle crear un ensamblado.

2. En **Explorador de soluciones**, seleccione el nodo de Proyecto VSIX. A continuación **Explorador de soluciones**, debería ver la ventana **propiedades** . Si no lo hace, seleccione la ventana **Ver** > **propiedades**o presione **F4**. En la ventana **propiedades** , seleccione los campos siguientes para `true`:

   - **Incluir ensamblado en el contenedor VSIX**

   - **Incluir símbolos de depuración en el contenedor VSIX**

   - **Incluir símbolos de depuración en la implementación de VSIX local**

3. Agregue el ensamblado como un recurso al Proyecto VSIX. Abra el archivo *source. Extension. vsixmanifest* y seleccione la pestaña **activos** . En la ventana **Agregar nuevo recurso** , en **tipo** , seleccione **Microsoft. VisualStudio. Assembly**, en **origen** , seleccione **un proyecto en la solución actual**y, en **proyecto** , seleccione **MyProjectWizard**.

4. Agregue las siguientes referencias al Proyecto VSIX. (En **Explorador de soluciones**, en el nodo del Proyecto VSIX, seleccione **referencias**, haga clic con el botón derecho y seleccione **Agregar referencia**). En el cuadro de diálogo **Agregar referencia** , en la pestaña **Framework** , busque el ensamblado **System. Windows Forms** y selecciónelo. Busque y seleccione los ensamblados **System** y **System. Drawing** . Ahora, seleccione la pestaña **extensiones** . Busque el ensamblado **EnvDTE** y selecciónelo. Busque también el ensamblado **Microsoft. VisualStudio. TemplateWizardInterface** y selecciónelo. Haga clic en **OK**.

5. Agregue una clase para la implementación del asistente al Proyecto VSIX. (En **Explorador de soluciones**, haga clic con el botón secundario en el nodo del Proyecto VSIX y seleccione **Agregar**, **nuevo elemento**y, a continuación, **clase**). Asigne a la clase el nombre **WizardImplementation**.

6. Reemplace el código del archivo *WizardImplementationClass.CS* por el código siguiente:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.TemplateWizard;
   using System.Windows.Forms;
   using EnvDTE;

   namespace MyProjectWizard
   {
       public class WizardImplementation:IWizard
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

                   customMessage = UserInputForm.CustomMessage;

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

    El **UserInputForm** al que se hace referencia en este código se implementará más adelante.

    La clase `WizardImplementation` contiene las implementaciones de método para cada miembro de <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. En este ejemplo, solo el método <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> realiza una tarea. Los demás métodos no hacen nada o devuelven `true`.

    El método <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> acepta cuatro parámetros:

   - Un parámetro <xref:System.Object> que se puede convertir en el objeto <xref:EnvDTE._DTE> raíz, para permitirle personalizar el proyecto.

   - Un parámetro <xref:System.Collections.Generic.Dictionary%602> que contiene una colección de todos los parámetros predefinidos en la plantilla. Para obtener más información sobre los parámetros de plantilla, vea [parámetros de plantilla](../ide/template-parameters.md).

   - Un parámetro <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> que contiene información sobre qué tipo de plantilla se utiliza.

   - Una <xref:System.Object> matriz que contiene un conjunto de parámetros que Visual Studio pasa al asistente.

     Este ejemplo agrega un valor de parámetro del formulario de entrada de datos al parámetro <xref:System.Collections.Generic.Dictionary%602>. Cada instancia del parámetro `$custommessage$` del proyecto se reemplazará por el texto escrito por el usuario.

7. Ahora cree el **UserInputForm**. En el archivo *WizardImplementation.CS* , agregue el código siguiente después del final de la `WizardImplementation` clase.

   ```csharp
   public partial class UserInputForm : Form
       {
           private static string customMessage;
           private TextBox textBox1;
           private Button button1;

           public UserInputForm()
           {
               this.Size = new System.Drawing.Size(155, 265);

               button1 = new Button();
               button1.Location = new System.Drawing.Point(90, 25);
               button1.Size = new System.Drawing.Size(50, 25);
               button1.Click += button1_Click;
               this.Controls.Add(button1);

               textBox1 = new TextBox();
               textBox1.Location = new System.Drawing.Point(10, 25);
               textBox1.Size = new System.Drawing.Size(70, 20);
               this.Controls.Add(textBox1);
           }
           public static string CustomMessage
           {
               get
               {
                   return customMessage;
               }
               set
               {
                   customMessage = value;
               }
           }
           private void button1_Click(object sender, EventArgs e)
           {
               customMessage = textBox1.Text;
               this.Close();
           }
       }
   ```

    El formulario de datos proporcionados por el usuario proporciona un formulario simple para escribir un parámetro personalizado. El formulario contiene un cuadro de texto denominado `textBox1` y un botón denominado `button1`. Cuando se hace clic en el botón, el texto del cuadro de texto se almacena en el parámetro `customMessage`.

## <a name="connect-the-wizard-to-the-custom-template"></a>Conexión del asistente a la plantilla personalizada

Para que la plantilla de proyecto personalizada use el Asistente personalizado, debe firmar el ensamblado del asistente y agregar algunas líneas a la plantilla de proyecto personalizada para que sepa dónde encontrar la implementación del asistente cuando se crea un nuevo proyecto.

1. Firmar el ensamblado. En el **Explorador de soluciones**, seleccione el Proyecto VSIX, haga clic con el botón derecho y seleccione **propiedades del proyecto**.

2. En la ventana **propiedades del proyecto** , seleccione la pestaña **firma** . en la pestaña **firma** , Active **firmar el ensamblado**. En el campo **elegir un archivo de clave de nombre seguro** , seleccione  **\<nuevo >** . En la ventana **crear clave de nombre seguro** , en el campo **nombre del archivo de clave** , escriba **key. snk**. Desactive la casilla **proteger mi archivo de clave con una contraseña** .

3. En el **Explorador de soluciones**, seleccione el Proyecto VSIX y busque la ventana **propiedades** .

4. Establezca el campo **Copiar la salida de la compilación en el directorio de salida** en **true**. Esto permite que el ensamblado se copie en el directorio de salida cuando se vuelva a generar la solución. Todavía está incluido en el `.vsix` archivo. Debe ver el ensamblado para averiguar su clave de firma.

5. Recompilar la solución.

6. Ahora puede encontrar el archivo Key. snk en el directorio del proyecto MyProjectWizard ( *\<la ubicación del disco > \MyProjectTemplate\MyProjectWizard\key.snk*). Copie el archivo *key. snk* .

7. Vaya al directorio de salida y busque el ensamblado ( *\<la ubicación del disco > \ MyProjectTemplate/MyProjectWizard \ bin \ Debug \ MyProjectWizard. dll*). Pegue el archivo *key. snk* aquí. (Esto no es absolutamente necesario, pero facilitará los siguientes pasos).

8. Abra una ventana de comandos y cambie al directorio en el que se ha creado el ensamblado.

9. Busque la herramienta de firma *SN. exe* . Por ejemplo, en un sistema operativo Windows 10 64 bits, una ruta de acceso típica sería la siguiente:

     *C:\Archivos de programa (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*

     Si no puede encontrar la herramienta, intente ejecutarla **donde/r. SN. exe** en la ventana de comandos. Anote la ruta de acceso.

10. Extraiga la clave pública del archivo *key. snk* . En la ventana de comandos, escriba

     **\<Ubicación de SN. exe > \sn.exe-p Key. snk OUTFILE. Key.**

     No olvide encerrar la ruta de acceso de *SN. exe* con comillas si hay espacios en los nombres de directorio.

11. Obtiene el token de clave pública del OUTFILE:

     **\<Ubicación de SN. exe > \sn.exe-t OUTFILE. Key.**

     Una vez más, no olvide las comillas. Debería ver una línea en la salida como esta.

     **El token de clave \<pública es un token >**

     Tome nota de este valor.

12. Agregue la referencia al Asistente personalizado para el archivo *. vstemplate* de la plantilla de proyecto. En el **Explorador de soluciones**, busque el archivo denominado *MyProjectTemplate. vstemplate*y ábralo. Después del final de la \<sección TemplateContent >, agregue la siguiente sección:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Donde **MyProjectWizard** es el nombre del ensamblado y **token** es el token que copió en el paso anterior.

13. Guarde todos los archivos en el proyecto y vuelva a generarlos.

## <a name="add-the-custom-parameter-to-the-template"></a>Agregar el parámetro personalizado a la plantilla

En este ejemplo, el proyecto que se usa como plantilla muestra el mensaje especificado en el formulario de datos proporcionados por el usuario del Asistente personalizado.

1. En el **Explorador de soluciones**, vaya al proyecto **MyProjectTemplate** y Abra *Class1.CS*.

2. En el método `Main` de la aplicación, agregue la siguiente línea de código.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    El parámetro `$custommessage$` se reemplaza por el texto escrito en el formulario de datos proporcionados por el usuario cuando se crea un proyecto a partir de la plantilla.

Este es el archivo de código completo antes de que se haya exportado a una plantilla.

```csharp
using System;
using System.Collections.Generic;
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;
$endif$using System.Text;

namespace $safeprojectname$
{
    public class Class1
    {
          static void Main(string[] args)
          {
               Console.WriteLine("$custommessage$");
          }
    }
}
```

## <a name="use-the-custom-wizard"></a>Usar el Asistente personalizado

Ahora puede crear un proyecto a partir de la plantilla y utilizar el asistente personalizado.

1. Vuelva a generar la solución e inicie la depuración. Aparece una segunda instancia de Visual Studio.

2. Cree un nuevo proyecto de MyProjectTemplate. (**Archivo** > nuevoproyecto > ).

3. En el cuadro de diálogo **nuevo proyecto** , busque "mi proyecto" para buscar la plantilla, escriba un nombre y haga clic en **Aceptar**.

     Se abrirá el formulario de datos proporcionados por el usuario.

4. Escriba un valor para el parámetro personalizado y haga clic en el botón.

     El formulario de datos proporcionados por el usuario del asistente se cierra y se crea un proyecto a partir de la plantilla.

5. En **Explorador de soluciones**, haga clic con el botón secundario en el archivo de código fuente y haga clic en **Ver código**.

     Observe que `$custommessage$` se ha reemplazado con el texto escrito en el formulario de datos proporcionados por el usuario del asistente.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)
- [WizardExtension (elemento, plantillas de Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Paquetes NuGet en plantillas de Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
