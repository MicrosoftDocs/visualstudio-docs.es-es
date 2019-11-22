---
title: Define validation constraints for UML models | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, validation constraints
ms.assetid: 87b3b0da-122d-4121-9318-200c38ff49d0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3dd76deb3b72d3b12d3b5892c2e5664273425c4c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295846"
---
# <a name="define-validation-constraints-for-uml-models"></a>Definir restricciones de validación para modelos UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede definir restricciones de validación que prueben si el modelo cumple una condición especificada. Por ejemplo, puede definir una restricción para asegurarse de que un usuario no crea ningún bucle de relaciones de herencia. La restricción se invoca cuando el usuario intenta abrir o guardar el modelo, aunque también se puede invocar manualmente. Si se produce un error en la restricción, se agrega un mensaje de error que se haya definido a la ventana de error. Puede empaquetar estas restricciones en una extensión de integración de Visual Studio ([VSIX](https://go.microsoft.com/fwlink/?LinkId=160780)) y distribuirla a otros usuarios de Visual Studio.

 También puede definir restricciones que validan el modelo respecto a recursos externos como bases de datos. If you want to validate program code against a layer diagram, see [Add custom architecture validation to layer diagrams](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="requirements"></a>Requisitos
 Vea [Requisitos](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="applying-validation-constraints"></a>Aplicar restricciones de validación
 Las restricciones de validación se aplican en tres casos: al guardar un modelo; al abrir un modelo; y al hacer clic en **Validar modelo UML** en el menú **Arquitectura** . En cada caso, solo se aplicarán las restricciones definidas para ese caso, aunque normalmente cada restricción se definiría para aplicarse en más de un caso.

 Los errores de validación se notifican en la ventana de errores de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y puede hacer doble clic en el error para seleccionar los elementos del modelo que tienen un error.

 For more information about applying validation, see [Validate your UML model](../modeling/validate-your-uml-model.md).

## <a name="defining-a-validation-extension"></a>Definir extensiones de validación
 Para crear una extensión de validación para un diseñador UML, se debe crear una clase que defina las restricciones de validación e incrustarla en una extensión de integración de Visual Studio (VSIX). Las extensiones VSIX actúan como contenedores que instalan la restricción. Hay dos métodos alternativos de definir una extensión de validación:

- **Create a validation extension in its own VSIX using a project template.** Este es el método más rápido. Utilícelo si no desea combinar las restricciones de validación con otros tipos de extensiones, como comandos de menú, elementos de cuadro de herramientas personalizados o controladores de gestos. Puede definir varias restricciones en una clase.

- **Create separate validation class and VSIX projects.** Use este método si desea combinar varios tipos de extensiones en la misma VSIX. Por ejemplo, si el comando de menú espera que el modelo respete restricciones concretas, podría incrustarlo en la misma VSIX como método de validación.

#### <a name="to-create-a-validation-extension-in-its-own-vsix"></a>Para crear una extensión de validación en una VSIX propia

1. En el cuadro de diálogo **Nuevo proyecto** , en **Proyectos de modelado**, seleccione **Extensión de validación**.

2. Abra el archivo **.cs** en el nuevo proyecto y modifique la clase para implementar la restricción de validación.

    Para obtener más información, vea [Evaluar la restricción de validación](#Implementing).

   > [!IMPORTANT]
   > Asegúrese de que los archivos **.cs** contienen la siguiente instrucción `using` :
   >
   >  `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

3. Puede agregar restricciones adicionales definiendo nuevos métodos. Para identificar un método como un método de validación, se debe etiquetar con los atributos de la misma manera que el método de validación inicial.

4. Pruebe las restricciones presionando F5. Para obtener más información, vea [Ejecutar una restricción de validación](#Executing).

5. Install the menu command on another computer by copying the file **bin\\\*\\\*.vsix** that is built by your project. Para obtener más información, vea [Instalar y desinstalar una extensión](#Installing).

   Cuando se agregan otros archivos **.cs** , normalmente se requieren las siguientes instrucciones `using` :

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Uml.Classes;

```

 A continuación se muestra el procedimiento alternativo:

#### <a name="to-create-a-separate-validation-constraint-in-a-class-library-project"></a>Para crear una restricción de validación independiente en un proyecto de biblioteca de clases

1. Cree un proyecto de biblioteca de clases, ya sea agregándolo a una solución VSIX existente o creando una nueva solución.

    1. En el menú **Archivo** , elija **Nuevo**, **Proyecto**.

    2. En **Plantillas instaladas**, expanda **Visual C#** o **Visual Basic**y, a continuación, en la columna central, elija **Biblioteca de clases**.

2. A menos que la solución ya contenga uno, cree un proyecto VSIX:

    1. En el **Explorador de soluciones**, en el menú contextual de la solución, elija  **Agregar**, **Nuevo proyecto**.

    2. En **Plantillas instaladas**, expanda **Visual C#** o **Visual Basic**y, a continuación, elija **Extensibilidad**. En la columna central, haga clic en **Proyecto VSIX**.

3. Establezca el proyecto VSIX como proyecto de inicio de la solución.

    - En el Explorador de soluciones, en el menú contextual del proyecto VSIX, elija **Establecer como proyecto de inicio**.

4. En **source.extension.vsixmanifest**, en **Contenido**, agregue el proyecto de biblioteca de clases como componente MEF:

    1. En la pestaña **Metadatos** , establezca un nombre para VSIX.

    2. En la pestaña **Destinos de instalación** , establezca las versiones de Visual Studio como destinos.

    3. En la pestaña **Activos** , elija **Nuevo**y, en el cuadro de diálogo, establezca:

         **Tipo** = **Componente MEF**

         **Origen** = **Un proyecto de la solución actual**

         **Proyecto** = *Su proyecto de biblioteca de clases*

#### <a name="to-define-the-validation-class"></a>Para definir la clase Validación

1. No necesita este procedimiento si ha creado una clase de validación con una VSIX propia a partir de la plantilla de proyecto de validación.

2. En el proyecto de validación de clases, agregue referencias a los ensamblados de [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] siguientes:

     `Microsoft.VisualStudio.Modeling.Sdk.[version]`

     `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`

     `Microsoft.VisualStudio.Uml.Interfaces`

     `System.ComponentModel.Composition`

3. Agregue un archivo al proyecto de biblioteca de clases con código similar al siguiente ejemplo.

    - Cada restricción de validación está incluida dentro de un método que se marca con un atributo concreto. El método acepta un parámetro de un tipo de elemento del modelo. Cuando se invoca la validación, el marco de validación aplicará cada método de validación a cada elemento del modelo que se ajuste a su tipo de parámetro.

    - Puede situar estos métodos en cualquier clase y espacio de nombres. Cámbielos según sus preferencias.

    ```
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using Microsoft.VisualStudio.Modeling.Validation;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.Uml.Classes;
    // You might also need the other Microsoft.VisualStudio.Uml namespaces.

    namespace Validation
    {
      public class MyValidationExtensions
      {
        // SAMPLE VALIDATION METHOD.
        // All validation methods have the following attributes.
        [Export(typeof(System.Action<ValidationContext, object>))]
        [ValidationMethod(
           ValidationCategories.Save
         | ValidationCategories.Open
         | ValidationCategories.Menu)]
        public void ValidateClassNames
          (ValidationContext context,
           // This type determines what elements
           // will be validated by this method:
           IClass elementToValidate)
        {
          // A validation method should not change the model.

          List<string> attributeNames = new List<string>();
          foreach (IProperty attribute in elementToValidate.OwnedAttributes)
          {
            string name = attribute.Name;
            if (!string.IsNullOrEmpty(name) && attributeNames.Contains(name))
            {
              context.LogError(
                string.Format("Duplicate attribute name '{0}' in class {1}", name, elementToValidate.Name),
                "001", elementToValidate);
            }
            attributeNames.Add(name);
          }

        }
        // Add more validation methods for different element types.
      }
    }
    ```

## <a name="Executing"></a> Executing a Validation Constraint
 A efectos de prueba, ejecute los métodos de validación en modo de depuración.

#### <a name="to-test-the-validation-constraint"></a>Para probar la restricción de validación

1. Presione **F5**o, en el menú **Depurar** , elija **Iniciar depuración**.

     Se iniciará una instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

     **Solución de problemas**: si no se inicia un nuevo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :

    - Si tiene más de un proyecto, asegúrese de que el proyecto VSIX está configurado como proyecto de inicio de la solución.

    - En el Explorador de soluciones, en el menú contextual del proyecto de inicio o único, elija **Propiedades**. In the project properties editor, select the **Debug** tab. Make sure that the string in the **Start external program** field is the full pathname of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], typically:

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. En la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra o cree un proyecto de modelado, y abra o cree un diagrama de modelado.

3. Para configurar una prueba para la restricción de ejemplo indicada en la sección anterior:

    1. Abra un diagrama de clases.

    2. Cree una clase y agregue dos atributos que tengan el mismo nombre.

4. En el menú contextual en cualquier parte del diagrama, elija **Validar**.

5. Cualquier error del modelo se notificará en la ventana de errores.

6. Haga doble clic en el informe de errores. Si los elementos mencionados en el informe están visibles en la pantalla, aparecerán resaltados.

     **Solución de problemas**: si el comando **Validar** no aparece en el menú, asegúrese de que:

    - El proyecto de validación aparece como un componente MEF en la pestaña **Activos** de **source.extensions.manifest** del proyecto VSIX.

    - Los atributos `Export` y `ValidationMethod` correctos están adjuntados a los métodos de validación.

    - `ValidationCategories.Menu` is included in the argument for the `ValidationMethod` attribute, and it is composed with other values using Logical OR (&#124;).

    - Los parámetros de todos los atributos `Import` y `Export` son válidos.

## <a name="Implementing"></a> Evaluating the Constraint
 El método de validación debe determinar si la restricción de validación que desea aplicar es true o false. Si es true, no debería hacer nada. Si es false, debería notificar un error utilizando los métodos proporcionados por el parámetro `ValidationContext` .

> [!NOTE]
> Los métodos de validación no deberían cambiar el modelo. No hay ninguna garantía de en qué momento ni en qué orden se van a ejecutar las restricciones. Si tiene que pasar información entre ejecuciones sucesivas de un método de validación en una ejecución de validación, puede utilizar la memoria caché del contexto que se describe en [Coordinar varias validaciones](#ContextCache).

 Por ejemplo, si desea comprobar que cada tipo (clase, interfaz o enumerador) tiene un nombre de al menos tres caracteres de longitud, podría utilizar este método:

```
public void ValidateTypeName(ValidationContext context, IType type)
{
  if (!string.IsNullOrEmpty(type.Name) && type.Name.Length < 3)
  {
    context.LogError(
      string.Format("Type name {0} is too short", type.Name),
               "001", type);
   }
 }
```

 Vea [Programming with the UML API](../modeling/programming-with-the-uml-api.md) para obtener información sobre los métodos y tipos que puede usar para leer el modelo y navegar por él.

### <a name="about-validation-constraint-methods"></a>Métodos de restricción de validación
 Cada restricción de validación se define mediante un método de la forma siguiente:

```
[Export(typeof(System.Action<ValidationContext, object>))]
 [ValidationMethod(ValidationCategories.Save
  | ValidationCategories.Menu
  | ValidationCategories.Open)]
public void ValidateSomething
  (ValidationContext context, IClassifier elementToValidate)
{...}
```

 Los atributos y parámetros de cada método de validación son los siguientes:

|||
|-|-|
|`[Export(typeof(System.Action <ValidationContext, object>))]`|Define el método como una restricción de validación utilizando Managed Extensibility Framework (MEF).|
|`[ValidationMethod (ValidationCategories.Menu)]`|Especifica cuándo se ejecutará la validación. Use bitwise OR (&#124;) if you want to combine more than one option.<br /><br /> `Menu` = invocado por el menú Validar.<br /><br /> `Save` = invocado al guardar el modelo.<br /><br /> `Open` = invocado al abrir el modelo. `Load` = invocado al guardar el modelo, pero en caso de una contravención advierte al usuario que puede que no sea posible volver a abrir el modelo. También se invoca durante la carga, antes de que se analice el modelo.|
|`public void ValidateSomething`<br /><br /> `(ValidationContext context,`<br /><br /> `IElement element)`|Reemplace el segundo parámetro `IElement` por el tipo de elemento al que desea aplicar la restricción. El método restricción se invocará en todos los elementos del tipo especificado.<br /><br /> El nombre del método es indiferente.|

 Puede definir tantos métodos de validación como desee, con diferentes tipos en el segundo parámetro. Cuando se invoca la validación, se llamará a cada método de validación en cada elemento del modelo que se ajusta al tipo de parámetro.

### <a name="reporting-validation-errors"></a>Notificar errores de validación
 Para crear un informe de errores, utilice los métodos proporcionados por `ValidationContext`:

 `context.LogError("error string", errorCode, elementsWithError);`

- `"error string"` aparece en la lista de errores de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

- `errorCode` es una cadena que debe ser un identificador único del error.

- `elementsWithError` identifica los elementos del modelo. Cuando el usuario hace doble clic en el informe de errores, se seleccionará la forma que representa este elemento.

  `LogError(),` `LogWarning()` y `LogMessage()` colocan los mensajes en secciones diferentes de la lista de errores.

## <a name="how-validation-methods-are-applied"></a>Cómo se aplican los métodos de validación
 La validación se aplica a cada elemento del modelo, incluidas las relaciones y las partes de elementos mayores, como atributos de una clase y parámetros de una operación.

 Cada método de validación se aplica a cada elemento que se ajusta al tipo de su segundo parámetro. Esto significa que si, por ejemplo, define un método de validación con un segundo parámetro de `IUseCase` y otro con su supertipo `IElement`, ambos métodos se aplicarán a cada caso de uso en el modelo.

 The hierarchy of types is summarized in [UML model element types](../modeling/uml-model-element-types.md).

 También puede tener acceso a los elementos siguiendo las relaciones. Por ejemplo, si fuera a definir un método de validación en `IClass`, podría recorrer sus propias propiedades:

```
public void ValidateTypeName(ValidationContext context, IClass c)
{
   foreach (IProperty property in c.OwnedAttributes)
   {
       if (property.Name.Length < 3)
       {
            context.LogError(
                 string.Format(
                        "Property name {0} is too short",
                        property.Name),
                 "001", property);
        }
   }
}
```

### <a name="creating-a-validation-method-on-the-model"></a>Crear un método de validación en el modelo
 Si desea asegurarse de que se llama a un método de validación exactamente una vez durante cada validación ejecutada, puede validar `IModel`:

```
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs; ...
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu)]
public void ValidateModel(ValidationContext context, IModel model)
{  foreach (IElement element in model.OwnedElements)
   { ...
```

### <a name="validating-shapes-and-diagrams"></a>Validar formas y diagramas
 Los métodos de validación no se invocan en elementos de visualización como los diagramas y las formas, porque el propósito principal de los métodos de validación es validar el modelo. Pero puede tener acceso al diagrama actual utilizando el contexto del diagrama.

 En su clase de validación, declare `DiagramContext` como una propiedad importada:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
...
[Import]
public IDiagramContext DiagramContext { get; set; }
```

 En un método de validación, puede utilizar `DiagramContext` para tener acceso al diagrama que tiene el foco en la actualidad, si hay alguno:

```
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu)]
public void ValidateModel(ValidationContext context, IModel model)
{
  IDiagram focusDiagram = DiagramContext.CurrentDiagram;
  if (focusDiagram != null)
  {
    foreach (IShape<IUseCase> useCaseShape in
              focusDiagram.GetChildShapes<IUseCase>())
    { ...
```

 Para registrar un error, debe obtener el elemento del modelo que la forma representa, porque no puede pasar una forma a `LogError`:

```
IUseCase useCase = useCaseShape.Element;
context.LogError(... , usecase);
```

### <a name="ContextCache"></a> Coordinating Multiple Validations
 Cuando se invoca la validación, por ejemplo, a través de un usuario desde un menú de diagrama, cada método de validación se aplica a cada elemento del modelo. Esto significa que, en una única invocación del marco de validación, el mismo método se puede aplicar muchas veces a distintos elementos.

 Esto presenta un problema para las validaciones que se encargan de las relaciones entre elementos. Puede escribir una validación que se inicie, por ejemplo, en un caso de uso y recorra las relaciones de **include** para comprobar que no hay ningún bucle. Sin embargo, cuando el método se aplica a cada caso de uso de un modelo que tiene muchos vínculos **include** , es probable que procese repetidamente las mismas áreas del modelo.

 Para evitar esta situación, existe una memoria caché del contexto en la que la información se conserva durante una ejecución de validación. Puede utilizarla para pasar información entre diferentes ejecuciones de los métodos de validación. Por ejemplo, puede almacenar una lista de los elementos con los que ya se ha trabajado en esta ejecución de validación. La memoria caché se crea al comienzo de cada ejecución de validación y no se puede utilizar para pasar información entre diferentes ejecuciones de validación.

|||
|-|-|
|`context.SetCacheValue<T> (name, value)`|Almacena un valor.|
|`context.TryGetCacheValue<T> (name, out value)`|Obtiene un valor. Devuelve true si es correcto.|
|`context.GetValue<T>(name)`|Obtiene un valor.|
|`Context.GetValue<T>()`|Obtiene un valor del tipo especificado.|

## <a name="Installing"></a> Installing and uninstalling an extension
 Puede instalar una extensión de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] en su propio equipo y en otros equipos.

#### <a name="to-install-an-extension"></a>Para instalar una extensión

1. En el equipo, busque el archivo **.vsix** compilado en el proyecto VSIX.

    1. En el **Explorador de soluciones**, en el menú contextual del proyecto VSIX, elija **Abrir carpeta en el Explorador de Windows**.

    2. Locate the file **bin\\\*\\** _YourProject_ **.vsix**

2. Copie el archivo **.vsix** en el equipo de destino en el que desea instalar la extensión. Puede tratarse de su propio equipo o de otro.

    - El equipo de destino debe tener una de las ediciones de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] que especificó en **source.extension.vsixmanifest**.

3. En el equipo de destino, abra el archivo **.vsix** .

     El**Instalador de extensiones de Visual Studio** se abre e instala la extensión.

4. Inicie o reinicie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

#### <a name="to-uninstall-an-extension"></a>Para desinstalar una extensión

1. En el menú **Herramientas** , elija **Extensiones y actualizaciones**.

2. Expanda **Extensiones instaladas**.

3. Seleccione la extensión y, a continuación, elija **Desinstalar**.

   En contadas ocasiones, una extensión defectuosa no se carga y crea un informe en la ventana de error, aunque no aparece en el Administrador de extensiones. In that case, you can remove the extension by deleting the file from the following location where *%LocalAppData%* is typically *DriveName*:\Users\\*UserName*\AppData\Local:

   *%LocalAppData%* **\Microsoft\VisualStudio\\[version]\Extensions**

## <a name="Example"></a> Ejemplo
 En este ejemplo se buscan bucles en la relación de dependencia entre los elementos.

 La validación se ejecutará al guardar y a través del comando del menú de validación.

```
/// <summary>
/// Verify that there are no loops in the dependency relationsips.
/// In our project, no element should be a dependent of itself.
/// </summary>
/// <param name="context">Validation context for logs.</param>
/// <param name="element">Element to start validation from.</param>
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu
     | ValidationCategories.Save | ValidationCategories.Open)]
public void NoDependencyLoops(ValidationContext context, INamedElement element)
{
    // The validation framework will call this method
    // for every element in the model. But when we follow
    // the dependencies from one element, we will validate others.
    // So we keep a list of the elements that we don't need to validate again.
    // The list is kept in the context cache so that it is passed
    // from one execution of this method to another.
    List<INamedElement> alreadySeen = null;
    if (!context.TryGetCacheValue("No dependency loops", out alreadySeen))
    {
       alreadySeen = new List<INamedElement>();
       context.SetCacheValue("No dependency loops", alreadySeen);
    }

    NoDependencyLoops(context, element,
                new INamedElement[0], alreadySeen);
}

/// <summary>
/// Log an error if there is any loop in the dependency relationship.
/// </summary>
/// <param name="context">Validation context for logs.</param>
/// <param name="element">The element to be validated.</param>
/// <param name="dependants">Elements we've followed in this recursion.</param>
/// <param name="alreadySeen">Elements that have already been validated.</param>
/// <returns>true if no error was detected</returns>
private bool NoDependencyLoops(ValidationContext context,
    INamedElement element, INamedElement[] dependants,
    List<INamedElement> alreadySeen)
{
    if (dependants.Contains(element))
    {
        context.LogError(string.Format("{0} should not depend on itself", element.Name),
        "Fabrikam.UML.NoGenLoops", // unique code for this error
        dependants.SkipWhile(e => e != element).ToArray());
            // highlight elements that are in the loop
        return false;
    }
    INamedElement[] dependantsPlusElement =
        new INamedElement[dependants.Length + 1];
    dependants.CopyTo(dependantsPlusElement, 0);
    dependantsPlusElement[dependantsPlusElement.Length - 1] = element;

    if (alreadySeen.Contains(element))
    {
        // We have already validated this when we started
        // from another element during this validation run.
        return true;
    }
    alreadySeen.Add(element);

    foreach (INamedElement supplier in element.GetDependencySuppliers())
    {
        if (!NoDependencyLoops(context, supplier,
             dependantsPlusElement, alreadySeen))
        return false;
    }
    return true;
}
```

## <a name="see-also"></a>Vea también
 [Define and install a modeling extension](../modeling/define-and-install-a-modeling-extension.md) [Programming with the UML API](../modeling/programming-with-the-uml-api.md)
