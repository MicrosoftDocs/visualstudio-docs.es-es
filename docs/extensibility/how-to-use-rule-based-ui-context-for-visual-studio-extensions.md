---
title: "Cómo: usar el contexto de la interfaz de usuario basada en reglas para extensiones de Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
ms.openlocfilehash: d1307f63464b0e652a97e9b06314b08112d8b097
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Cómo: usar el contexto de la interfaz de usuario basada en reglas para extensiones de Visual Studio
Visual Studio permite la carga de VSPackages cuando determinados conocido <xref:Microsoft.VisualStudio.Shell.UIContext>s se activan. Sin embargo, estos contextos de interfaz de usuario no son muy bien precisa, no dejando a los autores de extensión no hay ninguna opción pero para seleccionar un contexto de interfaz de usuario disponibles que activa antes del punto deseaban realmente el VSPackage para cargar. Para obtener una lista de contextos de interfaz de usuario conocidos, consulte <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Carga de paquetes puede afectar el rendimiento y cargarlos antes de que se necesitan no es el procedimiento recomendado. Visual Studio 2015 introdujo el concepto de los contextos de interfaz de usuario basada en reglas, un mecanismo que permite a los autores de extensión definir las condiciones exactas en las que se activa un contexto de la interfaz de usuario y cargar VSPackages asociados.  
  
## <a name="rule-based-ui-context"></a>Contexto de la interfaz de usuario basada en reglas  
 Una regla de"" consta de un nuevo contexto de la interfaz de usuario (un GUID) y una expresión booleana que hace referencia a uno o más "términos" se combina con lógica "y", "o", "no" las operaciones. "Términos de" se evalúan dinámicamente en tiempo de ejecución y se vuelve a evaluar la expresión siempre que cualquiera de sus cambios de términos. Cuando la expresión se evalúa como true, se activa el contexto de la interfaz de usuario asociada. En caso contrario, el contexto de la interfaz de usuario está desactivado.  
  
 Contexto de interfaz de usuario basada en reglas puede usarse en una variedad de formas:  
  
1.  Especificar las restricciones de visibilidad para comandos y ventanas de herramientas. Puede ocultar las ventanas de comandos/tools hasta que se cumpla la regla de contexto de la interfaz de usuario.  
  
2.  Las restricciones de carga como automático: carga automática de paquetes sólo cuando se cumpla la regla  
  
3.  Tarea retrasada: retrasar la carga hasta que haya transcurrido un intervalo especificado y aún se cumple la regla.  
  
 Puede utilizarse el mecanismo de cualquier extensión de Visual Studio.  
  
## <a name="create-a-rule-based-ui-context"></a>Crear un contexto de la interfaz de usuario basada en reglas  
 Suponga que tiene una extensión denominada TestPackage, lo que ofrece un comando de menú que se aplica solo a los archivos con la extensión "config". Antes de VS2015, era la mejor opción Cargar TestPackage cuando <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> se activó el contexto de la interfaz de usuario. Esto no es eficaz, puesto que la solución cargada no puede contener incluso un archivo .config. Permítanos cómo basada en reglas y contexto de interfaz de usuario se pueden usar para activar un contexto de la interfaz de usuario solo cuando un archivo con extensión .config está seleccionada y cargar TestPackage cuando se activa ese contexto de la interfaz de usuario.  
  
1.  Definir un nuevo GUID UIContext y agregar a la clase de VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> y <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
     Por ejemplo, supongamos que un nuevo UIContext "UIContextGuid" consiste en Agregar. El GUID creado (puede crear un GUID haciendo clic en Herramientas -> crear guid) es "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". A continuación, agregue lo siguiente en la clase de paquete:  
  
    ```csharp  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     Para los atributos, agregue lo siguiente: (detalles de estos atributos se explicará más adelante)  
  
    ```csharp  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     Estos metadatos definen el nuevo GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) y una expresión que hace referencia a un único término, "DotConfig". El término "DotConfig" se evalúa como true cuando la selección actual en la jerarquía activa tiene un nombre que coincide con el patrón de expresión regular "\\config$" (termina con ".config"). El valor (predeterminado) define un nombre opcional para la regla útil para la depuración.  
  
     Los valores del atributo se agregan a pkgdef del que se generan durante el tiempo de compilación posteriormente.  
  
2.  En el archivo VSCT de comandos del TestPackage, agregue la marca "DynamicVisibility" para los comandos adecuados:  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  En la sección de visibilidad de la VSCT, asociar los comandos adecuados para el nuevo UIContext GUID definido en #1:  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  En la sección de símbolos, agregue la definición de la UIContext:  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     Ahora, los comandos del menú contextual para los archivos *.config estará visibles solo cuando el elemento seleccionado en el Explorador de soluciones es un archivo de ".config" y el paquete no se cargará hasta que se seleccione uno de esos comandos.  
  
 A continuación, vamos a usar un depurador para confirmar que carga cuando se espera que el paquete. Para depurar TestPackage:  
  
1.  Establecer un punto de interrupción en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
2.  Compilar el TestPackage e iniciar la depuración.  
  
3.  Cree un proyecto o abra uno.  
  
4.  Seleccione cualquier archivo con una extensión que no sea de config. No se alcanzará el punto de interrupción.  
  
5.  Seleccione el archivo App.Config.  
  
 El TestPackage carga y se detiene en el punto de interrupción.  
  
## <a name="adding-more-rules-for-ui-context"></a>Agregar más reglas para el contexto de la interfaz de usuario  
 Puesto que las reglas de contexto de la interfaz de usuario son expresiones booleanas, puede agregar más restringido de las reglas para un contexto de la interfaz de usuario. Por ejemplo, en el contexto de la interfaz de usuario anterior, puede especificar que la regla aplica sólo cuando se carga una solución con un proyecto. De esta manera, los comandos no aparecen si abrir el archivo "config" como un archivo independiente, no como parte de un proyecto.  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 Ahora la expresión hace referencia a tres términos. Los dos primeros términos, "SingleProject" y "MultipleProjects", hacen referencia a otros contextos de interfaz de usuario conocida (mediante su GUID). El tercer término, "DotConfig" es el contexto de interfaz de usuario basada en reglas se definió anteriormente.  
  
## <a name="delayed-activation"></a>Activación retrasada  
 Las reglas pueden tener un retraso"opcional". Se especifica el retraso en milisegundos. Si está presente, el retraso provoca la activación o desactivación del contexto de la interfaz de usuario de la regla se retrasa ese intervalo de tiempo. Si una copia de los cambios en las reglas antes del intervalo de retraso, no ocurre nada. Este mecanismo se puede utilizar para las operaciones de inicialización - especialmente una inicialización sin depender de temporizadores o registrarse para recibir notificaciones de inactividad "escalonar".  
  
 Por ejemplo, puede especificar la regla de prueba de carga para que tenga un retraso de 100 milisegundos:  
  
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
  
|||  
|-|-|  
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|El GUID se refiere a un contexto de la interfaz de usuario. El término será true siempre que el contexto de la interfaz de usuario está activo y false en caso contrario.|  
|HierSingleSelectionName:\<patrón >|El término será true siempre que la selección en la jerarquía activa es un elemento único y el nombre del elemento seleccionado coincide con la expresión regular .net proporcionada por el "modelo".|  
|UserSettingsStoreQuery:\<consulta >|"query" representa una ruta de acceso completa en el almacén de configuración de usuario que se debe evaluar como un valor distinto de cero. La consulta se divide en una "colección" y "propertyName" en la barra diagonal que lo último.|  
|ConfigSettingsStoreQuery:\<consulta >|"query" representa una ruta de acceso completa en el almacén de configuración de la configuración que se debe evaluar como un valor distinto de cero. La consulta se divide en una "colección" y "propertyName" en la barra diagonal que lo último.|  
|ActiveProjectFlavor:\<projectTypeGuid >|El término será true siempre que el proyecto seleccionado actualmente es característico (agregado) y tiene un tipo que coincida con el tipo de proyecto especificado GUID.|  
|ActiveEditorContentType:\<contentType >|El término será true si el documento seleccionado es un editor de texto con el tipo de contenido especificado.|  
|ActiveProjectCapability:\<expresión >|El término es true si las capacidades del proyecto activo coincide con la expresión proporcionada. Una expresión puede ser algo como VB &#124; CSharp|  
|SolutionHasProjectCapability:\<expresión >|Es similar al anterior pero término es true cuando la solución tiene cualquier proyecto cargado que coincida con la expresión.|  
|SolutionHasProjectFlavor:\<projectTypeGuid >|El término será true siempre que una solución tiene proyectos es característico (agregado) y tiene un tipo que coincida con el tipo de proyecto especificado GUID.|


  
## <a name="compatibility-with-cross-version-extension"></a>Compatibilidad con la extensión entre versiones  
 La regla basada en contextos de interfaz de usuario es una característica nueva en Visual Studio 2015 y no se debería pasar a versiones anteriores. Esto crea un problema con las extensiones o paquetes que tienen como destino varias versiones de Visual Studio que tendría que ser cargue automáticamente en Visual Studio 2013 y versiones anteriores, pero se pueden beneficiar de contextos de interfaz de usuario basada en reglas para evitar que se cargue automáticamente en Visual Studio 2015.  
  
 Para admitir estos paquetes, AutoLoadPackages entradas del registro ahora pueden ofrecer una marca en el campo de valor para indicar que se debe omitir la entrada en Visual Studio 2015 y versiones posteriores. Esto puede hacerse mediante la adición de una opción de indicadores para <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Ahora puede agregar VSPackages **SkipWhenUIContextRulesActive** opción a su <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo para indicar que se debe omitir la entrada en Visual Studio 2015 y versiones posteriores.  
  
## <a name="extensible-ui-context-rules"></a>Reglas de contexto de interfaz de usuario extensibles  
 En ocasiones, los paquetes no pueden usar reglas estáticas de contexto de la interfaz de usuario. Por ejemplo, suponga que tiene un paquete admitir extensibilidad de modo que el estado del comando se basa en los tipos de editor que son compatibles con proveedores MEF importados. El comando está habilitado si hay una extensión compatible con el tipo de edición actual. En estos casos el propio paquete no puede usar una regla de contexto de la interfaz de usuario estática, ya que los términos, también cambian dependiendo de qué MEF las extensiones están disponibles.  
  
 Para admitir estos paquetes, contextos de interfaz de usuario basada en reglas admiten una expresión codificado de forma rígida "*" que indica todos los términos siguientes se combinarán con o. Esto permite el paquete maestro definir una regla conocida según el contexto de la interfaz de usuario y asociar su estado de comandos para este contexto. Posteriormente cualquier extensión MEF destinado para el paquete maestro puede agregar sus términos de editores admite sin afectar a otros términos o la expresión principal.  
  
 El constructor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> documentación muestra la sintaxis de las reglas de contexto de la interfaz de usuario extensibles.