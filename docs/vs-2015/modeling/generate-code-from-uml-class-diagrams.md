---
title: Generar código a partir de diagramas de clases de UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 23cefa3d072c2e582237152bff77a2271046053d
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871829"
---
# <a name="generate-code-from-uml-class-diagrams"></a>Generar código a partir de diagramas de clases UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para generar código C# de visual .net a partir de diagramas de clases UML en Visual Studio, use el comando **generar código** . De forma predeterminada, el comando genera un tipo C# para cada tipo UML que seleccione. Puede modificar y extender este comportamiento si modifica o copia las plantillas de texto que generan código. Puede especificar un comportamiento diferente para los tipos contenidos en los diferentes paquetes de su modelo.

 El comando **generar código** es especialmente adecuado para generar código a partir de la selección de elementos del usuario y para generar un archivo para cada clase UML u otro elemento. Por ejemplo, la captura de pantalla muestra dos archivos de C# generados a partir de dos clases UML.

 Como alternativa, si desea generar código en el que los archivos generados no tienen una relación 1:1 con los elementos UML, puede considerar la posibilidad de escribir plantillas de texto que se invocan con el comando **transformar todas las plantillas** . Para obtener más información acerca de este método, vea [generar archivos a partir de un modelo UML](../modeling/generate-files-from-a-uml-model.md).

 ![Diagrama de clases UML y archivos&#35; de clase C generados.](../modeling/media/oob-gencode1.png "oob_GenCode1")

 Para más información sobre los diagramas de clases UML en Visual Studio, vea los temas siguientes:

- [Diagrama de clases de UML: referencia](../modeling/uml-class-diagrams-reference.md)

- [Diagrama de clases de UML: directrices](../modeling/uml-class-diagrams-guidelines.md)

  Para ver qué versiones de Visual Studio admiten diagramas de clases UML, vea [compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="using-the-generate-code-command"></a>Usar el comando Generar código
 En el procedimiento siguiente se describe el comportamiento predeterminado del comando **generar código** :

#### <a name="to-generate-a-separate-file-for-each-element"></a>Para generar un archivo independiente para cada elemento

1. Cree un modelo de UML que contenga clases. Puede ser conveniente aplicar estereotipos a los elementos del modelo.

    Para obtener más información, vea transformaciones de [generación de código](#default)predeterminadas.

2. En un diagrama de clases o en el **Explorador de modelos UML**, seleccione los elementos de los que desea generar código. Puede seleccionar uno de los siguientes:

   - Un conjunto concreto de elementos.

   - Un paquete o el modelo, para generar el código a partir del contenido.

   - El diagrama, para seleccionar todos sus elementos.

3. Abra el menú contextual de un elemento seleccionado y, a continuación, elija **generar código**.

    La primera vez que se usa **generar código** en un modelo determinado, aparece un cuadro de diálogo. Este cuadro de diálogo le permite editar los parámetros de generación de código del modelo.

    Elija **Aceptar** a menos que sepa que desea cambiar estos parámetros.

    Para volver a este cuadro de diálogo más adelante, abra el **Explorador de modelos UML**. Abra el menú contextual del proyecto de modelado y, a continuación, elija **configurar generación de código**. Para obtener más información, vea [personalizar el comando generar código](#custom).

   Se generan archivos que contienen el código de C#. En el caso predeterminado, se genera un archivo para cada tipo y los archivos se generan en un proyecto de biblioteca de clases de C#. No obstante, puede personalizar este comportamiento. Para obtener más información, vea [personalizar el comando generar código](#custom).

   Se aplican al modelo algunas pruebas de validación para asegurarse de que se puede traducir a C#. Si se produce un error en las pruebas, se muestra un mensaje de error y no se realiza la generación de código. Si ha creado un comando de menú de validación, no se genera código para ningún elemento cuyo comando de validación produzca errores. Para obtener más información, vea [definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="default"></a>Transformaciones de generación de código predeterminadas
 En esta sección se resumen los resultados generados por el comando **generar código** , a menos que personalice el comando. Para obtener más información, vea [personalizar el comando generar código](#custom).

- Se genera un tipo de C# para cada tipo seleccionado en el modelo de UML. Cada tipo se coloca en un archivo de código independiente en la carpeta **GeneratedCode**

- Si el tipo UML está incluido en un paquete, el tipo de C# generado se coloca dentro de un espacio de nombres y el archivo se genera en una carpeta que tiene el mismo nombre que el espacio de nombres.

- Se genera una propiedad de C# para cada `Attribute` de una clase UML.

- Se genera un método de C# para cada `Operation` de un tipo UML.

- Se genera un campo de C# para cada asociación navegable en la que participa la clase.

  Si agrega un estereotipo a cada tipo UML, puede controlar más propiedades del tipo de C# generado.

|**Para crear este C# tipo**|**Dibujar este tipo UML**|**Aplicar este estereotipo**|
|---------------------------------|----------------------------|-------------------------------|
|Clase|Clase|\<ninguno > o<br /><br /> Clase de C#|
|Interfaz|Interfaz|\<ninguno > o<br /><br /> Interfaz de C#|
|Enumeración|Enumeración|\<ninguno > o<br /><br /> C# enum|
|delegado|Clase|Delegado de C#|
|Struct|Clase|Struct de C#|

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>Para establecer un estereotipo en un tipo u otro elemento

1. Abra el menú contextual del elemento en un diagrama o en el **Explorador de modelos UML**y, a continuación, elija **propiedades**.

2. En la ventana **propiedades** , elija la flecha desplegable de la propiedad **estereotipos** y, a continuación, active la casilla correspondiente al estereotipo que desea aplicar.

   > [!TIP]
   > Si no aparecen los estereotipos de C#, habilite el perfil de C# para el modelo o para un paquete que contiene los elementos del modelo en los que está interesado. Seleccione el paquete o la raíz del modelo en el **Explorador de modelos UML**. A continuación, en la ventana **propiedades** , elija **perfil**y, a C# continuación, habilite el perfil.

3. Expanda la propiedad estereotipos para ver las propiedades adicionales que puede establecer.

   Las propiedades de **Descripción** de tipos, atributos, operaciones y asociaciones se escriben `<summary>` en comentarios en el código generado. Marque como comentario los elementos vinculados a los tipos que se escriben en los comentarios `<remarks>`.

## <a name="varying-the-generated-code"></a>Modificar el código generado
 El código generado varía según las propiedades de cada tipo, atributo u operación. Por ejemplo, si establece la propiedad **is Abstract** de una clase en true, la `abstract` palabra clave aparecerá en la clase generada. Si establece la **multiplicidad** de un atributo en **\*0..** , la propiedad generada tendrá un `IEnumerable<>` tipo.

 Además, cada estereotipo proporciona varias propiedades adicionales que puede establecer. Estos valores se traducen a las palabras clave adecuadas en el código de C#. Por ejemplo, si establece la propiedad `Is Static` en una clase, la clase de C# será `static`.

 Para establecer estas propiedades adicionales, seleccione la clase u otro elemento en el diagrama. En el ventana Propiedades, expanda **estereotipos**y, a continuación C# , expanda el estereotipo, como  **C# clase**.  En las clases, estas propiedades adicionales incluyen:

- Atributos de CLR

- Is Partial

- Is Static

- Is Unsafe

- Package Visibility

  Cada atributo y operación tiene también propiedades de estereotipo que puede establecer. Si no ve las propiedades en un nuevo atributo, ejecute **generar código**.

## <a name="custom"></a>Personalizar el comando generar código
 El comando **generar código** funciona transformando los elementos del modelo mediante un conjunto de plantillas de texto. Para obtener más información acerca de las plantillas de texto, vea [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md).

 Las plantillas se especifican en un conjunto de *enlaces de plantilla de texto*. Un enlace de plantilla de texto especifica qué plantilla se debe aplicar, dónde se debe colocar la salida generada y otros parámetros del comando **generar código** .

 La primera vez que se ejecuta el comando **generar código** en un modelo determinado, adjunta un conjunto predeterminado de enlaces de plantilla a la raíz del modelo. Estos enlaces se aplican a todos los elementos en el modelo.

 Sin embargo, puede invalidarlos y agregarlos a estos enlaces predeterminados si adjunta sus propios enlaces a los paquetes, clases u otros elementos. Un enlace se aplica a todos los elementos contenidos dentro del elemento al que se adjunta. Por ejemplo, si desea que todos los tipos dentro de un paquete determinado se transformen mediante un conjunto diferente de plantillas o se generen en una carpeta diferente, puede adjuntar los enlaces de plantilla al paquete.

 Para inspeccionar los enlaces de plantilla asociados a un elemento de modelo, elija los puntos suspensivos **[...]** en la propiedad **enlaces de plantilla de texto** en el ventana Propiedades.

 El comando **generar código** aplica las plantillas a cada elemento del modelo que haya seleccionado. Para cada elemento, el conjunto de plantillas aplicado es el conjunto combinado de plantillas que se adjuntan a sus contenedores, hasta la raíz del modelo, inclusive.

 Si dos enlaces de plantilla de este conjunto tienen el mismo nombre, el enlace del contenedor menor invalida el del contenedor mayor. Por ejemplo, la raíz del modelo tiene un enlace con la **plantilla de clase**nombre. Para que su propia plantilla se aplique al contenido de un paquete determinado, defina su propio enlace de plantilla que tenga la **plantilla de clase**nombre.

 Se puede aplicar más de una plantilla a un elemento modelo. Puede generar más de un archivo a partir de cada elemento del modelo.

> [!NOTE]
> Los enlaces adjuntos a la raíz del modelo sirven como valores predeterminados para todos los elementos del modelo. Para ver estos enlaces predeterminados, abra el **Explorador de modelos UML**. Abra el menú contextual del proyecto de modelado y, después, elija **configurar generación de código**. También puede seleccionar la raíz del modelo en el Explorador de modelos UML. En el ventana Propiedades, elija **[...]** en la propiedad **enlaces de plantilla de texto** . Los enlaces no aparecerán hasta que se haya usado el comando **generar código** al menos una vez. Los enlaces de plantilla no se pueden adjuntar a un diagrama.

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>Para adjuntar los enlaces de plantilla de texto a un paquete u otro elemento del modelo

1. En el **Explorador de modelos UML**, abra el menú contextual de un elemento de modelo y, a continuación, elija **propiedades**. Generalmente, adjuntaría los enlaces de plantilla de texto a un paquete o a la raíz del modelo.

2. En la ventana **propiedades** , elija el botón de puntos suspensivos ( **[...]** ) en la propiedad **enlaces de plantilla de texto** .

    Aparece el cuadro de diálogo **enlaces de plantilla de texto** .

3. Elija **Agregar** para crear un nuevo enlace de plantilla de texto.

    \- o -

    Elija un enlace existente para editarlo.

    Cada enlace de plantilla define cómo se debería aplicar una plantilla especificada al elemento del modelo que seleccionó y otros elementos del modelo que contiene.

4. En el cuadro de diálogo, establezca las propiedades del enlace de plantilla de texto.

   |    **Propiedad**    |                                                                                                                                                                                                                                                                                                                    **Descripción**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        NOMBRE        |                                                                                                                                                                                                                                                  Nombre correspondiente a este enlace. Para invalidar un enlace heredado de un paquete contenedor o modelo, use el mismo nombre que el enlace que desea invalidar.                                                                                                                                                                                                                                                  |
   |     Overwrite      |                                                                                                                                                                                                                                                                                                      Si es true, se sobrescribe cualquier código existente.                                                                                                                                                                                                                                                                                                       |
   |    Nombre de destino     | Nombre del archivo que se generó.<br /><br /> Puede insertar expresiones en esta cadena, `{Name}` como o. `{Owner.Name}` Por ejemplo, puede escribir: `{Owner.Name}_{Name}`. La expresión se evalúa en el elemento del modelo. Puede usar las propiedades de los elementos, pero no los métodos. Para buscar qué propiedades se pueden usar, examine las propiedades de tipos en **Microsoft.VisualStudio.Uml.\*** . \*\*Importante:\*\*  `{Name}` o `{Owner.Name}` puede usarse únicamente en el **nombre de destino** propiedad. Para cambiar el nombre de la clase generada, tiene que modificar la plantilla. Para obtener más información, consulte [escribir una plantilla de texto](#writing). |
   |    Ruta de acceso del proyecto    |                                                                      Especifica la ruta de acceso al proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que contendrá los archivos de salida de la transformación. Use valores con tipo para crear un nuevo proyecto. Elija el botón de puntos suspensivos ( **[...]** ) para seleccionar un proyecto existente.<br /><br /> Se creará un nuevo proyecto si no existe uno. Será un proyecto de biblioteca de clases de C#.<br /><br /> Para ello, debe escribir directamente el proyecto. Puede incluir macros de variable de entorno como %ProgramFiles% o %LocalAppData%.                                                                       |
   |  Directorio de destino  |                                                                                          Carpeta en la que se genera el archivo de destino. La ruta de acceso es relativa a la carpeta de proyecto.<br /><br /> Puede usar la expresión `{PackageStructure}` para insertar una ruta de acceso que corresponda a los nombres de los paquetes contenedores. El valor predeterminado es `\GeneratedCode\{PackageStructure}`. También puede incluir variables de entorno como %TEMP% o %HomePath%. **Importante:** `{PackageStructure}` solo se puede usar en la propiedad **Directorio de destino** .                                                                                          |
   | Ruta de acceso del archivo de plantilla |                                                                                                                                                           Plantilla que realizará la transformación.<br /><br /> Puede usar las plantillas proporcionadas o crear otras propias. Puede buscar las plantillas proporcionadas en la siguiente ubicación:<br /><br /> …\Archivos de programa\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |

5. Puede adjuntar tantos enlaces a un elemento como desee.

## <a name="writing"></a>Escribir una plantilla de texto
 Puede escribir a sus propias plantillas de texto. Las plantillas de texto pueden generar código de programa o cualquier otro tipo de archivo de texto.

 Recomendamos comenzar por modificar las copias de las plantillas estándar. Puede copiar las plantillas de las ubicaciones siguientes:

 …\Archivos de programa\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\

 Para entender las plantillas de texto, consulte los siguientes temas.

- Una plantilla de texto es un prototipo del archivo resultante y contiene el texto resultante y el código de programa que lee el modelo. Para obtener más información, vea [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md).

- Para navegar por el modelo de UML en el código de programa, tiene que usar la API de UML. Para obtener más información, vea [navegar por el modelo UML](../modeling/navigate-the-uml-model.md) y [referencia de API para](../modeling/api-reference-for-uml-modeling-extensibility.md)la extensibilidad del modelado UML.

  Para usar las plantillas con el comando **generar código** , debe incluir la Directiva de modelado. Por ejemplo:

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`

  El atributo `ElementType` define el tipo de elemento UML al que se aplica esta plantilla.

  En la plantilla, `this` pertenece a una clase temporal que tiene las siguientes propiedades:

- `Element`= el [IElement](/previous-versions/dd516035(v=vs.140)) de UML al que se aplica la plantilla.

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>

- `Host`: [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

- `ModelBus`: [ModelBus](/previous-versions/ee904639(v=vs.140)). Para obtener más información, vea [integrar modelos UML con otros modelos y herramientas](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- `ProfileName` = "C#Profile"

- `ServiceProvider`: <xref:System.IServiceProvider>

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. Este es el almacén del SDK de visualización y modelado en el que se implementa el UML ModelStore. Para obtener el [IMODELSTORE](/previous-versions/ee789385(v=vs.140))UML, use `this.Element.GetModelStore()`.

  Puede encontrar útiles los siguientes puntos mientras escribe una plantilla de texto. Esta información se describe en detalle en [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md).

- Puede establecer la extensión de nombre de archivo del resultado en la directiva `Output`. Se requiere una directiva `Output` en cada plantilla de texto.

- La plantilla hace referencia automáticamente a algunos ensamblados. Estos ensamblados incluyen, por ejemplo, System.dll y Microsoft.VisualStudio.Uml.Interfaces.dll.

   Para usar otros ensamblados en el código generador del programa, debe usar una directiva `Assembly`. Por ejemplo:

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`

- Algunos espacios de nombres como `System` se importan automáticamente al código de programa. Para otros espacios de nombres, puede usar la directiva `Import` de la misma manera que usaría una instrucción `using`. Por ejemplo:

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`

- Use la directiva `Include` para hacer referencia al texto de otro archivo.

- El comando **generar código** ejecuta las partes de la `<# ... #>` plantilla entre corchetes. Las partes de la plantilla que están fuera de los corchetes se copian en el archivo de resultados. Es importante distinguir entre el código generador y el texto generado. El texto generado puede estar en cualquier lenguaje.

- `<#= Expressions #>` se evalúa y se convierte en cadenas.

## <a name="see-also"></a>Vea también
 [Diagrama de clases de UML: Diagramas de clases UML de referencia](../modeling/uml-class-diagrams-reference.md): [ Las](../modeling/uml-class-diagrams-guidelines.md) instrucciones [generan archivos a partir de un modelo UML](../modeling/generate-files-from-a-uml-model.md)
