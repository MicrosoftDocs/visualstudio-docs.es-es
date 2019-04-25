---
title: Agregar referencias en el Administrador de referencias
ms.date: 04/11/2018
ms.topic: conceptual
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b26c700e90189882f850d4bda1d47fb6f54c025
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2019
ms.locfileid: "58322329"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Procedimiento Agregar o quitar referencias con el Administrador de referencias

Puede usar el cuadro de diálogo **Administrador de referencias** para agregar y administrar referencias a componentes que usted, Microsoft u otra empresa hayan desarrollado. Si va a desarrollar una aplicación de Windows universal, el proyecto hará referencia automáticamente a todos los archivos DLL correctos del SDK de Windows. Si va a desarrollar una aplicación .NET, el proyecto hará referencia automáticamente a *mscorlib.dll*. Algunas API de .NET se exponen en los componentes que debe agregar manualmente. Las referencia a los componentes COM o a los componentes personalizados tienen que agregarse manualmente.

## <a name="reference-manager-dialog-box"></a>Cuadro de diálogo Administrador de referencias

En el cuadro de diálogo **Administrador de referencias** se muestran distintas categorías en el lado izquierdo, según el tipo de proyecto:

- **Ensamblados**, con los subgrupos **Framework** y **Extensiones**.

- **COM**, donde se enumeran todos los componentes a los que se puede hacer referencia.

- **Solución**, con el subgrupo **Proyectos**.

- **Windows**, con los subgrupos **Principal** y **Extensiones**. Puede explorar las referencias del SDK de Windows o los SDK de extensión mediante el **Examinador de objetos**.

- **Examinar**, con el subgrupo **Reciente**.

## <a name="add-a-reference"></a>Agregar una referencia

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **Referencias** o **Dependencias** y elija **Agregar referencia**. También puede hacer clic con el botón derecho en el nodo del proyecto y seleccionar **Agregar** > **Referencia**.

   Se abre el **Administrador de referencias** y se muestran las referencias disponibles por grupo.

2. Especifique las referencias que quiere agregar y seleccione **Aceptar**.

## <a name="assemblies-tab"></a>Pestaña Ensamblados

En la pestaña **Ensamblados** se muestran todos los ensamblados de .NET Framework a los que se puede hacer referencia. La pestaña **Ensamblados** no muestra ningún ensamblado de la caché global de ensamblados (GAC) porque los ensamblados de la GAC forman parte del entorno en tiempo de ejecución. Si implementa o copia una aplicación que contiene una referencia a un ensamblado registrado en la memoria caché global de ensamblados, el ensamblado no se implementará ni copiará con la aplicación, independientemente de la configuración de **Copia local**. Para más información, vea [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md).

Al agregar manualmente una referencia a cualquiera de los espacios de nombres EnvDTE (<xref:EnvDTE>, <xref:EnvDTE80>, <xref:EnvDTE90>, <xref:EnvDTE90a> o <xref:EnvDTE100>), establezca la propiedad **Incrustar tipos de interoperabilidad** de la referencia en **False** en la ventana **Propiedades**. Si establece esta propiedad en **True**, se pueden producir problemas de compilación debido a ciertas propiedades de EnvDTE que no se pueden insertar.

Todos los proyectos de escritorio contienen una referencia implícita a **mscorlib**. Los proyectos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] contienen una referencia implícita a <xref:Microsoft.VisualBasic>. Todos los proyectos contienen una referencia implícita a **System.Core**, aunque se quite de la lista de referencias.

Si un tipo de proyecto no admite ensamblados, la pestaña no aparecerá en el cuadro de diálogo **Administrador de referencias**.

La pestaña **Ensamblados** consta de dos subpestañas:

1. En **Framework** se enumeran todos los ensamblados que conforman la versión de la plataforma de destino.

    Los proyectos de las aplicaciones de la Tienda Windows 8.x contienen referencias a todos los ensamblados de las [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] de destino de forma predeterminada cuando se crea un proyecto. En los proyectos administrados, un nodo de solo lectura bajo la carpeta **Referencias** del **Explorador de soluciones** indica la referencia a todo el marco. Por consiguiente, la pestaña **Marco** no enumera ninguno de los ensamblados del marco y en su lugar muestra el siguiente mensaje: "Ya se hace referencia a todos los ensamblados de .NET Framework. Use el Examinador de objetos para ver las referencias de .NET Framework". Para los proyectos de escritorio, la pestaña **Marco** muestra los ensamblados de la plataforma de destino, y el usuario debe agregar las referencias que requiera la aplicación.

2. En **Extensiones** se muestran todos los ensamblados que los proveedores externos de componentes y controles han desarrollado para ampliar la plataforma de destino. Dependiendo del propósito de la aplicación del usuario, puede que se necesiten estos ensamblados.

   **Extensiones** se rellena con una enumeración de los ensamblados registrados en las ubicaciones siguientes:

   Equipo de 32 bits:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   Equipo de 64 bits:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   Y versiones anteriores de [identificador de plataforma de destino]

   Por ejemplo, si un proyecto tiene como destino .NET Framework 4 en una máquina de 32 bits, **Extensiones** enumerará los ensamblados que están registrados en *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.0\AssemblyFoldersEx* y *\Microsoft\.NETFramework\v2.0\AssemblyFoldersEx*.

Dependiendo de la versión de .NET Framework del proyecto, es posible que algunos componentes de la lista no aparezcan. Esta desincronización puede aparecer bajo las condiciones siguientes:

- Un componente que utiliza una versión reciente de .NET Framework es incompatible con un proyecto que tiene como destino una versión anterior de .NET Framework.

    Para obtener información sobre cómo cambiar la versión de .NET Framework de destino de un proyecto, vea [Cómo: Usar una versión de .NET Framework como destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

- Un componente que utiliza [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] es incompatible con un proyecto que tiene como destino [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].

    Al crear una nueva aplicación, algunos proyectos tienen como destino [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] de forma predeterminada.

No se deben agregar referencias de archivos a resultados de otro proyecto de la misma solución, ya que puede provocar errores de compilación. En lugar de hacerlo, use la pestaña **Proyectos** del cuadro de diálogo **Agregar referencia** para crear referencias entre proyectos. Esto facilita el trabajo en equipo, permitiendo una mejor administración de las bibliotecas de clases creadas en los proyectos. Para más información, vea [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> En Visual Studio 2015 o posterior, se crea una referencia de archivo en lugar de una referencia de proyecto si la versión de destino de .NET Framework de un proyecto es la 4.5 o posterior y la versión de .NET Framework de destino del otro proyecto es la 2, la 3, la 3.5 o la 4.0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Para mostrar un ensamblado en el cuadro de diálogo Agregar referencia

- Desplace o copie el ensamblado en una de las ubicaciones siguientes:

   - Directorio del proyecto actual. (Puede buscar estos ensamblados utilizando la ficha **Examinar** .)

   - Otros directorios del proyecto de la misma solución. (Puede buscar estos ensamblados mediante la pestaña **Proyectos**).

    \- o -

- Establezca una clave del Registro que especifique la ubicación de los ensamblados que se van a mostrar:

   Para un sistema operativo de 32 bits, agregue una de las siguientes claves del Registro.

   - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   Para un sistema operativo de 64 bits, agregue una de las siguientes claves del Registro en un subárbol del Registro de 32 bits.

   - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   *\<VersionMinimum\>* es la versión de .NET Framework más antigua que se aplica. Si *\<VersionMinimum\>* es v3.0, las carpetas especificadas en *AssemblyFoldersEx* se aplican a proyectos cuyo destino es .NET Framework 3.0 y versiones posteriores.

   *\<AssemblyLocation\>* es el directorio de los ensamblados que quiere que aparezcan en el cuadro de diálogo **Agregar referencia**, por ejemplo, *C:\MyAssemblies*.

   La creación de la clave del Registro en el nodo `HKEY_LOCAL_MACHINE` permite que todos los usuarios vean los ensamblados de la ubicación especificada en el cuadro de diálogo **Agregar referencia**. Crear la clave del Registro en el nodo `HKEY_CURRENT_USER` únicamente afecta a la configuración del usuario actual.

   Abra de nuevo el cuadro de diálogo **Agregar referencia**. Los ensamblados deben aparecer en la pestaña **.NET**. Si no es así, asegúrese de que los ensamblados se encuentren en el directorio *AssemblyLocation* especificado, reinicie Visual Studio e inténtelo de nuevo.

## <a name="projects-tab"></a>Pestaña Proyectos

La pestaña **Proyectos** muestra todos los proyectos compatibles de la solución actual, en la subpestaña **Solución**.

Un proyecto puede hacer referencia a otro proyecto con una versión de .NET Framework de destino diferente. Por ejemplo, podría crear un proyecto cuya versión de destino fuera [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] pero que hiciera referencia a un ensamblado compilado para .NET Framework 2. En cambio, el proyecto de .NET Framework 2 no puede hacer referencia a un proyecto de [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]. Para obtener más información, consulte [Información general sobre la compatibilidad con múltiples versiones](../ide/visual-studio-multi-targeting-overview.md).

Un proyecto que tenga como destino [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] es incompatible con un proyecto que tenga como destino [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].

Se crea una referencia de archivo en lugar de una referencia de proyecto si un proyecto tiene como destino .NET Framework 4 y otro proyecto tiene como destino una versión anterior.

Un proyecto cuyo destino sea [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] no puede agregar una referencia de proyecto a un proyecto cuyo destino sea .NET Framework, y viceversa.

## <a name="universal-windows-tab"></a>Pestaña Windows universal

La pestaña **Windows universal** muestra todos los SDK que son específicos de las plataformas en las que se ejecutan sistemas operativos Windows.
Esta pestaña contiene dos subgrupos: **Principal** y **Extensiones**.

### <a name="core-subgroup"></a>Subgrupo Principal

Los proyectos de aplicación Windows universal hacen referencia de forma predeterminada al SDK de Windows universal. Por consiguiente, el subgrupo **Principal** del **Administrador de referencias** no muestra ninguno de los ensamblajes del SDK de Windows universal.

### <a name="extensions-subgroup"></a>Subgrupo Extensiones

El subgrupo **Extensiones** muestra los SDK del usuario que amplían la plataforma Windows de destino.

Un SDK es una colección de archivos que Visual Studio trata como un único componente. En la pestaña **Extensiones**, los SDK que se aplican al proyecto desde el que se ha invocado el cuadro de diálogo **Administrador de referencias** se muestran como entradas individuales. Cuando se agrega a un proyecto, todo el contenido de los SDK lo usa Visual Studio, de modo que el usuario no necesita realizar ninguna acción adicional para usar el contenido de los SDK en IntelliSense, cuadro de herramientas, diseñadores, Explorador de objetos, compilación, implementación, depuración y empaquetado.

Para más información sobre cómo mostrar el SDK en la pestaña **Extensiones**, vea [Creación de un Kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Si un proyecto hace referencia a un SDK que depende de otro SDK, Visual Studio no usará el segundo SDK a menos que se agregue manualmente una referencia al segundo SDK. Cuando un usuario elige un SDK en la pestaña **Extensiones**, el cuadro de diálogo **Administrador de referencias** ayuda a identificar las dependencias del SDK al mostrar todas las dependencias del SDK en el panel de detalles.

Si un tipo de proyecto no admite extensiones, esta pestaña no aparecerá en el cuadro de diálogo **Administrador de referencias**.

## <a name="com-tab"></a>Pestaña COM

La pestaña **COM** muestra todos los componentes COM a los que se puede hacer referencia. Si desea agregar una referencia a una DLL COM registrada que contiene un manifiesto interno, quite primero la DLL del Registro. Si no lo hace, Visual Studio agregará la referencia del ensamblado como un control ActiveX, en lugar de como una DLL nativa.

Si un tipo de proyecto no admite COM, la pestaña no aparecerá en el cuadro de diálogo **Administrador de referencias**.

## <a name="browse-button"></a>Botón Examinar

Puede usar el botón **Examinar** para buscar un componente en el sistema de archivos.

Un proyecto puede hacer referencia a un componente con una versión de .NET Framework de destino diferente. Por ejemplo, podría crear una aplicación que tuviera como destino .NET Framework 4.7 y que hiciera referencia a un componente que tuviera como destino .NET Framework 4. Para obtener más información, consulte [Información general sobre la compatibilidad con múltiples versiones](../ide/visual-studio-multi-targeting-overview.md).

No se deben agregar referencias de archivos a resultados de otro proyecto de la misma solución, ya que se pueden producir errores de compilación. En lugar de ello, use la pestaña **Solución** del cuadro de diálogo **Administrador de referencias** para crear referencias entre proyectos. Esto facilita el desarrollo en equipo, permitiendo una mejor administración de las bibliotecas de clases que se crean en los proyectos. Para más información, vea [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md).

No puede buscar un SDK y agregarlo al proyecto. Solo puede buscar un archivo (por ejemplo, un ensamblado o *.winmd*) y agregarlo al proyecto.

Cuando se hace referencia a un archivo WinMD, el diseño esperado es que los archivos *\<FileName>.winmd*, *\<FileName>.dll* y *\<FileName>.pri* aparezcan colocados unos junto a otros. Si hace referencia a un archivo WinMD en los escenarios siguientes, se copiará un conjunto de archivos incompleto en el directorio de resultados del proyecto y, por tanto, se producirán errores de compilación y en tiempo de ejecución.

- **Componente nativo**: un proyecto nativo creará un archivo WinMD para cada conjunto disjunto de espacios de nombre y un archivo DLL con la implementación. Los archivos WinMD tendrán nombres dispares. Al hacer referencia a este archivo de componente nativo, MSBuild no reconocerá que el archivo WinMD con un nombre dispar crea un componente. Por tanto, solo se copiarán los archivos *\<FileName>.dll*  y *\<FileName>.winmd* con idéntico nombre y se producirán errores en tiempo de ejecución. Para solucionar este problema, cree un SDK de extensión. Para obtener más información, vea [Creación de un Kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md).

- **Uso de controles**: como mínimo, un control XAML está compuesto por un *\<FileName>.winmd*, *\<FileName>.dll*, *\<FileName>.pri*, *\<XamlName>.xaml* y un *\<ImageName>.jpg*. Cuando se compila el proyecto, los archivos de recursos asociados a la referencia de archivo no se copian en el directorio de salida del proyecto y solo se copian *\<FileName>.winmd*, *\<FileName>.dll* y *\<FileName>.pri*. Se registra un error de compilación para informar al usuario de que faltan los recursos *\<XamlName>.xaml* y *\<ImageName>.jpg*. Para permitir un funcionamiento correcto, el usuario tendrá que copiar manualmente estos archivos de recursos en el directorio de salida del proyecto para la compilación y depuración/tiempo de ejecución. Para solucionar este problema, cree un SDK de extensión siguiendo los pasos de [Creación de un Kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md) o edite el archivo de proyecto para agregar la siguiente propiedad:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Si agrega la propiedad, es posible que la compilación se ejecute más lentamente.

## <a name="recent"></a>Reciente

Los grupos **Ensamblados**, **COM**, **Windows** y **Examinar** tienen cada uno una pestaña **Recientes**, que muestra una lista de los componentes que se agregaron recientemente a proyectos.

## <a name="search"></a>Buscar

La barra de búsqueda del cuadro de diálogo **Administrador de referencias** funciona según la pestaña que tiene el foco. Por ejemplo, si el usuario escribe "System" en la barra de búsqueda mientras la pestaña **Solución** tiene el foco, la búsqueda no devuelve ningún resultado a menos que la solución conste de un nombre de proyecto que contenga "System".

## <a name="see-also"></a>Vea también

- [Administración de referencias en un proyecto](../ide/managing-references-in-a-project.md)