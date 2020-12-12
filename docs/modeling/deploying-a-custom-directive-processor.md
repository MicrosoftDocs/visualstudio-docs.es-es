---
title: Implementar un procesador de directivas personalizadas
description: Obtenga información sobre los métodos disponibles para implementar un procesador de directivas personalizado en Visual Studio o en cualquier equipo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, custom directive processors
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 638367f2c3a1238edc257a255280c5197e11d3f0
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363931"
---
# <a name="deploying-a-custom-directive-processor"></a>Implementar un procesador de directivas personalizadas

Para usar un procesador de directivas personalizado en Visual Studio en cualquier equipo, debe registrarlo con uno de los métodos descritos en este tema.

A continuación se indican los métodos que puede usar:

- [Extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Proporciona una manera de instalar y desinstalar el procesador de directivas tanto en el propio equipo como en otros equipos. Por lo general, puede empaquetar otras características en la misma extensión VSIX.

- [VSPackage](../extensibility/internals/vspackages.md). Si define un paquete de VS que contiene otras características además del procesador de directivas, este constituye un método práctico para registrar el procesador de directivas.

- Establecer una clave del Registro. En este método, agrega una entrada del Registro para el procesador de directivas.

Solo debe usar uno de estos métodos si desea transformar la plantilla de texto en Visual Studio o en MSBuild. Si utiliza un host personalizado en su propia aplicación, el host personalizado es el responsable de localizar los procesadores de directivas para cada directiva.

## <a name="deploying-a-directive-processor-in-a-vsix"></a>Implementar un procesador de directivas en una extensión VSIX

Puede Agregar un procesador de directivas personalizado a una [extensión de Visual Studio (VSIX)](../extensibility/starting-to-develop-visual-studio-extensions.md).

 Debe asegurarse de que los dos elementos siguientes están incluidos en el archivo .vsix:

- El ensamblado (.dll) que contiene la clase de procesador de directivas personalizado.

- Un archivo .pkgdef que registra el procesador de directivas. El nombre de raíz del archivo debe ser igual que el ensamblado. Por ejemplo, los archivos pueden tener los nombres CDP.dll y CDP.pkgdef.

Para inspeccionar o cambiar el contenido de un archivo .vsix, cambie su extensión de nombre de archivo a .zip y, a continuación, ábralo. Después de editar el contenido, vuelva a establecer el nombre de archivo en .vsix.

Hay varias maneras de crear un archivo .vsix. El siguiente procedimiento describe un método.

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Para desarrollar un procesador de directivas personalizado en un proyecto VSIX

1. Cree un nuevo proyecto de **Proyecto VSIX** .

2. En **source. Extension. vsixmanifest**, establezca el tipo de contenido y las ediciones admitidas.

    1. En el editor de manifiestos de VSIX, en la pestaña **activos** , elija **nuevo** y establezca las propiedades del nuevo elemento:

         **Tipo**  =  de contenido **VSPackage**

         **Proyecto de origen** = \<*the current project*>

    2. Haga clic en **ediciones seleccionadas** y compruebe los tipos de instalación en los que desea que se pueda usar el procesador de directivas.

3. Agregue un archivo .pkgdef y establezca sus propiedades para incluirlo en el proyecto VSIX.

    1. Cree un archivo de texto y asígnele el nombre \<*assemblyName*> . pkgdef.

         \<*assemblyName*> suele ser el mismo que el nombre del proyecto.

    2. Selecciónelo en el Explorador de soluciones y establezca sus propiedades de la manera siguiente:

         **Acción de compilación** = **Contenido**

         **Copiar en el directorio**  =  de salida **Copiar siempre**

         **Incluir en VSIX**  =  **True**

    3. Establezca el nombre de la extensión VSIX y asegúrese de que el identificador es único.

4. Agregue el siguiente texto en el archivo .pkgdef.

    ```
    [$RootKey$\TextTemplating]
    [$RootKey$\TextTemplating\DirectiveProcessors]
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]
    @="Custom Directive Processor description"
    "Class"="NamespaceName.ClassName"
    "CodeBase"="$PackageFolder$\AssemblyName.dll"
    ```

     Reemplace los siguientes nombres con sus propios nombres: `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName`, `AssemblyName`.

5. Agregue las referencias siguientes al proyecto:

    - **Microsoft. VisualStudio. TextTemplating. \* . 0,1**

    - **Microsoft. VisualStudio. TextTemplating. interfaces. \* . 0,1**

    - **Microsoft. VisualStudio. \* TextTemplating. VSHost.. 0,1**

6. Agregue la clase de procesador de directivas personalizado al proyecto.

     Se trata de una clase pública que debe implementar <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

#### <a name="to-install-the-custom-directive-processor"></a>Para instalar el procesador de directivas personalizado

1. En el explorador de Windows, abra el directorio de compilación (normalmente bin\Debug o bin\Release).

2. Si desea instalar el procesador de directivas en otro equipo, copie el archivo .vsix en el otro equipo.

3. Haga doble clic en el archivo .vsix. Aparece el instalador de extensiones de Visual Studio.

4. Reinicie Visual Studio. Ahora podrá ejecutar plantillas de texto que contienen directivas que hacen referencia al procesador de directivas personalizado. Cada directiva tiene el formato:

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Para desinstalar o deshabilitar temporalmente el procesador de directivas personalizado

1. En el menú **herramientas** de Visual Studio, haga clic en **Administrador de extensiones**.

2. Seleccione el VSIX que contiene el procesador de directivas y, a continuación, haga clic en **desinstalar** o **deshabilitar**.

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>Solucionar problemas de un procesador de directivas en una extensión VSIX
 Si el procesador de directivas no funciona, las siguientes sugerencias pueden servir de ayuda:

- El nombre del procesador que especifica en la directiva personalizada debe coincidir con el valor de `CustomDirectiveProcessorName` que especificó en el archivo .pkgdef.

- El método `IsDirectiveSupported` debe devolver `true` cuando se pasa el nombre de `CustomDirective`.

- Si no puede ver la extensión en el administrador de extensiones, pero el sistema no le permitirá instalarla, elimine la extensión de **%LocalAppData%\Microsoft\VisualStudio. \\ \* 0 \\ \ extensiones**.

- Abra el archivo .vsix e inspeccione su contenido. Para abrirlo, cambie la extensión del nombre del archivo a .zip. Compruebe que contiene los archivos .dll, .pkgdef y extension.vsixmanifest. El archivo extension.vsixmanifest debe contener la lista adecuada del nodo SupportedProducts y un nodo VsPackage bajo el nodo Contenido:

     `<Content>`

     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`

     `</Content>`

## <a name="deploying-a-directive-processor-in-a-vspackage"></a>Implementar un procesador de directivas en un paquete VSPackage
 Si su procesador de directivas forma parte de un paquete VSPackage que se instalará en la GAC, puede hacer que el sistema genere el archivo .pkgdef automáticamente.

 Coloque el siguiente atributo en su clase de paquete:

```csharp
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]
```

> [!NOTE]
> Este atributo se coloca en la clase de paquete, no en la clase de procesador de directivas.

 El archivo .pkgdef se generará al compilar el proyecto. Al instalar el paquete VSPackage, el archivo .pkgdef registrará el procesador de directivas.

 Compruebe que el archivo .pkgdef aparece en la carpeta de compilación, que normalmente es bin\Debug o bin\Release. Si no aparece, abra el archivo .csproj en un editor de texto y quite el siguiente nodo: `<GeneratePkgDefFile>false</GeneratePkgDefFile>`.

 Para obtener más información, consulte [VSPackages](../extensibility/internals/vspackages.md).

## <a name="setting-a-registry-key"></a>Establecer una clave del Registro
 Este método para instalar un procesador de directivas personalizado es el menos adecuado. No proporciona ninguna forma práctica de habilitar y deshabilitar el procesador de directivas, y no proporciona ningún método para distribuir el procesador de directivas a otros usuarios.

> [!CAUTION]
> Una modificación incorrecta del Registro puede provocar daños graves en el sistema. Antes de efectuar cambios en el Registro, asegúrese de realizar una copia de seguridad de la información importante del equipo.

#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>Para registrar un procesador de directivas estableciendo una clave del Registro

1. Ejecute `regedit`.

2. En regedit, navegue a

    **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ \* . 0 \ TextTemplating\DirectiveProcessors**

    Si desea instalar el procesador de directivas en la versión experimental de Visual Studio, inserte "exp" después de "11,0".

3. Agregue una clave del Registro con el mismo nombre que la clase de procesador de directivas.

   - En el árbol del registro, haga clic con el botón secundario en el nodo **DirectiveProcessors** , elija **nuevo** y, a continuación, haga clic en **clave**.

4. En el nuevo nodo, agregue valores de cadena para Class y CodeBase o Assembly, según las siguientes tablas.

   1. Haga clic con el botón secundario en el nodo que ha creado, seleccione **nuevo** y, a continuación, haga clic en **valor de cadena**.

   2. Edite el nombre del valor.

   3. Haga doble clic en el nombre y edite los datos.

   Si el procesador de directivas personalizado no se encuentra en la GAC, las subclaves del Registro deben ser similares a las que aparecen en la siguiente tabla:

|Nombre|Tipo|Datos|
|-|-|-|
|(Es el valor predeterminado).|REG_SZ|(valor no establecido)|
|Clase|REG_SZ|**\<Namespace Name>.\<Class Name>**|
|CodeBase|REG_SZ|**\<Your Path>\\<el nombre del ensamblado\>**|

 Si el ensamblado se encuentra en la GAC, las subclaves del Registro deben ser similares a las que se muestran en la siguiente tabla:

|Nombre|Tipo|Datos|
|-|-|-|
|(Es el valor predeterminado).|REG_SZ|(valor no establecido)|
|Clase|REG_SZ|\<**Your Fully Qualified Class Name**>|
|Ensamblado|REG_SZ|\<**Your Assembly Name in the GAC**>|

## <a name="see-also"></a>Consulta también

- [Crear procesadores de directivas personalizadas para las plantillas de texto T4](../modeling/creating-custom-t4-text-template-directive-processors.md)
