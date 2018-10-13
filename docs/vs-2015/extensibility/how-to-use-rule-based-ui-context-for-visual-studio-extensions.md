---
title: 'Cómo: utilizar el contexto de interfaz de usuario basada en reglas para extensiones de Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 8
ms.author: gregvanl
ms.openlocfilehash: e9a0f740232493d24cf1bdcd6decba338036e6c9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194706"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Cómo: utilizar el contexto de interfaz de usuario basada en reglas para extensiones de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio permite la carga de VSPackages cuando lo ciertos conocido <xref:Microsoft.VisualStudio.Shell.UIContext>s se activan. Sin embargo, estos contextos de interfaz de usuario no son muy finos más preciso, no dejando a los autores de extensiones no hay ninguna opción, pero para elegir un contexto de interfaz de usuario disponibles que activa antes del punto querían el VSPackage para cargar. Para obtener una lista de contextos de interfaz de usuario conocidos, consulte <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Cargando paquetes puede afectar al rendimiento y cargarlos antes de lo que se necesitan no es el procedimiento recomendado. Visual Studio 2015 introdujo el concepto de contextos de interfaz de usuario basada en reglas, un mecanismo que permite a los autores de extensión definir las condiciones precisas en las que se activa un contexto de interfaz de usuario y cargar VSPackages asociados.  
  
## <a name="rule-based-ui-context"></a>Contexto de interfaz de usuario basada en reglas  
 Una "regla" consta de un nuevo contexto de interfaz de usuario (GUID) y una expresión booleana que hace referencia a uno o más "términos" combina con lógica "and", "o", "no" las operaciones. "Términos de" se evalúan dinámicamente en tiempo de ejecución y se vuelve a evaluar la expresión siempre que cualquiera de sus cambios de términos. Cuando la expresión se evalúa como true, se activa el contexto de interfaz de usuario asociada. En caso contrario, el contexto de interfaz de usuario está desactivado.  
  
 Contexto de interfaz de usuario basada en reglas puede usarse en una variedad de formas:  
  
1.  Especificar las restricciones de visibilidad para los comandos y ventanas de herramientas. Puede ocultar las ventanas de herramientas o comandos hasta que se cumpla la regla de contexto de interfaz de usuario.  
  
2.  Las restricciones de carga como auto: carga automática de paquetes solo cuando se cumple la regla  
  
3.  Tarea retrasada: retardar la carga hasta que haya transcurrido un intervalo especificado y todavía se cumple la regla.  
  
 El mecanismo se puede usar cualquier extensión de Visual Studio.  
  
## <a name="create-a-rule-based-ui-context"></a>Crear un contexto de interfaz de usuario basada en reglas  
 Suponga que tiene una extensión denominada TestPackage, que ofrece un comando de menú que se aplica solo a los archivos con extensión "config". Antes de VS2015, era la mejor opción Cargar TestPackage cuando <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> se activó el contexto de interfaz de usuario. Esto no es eficaz, puesto que la solución cargada no puede contener incluso un archivo .config. Nos gustaría vea cómo pueden usar el contexto de interfaz de usuario basada en reglas para activar un contexto de interfaz de usuario solo cuando un archivo con extensión .config está seleccionado y cargue TestPackage cuando se activa ese contexto de interfaz de usuario.  
  
1.  Definir un nuevo GUID UIContext y agregar a la clase de VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> y <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
     Por ejemplo, supongamos que una nueva interfaz de usuario Solutionopening "UIContextGuid" consiste en Agregar. El GUID creado (puede crear un GUID haciendo clic en Herramientas -> crear guid) es "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". A continuación, agregue lo siguiente dentro de la clase de paquete:  
  
    ```csharp  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     Los atributos, agregue lo siguiente: (detalles de estos atributos se explicará más adelante)  
  
    ```csharp  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     Estos metadatos definen el nuevo GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) y una expresión que hace referencia a un único término, "DotConfig". El término "DotConfig" se evalúa como true cuando la selección actual en la jerarquía activa tiene un nombre que coincide con el patrón de expresión regular "\\.config$" (termina con ".config"). El valor (predeterminado) define un nombre opcional para la regla útil para depurar.  
  
     Los valores del atributo se agregan a pkgdef generado durante el tiempo de compilación más adelante.  
  
2.  En el archivo VSCT para comandos de TestPackage, agregue la marca "DynamicVisibility" para los comandos adecuados:  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  En la sección de visibilidades de la VSCT, asociar los comandos adecuados para la interfaz de usuario nueva Solutionopening GUID definido en #1:  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  En la sección Symbols, agregue la definición de la interfaz de usuario Solutionopening:  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     Ahora, los comandos de menú contextual para los archivos *.config estará visibles solo cuando el elemento seleccionado en el Explorador de soluciones es un archivo "config" y no se cargará el paquete hasta que se selecciona uno de esos comandos.  
  
 A continuación, vamos a usar un depurador para confirmar que carga cuando se espera que el paquete. Para depurar TestPackage:  
  
1.  Establecer un punto de interrupción en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
2.  Compilar el TestPackage e iniciar la depuración.  
  
3.  Cree un proyecto o abra uno.  
  
4.  Seleccione cualquier archivo con una extensión distinta de config. No se alcanzará el punto de interrupción.  
  
5.  Seleccione el archivo App.Config.  
  
 El TestPackage carga y se detiene en el punto de interrupción.  
  
## <a name="adding-more-rules-for-ui-context"></a>Agregar más reglas para el contexto de interfaz de usuario  
 Puesto que las reglas de contexto de interfaz de usuario son expresiones booleanas, puede agregar más restringido de las reglas para un contexto de interfaz de usuario. Por ejemplo, en el contexto de interfaz de usuario anterior, puede especificar que la regla aplica solo cuando se carga una solución con un proyecto. De este modo, los comandos no aparecen si abre un archivo "config" como un archivo independiente, no como parte de un proyecto.  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 Ahora la expresión hace referencia a tres términos. Los dos primeros términos, "SingleProject" y "MultipleProjects", hacen referencia a otros contextos de interfaz de usuario conocidos (por sus GUID). El tercer término, "DotConfig" es el contexto de interfaz de usuario basada en reglas definimos anteriormente.  
  
## <a name="delayed-activation"></a>Activación retrasada  
 Las reglas pueden tener un retraso"opcional". Se especifica el retraso en milisegundos. Si está presente, el retraso provoca la activación o desactivación del contexto de interfaz de usuario de una regla que se retrase por ese intervalo de tiempo. Si el intervalo de retraso antes de realizar copias de los cambios de regla, no ocurre nada. Este mecanismo se puede usar "escalonar" pasos de inicialización - especialmente una inicialización única sin depender de temporizadores o registrarse para notificaciones de inactividad.  
  
 Por ejemplo, puede especificar la regla de prueba de carga para tener un retraso de 100 milisegundos:  
  
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
 Estos son los distintos tipos de término que se admiten:  
  
|||  
|-|-|  
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|El GUID se refiere a un contexto de interfaz de usuario. El término será true siempre que el contexto de interfaz de usuario está activo y false en caso contrario.|  
|HierSingleSelectionName:\<patrón >|El término será true siempre que la selección de la jerarquía activa es un elemento único y el nombre del elemento seleccionado coincide con la expresión regular .net proporcionada por "pattern".|  
|UserSettingsStoreQuery:\<consulta >|"query" representa una ruta de acceso completa en el almacén de configuración de usuario que se debe evaluar como un valor distinto de cero. La consulta se divide en una "colección" y "propertyName" en la barra diagonal último.|  
|ConfigSettingsStoreQuery:\<consulta >|"query" representa una ruta de acceso completa en el almacén de configuración de la configuración que se debe evaluar como un valor distinto de cero. La consulta se divide en una "colección" y "propertyName" en la barra diagonal último.|  
|ActiveProjectFlavor:\<projectTypeGuid >|El término será true siempre que el proyecto seleccionado actualmente es característico (agregado) y tiene un tipo de coincidencia de GUID de tipo de proyecto determinado.|  
|ActiveEditorContentType:\<contentType >|El término será true cuando el documento seleccionado es un editor de texto con el tipo de contenido.|  
|ActiveProjectCapability:\<expresión >|El término es true cuando las capacidades del proyecto activo coincide con la expresión proporcionada. Una expresión puede ser algo parecido a VB &#124; CSharp|  
|SolutionHasProjectCapability:\<expresión >|Es similar al anterior pero término es true cuando la solución tiene ningún proyecto cargado que coincida con la expresión.|  
|SolutionHasProjectFlavor:\<projectTypeGuid >|El término será true siempre que sea una solución tiene proyectos que es característico (agregado) y tiene un tipo de coincidencia de GUID de tipo de proyecto determinado.|


  
## <a name="compatibility-with-cross-version-extension"></a>Compatibilidad con la extensión de entre versiones  
 La regla basada en contextos de interfaz de usuario es una característica nueva en Visual Studio 2015 y no se podría pasar a versiones anteriores. Esto crea un problema con las extensiones o paquetes que tienen como destino varias versiones de Visual Studio que tendría que ser cargan automáticamente en Visual Studio 2013 y versiones anteriores, pero puede beneficiarse de contextos de interfaz de usuario basada en reglas para evitar que se cargan automáticamente en Visual Studio 2015.  
  
 Para admitir estos paquetes, AutoLoadPackages entradas del registro ahora pueden proporcionar una marca en su campo de valor para indicar que se debe omitir la entrada en Visual Studio 2015 y versiones posteriores. Esto puede hacerse mediante la adición de una opción de indicadores para <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Ahora pueden agregar los paquetes VSPackage **SkipWhenUIContextRulesActive** opción a su <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo para indicar que se debe omitir la entrada en Visual Studio 2015 y versiones posteriores.  
  
## <a name="extensible-ui-context-rules"></a>Reglas de contexto de interfaz de usuario extensibles  
 A veces, los paquetes no pueden usar reglas de contexto de interfaz de usuario estáticas. Por ejemplo, suponga que tiene un paquete que admiten la extensibilidad tal que el estado del comando se basa en los tipos de editor que son compatibles con los proveedores MEF importados. El comando está habilitado si hay una extensión que admiten el tipo de edición actual. En estos casos el propio paquete no puede usar una regla de contexto de interfaz de usuario estática, puesto que los términos cambiarían dependiendo de qué MEF las extensiones están disponibles.  
  
 Para admitir estos paquetes, contextos de interfaz de usuario basada en reglas admite una expresión de codificado de forma rígida "*" que indica todos los términos siguientes se combinará con o. Esto permite el paquete maestro definir una regla conocida según el contexto de interfaz de usuario y vincular su estado de comando en este contexto. Posteriormente cualquier extensión MEF de destino para el paquete maestro puede agregar sus términos para los editores que admite sin que afecte a otros términos o la expresión maestra.  
  
 El constructor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> documentación muestra la sintaxis de las reglas de contexto de interfaz de usuario extensibles.

