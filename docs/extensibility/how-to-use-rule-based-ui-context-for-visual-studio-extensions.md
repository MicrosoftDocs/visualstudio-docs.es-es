---
title: 'Cómo: usar el contexto de la interfaz de usuario basada en reglas para las extensiones de Visual Studio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 4ee29937b11110ee6aae65628b81ea49588fdd22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86972314"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Cómo: usar el contexto de la interfaz de usuario basada en reglas para las extensiones de Visual Studio

Visual Studio permite la carga de VSPackages cuando <xref:Microsoft.VisualStudio.Shell.UIContext> se activan determinados s conocidos. Sin embargo, estos contextos de la interfaz de usuario no son precisos, lo que deja a los autores de la extensión ninguna opción, pero para elegir un contexto de interfaz de usuario disponible que se active antes del punto en el que realmente querían que se cargase el VSPackage. Para obtener una lista de contextos de interfaz de usuario conocidos, vea <xref:Microsoft.VisualStudio.Shell.KnownUIContexts> .

La carga de paquetes puede afectar al rendimiento y cargarlos antes de lo necesario no es el procedimiento recomendado. Visual Studio 2015 presentó el concepto de contextos de interfaz de usuario basados en reglas, un mecanismo que permite a los autores de extensiones definir las condiciones precisas en las que se activa un contexto de la interfaz de usuario y se cargan los VSPackages asociados.

## <a name="rule-based-ui-context"></a>Contexto de la interfaz de usuario basada en reglas

Una "regla" se compone de un nuevo contexto de la interfaz de usuario (un GUID) y una expresión booleana que hace referencia a uno o más "términos" combinados con operaciones lógicas "and", "or", "not". Los "términos" se evalúan dinámicamente en tiempo de ejecución y la expresión se vuelve a evaluar siempre que se cambia cualquiera de sus términos. Cuando la expresión se evalúa como true, se activa el contexto de la interfaz de usuario asociada. De lo contrario, el contexto de la interfaz de usuario se desactivará.

El contexto de la interfaz de usuario basada en reglas se puede usar de varias maneras:

1. Especifique las restricciones de visibilidad para los comandos y las ventanas de herramientas. Puede ocultar los comandos y las ventanas de herramientas hasta que se cumpla la regla de contexto de la interfaz de usuario.

2. Como restricciones de carga automática: cargar paquetes automáticamente solo cuando se cumple la regla.

3. Como tarea retrasada: carga retrasada hasta que se ha pasado un intervalo especificado y se sigue cumpliendo la regla.

   Cualquier extensión de Visual Studio puede usar el mecanismo.

## <a name="create-a-rule-based-ui-context"></a>Crear un contexto de interfaz de usuario basado en reglas
 Supongamos que tiene una extensión denominada TestPackage, que ofrece un comando de menú que solo se aplica a los archivos con la extensión *. config* . Antes de VS2015, la mejor opción era cargar TestPackage cuando <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> se activó el contexto de la interfaz de usuario. La carga de TestPackage de esta manera no es eficaz, ya que la solución cargada no puede incluir incluso un archivo *. config* . Estos pasos muestran cómo se puede usar el contexto de la interfaz de usuario basada en reglas para activar un contexto de la interfaz de usuario solo cuando se selecciona un archivo con la extensión *. config* y cargar TestPackage cuando se activa el contexto de la interfaz de usuario.

1. Defina un nuevo GUID de Solutionopening y agregue a la clase VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> y <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute> .

    Por ejemplo, supongamos que se va a agregar un nuevo Solutionopening "UIContextGuid". El GUID creado (puede crear un GUID haciendo clic en **herramientas**  >  **crear GUID**) es "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". A continuación, agregue la siguiente declaración dentro de la clase de paquete:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    En el caso de los atributos, agregue los siguientes valores: (los detalles de estos atributos se explicarán más adelante)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Estos metadatos definen el nuevo GUID de Solutionopening (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) y una expresión que hace referencia a un único término, "DotConfig". El término "DotConfig" se evalúa como true siempre que la selección actual en la jerarquía activa tiene un nombre que coincide con el patrón de expresión regular " \\ . config $" (termina con *. config*). El valor (predeterminado) define un nombre opcional para la regla útil para la depuración.

    Los valores del atributo se agregan a la archivo pkgdef que se genera durante la compilación después.

2. En el archivo VSCT para los comandos de TestPackage, agregue la marca "DynamicVisibility" a los comandos adecuados:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. En la sección visibilidades de VSCT, enlace los comandos adecuados al nuevo GUID de Solutionopening definido en #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. En la sección de símbolos, agregue la definición de Solutionopening:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Ahora, los comandos del menú contextual para los archivos * \* . config* solo estarán visibles cuando el elemento seleccionado en el explorador de soluciones sea un archivo *. config* y el paquete no se cargará hasta que se seleccione uno de estos comandos.

   A continuación, use un depurador para confirmar que el paquete solo se carga cuando lo espera. Para depurar TestPackage:

5. Establezca un punto de interrupción en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.

6. Compile TestPackage e inicie la depuración.

7. Cree un proyecto o abra uno.

8. Seleccione cualquier archivo con una extensión distinta de *. config*. No se debe alcanzar el punto de interrupción.

9. Seleccione el archivo de *App.Config* .

   TestPackage se carga y se detiene en el punto de interrupción.

## <a name="add-more-rules-for-ui-context"></a>Agregar más reglas para el contexto de la interfaz de usuario
 Dado que las reglas de contexto de la interfaz de usuario son expresiones booleanas, puede agregar reglas más restringidas para un contexto de la interfaz de usuario. Por ejemplo, en el contexto de la interfaz de usuario anterior, puede especificar que la regla se aplique solo cuando se cargue una solución con un proyecto. De esta manera, los comandos no se mostrarán si abre un archivo *. config* como un archivo independiente, no como parte de un proyecto.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT.SolutionHasSingleProject_string , VSConstants.UICONTEXT.SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Ahora la expresión hace referencia a tres términos. Los dos primeros términos, "SingleProject" y "MultipleProjects", hacen referencia a otros contextos conocidos de la interfaz de usuario (por sus GUID). El tercer término, "DotConfig", es el contexto de la interfaz de usuario basado en reglas que se definió anteriormente en este artículo.

## <a name="delayed-activation"></a>Activación diferida
 Las reglas pueden tener un "retraso" opcional. El retraso se especifica en milisegundos. Si está presente, el retraso hace que la activación o desactivación del contexto de la interfaz de usuario de una regla se retrase en ese intervalo de tiempo. Si la regla vuelve a cambiar antes del intervalo de retraso, no sucede nada. Este mecanismo se puede usar para "escalonar" pasos de inicialización, especialmente la inicialización de un solo uso sin depender de temporizadores o registros de notificaciones inactivas.

 Por ejemplo, puede especificar que la regla de carga de prueba tenga un retraso de 100 milisegundos:

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Tipos de términos

Estos son los distintos tipos de términos que se admiten:

|Término|Descripción|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|El GUID hace referencia a un contexto de la interfaz de usuario. El término será true siempre que el contexto de la interfaz de usuario esté activo y false en caso contrario.|
|HierSingleSelectionName:\<pattern>|El término será true siempre que la selección en la jerarquía activa sea un elemento único y el nombre del elemento seleccionado coincida con la expresión regular de .net proporcionada por "pattern".|
|UserSettingsStoreQuery:\<query>|"consulta" representa una ruta de acceso completa en el almacén de configuración de usuario, que debe evaluarse como un valor distinto de cero. La consulta se divide en una "colección" y "propertyName" en la última barra diagonal.|
|ConfigSettingsStoreQuery:\<query>|"Query" representa una ruta de acceso completa en el almacén de valores de configuración, que debe evaluarse como un valor distinto de cero. La consulta se divide en una "colección" y "propertyName" en la última barra diagonal.|
|ActiveProjectFlavor:\<projectTypeGuid>|El término será true siempre que el proyecto seleccionado esté determinado (agregado) y tenga un tipo que coincida con el GUID de tipo de proyecto especificado.|
|ActiveEditorContentType:\<contentType>|El término será true cuando el documento seleccionado sea un editor de texto con el tipo de contenido especificado. Nota: cuando se cambia el nombre del documento seleccionado, este término no se actualiza hasta que se cierra y se vuelve a abrir el archivo.|
|ActiveProjectCapability:\<Expression>|El término es verdadero cuando las capacidades del proyecto activo coinciden con la expresión proporcionada. Una expresión puede ser similar a VB &#124; CSharp.|
|SolutionHasProjectCapability:\<Expression>|Similar a la anterior, pero el término es true cuando la solución tiene cualquier proyecto cargado que coincida con la expresión.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|El término será true siempre que una solución tenga un proyecto que se pueda asignar (agregar) y tenga un tipo que coincida con el GUID de tipo de proyecto especificado.|
|ProjectAddedItem:\<pattern>| El término es true cuando un archivo que coincide con el "patrón" se agrega a un proyecto en el soluion que se abre.|
|ActiveProjectOutputType:\<outputType>|El término es true cuando el tipo de salida del proyecto activo coincide exactamente.  OutputType podría ser un entero o un <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> tipo.|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|El término es verdadero cuando el proyecto activo tiene la propiedad de compilación especificada y el valor de propiedad coincide con el filtro regex proporcionado. Consulte [persistencia de datos en archivos de proyecto de MSBuild](internals/persisting-data-in-the-msbuild-project-file.md) para obtener más información sobre las propiedades de compilación.|
|SolutionHasProjectBuildProperty:\<buildProperty>=\<regex>|El término es verdadero cuando la solución tiene un proyecto cargado con la propiedad de compilación especificada y el valor de propiedad coincide con el filtro regex proporcionado.|

## <a name="compatibility-with-cross-version-extension"></a>Compatibilidad con la extensión entre versiones

Los contextos de la interfaz de usuario basados en reglas son una característica nueva de Visual Studio 2015 y no se trasladan a versiones anteriores. No migrar a versiones anteriores crea un problema con extensiones o paquetes destinados a varias versiones de Visual Studio. Estas versiones tendrían que cargarse automáticamente en Visual Studio 2013 y versiones anteriores, pero pueden beneficiarse de los contextos de la interfaz de usuario basados en reglas para evitar que se carguen automáticamente en Visual Studio 2015.

Para admitir estos paquetes, las entradas de AutoLoadPackages en el registro ahora pueden proporcionar una marca en su campo de valor para indicar que la entrada debe omitirse en Visual Studio 2015 y versiones posteriores. Esto puede hacerse agregando una opción Flags a <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> . Ahora, los VSPackages pueden agregar la opción **SkipWhenUIContextRulesActive** a su <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo para indicar que la entrada debe omitirse en Visual Studio 2015 y versiones posteriores.
## <a name="extensible-ui-context-rules"></a>Reglas de contexto de IU extensible

A veces, los paquetes no pueden usar reglas de contexto de interfaz de usuario estática. Por ejemplo, supongamos que tiene un paquete que admite la extensibilidad de modo que el estado del comando se basa en los tipos de editor que son compatibles con los proveedores MEF importados. El comando se habilita si hay una extensión que admite el tipo de edición actual. En tales casos, el propio paquete no puede usar una regla de contexto de la interfaz de usuario estática, ya que los términos cambiarán en función de las extensiones de MEF que estén disponibles.

Para admitir estos paquetes, los contextos de la interfaz de usuario basados en reglas admiten una expresión codificada "*" que indica que todos los términos siguientes se combinarán con o. Esto permite al paquete maestro definir un contexto de interfaz de usuario basado en reglas conocido y asociar su estado de comando a este contexto. Después, cualquier extensión de MEF destinada al paquete maestro puede agregar sus términos para los editores que admite sin afectar a otros términos o a la expresión maestra.

La documentación del constructor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> muestra la sintaxis de las reglas de contexto de la interfaz de usuario extensible.
