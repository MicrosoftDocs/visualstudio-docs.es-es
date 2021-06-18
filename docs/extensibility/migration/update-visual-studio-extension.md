---
title: Actualización de una Visual Studio extensión
description: Aprenda a actualizar la extensión Visual Studio para que funcione con Visual Studio 2022.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 514c9654a741e4e1e565f0cb2becdbe3157fab0c
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308628"
---
# <a name="update-a-visual-studio-extension-for-visual-studio-2022"></a>Actualización de Visual Studio extensión para Visual Studio 2022

Puede actualizar la extensión para que funcione con Visual Studio versión preliminar de 2022 siguiendo esta guía. Visual Studio versión preliminar de 2022 es una aplicación de 64 bits y presenta algunos cambios importantes en el SDK de VS. Esta guía le guía por los pasos necesarios para que la extensión funcione con la versión preliminar actual de Visual Studio 2022, de modo que la extensión pueda estar lista para que los usuarios puedan instalarla antes de que Visual Studio 2022 llegue a la versión general.

## <a name="installing"></a>Instalación

Instale Visual Studio versión preliminar de 2022 desde Visual Studio de descarga de la versión [preliminar de 2022.](https://visualstudio.microsoft.com/vs/preview/vs2022)

### <a name="extensions-written-in-a-net-language"></a>Extensiones escritas en un lenguaje .NET

El SDK de VS Visual Studio 2022 para extensiones administradas se ha configurado *exclusivamente* en NuGet:

- El meta-paquete [Microsoft.VisualStudio.Sdk](https://www.nuget.org/packages/Microsoft.VisualStudio.Sdk/) (versiones 17.x) incluye la mayoría o todos los ensamblados de referencia que necesitará.
- Se debe hacer referencia al paquete [Microsoft.VSSDK.BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) (versiones 17.x) desde el proyecto VSIX para que pueda compilar un VSIX compatible con Visual Studio 2022.

Las extensiones *deben* compilarse con la plataforma "Any CPU" o "x64". La plataforma "x86" no es compatible Visual Studio proceso de 64 bits de 2022.

### <a name="extensions-written-in-c"></a>Extensiones escritas en C++

El SDK de VS para las extensiones compiladas con C++ está disponible con el SDK Visual Studio instalado, como de costumbre.

Las extensiones *deben* compilarse específicamente en el SDK Visual Studio 2022 y para amd64.

### <a name="update-your-extension-to-visual-studio-2022"></a>Actualización de la extensión a Visual Studio 2022

#### <a name="extensions-with-running-code"></a>Extensiones con código en ejecución

Las extensiones con código *en ejecución* deben compilarse específicamente para Visual Studio 2022. Visual Studio 2022 no cargará ninguna extensión que no se Visual Studio 2022 específicamente.

Obtenga información sobre cómo migrar las extensiones Visual Studio 2022 a Visual Studio 2022:

1. [Modernice los proyectos.](#modernize-your-vsix-project)
1. [Refactorice el código fuente en un proyecto](#use-shared-projects-for-multi-targeting) compartido para permitir el destino Visual Studio 2022 y versiones anteriores.
1. [Agregue un Visual Studio VSIX de destino 2022](#add-a-visual-studio-2022-target)y la tabla de [remapping del paquete o ensamblado](migrated-assemblies.md).
1. [Realizar los ajustes de código necesarios.](#handle-breaking-api-changes)
1. [Probar la extensión Visual Studio 2022](#test-your-extension).
1. [Publicar la extensión Visual Studio 2022](#publish-your-extension).

#### <a name="extensions-without-running-code"></a>Extensiones sin ejecutar código

Las extensiones que no contienen ningún código en ejecución (por ejemplo, plantillas de proyecto o elemento) no son necesarias para seguir los pasos anteriores, incluida la producción de dos VSX distintos. 

En su lugar, se debe modificar el VSIX para que su `source.extension.vsixmanifest` archivo declare dos destinos de instalación, como este:

```xml
<Installation>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0,17.0)">
      <ProductArchitecture>x86</ProductArchitecture>
   </InstallationTarget>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
</Installation>
```

Puede omitir los pasos de este artículo sobre el uso de proyectos compartidos y varios VSX. Puede continuar con las [pruebas](#test-your-extension).

> [!NOTE]
> Si va a crear una nueva extensión *de* Visual Studio mediante la versión preliminar de Visual Studio 2022 y quiere (también) tener como destino Visual Studio 2019 o una versión anterior, consulte esta [guía](target-previous-versions.md).

### <a name="msbuild-tasks"></a>tareas de MSBuild

Si va a crear tareas de MSBuild, tenga en cuenta que en Visual Studio 2022 es mucho más probable que se carguen en un proceso de MSBuild.exe de 64 bits. Si la tarea requiere que se ejecute un proceso de 32 bits, consulte esta documentación de [MSBuild](../../msbuild/how-to-configure-targets-and-tasks.md#usingtask-attributes-and-task-parameters) para asegurarse de que MSBuild sabe cargar la tarea en un proceso de 32 bits.

## <a name="modernize-your-vsix-project"></a>Modernización del proyecto VSIX

Antes de agregar compatibilidad Visual Studio 2022 a la extensión, se recomienda encarecidamente aprovechar este tiempo para limpiar y modernizar el proyecto existente antes de ir más allá, lo que incluye:

1. [Migre packages.config `PackageReference` a ](/nuget/consume-packages/migrate-packages-config-to-package-reference).

1. Reemplace cualquier referencia de ensamblado directo de VS SDK por elementos PackageReference.

   ```diff
   -<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   +<PackageReference Include="Microsoft.VisualStudio.OLE.Interop" Version="..." />
   ```

   > [!TIP]
   > Puede reemplazar muchas *referencias* de ensamblado por un *solo* PackageReference en nuestro metapaquete:
   >
   >```diff
   >-<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop.8.0" />
   >+<PackageReference Include="Microsoft.VisualStudio.Sdk" >Version="..." />
   >```

   Asegúrese de elegir las versiones de paquete que coincidan con la versión mínima de Visual Studio de destino.

   Es posible que algunos ensamblados que no son únicos del SDK de VS (por ejemplo, Newtonsoft.Json.dll) se hayan podido detectar mediante una referencia simple antes de Visual Studio 2022, pero en Visual Studio 2022 requiere una referencia de paquete en su lugar porque en Visual Studio 2022, quitamos algunos directorios de entorno de ejecución y SDK de Visual Studio de la ruta de búsqueda de ensamblados predeterminada de `<Reference Include="Newtonsoft.Json" />` MSBuild.

   Al cambiar de referencias de ensamblado directas a referencias de paquetes NuGet, puede elegir referencias de ensamblado adicionales y paquetes del analizador debido a que NuGet instala automáticamente el cierre transitivo de dependencias. Esto suele ser correcto, pero puede dar lugar a advertencias adicionales que se marcan durante la compilación. Solucione estas advertencias y resuelva tantas como pueda, y considere la posibilidad de suprimir esas advertencias que no puede resolver mediante `#pragma warning disable <id>` regiones en código.

## <a name="use-shared-projects-for-multi-targeting"></a>Uso de proyectos compartidos para la compatibilidad con múltiples destinos

[Los proyectos](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) compartidos son un tipo de proyecto que se introdujo en Visual Studio 2015. Los proyectos compartidos Visual Studio permitir que los archivos de código fuente se compartan entre varios proyectos y se compilen de forma diferente mediante símbolos de compilación condicional y conjuntos únicos de referencias.

Dado que Visual Studio 2022 requiere un conjunto distinto de ensamblados de referencia de todas las versiones anteriores de VS, nuestra guía es usar proyectos compartidos para tener una extensión adecuadamente de varios destinos a versiones anteriores a Visual Studio 2022 y Visual Studio 2022 (y versiones posteriores), lo que proporciona uso compartido de código, pero referencias distintas.

En el contexto de Visual Studio, podría tener un proyecto VSIX para Visual Studio 2022 y versiones posteriores y un proyecto VSIX para Visual Studio 2019 y versiones anteriores. Cada uno de estos proyectos contendrá solo un y las referencias de paquete al `source.extension.vsixmanifest` SDK 16.x o al SDK 17.x. Estos proyectos VSIX también tendrían una referencia de proyecto compartido a un nuevo proyecto compartido que hospedará todo el código fuente que se puede compartir entre las dos versiones de VS.

Como punto de partida, para este documento se supone que ya tiene un proyecto VSIX que tiene como destino Visual Studio 2019 y que quiere que la extensión funcione en Visual Studio 2022.

Todos estos pasos se pueden completar con Visual Studio 2019.

1. Si aún no lo ha hecho, [modernice](#modernize-your-vsix-project) los proyectos para facilitar los pasos más adelante en este proceso de actualización.

1. Agregue un nuevo proyecto compartido a la solución para cada proyecto existente que haga referencia al SDK de VS.
   ![Agregar nuevo proyecto comando Nueva ](media/update-visual-studio-extension/add-new-project.png)
    ![ plantilla de proyecto](media/update-visual-studio-extension/new-shared-project-template.png)

1. Agregue una referencia de cada proyecto de referencia de VS SDK a su homólogo de proyecto compartido.
   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Agregar referencia de proyecto compartido" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Mueva todo el código fuente (incluidos .cs, .resx) de cada proyecto de referencia de VS SDK a su homólogo de proyecto compartido.
Deje el `source.extension.vsixmanifest` archivo en el proyecto VSIX.
   ![El proyecto compartido contiene todos los archivos de código fuente](media/update-visual-studio-extension/source-files-in-shared-project.png)

1. Los archivos de metadatos (notas de la versión, licencia, iconos, entre otros) y los archivos VSCT deben moverse a un directorio compartido y agregarse como archivos vinculados al proyecto VSIX.
   ![Agregar metadatos y archivos VSCT como archivos vinculados](media/update-visual-studio-extension/add-linked-items-to-vsix.png)
    - Para los archivos de metadatos, establezca BuildAction en `Content` y establezca Incluir en VSIX en `true` .

      ![Incluir archivos de metadatos en VSIX](./media/update-visual-studio-extension/include-metadata-files-in-vsix.png)
    - En el caso de los archivos VSCT, establezca BuildAction en `VSCTCompile` y no incluya en VSIX.
      Visual Studio que se quejan de que esta configuración no se admite, pero puede cambiar manualmente la acción de compilación descargando el proyecto y cambiando `Content` a `VSCTCompile`

    ```diff
    -<Content Include="..\SharedFiles\VSIXProject1Package.vsct">
    -  <Link>VSIXProject1Package.vsct</Link>
    -</Content>
    +<VSCTCompile Include="..\SharedFiles\VSIXProject1Package.vsct">
    +  <Link>VSIXProject1Package.vsct</Link>
    +  <ResourceName>Menus.ctmenu</ResourceName>
    +</VSCTCompile>
    ```

      ![Establecer archivos VSCT como VSCTCompile](media/update-visual-studio-extension/build-linked-vsct-files.png)

1. Compile los proyectos para confirmar que no ha introducido ningún error nuevo.

El proyecto ya está listo para agregar compatibilidad Visual Studio 2022.

## <a name="add-a-visual-studio-2022-target"></a>Agregar un destino Visual Studio 2022

En este documento se da por supuesto que ha completado los pasos para factorización de la [Visual Studio con proyectos compartidos.](#use-shared-projects-for-multi-targeting)

Continúe para agregar Visual Studio compatibilidad con 2022 a la extensión con estos pasos, que se pueden completar mediante Visual Studio 2019:

1. Agregue un nuevo proyecto VSIX a la solución. Este será el proyecto que tiene como destino Visual Studio 2022. Quite cualquier código fuente que se produjese con la plantilla, pero *mantenga el `source.extension.vsixmanifest` archivo*.

1. En el nuevo proyecto VSIX, agregue una referencia de proyecto compartido al mismo proyecto compartido al que hace referencia Visual Studio VSIX de destino de 2019.

   ![Una solución con un proyecto compartido y dos proyectos VSIX](media/update-visual-studio-extension/shared-project-with-two-heads.png)

1. Compruebe que el nuevo proyecto VSIX se compila correctamente. Es posible que tenga que agregar referencias para que coincidan con el proyecto VSIX original para resolver los errores del compilador.

1. En el caso de las extensiones de VS administradas, actualice las referencias de paquete de la versión 16.x (o anterior) a las versiones del paquete 17.x del archivo de proyecto de destino de Visual Studio 2022 mediante el Administrador de paquetes de NuGet o editando directamente el archivo de proyecto:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    ```

   Usará versiones que están disponibles realmente en nuget.org. Los usados anteriormente son solo con fines de demostración.

   En muchos casos, los IDs de paquete han cambiado. Consulte la tabla [de asignación de paquetes](migrated-assemblies.md) o ensamblados para obtener una lista de los cambios Visual Studio 2022.

   Las extensiones escritas en C++ aún no tienen un SDK disponible con el que compilar.

1. Para los proyectos de C++, deben compilarse para amd64. En el caso de las extensiones administradas, considere la posibilidad de cambiar el proyecto de compilar para cualquier CPU a tener como destino , para reflejar que en Visual Studio 2022 la extensión siempre se carga en un proceso de `x64` 64 bits. `Any CPU` también está bien, pero puede generar advertencias si hace referencia a archivos binarios nativos solo x64.

   Cualquier dependencia que pueda tener la extensión en un módulo nativo tendrá que actualizarse de una imagen x86 a una imagen amd64.

1. Edite `source.extension.vsixmanifest` el archivo para reflejar el destino Visual Studio 2022. Establezca la `<InstallationTarget>` etiqueta para que refleje Visual Studio 2022 e indique una carga de amd64:

   ```xml
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
   ```

   En Visual Studio 2019, el diseñador de este archivo no expone el nuevo elemento, por lo que este cambio tendrá que realizarse con un editor xml, al que puede acceder a través del comando Abrir con `ProductArchitecture` **en Explorador de soluciones**. 

   Este `ProductArchitecture` elemento es crítico. Visual Studio 2022 no *instalará* la extensión sin ella.

   | Elemento | Value | Descripción |
   | - | - | - |
   | ProductArchitecture | X86, AMD64 | Las plataformas compatibles con este VSIX. No distingue mayúsculas de minúsculas. Una plataforma por elemento y un elemento por InstallTarget. Para las versiones de producto inferiores a 17.0, el valor predeterminado es x86 y se puede omitir.  Para las versiones de producto 17.0 y posteriores, este elemento es necesario y no hay ningún valor predeterminado. Para Visual Studio 2022, el único contenido válido para este elemento es "amd64". |

1. Realice cualquier otro ajuste necesario en source.extension.vsixmanifest para que coincida con el que tiene como destino Visual Studio 2019 (si lo hubiera). Es fundamental que el identificador de VSIX, en el elemento `Identity` del manifiesto, sea idéntico para ambas extensiones.

En este momento, tiene una extensión Visual Studio VSIX de destino de 2022. Debe compilar el proyecto VSIX Visual Studio de destino de 2022 y trabajar con los saltos de [compilación que aparezcan.](#handle-breaking-api-changes) Si no tiene interrupciones de compilación en el proyecto VSIX de Visual Studio de destino 2022, enhorabuena: ya está listo para las pruebas.

## <a name="handle-breaking-api-changes"></a>Control de cambios importantes en la API

Hay cambios [importantes en la API](breaking-api-list.md) Visual Studio 2022 que pueden requerir cambios en el código desde que se ejecutó en versiones anteriores. Revise ese documento para obtener sugerencias sobre cómo actualizar el código para cada uno de ellos.

Al adaptar el código, se [](#use-conditional-compilation-symbols) recomienda usar la compilación condicional para que el código pueda seguir siendo compatible con la versión anterior a la Visual Studio 2022, al tiempo que se agrega compatibilidad con Visual Studio 2022.

Cuando obtenga la extensión de Visual Studio de destino de 2022, continúe [con](#test-your-extension)la prueba de .

## <a name="use-conditional-compilation-symbols"></a>Uso de símbolos de compilación condicional

Si desea usar el mismo código fuente, incluso el mismo archivo, para Visual Studio 2022 y versiones anteriores, es posible que tenga que usar la compilación condicional para poder bifurcar el código para adaptarlo a los cambios importantes. La compilación condicional es una característica de los lenguajes C#, Visual Basic y C++ que se puede usar para compartir la mayoría del código a la vez que se mantienen las API divergentes en lugares específicos.

Puede encontrar más información sobre el uso de directivas de preprocesador y símbolos de compilación condicional en la documentación de Microsoft [#if directiva de preprocesador](/dotnet/csharp/language-reference/preprocessor-directives#conditional-compilation).

Los proyectos que tienen como destino versiones anteriores Visual Studio necesitarán un símbolo de compilación condicional que se pueda usar para bifurcar el código y usar las distintas API. Puede establecer el símbolo de compilación condicional en la página de propiedades del proyecto, como se muestra en la siguiente imagen:

![Establecimiento de símbolos de compilación condicional](media/update-visual-studio-extension/conditional-compilation-symbols.png)

Asegúrese de establecer el símbolo de compilación para todas *las* configuraciones, ya que, de forma predeterminada, el símbolo que escriba solo se puede aplicar a una configuración.

### <a name="c-techniques"></a>Técnicas de C \#

A continuación, puede usar ese símbolo como una directiva de preprocesador ( `#if` ) como se muestra en el código siguiente. A continuación, puede bifurcar el código para tratar con el cambio importante entre las distintas Visual Studio versiones.

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
#if Visual Studio 2019
    shell.LoadUILibrary(myGuid, myFlags, out uint ptrLib);
#else
    shell.LoadUILibrary(myGuid, myFlags, out IntPtr ptrLib);
#endif
```

En algunos casos, puede usar simplemente para evitar asignar un nombre al tipo, lo que evita la `var` necesidad `#if` de regiones. El fragmento de código anterior también se puede escribir como:

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
    shell.LoadUILibrary(myGuid, myFlags, out var ptrLib);
```

Al usar la sintaxis, observe cómo puede usar la lista desplegable de contexto del servicio de lenguaje del documento que se muestra a continuación para cambiar el resaltado de sintaxis y la otra ayuda que ofrece el servicio de lenguaje para centrar la atención en una versión de Visual Studio de destino para nuestra extensión frente `#if` a otra.

![Compilación condicional en un proyecto compartido](media/update-visual-studio-extension/conditional-compilation-if-region.png)

### <a name="xaml-sharing-techniques"></a>Técnicas de uso compartido de XAML

XAML no tiene ningún preprocesador para permitir la personalización de contenido basado en símbolos de preprocesador. Es posible que sea necesario copiar y mantener dos páginas XAML en las que su contenido debe diferir Visual Studio 2022 y versiones anteriores.

Sin embargo, en algunos casos, una referencia a un tipo que existe en ensamblados distintos en Visual Studio 2022 y versiones anteriores podría seguir siendo representable en un archivo XAML quitando el espacio de nombres que hace referencia al ensamblado:

```diff
-xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
-Value="{DynamicResource {x:Static vsui:TreeViewColors.SelectedItemActiveBrushKey}}"
+Value="{DynamicResource TreeViewColors.SelectedItemActiveBrushKey}"
```

## <a name="test-your-extension"></a>Prueba de la extensión

Para probar una extensión que tenga como destino Visual Studio 2022, deberá tener Visual Studio versión preliminar de 2022 instalada.
No podrá ejecutar extensiones de 64 bits en versiones de Visual Studio anteriores a Visual Studio versión preliminar de 2022.

Puede usar Visual Studio versión preliminar de 2022 para compilar y probar las extensiones tanto si tienen como destino Visual Studio 2022 o una versión anterior. Al iniciar un proyecto VSIX desde Visual Studio 2022, se inicia una instancia experimental de Visual Studio proyecto.

Se recomienda encarecidamente probar con cada versión de Visual Studio que se va a admitir la extensión.

Ahora está listo para publicar [la extensión](#publish-your-extension).

## <a name="publish-your-extension"></a>Publicación de la extensión

Excelente, por lo que ha agregado un destino Visual Studio 2022 a la extensión y lo ha probado. Ahora está listo para publicar la extensión para que el mundo se conste.

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

La publicación de la extensión [en Visual Studio Marketplace](https://marketplace.visualstudio.com/) es una excelente manera de conseguir que los nuevos usuarios busquen e instalen la extensión. Tanto si la extensión tiene como destino Visual Studio 2022 exclusivamente o también tiene como destino versiones anteriores de VS, Marketplace le ofrece soporte técnico.

En el futuro, Marketplace le permitirá cargar varios VSIX en una sola lista de Marketplace, lo que le permitirá cargar su VSIX de destino de Visual Studio 2022 y un VSIX anterior a Visual Studio 2022. Los usuarios obtienen automáticamente el VSIX adecuado para la versión de VS que han instalado, al usar el administrador de extensiones de VS.

Para las versiones preliminares de Visual Studio 2022, Marketplace solo admitirá un único archivo VSIX por anuncio de Marketplace. Aunque Visual Studio 2022 está en versión preliminar, le recomendamos que tenga una lista independiente Visual Studio 2022 solo de Marketplace para la extensión. De este modo, puede iterar la extensión Visual Studio 2022 según sea necesario sin afectar a los clientes en versiones anteriores de Visual Studio. También puede marcar la extensión como "versión preliminar" para establecer la expectativa de que probablemente sea menos confiable, incluso si el origen de esa falta de responsabilidad es Visual Studio 2022, que la extensión estándar.

### <a name="custom-installer"></a>Instalador personalizado

Si compila una msi/EXE para instalar la extensión y generar vsixinstaller.exe para instalar (parte de) la extensión, sepa que se ha actualizado el instalador VSIX de Visual Studio 2022. Los desarrolladores tendrán que usar la versión del instalador de VSIX que se incluye con Visual Studio 2022 para instalar extensiones en Visual Studio 2022. El instalador VSIX de Visual Studio 2022 también instalará las extensiones aplicables destinadas a versiones anteriores de Visual Studio que se instalan en paralelo con Visual Studio 2022 en la misma máquina.

### <a name="network-share"></a>Recurso compartido de red

Puede compartir la extensión a través de una LAN o de cualquier otra manera. Si tiene como destino Visual Studio 2022 y versiones anteriores a Visual Studio 2022, deberá compartir varios VSIX individualmente y darles nombres de archivo (o colocarlos en carpetas únicas) que ayuden a los usuarios a saber qué VSIX instalar en función de la versión de Visual Studio que han instalado.

### <a name="other-considerations"></a>Otras consideraciones

#### <a name="dependencies"></a>Dependencias

Si el VSIX especifica otro VSIX como dependencia a través del elemento , cada VSIX al que se hace referencia debe instalarse en los mismos destinos y arquitecturas de producto `<dependency>` que el VSIX. Si un VSIX dependiente no admite la instalación de destino de Visual Studio, se producirá un error en vsIX. Es correcto que el VSIX dependiente admita más destinos y arquitecturas que los que tiene, pero no menos. Esta restricción significa que el enfoque de implementación y distribución de un VSIX con dependencias debe reflejar el de sus dependientes.

## <a name="q--a"></a>Q & A

**P:** Mi extensión no requiere ningún cambio de interoperabilidad, ya que solo proporciona datos (por ejemplo, plantillas), ¿puedo crear una sola extensión que incluya también Visual Studio 2022?

**R.** : Sí.  Consulte [Extensiones sin ejecutar código para](#extensions-without-running-code) obtener más información al respecto.

**P:** Una dependencia de NuGet aporta ensamblados de interoperabilidad antiguos y provoca clases en conflicto.

**A**: agregue la siguiente línea al archivo .csproj para evitar ensamblados duplicados:

```xml
    <PackageReference Include="<Name of offending assembly>" ExcludeAssets="compile" PrivateAssets="all" />
```

Esto impedirá que las referencias de paquete importen la versión anterior del ensamblado desde otras dependencias.

**P:** Mis comandos y teclas de acceso rápido no funcionan en Visual Studio después de cambiar mis archivos de origen a un proyecto compartido.

**Un**: [Paso 2.4](samples.md#step-2---refactor-source-code-into-a-shared-project) del ejemplo optimizador de imágenes muestra cómo agregar archivos VSCT como elementos vinculados para que se compilen en el archivo VSCT.

## <a name="next-steps"></a>Pasos siguientes

Siga un ejemplo paso a paso, [ImageOptimizer,](samples.md)con vínculos al proyecto y los cambios de código para cada paso.
