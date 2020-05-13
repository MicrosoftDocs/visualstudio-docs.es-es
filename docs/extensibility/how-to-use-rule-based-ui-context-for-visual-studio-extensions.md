---
title: 'Cómo: Usar el contexto de interfaz de usuario basado en reglas para las extensiones de Visual Studio . Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: de1a1e0a2022482433f81b0b2810b0d201ab7b8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710596"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Cómo: Usar el contexto de interfaz de usuario basado en reglas para las extensiones de Visual Studio

Visual Studio permite cargar VSPackages cuando <xref:Microsoft.VisualStudio.Shell.UIContext>se activan ciertas s conocidas. Sin embargo, estos contextos de interfaz de usuario no son de grano fino, lo que deja a los autores de la extensión no hay más opción que elegir un contexto de interfaz de usuario disponible que se activa antes del punto que realmente quería que el VSPackage cargar. Para obtener una lista de contextos <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>de interfaz de usuario conocidos, vea .

La carga de paquetes puede tener un impacto en el rendimiento y cargarlos antes de lo necesario no es la mejor práctica. Visual Studio 2015 introdujo el concepto de contextos de interfaz de usuario basados en reglas, un mecanismo que permite a los autores de extensiones definir las condiciones precisas en las que se activa un contexto de interfaz de usuario y se cargan los VSPackages asociados.

## <a name="rule-based-ui-context"></a>Contexto de interfaz de usuario basado en reglas

Una "Regla" consta de un nuevo contexto de interfaz de usuario (un GUID) y una expresión booleana que hace referencia a uno o más "Términos" combinados con operaciones lógicas "y", "o", "no". Los "Términos" se evalúan dinámicamente en tiempo de ejecución y la expresión se vuelve a evaluar cada vez que cambia cualquiera de sus términos. Cuando la expresión se evalúa como true, se activa el contexto de interfaz de usuario asociado. De lo contrario, el contexto de la interfaz de usuario se desactiva.

El contexto de interfaz de usuario basado en reglas se puede usar de varias maneras:

1. Especifique restricciones de visibilidad para comandos y ventanas de herramientas. Puede ocultar las ventanas de comandos/herramientas hasta que se cumpla la regla de contexto de interfaz de usuario.

2. Como restricciones de carga automática: paquetes de carga automática solo cuando se cumple la regla.

3. Como tarea retrasada: retrasar la carga hasta que haya pasado un intervalo especificado y se siga cumpliendo la regla.

   El mecanismo puede ser utilizado por cualquier extensión de Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Crear un contexto de interfaz de usuario basado en reglas
 Supongamos que tiene una extensión denominada TestPackage, que ofrece un comando de menú que solo se aplica a los archivos con extensión *.config.* Antes de VS2015, la mejor opción <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> era cargar TestPackage cuando se activó el contexto de interfaz de usuario. Cargar TestPackage de esta manera no es eficaz, ya que la solución cargada ni siquiera puede contener un archivo *.config.* Estos pasos muestran cómo se puede usar el contexto de interfaz de usuario basado en reglas para activar un contexto de interfaz de usuario solo cuando se selecciona un archivo con extensión *.config* y cargar TestPackage cuando se activa ese contexto de interfaz de usuario.

1. Defina un nuevo GUID UIContext y <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> agréguelo a la clase VSPackage y <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.

    Por ejemplo, supongamos que se va a agregar un nuevo UIContext "UIContextGuid". El GUID creado (puede crear un GUID haciendo clic en **Herramientas** > crear**GUID**) es "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". A continuación, agregue la siguiente declaración dentro de la clase de paquete:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Para los atributos, agregue los siguientes valores: (Los detalles de estos atributos se explicarán más adelante)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Estos metadatos definen el nuevo GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) y una expresión que hace referencia a un único término, "DotConfig". El término "DotConfig" se evalúa como true cada vez que la selección actual\\en la jerarquía activa tiene un nombre que coincide con el patrón de expresión regular " .config$" (termina con *.config*). El valor (Predeterminado) define un nombre opcional para la regla útil para la depuración.

    Los valores del atributo se agregan a pkgdef generado durante el tiempo de compilación después.

2. En el archivo VSCT para los comandos de TestPackage, agregue el indicador "DynamicVisibility" a los comandos adecuados:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. En la sección Visibilities del VSCT, vincule los comandos adecuados al nuevo GUID de UIContext definido en #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. En la sección Símbolos, agregue la definición de UIContext:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Ahora, los comandos * \** de menú contextual para los archivos .config solo estarán visibles cuando el elemento seleccionado en el explorador de soluciones sea un archivo *.config* y el paquete no se cargará hasta que se seleccione uno de esos comandos.

   A continuación, use un depurador para confirmar que el paquete se carga solo cuando lo espera. Para depurar TestPackage:

5. Establezca un punto <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> de interrupción en el método.

6. Compile TestPackage e inicie la depuración.

7. Cree un proyecto o abra uno.

8. Seleccione cualquier archivo con una extensión que no sea *.config*. El punto de interrupción no debe ser alcanzado.

9. Seleccione el archivo *App.Config.*

   El TestPackage carga y se detiene en el punto de interrupción.

## <a name="add-more-rules-for-ui-context"></a>Agregar más reglas para el contexto de la interfaz de usuario
 Dado que las reglas de contexto de interfaz de usuario son expresiones booleanas, puede agregar reglas más restringidas para un contexto de interfaz de usuario. Por ejemplo, en el contexto de interfaz de usuario anterior, puede especificar que la regla solo se aplica cuando se carga una solución con un proyecto. De esta manera, los comandos no aparecerán si abre un archivo *.config* como un archivo independiente, no como parte de un proyecto.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Ahora la expresión hace referencia a tres términos. Los dos primeros términos, "SingleProject" y "MultipleProjects", hacen referencia a otros contextos de interfaz de usuario conocidos (por sus GUID). El tercer término, "DotConfig" es el contexto de interfaz de usuario basado en reglas definido anteriormente en este artículo.

## <a name="delayed-activation"></a>Activación retrasada
 Las reglas pueden tener un "Retraso" opcional. El retardo se especifica en milisegundos. Si está presente, el retraso hace que la activación o desactivación del contexto de interfaz de usuario de una regla se retrase en ese intervalo de tiempo. Si la regla vuelve a cambiar antes del intervalo de retardo, no sucede nada. Este mecanismo se puede utilizar para "escalonar" los pasos de inicialización, especialmente la inicialización de una sola vez sin depender de temporizadores o registrarse para notificaciones inactivas.

 Por ejemplo, puede especificar la regla de carga de prueba para que tenga un retraso de 100 milisegundos:

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

Aquí están los diversos tipos de término que se soportan:

|Término|Descripción|
|-|-|
|Nnnnnnnnnnn-nnnn-nnnn-nnnnnnnnnnnnnnnnnnnnnnn.|El GUID hace referencia a un contexto de interfaz de usuario. El término será true siempre que el contexto de la interfaz de usuario esté activo y false en caso contrario.|
|HierSingleSelectionName:\<> de patrón|El término será true siempre que la selección en la jerarquía activa sea un único elemento y el nombre del elemento seleccionado coincida con la expresión regular .Net dada por "patrón".|
|UserSettingsStoreQuery:\<> de consulta|"consulta" representa una ruta de acceso completa en el almacén de configuración de usuario, que debe evaluarse como un valor distinto de cero. La consulta se divide en una "colección" y "propertyName" en la última barra diagonal.|
|ConfigSettingsStoreQuery:\<> de consulta|"consulta" representa una ruta de acceso completa en el almacén de configuración de configuración, que debe evaluarse como un valor distinto de cero. La consulta se divide en una "colección" y "propertyName" en la última barra diagonal.|
|ActiveProjectFlavor:\<projectTypeGuid>|El término será true siempre que el proyecto seleccionado tenga sabor (agregado) y tenga un sabor que coincida con el GUID de tipo de proyecto especificado.|
|ActiveEditorContentType:\<contentType>|El término será true cuando el documento seleccionado sea un editor de texto con el tipo de contenido especificado. Nota: cuando se cambia el nombre del documento seleccionado, este término no se actualiza hasta que el archivo se cierra y se vuelve a abrir.|
|ActiveProjectCapability:\<expresión>|El término es true cuando las capacidades activas del proyecto coinciden con la expresión proporcionada. Una expresión puede ser algo así como VB &#124; CSharp.|
|SolutionHasProjectCapability:\<> de expresión|Similar a anterior, pero term es true cuando la solución tiene cualquier proyecto cargado que coincida con la expresión.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|El término será true siempre que una solución tenga un proyecto con sabor (agregado) y tenga un sabor que coincida con el GUID de tipo de proyecto especificado.|
|ProjectAddedItem:\<> de patrón| El término es true cuando se agrega un archivo que coincide con el "patrón" a un proyecto en el soluion que se abre.|
|ActiveProjectOutputType:\<outputType>|El término es true cuando el tipo de salida para el proyecto activo coincide exactamente.  El outputType podría ser <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> un entero o un tipo.|
|ActiveProjectBuildProperty:\<>de\<compilación de la> de regex|El término es true cuando el proyecto activo tiene la propiedad de compilación especificada y el valor de propiedad coincide con el filtro regex proporcionado. Consulte [Persisting Data in MSBuild Project Files](internals/persisting-data-in-the-msbuild-project-file.md) para obtener más detalles sobre las propiedades de compilación.|
|SolutionHasProjectBuildProperty:\<buildProperty\<>á regex>|El término es true cuando la solución tiene un proyecto cargado con la propiedad de compilación especificada y el valor de propiedad coincide con el filtro regex proporcionado.|

## <a name="compatibility-with-cross-version-extension"></a>Compatibilidad con la extensión entre versiones

Contextos de interfaz de usuario basados en reglas es una nueva característica de Visual Studio 2015 y no se portaría a versiones anteriores. Al no migrar a versiones anteriores, se crea un problema con las extensiones o paquetes que tienen como destino varias versiones de Visual Studio. Esas versiones tendrían que cargarse automáticamente en Visual Studio 2013 y versiones anteriores, pero pueden beneficiarse de los contextos de interfaz de usuario basados en reglas para evitar que se carguen automáticamente en Visual Studio 2015.

Para admitir estos paquetes, las entradas de AutoLoadPackages en el registro ahora pueden proporcionar una marca en su campo value para indicar que la entrada debe omitirse en Visual Studio 2015 y versiones posteriores. Esto se puede hacer agregando <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>una opción de marcas a . VSPackages ahora puede agregar **SkipWhenUIContextRulesActive** opción a su <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo para indicar que la entrada debe omitirse en Visual Studio 2015 y versiones posteriores.
## <a name="extensible-ui-context-rules"></a>Reglas de contexto de interfaz de usuario extensible

A veces, los paquetes no pueden usar reglas de contexto de interfaz de usuario estáticas. Por ejemplo, supongamos que tiene un paquete que admite la extensibilidad, de forma que el estado del comando se basa en tipos de editor admitidos por los proveedores MEF importados. El comando está habilitado si hay una extensión que admita el tipo de edición actual. En tales casos, el propio paquete no puede usar una regla de contexto de interfaz de usuario estática, ya que los términos cambiarían en función de las extensiones MEF disponibles.

Para admitir estos paquetes, los contextos de interfaz de usuario basados en reglas admiten una expresión codificada de forma rígida "*" que indica que todos los términos siguientes se unirán con OR. Esto permite que el paquete maestro defina un contexto de interfaz de usuario basado en reglas conocido y vincule su estado de comando a este contexto. Después, cualquier extensión MEF destinada al paquete maestro puede agregar sus términos para los editores que admite sin afectar a otros términos o a la expresión maestra.

La <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> documentación del constructor muestra la sintaxis de las reglas de contexto de interfaz de usuario extensible.
