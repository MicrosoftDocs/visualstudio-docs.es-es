---
title: Creación de un sistema básico de proyectos, Parte 2 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7823dc949e78cc6d22514a1ba93476fd5f42d076
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739713"
---
# <a name="create-a-basic-project-system-part-2"></a>Crear un sistema básico de proyectos, parte 2
El primer tutorial de esta serie, Crear un sistema de [proyecto básico, parte 1](../extensibility/creating-a-basic-project-system-part-1.md), muestra cómo crear un sistema de proyecto básico. Este tutorial se basa en el sistema de proyectos básico agregando una plantilla de Visual Studio, una página de propiedades y otras características. Debe completar el primer tutorial antes de iniciar este.

En este tutorial se enseña cómo crear un tipo de proyecto que tiene la extensión de nombre de archivo de proyecto *.myproj*. Para completar el tutorial, no es necesario crear su propio lenguaje porque el tutorial toma prestado del sistema de proyectos de Visual C.

Este tutorial enseña cómo realizar estas tareas:

- Cree una plantilla de Visual Studio.

- Implementar una plantilla de Visual Studio.

- Cree un nodo secundario de tipo de proyecto en el cuadro de diálogo **Nuevo proyecto.**

- Habilite la sustitución de parámetros en la plantilla de Visual Studio.

- Cree una página de propiedades de proyecto.

> [!NOTE]
> Los pasos de este tutorial se basan en un proyecto de C. Sin embargo, excepto para detalles como las extensiones de nombre de archivo y el código, puede usar los mismos pasos para un proyecto de Visual Basic.

## <a name="create-a-visual-studio-template"></a>Crear una plantilla de Visual Studio
- Crear un sistema de [proyecto básico, la parte 1](../extensibility/creating-a-basic-project-system-part-1.md) muestra cómo crear una plantilla de proyecto básica y agregarla al sistema de proyectos. También se muestra cómo registrar esta plantilla <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> con Visual Studio mediante el atributo, que escribe la ruta de acceso completa de la * \\\\ * carpeta Plantillas , Proyectos , SimpleProject en el registro del sistema.

Mediante el uso de una plantilla de Visual Studio (archivo *.vstemplate)* en lugar de una plantilla de proyecto básica, puede controlar cómo aparece la plantilla en el cuadro de diálogo **Nuevo proyecto** y cómo se sustituyen los parámetros de plantilla. Un archivo *.vstemplate* es un archivo XML que describe cómo se deben incluir los archivos de origen cuando se crea un proyecto mediante la plantilla del sistema de proyecto. El propio sistema del proyecto se compila recopilando el archivo *.vstemplate* y los archivos de origen en un archivo *.zip* y se implementa copiando el archivo *.zip* en una ubicación conocida por Visual Studio. Este proceso se explica con más detalle más adelante en este tutorial.

1. En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra la solución SimpleProject que creó siguiendo Crear un sistema de [proyecto básico, parte 1.](../extensibility/creating-a-basic-project-system-part-1.md)

2. En el archivo *SimpleProjectPackage.cs,* busque el atributo ProvideProjectFactory. Reemplace el segundo parámetro (el nombre del proyecto) por null y el cuarto parámetro (la ruta de acceso a la carpeta de plantilla de proyecto) por ". \\"NullPath", como se indica a continuación.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Agregue un archivo XML denominado *SimpleProject.vstemplate* a la * \\carpeta Templates-Projects-SimpleProject.\\ *

4. Reemplace el contenido de *SimpleProject.vstemplate* por el código siguiente.

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

5. En la ventana **Propiedades** , seleccione los cinco archivos de la **Build Action** * \\carpeta Plantillas, Proyectos y SimpleProject\\ * y establezca la Acción de compilación en **ZipProject**.

    ![Carpeta de proyecto simple](../extensibility/media/simpproj2.png "SimpProj2")

    La \<sección> TemplateData determina la ubicación y el aspecto del tipo de proyecto SimpleProject en el cuadro de diálogo **Nuevo proyecto,** como se indica a continuación:

- El \<elemento Name> nombra la plantilla de proyecto para que sea SimpleProject Application.

- El \<elemento de> Descripción contiene la descripción que aparece en el cuadro de diálogo **Nuevo proyecto** cuando se selecciona la plantilla de proyecto.

- El \<elemento Icon> especifica el icono que aparece junto con el tipo de proyecto SimpleProject.

- El \<elemento projectType> nombre el tipo de proyecto en el cuadro de diálogo **Nuevo proyecto.** Este nombre reemplaza el parámetro de nombre de proyecto de la ProvideProjectFactory atributo.

  > [!NOTE]
  > El \<elemento de> `LanguageVsTemplate` ProjectType `ProvideProjectFactory` debe coincidir con el argumento del atributo en el archivo SimpleProjectPackage.cs.

  La \<sección TemplateContent> describe estos archivos que se generan cuando se crea un nuevo proyecto:

- *SimpleProject.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Los tres `ReplaceParameters` archivos se han establecido en true, lo que permite la sustitución de parámetros. El *Program.cs* archivo `OpenInEditor` Program.cs se ha establecido en true, lo que hace que el archivo se abra en el editor de código cuando se crea un proyecto.

  Para obtener más información acerca de los elementos del esquema de plantilla de Visual Studio, vea la referencia de esquema de plantilla de [Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Si un proyecto tiene más de una plantilla de Visual Studio, cada plantilla está en una carpeta independiente. Cada archivo de esa carpeta debe tener la acción de **compilación** establecida en **ZipProject**.

## <a name="adding-a-minimal-vsct-file"></a>Adición de un archivo .vsct mínimo
 Visual Studio debe ejecutarse en modo de instalación para reconocer una plantilla de Visual Studio nueva o modificada. El modo de instalación requiere la presentación de un archivo *.vsct.* Por lo tanto, debe agregar un archivo *.vsct* mínimo al proyecto.

1. Agregue un archivo XML denominado *SimpleProject.vsct* al proyecto SimpleProject.

2. Reemplace el contenido del archivo *SimpleProject.vsct* por el código siguiente.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Establezca la acción de **compilación** de este archivo en **VSCTCompile**. Solo puede hacerlo en el archivo *.csproj,* no en la ventana **Propiedades.** Asegúrese de que la acción de **compilación** de este archivo está establecida en **Ninguno** en este momento.

    1. Haga clic con el botón secundario en el nodo SimpleProject y, a continuación, haga clic en **Editar SimpleProject.csproj**.

    2. En el archivo *.csproj,* busque el elemento *SimpleProject.vsct.*

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Cambie la acción de compilación a **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. el archivo de proyecto y cierre el editor.

    5. Guarde el nodo SimpleProject y, a continuación, en el **Explorador** de soluciones, haga clic en **Volver a cargar proyecto**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Examine los pasos de compilación de la plantilla de Visual Studio
 El sistema de compilación de proyectos de VSPackage normalmente ejecuta Visual Studio en modo de instalación cuando se cambia el archivo *.vstemplate* o se vuelve a generar el proyecto que contiene el archivo *.vstemplate.* Puede seguir el nivel de detalle de MSBuild en Normal o superior.

1. En el menú **Herramientas** , haga clic en **Opciones**.

2. Expanda el nodo **Proyectos y soluciones** y, a continuación, seleccione Compilar y **ejecutar**.

3. Establezca la verbosidad de la generación de compilación del proyecto de **MSBuild** en **Normal**. Haga clic en **OK**.

4. Vuelva a generar el proyecto SimpleProject.

    El paso de compilación para crear el archivo de proyecto *.zip* debe ser similar al siguiente ejemplo.

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

## <a name="deploy-a-visual-studio-template"></a>Implementar una plantilla de Visual Studio
Las plantillas de Visual Studio no contienen información de ruta de acceso. Por lo tanto, el archivo *.zip* de plantilla debe implementarse en una ubicación conocida por Visual Studio. La ubicación de la carpeta ProjectTemplates suele ser *<%LOCALAPPDATA%>.Microsoft-VisualStudio-14.0Exp-ProjectTemplates*.

Para implementar el generador de proyectos, el programa de instalación debe tener privilegios de administrador. Implementa plantillas en el nodo de instalación de Visual Studio: *... .*. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

## <a name="test-a-visual-studio-template"></a>Probar una plantilla de Visual Studio
Pruebe el generador de proyectos para ver si crea una jerarquía de proyectos mediante la plantilla de Visual Studio.

1. Restablezca la instancia experimental del SDK de Visual Studio.

    En: [!INCLUDE[win7](../debugger/includes/win7_md.md)]en el menú **Inicio,** busque la carpeta **MICROSOFT Visual Studio/Microsoft Visual Studio SDK/Tools** y, a continuación, seleccione Restablecer la instancia experimental de Microsoft Visual **Studio**.

    En versiones posteriores de Windows: en la pantalla **Inicio,** escriba **Restablecer la versión \<** de Microsoft Visual Studio> Instancia experimental .

2. Aparece una ventana del símbolo del sistema. Cuando vea las palabras **Pulse cualquier tecla para continuar**, haga clic en **ENTRAR**. Después de cerrar la ventana, abra Visual Studio.

3. Vuelva a generar el proyecto SimpleProject e inicie la depuración. Aparece la instancia experimental.

4. En la instancia experimental, cree un proyecto SimpleProject. En el cuadro de diálogo **Nuevo proyecto** , seleccione **SimpleProject**.

5. Debería ver una nueva instancia de SimpleProject.

    ![Proyecto simple nueva instancia](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Mi proyecto nueva instancia](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Crear un nodo secundario de tipo de proyecto
Puede agregar un nodo secundario a un nodo de tipo de proyecto en el cuadro de diálogo **Nuevo proyecto.** Por ejemplo, para el tipo de proyecto SimpleProject, podría tener nodos secundarios para aplicaciones de consola, aplicaciones de ventana, aplicaciones web, etc.

Los nodos secundarios se crean modificando \<el archivo de \<proyecto y agregando OutputSubPath> elementos secundarios a los elementos de> ZipProject. Cuando se copia una plantilla durante la compilación o la implementación, cada nodo secundario se convierte en una subcarpeta de la carpeta de plantillas de proyecto.

En esta sección se muestra cómo crear un nodo secundario de consola para el tipo de proyecto SimpleProject.

1. Cambie el nombre de la * \\\\ * carpeta Plantillas , Proyectos , SimpleProject a * \\Plantillas , Proyectos , ConsolaApp\\*.

2. En la ventana **Propiedades** , seleccione los cinco archivos de la **Build Action** * \\carpeta Plantillas, Proyectos y\\ Consolación* y asegúrese de que la acción de compilación está establecida en **ZipProject**.

3. En el archivo SimpleProject.vstemplate, agregue la siguiente \<línea al final de la sección TemplateData>, justo antes de la etiqueta de cierre.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    Esto hace que la plantilla de aplicación de consola aparezca tanto en el nodo secundario de la consola como en el nodo primario SimpleProject, que está un nivel por encima del nodo secundario.

4. Guarde el archivo *SimpleProject.vstemplate.*

5. En el archivo *.csproj,* agregue \<OutputSubPath> a cada uno de los ZipProject elementos. Descargue el proyecto, como antes, y edite el archivo de proyecto.

6. Busque \<los elementos de> ZipProject. A \<cada elemento de> \<ZipProject, agregue un elemento de> OutputSubPath y asípiese el valor Console. El ZipProject

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

7. Agregue \<este> PropertyGroup al archivo de proyecto:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Guarde el archivo de proyecto y vuelva a cargar el proyecto.

## <a name="test-the-project-type-child-node"></a>Pruebe el nodo secundario del tipo de proyecto
Pruebe el archivo de proyecto modificado para ver si el nodo secundario **Consola** aparece en el cuadro de diálogo **Nuevo proyecto.**

1. Ejecute la herramienta Restablecer la instancia experimental de **Microsoft Visual Studio.**

2. Vuelva a generar el proyecto SimpleProject e inicie la depuración. La instancia experimental debe aparecer

3. En el cuadro de diálogo **Nuevo proyecto,** haga clic en el nodo **SimpleProject.** La plantilla Aplicación de **consola** debe aparecer en el panel **Plantillas.**

4. Expanda el nodo **SimpleProject.** Debería aparecer el nodo secundario **Consola.** La plantilla **Aplicación SimpleProject** sigue apareciendo en el panel **Plantillas.**

5. Haga clic en **Cancelar** y detenga la depuración.

    ![Paquete acumulativo simple de proyectos](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Nodo simple de la consola del proyecto](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Parámetros de plantilla de proyecto sustitutos
- [Al crear un sistema](../extensibility/creating-a-basic-project-system-part-1.md) de proyecto básico, la parte 1 mostró cómo sobrescribir el `ProjectNode.AddFileFromTemplate` método para realizar un tipo básico de sustitución de parámetros de plantilla. En esta sección se enseña cómo usar los parámetros de plantilla de Visual Studio más sofisticados.

Al crear un proyecto mediante una plantilla de Visual Studio en el cuadro de diálogo **Nuevo proyecto,** los parámetros de plantilla se reemplazan por cadenas para personalizar el proyecto. Un parámetro de plantilla es un token especial que comienza y termina con un signo de dólar, por ejemplo, $time$. Los dos parámetros siguientes son especialmente útiles para habilitar la personalización en proyectos basados en la plantilla:

- $GUID[1-10]$ es reemplazada por un nuevo Guid. Puede especificar hasta 10 GUID únicos, por ejemplo, $guid1$.

- $safeprojectname$ es el nombre proporcionado por un usuario en el cuadro de diálogo **Nuevo proyecto,** modificado para quitar todos los caracteres y espacios no seguros.

  Para obtener una lista completa de parámetros de plantilla, vea [Parámetros de plantilla](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Para sustituir los parámetros de la plantilla de proyecto

1. En el archivo *SimpleProjectNode.cs,* quite el `AddFileFromTemplate` método.

2. En el \< * \\archivo Templates-Projects-ConsoleApp-SimpleProject.myproj,* busque la propiedad> RootNamespace y cambie su valor a $safeprojectname$.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. En el * \\archivo Templates-Projects-SimpleProject-Program.cs,* sustituya el contenido del archivo por el código siguiente:

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

4. Vuelva a generar el proyecto SimpleProject e inicie la depuración. Debería aparecer la instancia experimental.

5. Cree una nueva aplicación De simpleProject Console. (En el panel Tipos de **proyecto,** seleccione **SimpleProject**. En **Plantillas instaladas**de Visual Studio , seleccione Aplicación de **consola**.)

6. En el proyecto recién creado, abra *Program.cs*. Debe tener un aspecto similar al siguiente (los valores GUID del archivo diferirán):

    ```csharp
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

## <a name="create-a-project-property-page"></a>Crear una página de propiedades de proyecto
Puede crear una página de propiedades para el tipo de proyecto para que los usuarios puedan ver y cambiar las propiedades de los proyectos que se basan en la plantilla. En esta sección se muestra cómo crear una página de propiedades independiente de la configuración. Esta página de propiedades básica utiliza una cuadrícula de propiedades para mostrar las propiedades públicas que expone en la clase de página de propiedades.

Derive la clase de `SettingsPage` página de propiedades de la clase base. La cuadrícula de `SettingsPage` propiedades proporcionada por la clase es consciente de la mayoría de los tipos de datos primitivos y sabe cómo mostrarlos. Además, `SettingsPage` la clase sabe cómo conservar los valores de propiedad en el archivo de proyecto.

La página de propiedades que cree en esta sección le permite modificar y guardar estas propiedades del proyecto:

- AssemblyName

- OutputType

- RootNamespace.

1. En el archivo *SimpleProjectPackage.cs,* agregue este `ProvideObject` atributo a la `SimpleProjectPackage` clase:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Esto registra la clase `GeneralPropertyPage` de página de propiedades con COM.

2. En el archivo *SimpleProjectNode.cs,* agregue estos `SimpleProjectNode` dos métodos invalidados a la clase:

    ```csharp
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

    Ambos métodos devuelven una matriz de GUID de página de propiedades. El GUID de GeneralPropertyPage es el único elemento de la matriz, por lo que el cuadro de diálogo **Páginas** de propiedades mostrará solo una página.

3. Agregue un archivo de clase denominado *GeneralPropertyPage.cs* al proyecto SimpleProject.

4. Reemplace el contenido de este archivo utilizando el siguiente código:

    ```csharp
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
                this.assemblyName = this.ProjectMgr.GetProjectProperty("AssemblyName", true);
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty("RootNamespace", false);

                string outputType = this.ProjectMgr.GetProjectProperty("OutputType", false);
                this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType);
            }

            protected override int ApplyChanges()
            {
                this.ProjectMgr.SetProjectProperty("AssemblyName", this.assemblyName);
                this.ProjectMgr.SetProjectProperty("OutputType", this.outputType.ToString());
                this.ProjectMgr.SetProjectProperty("RootNamespace", this.defaultNamespace);
                this.IsDirty = false;

                return VSConstants.S_OK;
            }
        }
    }
    ```

    La `GeneralPropertyPage` clase expone las tres propiedades públicas AssemblyName, OutputType y RootNamespace. Dado que AssemblyName no tiene ningún método set, se muestra como una propiedad de solo lectura. OutputType es una constante enumerada, por lo que aparece como lista desplegable.

    La `SettingsPage` clase `ProjectMgr` base proporciona para conservar las propiedades. El `BindProperties` método `ProjectMgr` se utiliza para recuperar los valores de propiedad persistentes y establecer las propiedades correspondientes. El `ApplyChanges` método `ProjectMgr` se utiliza para obtener los valores de las propiedades y conservarlos en el archivo de proyecto. El método de `IsDirty` conjunto de propiedades se establece en true para indicar que las propiedades deben conservarse. La persistencia se produce al guardar el proyecto o la solución.

5. Vuelva a generar la solución SimpleProject e inicie la depuración. Debería aparecer la instancia experimental.

6. En la instancia experimental, cree una nueva aplicación SimpleProject.

7. Visual Studio llama al generador de proyectos para crear un proyecto mediante la plantilla de Visual Studio. El nuevo archivo *Program.cs* se abre en el editor de código.

8. Haga clic con el botón secundario en el nodo del proyecto en el **Explorador**de soluciones y, a continuación, haga clic en **Propiedades**. Se muestra el cuadro de diálogo **Páginas de propiedades**.

    ![Página de propiedades del proyecto simple](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Pruebe la página de propiedades del proyecto
Ahora puede probar si puede modificar y cambiar los valores de propiedad.

1. En el cuadro de diálogo Páginas de propiedades **MyConsoleApplication** , cambie **DefaultNamespace** a **MyApplication**.

2. Seleccione la propiedad **OutputType** y, a continuación, seleccione **Biblioteca de clases**.

3. Haga clic en **Aplicar** y en **Aceptar**.

4. Vuelva a abrir el cuadro de diálogo **Páginas** de propiedades y compruebe que los cambios se han pertenido.

5. Cierre la instancia experimental de Visual Studio.

6. Vuelva a abrir la instancia experimental.

7. Vuelva a abrir el cuadro de diálogo **Páginas** de propiedades y compruebe que los cambios se han pertenido.

8. Cierre la instancia experimental de Visual Studio.
    ![Cierre la instancia experimental](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
