---
title: 'Cómo: Utilizar los asistentes con las plantillas de proyectos'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d2dc057dfa518bb52c6ba4d30cd0f3e0a822cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710545"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Cómo: Usar asistentes con plantillas de proyecto

Visual Studio proporciona la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> que, cuando se implementa, permite ejecutar código personalizado cuando un usuario crea un proyecto a partir de una plantilla.

La personalización de plantillas de proyecto se puede usar para mostrar la interfaz de usuario personalizada que recopila la entrada del usuario para personalizar la plantilla, agregar archivos adicionales a la plantilla o cualquier otra acción permitida en un proyecto.

Los <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> métodos de interfaz se llaman en varios momentos mientras se crea el proyecto, comenzando tan pronto como un usuario hace clic en **Aceptar** en el **nuevo proyecto** cuadro de diálogo. Cada método de la interfaz se denomina de modo que describa el punto en el que se llama. Por ejemplo, Visual <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Studio llama inmediatamente cuando comienza a crear el proyecto, por lo que es una buena ubicación para escribir código personalizado para recopilar la entrada del usuario.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Crear un proyecto de plantilla de proyecto con un proyecto VSIX

Empieza a crear una plantilla personalizada con el proyecto de plantilla de proyecto, que forma parte del SDK de Visual Studio. En este procedimiento, usaremos un proyecto de plantilla de proyecto de C, pero también hay un proyecto de plantilla de proyecto de Visual Basic. A continuación, agregue un proyecto VSIX a la solución que contiene el proyecto de plantilla de proyecto.

1. Cree un proyecto de plantilla de proyecto **File** > de C- (en Visual Studio, seleccione**Nuevo** > **proyecto** de archivo y busque "plantilla de proyecto"). Asílo **llamo MyProjectTemplate**.

   > [!NOTE]
   > Es posible que se le pida que instale el SDK de Visual Studio. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

2. Agregue un nuevo proyecto VSIX en la misma solución que el proyecto de plantilla de proyecto (en el Explorador de **soluciones**, seleccione el nodo de solución, haga clic con el botón derecho y seleccione **Agregar** > **nuevo proyecto** y busque "vsix"). Asílo llamo **MyProjectWizard.**

3. Establezca el proyecto VSIX como el proyecto de inicio. En el **Explorador**de soluciones , seleccione el nodo del proyecto VSIX, haga clic con el botón derecho y seleccione **Establecer como proyecto**de inicio .

4. Agregue el proyecto de plantilla como un recurso del proyecto VSIX. En **el Explorador**de soluciones , en el nodo del proyecto VSIX, busque el archivo *source.extension.vsixmanifest.* Haga doble clic en él para abrirlo en el editor de manifiestos.

5. En el editor de **manifiestos,** seleccione la pestaña Activos en el lado izquierdo de la ventana.

6. En la pestaña **Activos,** seleccione **Nuevo**. En la ventana **Agregar nuevo recurso,** para el campo Tipo , seleccione **Microsoft.VisualStudio.ProjectTemplate**. En el campo **Origen,** seleccione Un proyecto en la **solución actual.** En el campo **Proyecto** , seleccione **MyProjectTemplate**. A continuación, haga clic en **Aceptar**.

7. Compile la solución y comience la depuración. Se muestra una segunda instancia de Visual Studio. Esto puede tardar unos minutos.

8. En la segunda instancia de Visual Studio, intente crear un nuevo proyecto con la nueva plantilla (**Archivo** > **nuevo** > **proyecto**, busque "myproject"). El nuevo proyecto debe aparecer con una clase denominada **Class1**. ¡Ahora ha creado una plantilla de proyecto personalizada! Detenga la depuración ahora.

## <a name="create-a-custom-template-wizard"></a>Crear un asistente de plantilla personalizado

Este procedimiento muestra cómo crear un asistente personalizado que abre un formulario Windows Forms antes de crear el proyecto. El formulario permite a los usuarios agregar un valor de parámetro personalizado que se agrega al código fuente durante la creación del proyecto.

1. Configure el proyecto VSIX para permitirle crear un ensamblaje.

2. En **el Explorador**de soluciones , seleccione el nodo del proyecto VSIX. Debajo **del Explorador**de soluciones , debería ver la ventana **Propiedades.** Si no lo hace, seleccione **Ver** > **ventana Propiedades**o pulse **F4**. En la ventana **Propiedades,** seleccione `true`los siguientes campos para:

   - **Incluir ensamblaje en el contenedor VSIX**

   - **Incluir símbolos de depuración en el contenedor VSIX**

   - **Incluir símbolos de depuración en la implementación local de VSIX**

3. Agregue el ensamblado como un recurso al proyecto VSIX. Abra el archivo *source.extension.vsixmanifest* y seleccione la pestaña **Assets.** En la ventana **Agregar nuevo recurso** , en **Tipo,** seleccione **Microsoft.VisualStudio.Assembly**, en **Origen,** seleccione Un proyecto en la **solución actual**y, en **Proyecto,** seleccione **MyProjectWizard**.

4. Agregue las siguientes referencias al proyecto VSIX. (En el Explorador de **soluciones**, en el nodo del proyecto VSIX, seleccione **Referencias**, haga clic con el botón derecho y seleccione **Agregar referencia**.) En el cuadro de diálogo **Agregar referencia,** en la pestaña **Marco** de trabajo, busque el ensamblado **System.Windows Forms** y selecciónelo. Busque y seleccione también los ensamblajes **System** y **System.Drawing.** Ahora seleccione la pestaña **EnvDTE** **Extensiones.** También busque el **Microsoft.VisualStudio.TemplateWizardInterface** ensamblado y selecciónelo. Haga clic en **OK**.

5. Agregue una clase para la implementación del asistente al proyecto VSIX. (En **el Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto VSIX y seleccione **Agregar**, a continuación, **Nuevo elemento**y, a continuación, **Clase**.) Asigne a la clase el nombre **WizardImplementation**.

6. Reemplace el código del archivo *WizardImplementationClass.cs* por el código siguiente:

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

   - Un parámetro <xref:System.Collections.Generic.Dictionary%602> que contiene una colección de todos los parámetros predefinidos en la plantilla. Para obtener más información sobre los parámetros de plantilla, consulte [Parámetros](../ide/template-parameters.md)de plantilla .

   - Un parámetro <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> que contiene información sobre qué tipo de plantilla se utiliza.

   - Matriz <xref:System.Object> que contiene un conjunto de parámetros pasados al asistente por Visual Studio.

     Este ejemplo agrega un valor de parámetro del formulario de entrada de datos al parámetro <xref:System.Collections.Generic.Dictionary%602>. Cada instancia del parámetro `$custommessage$` del proyecto se reemplazará por el texto escrito por el usuario.

7. Ahora cree **userInputForm**. En el archivo *WizardImplementation.cs,* agregue el código `WizardImplementation` siguiente después del final de la clase.

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

## <a name="connect-the-wizard-to-the-custom-template"></a>Conecte el asistente a la plantilla personalizada

Para que la plantilla de proyecto personalizada use el asistente personalizado, debe firmar el ensamblado del asistente y agregar algunas líneas a la plantilla de proyecto personalizada para que sepa dónde encontrar la implementación del asistente cuando se crea un nuevo proyecto.

1. Firme el ensamblado. En el **Explorador**de soluciones , seleccione el proyecto VSIX, haga clic con el botón derecho y seleccione **Propiedades del proyecto**.

2. En la ventana Propiedades del **proyecto,** seleccione la ficha **Firma** en la ficha **Firma,** active **Firmar el ensamblado**. En el campo Elegir un archivo ** \< **de clave de nombre **seguro,** seleccione Nueva>. En la ventana Crear clave de **nombre seguro,** en el campo Nombre de **archivo** de clave, escriba **key.snk**. Desactive el campo **Proteger mi archivo de claves con una contraseña.**

3. En el Explorador de **soluciones**, seleccione el proyecto VSIX y busque la ventana **Propiedades.**

4. Establezca el campo **Copiar salida de compilación en Directorio** de salida en **true**. Esto permite que el ensamblado se copie en el directorio de salida cuando se reconstruya la solución. Todavía está contenido en `.vsix` el archivo. Debe ver el ensamblado para averiguar su clave de firma.

5. Recompile la solución.

6. Ahora puede encontrar el archivo key.snk en el directorio del proyecto MyProjectWizard*\<(la ubicación del disco>, MyProjectTemplate, MyProjectWizard, key.snk*). Copie el archivo *key.snk.*

7. Vaya al directorio de salida y busque el ensamblado*\<(la ubicación del disco>,MyProjectTemplate/MyProjectWizard, bin, Debug, MyProjectWizard.dll*). Pegue el archivo *key.snk* aquí. (Esto no es absolutamente necesario, pero facilitará los siguientes pasos.)

8. Abra una ventana de comandos y cambie al directorio en el que se ha creado el ensamblado.

9. Busque la herramienta de firma *sn.exe.* Por ejemplo, en un sistema operativo Windows 10 de 64 bits, una ruta de acceso típica sería la siguiente:

     *C:'Archivos de programa'''Microsoft SDKs'Windows'v10.0A'bin'NETFX 4.6.1 Herramientas*

     Si no puede encontrar la herramienta, intente ejecutar **donde /R . sn.exe** en la ventana de comandos. Tome nota de la ruta.

10. Extraiga la clave pública del archivo *key.snk.* En la ventana de comandos, escriba

     **\<ubicación de sn.exe>-sn.exe -p key.snk outfile.key.**

     ¡No olvide rodear la ruta de acceso de *sn.exe* con comillas si hay espacios en los nombres de directorio!

11. Obtenga el token de clave pública del archivo de salida:

     **\<ubicación de sn.exe>-sn.exe -t outfile.key.**

     Una vez más, no olvide las comillas. Debería ver una línea en la salida como esta

     **El token \<de clave pública es token>**

     Anote este valor.

12. Agregue la referencia al asistente personalizado al archivo *.vstemplate* de la plantilla de proyecto. En el Explorador de **soluciones**, busque el archivo denominado *MyProjectTemplate.vstemplate*y ábralo. Después del \<final de la sección TemplateContent>, agregue la siguiente sección:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Donde **MyProjectWizard** es el nombre del ensamblado y **token** es el token que copió en el paso anterior.

13. Guarde todos los archivos en el proyecto y vuelva a generar.

## <a name="add-the-custom-parameter-to-the-template"></a>Agregue el parámetro personalizado a la plantilla

En este ejemplo, el proyecto utilizado como plantilla muestra el mensaje especificado en el formulario de entrada de usuario del asistente personalizado.

1. En el Explorador de **soluciones**, vaya al proyecto **MyProjectTemplate** y abra *Class1.cs*.

2. En el método `Main` de la aplicación, agregue la siguiente línea de código.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    El parámetro `$custommessage$` se reemplaza por el texto escrito en el formulario de datos proporcionados por el usuario cuando se crea un proyecto a partir de la plantilla.

Aquí está el archivo de código completo antes de que se haya exportado a una plantilla.

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

## <a name="use-the-custom-wizard"></a>Utilice el asistente personalizado

Ahora puede crear un proyecto a partir de la plantilla y utilizar el asistente personalizado.

1. Vuelva a generar la solución e inicie la depuración. Aparece una segunda instancia de Visual Studio.

2. Cree un nuevo proyecto MyProjectTemplate. (**Archivo** > **nuevo** > **proyecto**).

3. En el cuadro de diálogo **Nuevo proyecto,** busque "myproject" para buscar la plantilla, escriba un nombre y haga clic en **Aceptar**.

     Se abrirá el formulario de datos proporcionados por el usuario.

4. Escriba un valor para el parámetro personalizado y haga clic en el botón.

     El formulario de datos proporcionados por el usuario del asistente se cierra y se crea un proyecto a partir de la plantilla.

5. En **el Explorador**de soluciones , haga clic con el botón secundario en el archivo de código fuente y haga clic en Ver **código**.

     Observe que `$custommessage$` se ha reemplazado con el texto escrito en el formulario de datos proporcionados por el usuario del asistente.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Personalización de plantillas](../ide/customizing-project-and-item-templates.md)
- [Elemento WizardExtension (plantillas de Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Paquetes NuGet en plantillas de Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
