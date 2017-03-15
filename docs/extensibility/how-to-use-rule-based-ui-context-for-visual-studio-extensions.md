---
title: "C&#243;mo: utilizar el contexto de interfaz de usuario basada en reglas para extensiones de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 7
ms.author: "gregvanl"
caps.handback.revision: 7
---
# C&#243;mo: utilizar el contexto de interfaz de usuario basada en reglas para extensiones de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio permite la carga de VSPackages cuando determinados conocidos <xref:Microsoft.VisualStudio.Shell.UIContext>s se activan. Sin embargo, estos contextos de interfaz de usuario no son muy finos específico, no dejando opciones de autores de extensiones pero para seleccionar un contexto de interfaz de usuario disponibles que activa antes del punto deseaban VSPackage que se va a cargar. Para obtener una lista de contextos de interfaz de usuario conocidos, consulte <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Carga de paquetes puede afectar al rendimiento y cargarlos antes de que se necesitan no es el procedimiento recomendado. Visual Studio 2015 introdujo el concepto de contextos de interfaz de usuario basada en reglas, un mecanismo que permite a los autores de extensión definir las condiciones precisas en las que se activa un contexto de interfaz de usuario y cargar VSPackages asociado.  
  
## Contexto de interfaz de usuario basada en reglas  
 Una "regla" consta de un nuevo contexto de la interfaz de usuario \(un GUID\) y una expresión booleana que hace referencia a uno o más "términos" combinada con lógica "y", "o", "no" las operaciones. "Términos" se evalúan dinámicamente en tiempo de ejecución y se vuelve a evaluar la expresión siempre que cualquiera de sus cambios de términos. Cuando la expresión se evalúa como true, se activa el contexto de la interfaz de usuario asociada. En caso contrario, el contexto de la interfaz de usuario está desactivado.  
  
 Contexto de interfaz de usuario basada en reglas puede utilizarse en una variedad de formas:  
  
1.  Especificar las restricciones de visibilidad para los comandos y ventanas de herramientas. Puede ocultar las ventanas de herramientas o comandos hasta que se cumpla la regla de contexto de la interfaz de usuario.  
  
2.  Carga automática de restricciones: paquetes de carga automática sólo cuando se cumpla la regla  
  
3.  Tarea retrasada: retardar la carga hasta que haya transcurrido un intervalo especificado y que aún se cumple la regla.  
  
 Puede utilizarse el mecanismo de cualquier extensión de Visual Studio.  
  
## Crear un contexto de interfaz de usuario basada en reglas  
 Suponga que tiene una extensión llamada TestPackage, que ofrece un comando de menú que se aplica sólo a archivos con extensión "config". Antes de VS2015, era cargar TestPackage la mejor opción cuando <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> se activó el contexto de la interfaz de usuario. Esto no es eficaz, puesto que la solución cargada no puede contener incluso un archivo .config. Permítanos vea cómo pueden usar el contexto de interfaz de usuario basada en reglas para activar un contexto de interfaz de usuario sólo cuando un archivo con extensión .config está seleccionado y cargue TestPackage cuando se activa ese contexto de interfaz de usuario.  
  
1.  Definir un nuevo GUID UIContext y agregue a la clase de VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> y <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
     Por ejemplo, supongamos que un nuevo UIContext es "UIContextGuid" que se va a agregar. El GUID creado \(puede crear un GUID, haga clic en Herramientas \-\> crear guid\) es "8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B". A continuación, agregue lo siguiente en la clase de paquete:  
  
    ```c#  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     Para los atributos, agregue lo siguiente: \(detalles de estos atributos se explicará más adelante\)  
  
    ```c#  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     Estos metadatos definen el nuevo GUID UIContext \(8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B\) y una expresión que hace referencia a un único término, "DotConfig". El término "DotConfig" se evalúa en true, siempre que la selección actual en la jerarquía activa tiene un nombre que coincide con el patrón de expresión regular "\\.config$" \(termina con "config"\). El valor \(predeterminado\), define un nombre opcional para la regla útil para depurar.  
  
     Los valores del atributo se agregan a pkgdef generado durante el tiempo de compilación posteriormente.  
  
2.  En el archivo VSCT de comandos de TestPackage, agregue la marca "DynamicVisibility" para los comandos adecuados:  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  En la sección de visibilidad de la VSCT, asociar los comandos adecuados para el nuevo UIContext GUID definido en \#1:  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  En la sección de símbolos, agregue la definición de la UIContext:  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     Ahora, los comandos de menú contextual para archivos \*.config será visibles sólo cuando el elemento seleccionado en el Explorador de soluciones es un archivo "config" y el paquete no se cargará hasta que se selecciona uno de esos comandos.  
  
 A continuación, vamos a usar un depurador para confirmar que carga cuando se espera que el paquete. Para depurar TestPackage:  
  
1.  Establecer un punto de interrupción en la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> \(método\).  
  
2.  Crear el TestPackage e iniciar la depuración.  
  
3.  Cree un proyecto o abra uno.  
  
4.  Seleccione cualquier archivo con una extensión distinta de config. No se alcanzará el punto de interrupción.  
  
5.  Seleccione el archivo App.Config.  
  
 El TestPackage se carga y se detiene en el punto de interrupción.  
  
## Agregar más reglas de contexto de la interfaz de usuario  
 Puesto que las reglas de contexto de la interfaz de usuario son expresiones booleanas, puede agregar reglas más restringidas para un contexto de interfaz de usuario. Por ejemplo, en el contexto de la interfaz de usuario anterior, puede especificar que la regla aplica sólo cuando se carga una solución con un proyecto. De esta forma, los comandos no se muestran si abre un archivo "config" como un archivo independiente, no como parte de un proyecto.  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 Ahora la expresión hace referencia a tres términos. Los primeros dos términos, "SingleProject" y "MultipleProjects" hacen referencia a otros contextos de interfaz de usuario conocido \(por sus GUID\). El tercer término, "DotConfig" es el contexto de interfaz de usuario basada en reglas que definimos anteriormente.  
  
## Activación retrasada  
 Las reglas pueden tener un retraso"opcional". Se especifica el retraso en milisegundos. Si está presente, el retraso provoca la activación o desactivación del contexto de interfaz de usuario de la regla se retrasa en ese intervalo de tiempo. Si los cambios de regla de nuevo antes del intervalo de retardo, no ocurre nada. Este mecanismo se puede utilizar los pasos de inicialización \- especialmente una inicialización única sin depender de temporizadores o registrarse para notificaciones de inactividad "escalonar".  
  
 Por ejemplo, puede especificar la regla de prueba de carga para tener un retraso de 100 milisegundos:  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## Tipos de términos  
 Estos son los distintos tipos de término que se admiten:  
  
|||  
|-|-|  
|{nnnnnnnn\-nnnn\-nnnn\-nnnn\-nnnnnnnnnnnn}|El GUID se refiere a un contexto de interfaz de usuario. El término será true siempre que el contexto de la interfaz de usuario está activo y false en caso contrario.|  
|HierSingleSelectionName: \< modelo \>|El término será true, siempre que la selección en la jerarquía activa es un elemento único y el nombre del elemento seleccionado coincide con la expresión regular de .net especificada por "pattern".|  
|UserSettingsStoreQuery: \< consulta \>|"consulta" representa una ruta de acceso completa en el almacén de configuración de usuario que se debe evaluar como un valor distinto de cero. La consulta se divide en una "colección" y "propertyName" en la última barra.|  
|ConfigSettingsStoreQuery: \< consulta \>|"consulta" representa una ruta de acceso completa en el almacén de configuración de la configuración que se debe evaluar como un valor distinto de cero. La consulta se divide en una "colección" y "propertyName" en la última barra.|  
|ActiveProjectFlavor: \< projectTypeGuid \>|El término será true siempre que el proyecto seleccionado actualmente es característicos \(agregado\) y tiene un tipo que coinciden con el GUID del tipo de proyecto determinado.|  
|ActiveEditorContentType: \< contentType \>|El término será true cuando el documento seleccionado es un editor de texto con el tipo de contenido especificado.|  
|ActiveProjectCapability: \< expresión \>|El término es true cuando las capacidades del proyecto activo coincide con la expresión proporcionada. Una expresión puede ser algo parecido a VB &#124; CSharp|  
|SolutionHasProjectCapability: \< expresión \>|Es similar al anterior pero término es true cuando la solución tiene cualquier proyecto cargado que coincida con la expresión.|  
  
## Compatibilidad con extensión entre versiones  
 Regla basado en contextos de interfaz de usuario es una característica nueva en Visual Studio 2015 y transportar no a versiones anteriores. Esto crea un problema con las extensiones o paquetes que tienen como destino varias versiones de Visual Studio que tendría que se cargan automáticamente en Visual Studio 2013 y versiones anteriores, pero se pueden beneficiar de la regla según contextos de interfaz de usuario para evitar que se cargan automáticamente en Visual Studio 2015.  
  
 Para admitir estos paquetes, AutoLoadPackages entradas del registro ahora pueden ofrecer una marca en el campo de valor para indicar que se debe omitir la entrada en Visual Studio 2015 y posterior. Esto puede hacerse mediante la adición de una opción de indicadores para <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Ahora puede agregar VSPackages **SkipWhenUIContextRulesActive** opción a sus <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo para indicar que se debe omitir la entrada en Visual Studio 2015 y versiones posteriores.  
  
## Reglas de contexto de IU extensible  
 A veces, los paquetes no pueden usar reglas estáticas de contexto de la interfaz de usuario. Por ejemplo, suponga que tiene un paquete compatible con extensibilidad de modo que el estado del comando se basa en los tipos de editor que son compatibles con los proveedores MEF importados. El comando está habilitado si hay una extensión compatible con el tipo de edición actual. En estos casos el paquete en sí no puede usar una regla estática de contexto de la interfaz de usuario, ya que los términos cambiarían dependiendo de qué MEF extensiones están disponibles.  
  
 Para admitir estos paquetes, contextos de interfaz de usuario en función de reglas admite una expresión codificado de forma rígida "\*" que indica todos los términos siguientes se combinará con o. Esto permite el paquete maestro definir una regla conocida según el contexto de la interfaz de usuario y vincular su estado de comando en este contexto. Después cualquier extensión MEF como destinado para el paquete principal puede agregar sus términos para los editores admite sin afectar a otros términos o la expresión principal.  
  
 El constructor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> documentación muestra la sintaxis de las reglas de contexto de la interfaz de usuario extensibles.