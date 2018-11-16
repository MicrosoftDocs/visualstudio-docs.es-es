---
title: Creación de un sistema de proyectos básico, parte 2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 98cdcf426f2aeeb794e9e33754108c792f9725e5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753973"
---
# <a name="creating-a-basic-project-system-part-2"></a>Creación de un sistema de proyectos básico, parte 2
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El primer tutorial de esta serie, [creación de un sistema de proyectos básico, parte 1](../extensibility/creating-a-basic-project-system-part-1.md), se muestra cómo crear un sistema de proyectos básico. En este tutorial se basa en el sistema de proyectos básico mediante la adición de una plantilla de Visual Studio, una página de propiedades y otras características. Debe completar el primer tutorial antes de iniciar esta.  
  
 En este tutorial se enseña cómo crear un tipo de proyecto que tiene el .myproj de extensión de nombre de archivo de proyecto. Para completar el tutorial, no es necesario que crear su propio lenguaje porque toma prestado el tutorial desde el sistema de proyecto de Visual C# existente.  
  
 En este tutorial se enseña cómo realizar estas tareas:  
  
-   Crear una plantilla de Visual Studio.  
  
-   Implementar una plantilla de Visual Studio.  
  
-   Crear un nodo de elemento secundario de tipo de proyecto en el **nuevo proyecto** cuadro de diálogo.  
  
-   Habilitar la sustitución de parámetros en la plantilla de Visual Studio.  
  
-   Crear una página de propiedades del proyecto.  
  
> [!NOTE]
>  Los pasos descritos en este tutorial se basan en un proyecto de C#. Sin embargo, excepto para obtener información específica como extensiones de nombre de archivo y el código, puede usar los mismos pasos para un proyecto de Visual Basic.  
  
## <a name="creating-a-visual-studio-template"></a>Crear una plantilla de Visual Studio  
 [Creación de un sistema de proyectos básico, parte 1](../extensibility/creating-a-basic-project-system-part-1.md) se muestra cómo crear una plantilla de proyecto básico y agregarlo al sistema del proyecto. También muestra cómo registrar esta plantilla con Visual Studio mediante el uso de la <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atributo, que escribe la ruta de acceso completa de la carpeta \Templates\Projects\SimpleProject\ en el registro del sistema.  
  
 Mediante el uso de una plantilla de Visual Studio (archivo .vstemplate) en lugar de una plantilla de proyecto básico, puede controlar cómo la plantilla aparece en el **nuevo proyecto** cuadro de diálogo y cómo se sustituyen los parámetros de plantilla.  Un archivo .vstemplate es un archivo XML que se describe cómo los archivos de origen se incluirán cuando se crea un proyecto mediante la plantilla de proyecto del sistema. El sistema del proyecto es compilado por recopilar el archivo .vstemplate y los archivos de origen en un archivo .zip e implementado copiando el archivo .zip a una ubicación conocida para Visual Studio. Este proceso se explica con más detalle más adelante en este tutorial.  
  
1. En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra la solución SimpleProject que creó siguiendo [creación de un sistema de proyectos básico, parte 1](../extensibility/creating-a-basic-project-system-part-1.md).  
  
2. En el archivo SimpleProjectPackage.cs, busque el atributo ProvideProjectFactory. Reemplace el segundo parámetro (el nombre del proyecto) con el valor null y el cuarto parámetro (la ruta de acceso a la carpeta de plantillas de proyecto) ". \\\NullPath ", como se indica a continuación.  
  
   ```  
   [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
       ".\\NullPath",  
   LanguageVsTemplate = "SimpleProject")]  
   ```  
  
3. Agregue un archivo XML denominado SimpleProject.vstemplate a la carpeta \Templates\Projects\SimpleProject\.  
  
4. Reemplace el contenido de SimpleProject.vstemplate con el código siguiente.  
  
   ```xml  
   <VSTemplate Version="2.0.0" Type="Project"  
       xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
     <TemplateData>  
       <Name>SimpleProject Application</Name>  
       <Description>  
           A project for creating a SimpleProject application  
        </Description>  
        <Icon>SimpleProject.ico</Icon>  
        <ProjectType>SimpleProject</ProjectType>  
     </TemplateData>  
     <TemplateContent>  
       <Project File="SimpleProject.myproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
             Program.cs  
         </ProjectItem>  
         <ProjectItem ReplaceParameters="true" OpenInEditor="false">  
            AssemblyInfo.cs  
         </ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
5. En el **propiedades** ventana, seleccione todos los cinco archivos en la carpeta \Templates\Projects\SimpleProject\ y establezca el **acción de compilación** a **ZipProject**.  
  
   ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
   El \<TemplateData > sección determina la ubicación y la apariencia del tipo de proyecto SimpleProject en el **nuevo proyecto** cuadro de diálogo, como se indica a continuación:  
  
- El \<nombre > nombres de elementos de la plantilla de proyecto aplicación SimpleProject.  
  
- El \<descripción > elemento contiene la descripción que aparece en el **nuevo proyecto** cuadro de diálogo cuando se selecciona la plantilla de proyecto.  
  
- El \<icono > elemento especifica el icono que aparece junto con el tipo de proyecto SimpleProject.  
  
- El \<ProjectType > elemento nombra el tipo de proyecto en el **nuevo proyecto** cuadro de diálogo. Este nombre reemplaza el parámetro de nombre de proyecto del atributo ProvideProjectFactory.  
  
  > [!NOTE]
  >  El \<ProjectType > elemento debe coincidir con el `LanguageVsTemplate` argumento de la `ProvideProjectFactory` atributo en el archivo SimpleProjectPackage.cs.  
  
  El \<TemplateContent > sección describen estos archivos que se generan cuando se crea un nuevo proyecto:  
  
- SimpleProject.myproj  
  
- Program.cs  
  
- AssemblyInfo.cs  
  
  Tienen los tres archivos `ReplaceParameters` establecida en true, lo que permite la sustitución de parámetros.  El archivo Program.cs tiene `OpenInEditor` establecido en true, lo que hace que el archivo se abre en el editor de código cuando se crea un proyecto.  
  
  Para obtener más información acerca de los elementos en el esquema de plantilla de Visual Studio, consulte el [Visual Studio Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md).  
  
> [!NOTE]
>  Si un proyecto tiene más de una plantilla de Visual Studio, cada plantilla está en una carpeta independiente. Todos los archivos de esa carpeta deben tener la **acción de compilación** establecido en **ZipProject**.  
  
## <a name="adding-a-minimal-vsct-file"></a>Adición de un archivo .vsct mínimo  
 Visual Studio se debe ejecutar en modo de instalación para reconocer una plantilla de Visual Studio nueva o modificada. Modo de instalación requiere un archivo .vsct estén presentes. Por lo tanto, debe agregar un archivo .vsct mínimo al proyecto.  
  
1.  Agregue un archivo XML denominado SimpleProject.vsct al proyecto SimpleProject.  
  
2.  Reemplace el contenido del archivo SimpleProject.vsct con el código siguiente.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3.  Establecer el **acción de compilación** de este archivo en **VSCTCompile**. Puede hacerlo solo en el archivo .csproj, no en el **propiedades** ventana. Asegúrese de que el **acción de compilación** de este archivo se establece en **ninguno** en este momento.  
  
    1.  Haga clic en el nodo SimpleProject y, a continuación, haga clic en **SimpleProject.csproj editar**.  
  
    2.  En el archivo .csproj, busque el elemento SimpleProject.vsct.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  Cambiar la acción de compilación a **VSCTCompile**.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  el archivo de proyecto y cierre el editor.  
  
    5.  Guardar el nodo SimpleProject y, a continuación, en el **el Explorador de soluciones** haga clic en **recargar el proyecto**.  
  
## <a name="examining-the-visual-studio-template-build-steps"></a>Examen de los pasos de compilación de la plantilla de Visual Studio  
 El sistema de compilación del proyecto de VSPackage normalmente ejecuta Visual Studio en modo de instalación cuando se cambia el archivo .vstemplate o se vuelve a generar el proyecto que contiene el archivo .vstemplate. Puede seguir estableciendo el nivel de detalle de MSBuild en Normal o superior.  
  
1. En el menú **Herramientas** , haga clic en **Opciones**.  
  
2. Expanda el **proyectos y soluciones** nodo y, a continuación, seleccione **compilar y ejecutar**.  
  
3. Establecer **detalles de la salida de compilación del proyecto de MSBuild** a **Normal**. Haga clic en **Aceptar**.  
  
4. Recompile el proyecto SimpleProject.  
  
   El paso de compilación para crear el archivo .zip del proyecto debe parecerse al ejemplo siguiente.  
  
```  
ZipProjects:  
1>  Zipping ProjectTemplates  
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".  
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip  
1>ZipItems:  
1>  Zipping ItemTemplates  
1>  SimpleProject ->  
```  
  
## <a name="deploying-a-visual-studio-template"></a>Implementar una plantilla de Visual Studio  
 Plantillas de Visual Studio no contienen información de ruta de acceso. Por lo tanto, el archivo .zip de plantilla debe implementarse en una ubicación que se conoce a Visual Studio. La ubicación de la carpeta ProjectTemplates suele  **\<% LOCALAPPDATA % > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates**.  
  
 Para implementar el generador de proyectos, el programa de instalación debe tener privilegios de administrador. Implementa plantillas bajo el nodo de la instalación de Visual Studio: **...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates**.  
  
## <a name="testing-a-visual-studio-template"></a>Prueba de una plantilla de Visual Studio  
 Pruebe el generador de proyectos para ver si crea una jerarquía de proyectos mediante la plantilla de Visual Studio.  
  
1. Restablecer la instancia experimental de Visual Studio SDK.  
  
    En [!INCLUDE[win7](../includes/win7-md.md)]: en el menú Inicio, busque el **Microsoft Visual Studio o Microsoft Visual Studio SDK/herramientas** carpeta y, a continuación, seleccione **restablecer la instancia de Microsoft Visual Studio Experimental**.  
  
    En versiones posteriores de Windows: en la pantalla Inicio, escriba **restablecer Microsoft Visual Studio \<versión > instancia Experimental**.  
  
2. Aparecerá una ventana de símbolo del sistema. Cuando vea las palabras `Press any key to continue`, haga clic en ENTRAR. Después de cerrar la ventana, abra Visual Studio.  
  
3. Recompilar el proyecto SimpleProject e iniciar la depuración. Aparece la instancia experimental.  
  
4. En la instancia experimental, cree un proyecto SimpleProject. En el **nuevo proyecto** cuadro de diálogo, seleccione **SimpleProject**.  
  
5. Debería ver una nueva instancia de SimpleProject.  
  
   ![](../extensibility/media/simpproj2-newproj.png "SimpProj2_NewProj")  
  
   ![](../extensibility/media/simpproj2-myproj.png "SimpProj2_MyProj")  
  
## <a name="creating-a-project-type-child-node"></a>Creación de un nodo secundario de tipo de proyecto  
 Puede agregar un nodo secundario a un nodo de tipo de proyecto en el **nuevo proyecto** cuadro de diálogo.  Por ejemplo, para el tipo de proyecto SimpleProject, podría tener nodos secundarios para las aplicaciones de consola, aplicaciones de la ventana, las aplicaciones web y así sucesivamente.  
  
 Los nodos secundarios se crean al modificar el archivo de proyecto y agregar \<OutputSubPath > elementos secundarios a la \<ZipProject > elementos. Cuando se copia una plantilla durante la compilación o implementación, todos los nodos secundarios se convierte en una subcarpeta de la carpeta de plantillas de proyecto.  
  
 En esta sección se muestra cómo crear un nodo secundario de consola para el tipo de proyecto SimpleProject.  
  
1.  Cambie el nombre de la carpeta \Templates\Projects\SimpleProject\ a \Templates\Projects\ConsoleApp\\.  
  
2.  En el **propiedades** ventana, seleccione todos los cinco archivos en la carpeta \Templates\Projects\ConsoleApp\ y asegúrese de que el **acción de compilación** está establecido en **ZipProject**.  
  
3.  En el archivo SimpleProject.vstemplate, agregue la siguiente línea al final de la \<TemplateData > sección justo antes de la etiqueta de cierre.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     Esto hace que la plantilla de aplicación de consola que aparezcan en el nodo secundario de consola y en el nodo primario SimpleProject, que es un nivel por encima del nodo secundario.  
  
4.  Guarde el archivo SimpleProject.vstemplate.  
  
5.  En el archivo .csproj, agregue \<OutputSubPath > para cada uno de los elementos ZipProject. Descargue el proyecto, como antes y edite el archivo de proyecto.  
  
6.  Busque el \<ZipProject > elementos. A cada \<ZipProject > elemento, agregue un \<OutputSubPath > elemento y asígnele el valor de la consola. El ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>  
    ```  
  
7.  Agregar esto \<PropertyGroup > al archivo de proyecto:  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8.  Guarde el archivo de proyecto y recargar el proyecto.  
  
## <a name="testing-the-project-type-child-node"></a>Probar el nodo secundario de tipo de proyecto  
 Probar el archivo de proyecto modificado para ver si el **consola** nodo secundario aparece en el **nuevo proyecto** cuadro de diálogo.  
  
1. Ejecute el **restablecer la instancia de Microsoft con Visual Studio Experimental** herramienta.  
  
2. Recompilar el proyecto SimpleProject e iniciar la depuración. Debe aparecer la instancia experimental  
  
3. En el **nuevo proyecto** cuadro de diálogo, haga clic en el **SimpleProject** nodo. El **aplicación de consola** plantilla debe aparecer en el **plantillas** panel.  
  
4. Expanda el **SimpleProject** nodo. El **consola** debería aparecer el nodo secundario. El **SimpleProject aplicación** plantilla sigue apareciendo en el **plantillas** panel.  
  
5. . Haga clic en **cancelar** y detener la depuración  
  
   ![](../extensibility/media/simpproj2-rollup.png "SimpProj2_Rollup")  
  
   ![](../extensibility/media/simpproj2-subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substituting-project-template-parameters"></a>Sustitución de parámetros de plantilla de proyecto  
 [Creación de un sistema de proyectos básico, parte 1](../extensibility/creating-a-basic-project-system-part-1.md) se ha explicado cómo sobrescribir los `ProjectNode.AddFileFromTemplate` método para hacer un tipo básico de sustitución de parámetros de plantilla. Esta sección explican cómo usar los parámetros de plantilla de Visual Studio más sofisticados.  
  
 Cuando crea un proyecto mediante el uso de una plantilla de Visual Studio en el **nuevo proyecto** cuadro de diálogo plantilla de parámetros se reemplazan por cadenas para personalizar el proyecto. Un parámetro de plantilla es un token especial que empieza y termina con un signo de dólar, por ejemplo, $time$. Los dos parámetros siguientes son especialmente útiles para habilitar la personalización en los proyectos que se basan en la plantilla:  
  
- $ $GUID [1-10] se sustituirá por un nuevo Guid. Puede especificar hasta 10 GUID únicos, por ejemplo, guid1 $$.  
  
- $safeprojectname$ es el nombre proporcionado por el usuario en el **nuevo proyecto** cuadro de diálogo, puede modificado para quitar todos los caracteres no seguros y espacios.  
  
  Para obtener una lista completa de parámetros de plantilla, vea [Parámetros de plantilla](../ide/template-parameters.md).  Si desea crear su propio parámetro de plantilla personalizada, vea [NIB: Cómo: pasar parámetros personalizados a plantillas](http://msdn.microsoft.com/en-us/5bc2ad11-84c7-4683-a276-e5e00d85d8fb).  
  
#### <a name="to-substitute-project-template-parameters"></a>Sustituir los parámetros de plantilla de proyecto  
  
1.  En el archivo SimpleProjectNode.cs, quite el `AddFileFromTemplate` método.  
  
2.  En el archivo \Templates\Projects\ConsoleApp\SimpleProject.myproj, busque el \<RootNamespace > propiedad y cambie su valor a $safeprojectname$.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  En el archivo \Templates\Projects\SimpleProject\Program.cs, reemplace el contenido del archivo con el código siguiente:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace $safeprojectname$  
    {  
        [Guid("$guid1$")]  
        public class $safeprojectname$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
4.  Recompilar el proyecto SimpleProject e iniciar la depuración. Debería aparecer la instancia experimental.  
  
5.  Cree una nueva aplicación de consola SimpleProject. (En el **tipos de proyecto** panel, seleccione **SimpleProject**. En **plantillas instaladas de Visual Studio**, seleccione **aplicación de consola**.)  
  
6.  En el proyecto recién creado, abra Program.cs. Debe parecerse a lo siguiente (los valores de GUID en el archivo variará.):  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace Console_Application1  
    {  
        [Guid("00000000-0000-0000-00000000-00000000)"]  
        public class Console_Application1  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
## <a name="creating-a-project-property-page"></a>Creación de una página de propiedades del proyecto  
 Puede crear una página de propiedades para el tipo de proyecto para que los usuarios pueden ver y cambiar las propiedades de los proyectos que se basan en la plantilla. En esta sección se muestra cómo crear una página de propiedades independientes de la configuración. Esta página de propiedades básica usa una cuadrícula de propiedades para mostrar las propiedades públicas que se exponen en la clase de página de propiedades.  
  
 Derive la clase de página de propiedades de la `SettingsPage` clase base. La cuadrícula de propiedades proporcionada por el `SettingsPage` clase es compatible con los tipos de datos más primitivos y sabe cómo mostrarlos.  Además, el `SettingsPage` clase sabe cómo conservar los valores de propiedad al archivo de proyecto.  
  
 La página de propiedad que cree en esta sección le permite modificar y guardar estas propiedades de proyecto:  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace.  
  
1. En el archivo SimpleProjectPackage.cs, agregue esto `ProvideObject` atributo a la `SimpleProjectPackage` clase:  
  
   ```  
   [ProvideObject(typeof(GeneralPropertyPage))]  
   public sealed class SimpleProjectPackage : ProjectPackage  
   ```  
  
    Esto registra la clase de página de propiedades `GeneralPropertyPage` con COM.  
  
2. En el archivo SimpleProjectNode.cs, agregue estos dos métodos invalidados a la `SimpleProjectNode` clase:  
  
   ```  
   protected override Guid[] GetConfigurationIndependentPropertyPages()  
   {  
       Guid[] result = new Guid[1];  
       result[0] = typeof(GeneralPropertyPage).GUID;  
       return result;  
   }  
   protected override Guid[] GetPriorityProjectDesignerPages()  
   {  
       Guid[] result = new Guid[1];  
       result[0] = typeof(GeneralPropertyPage).GUID;  
        return result;  
   }  
   ```  
  
    Ambos métodos devuelven una matriz de GUID de página de propiedades.  GeneralPropertyPage GUID es el único elemento de la matriz, por lo que la **páginas de propiedades** cuadro de diálogo mostrará sólo una página.  
  
3. Agregue un archivo de clase denominado GeneralPropertyPage.cs al proyecto SimpleProject.  
  
4. Reemplace el contenido de este archivo con el código siguiente:  
  
   ```  
   using System;  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio;  
   using Microsoft.VisualStudio.Project;  
   using System.ComponentModel;  
  
   namespace SimpleProject  
   {  
       [ComVisible(true)]  
       [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]  
       public class GeneralPropertyPage : SettingsPage  
       {  
           private string assemblyName;  
           private OutputType outputType;  
           private string defaultNamespace;  
  
           public GeneralPropertyPage()  
           {  
               this.Name = "General";  
           }  
  
           [Category("AssemblyName")]  
           [DisplayName("AssemblyName")]  
           [Description("The output file holding assembly metadata.")]  
           public string AssemblyName  
           {  
               get { return this.assemblyName; }  
           }  
           [Category("Application")]  
           [DisplayName("OutputType")]  
           [Description("The type of application to build.")]  
           public OutputType OutputType  
           {  
               get { return this.outputType; }  
               set { this.outputType = value; this.IsDirty = true; }  
           }  
           [Category("Application")]  
           [DisplayName("DefaultNamespace")]  
           [Description("Specifies the default namespace for added items.")]  
           public string DefaultNamespace  
           {  
               get { return this.defaultNamespace; }  
               set { this.defaultNamespace = value; this.IsDirty = true; }  
           }  
  
           protected override void BindProperties()  
           {  
               this.assemblyName = this.ProjectMgr.GetProjectProperty(  
   "AssemblyName", true);  
               this.defaultNamespace = this.ProjectMgr.GetProjectProperty(  
   "RootNamespace", false);  
  
               string outputType = this.ProjectMgr.GetProjectProperty(  
   "OutputType", false);  
               this.outputType =   
   (OutputType)Enum.Parse(typeof(OutputType), outputType);  
           }  
  
           protected override int ApplyChanges()  
           {  
               this.ProjectMgr.SetProjectProperty(  
   "AssemblyName", this.assemblyName);  
               this.ProjectMgr.SetProjectProperty(  
   "OutputType", this.outputType.ToString());  
               this.ProjectMgr.SetProjectProperty(  
   "RootNamespace", this.defaultNamespace);  
               this.IsDirty = false;  
  
               return VSConstants.S_OK;  
           }  
       }  
   }  
   ```  
  
    La `GeneralPropertyPage` clase expone tres propiedades públicas AssemblyName OutputType y RootNamespace. AssemblyName no tiene ningún método de conjunto, se muestra como una propiedad de solo lectura. OutputType es una constante enumerada, para que aparezca como lista desplegable.  
  
    El `SettingsPage` proporciona la clase base `ProjectMgr` para conservar las propiedades. El `BindProperties` usos del método `ProjectMgr` para recuperar los valores de propiedad persisted y establecer las propiedades correspondientes.  El `ApplyChanges` usos del método `ProjectMgr` para obtener los valores de las propiedades y hacer que persistan en el archivo de proyecto. Establece la propiedad método establece `IsDirty` en true para indicar que tienen las propiedades que se deben conservar.  Persistencia se produce cuando se guarda el proyecto o solución.  
  
5. Recompile la solución SimpleProject e iniciar la depuración. Debería aparecer la instancia experimental.  
  
6. En la instancia experimental, cree una nueva aplicación SimpleProject.  
  
7. Visual Studio llama el generador de proyectos para crear un proyecto mediante la plantilla de Visual Studio. Se abre el nuevo archivo Program.cs en el editor de código.  
  
8. Haga clic en el nodo del proyecto en **el Explorador de soluciones**y, a continuación, haga clic en **propiedades**. Aparece el cuadro de diálogo **Páginas de propiedades**.  
  
   ![](../extensibility/media/simpproj2-proppage.png "SimpProj2_PropPage")  
  
## <a name="testing-the-project-property-page"></a>Probar la página de propiedades del proyecto  
 Ahora puede probar si puede modificar y cambiar los valores de propiedad.  
  
1. En el **páginas de propiedades MyConsoleApplication** cuadro de diálogo, cambie el **DefaultNamespace** a **MyApplication**.  
  
2. Seleccione el **OutputType** propiedad y, a continuación, seleccione **biblioteca de clases**.  
  
3. Haga clic en **aplicar**y, a continuación, haga clic en **Aceptar**.  
  
4. Vuelva a abrir el **páginas de propiedades** diálogo cuadro y compruebe que se han guardado los cambios.  
  
5. Cierre la instancia experimental de Visual Studio.  
  
6. Vuelva a abrir la instancia experimental.  
  
7. Vuelva a abrir el **páginas de propiedades** diálogo cuadro y compruebe que se han guardado los cambios.  
  
8. Cierre la instancia experimental de Visual Studio.  
  
   ![](../extensibility/media/simpproj2-proppage2.png "SimpProj2_PropPage2")

