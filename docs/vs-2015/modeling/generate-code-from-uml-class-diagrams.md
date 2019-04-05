---
title: Generar código a partir de diagramas de clases UML | Documentos de Microsoft
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
ms.openlocfilehash: ffe24127fc0b02b2abb8b4c91ff57345cf88ff7f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999498"
---
# <a name="generate-code-from-uml-class-diagrams"></a>Generar código a partir de diagramas de clases UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para generar código de Visual C# .NET a partir de diagramas de clases UML en Visual Studio, utilice el **generar código** comando. De forma predeterminada, el comando genera un tipo C# para cada tipo UML que seleccione. Puede modificar y extender este comportamiento si modifica o copia las plantillas de texto que generan código. Puede especificar un comportamiento diferente para los tipos contenidos en los diferentes paquetes de su modelo.  

 El **generar código** comando es especialmente adecuado para generar código a partir de la selección del usuario de elementos y para generar un archivo para cada clase UML u otro elemento. Por ejemplo, la captura de pantalla muestra dos archivos de C# generados a partir de dos clases UML.  

 Como alternativa, si desea generar código en el que los archivos generados no tiene una relación 1:1 con los elementos UML, podría considerar la posibilidad escribir plantillas de texto que se invocan con el **Transformar todas las plantillas** comando. Para obtener más información acerca de ese método, consulte [generar archivos a partir de un modelo UML](../modeling/generate-files-from-a-uml-model.md).  

 ![Clases de UML diagrama y generado C&#35; archivos de clase. ](../modeling/media/oob-gencode1.png "oob_GenCode1")  

 Para más información sobre los diagramas de clases UML en Visual Studio, vea los temas siguientes:  

- [Diagrama de clases de UML: referencia](../modeling/uml-class-diagrams-reference.md)  

- [Diagrama de clases de UML: directrices](../modeling/uml-class-diagrams-guidelines.md)  

  Para ver qué versiones de Visual Studio admiten diagramas de clases UML, vea [compatibilidad con la versión de arquitectura y las herramientas de modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  

## <a name="using-the-generate-code-command"></a>Usar el comando Generar código  
 El procedimiento siguiente describe el comportamiento predeterminado de la **generar código** comando:  

#### <a name="to-generate-a-separate-file-for-each-element"></a>Para generar un archivo independiente para cada elemento  

1. Cree un modelo de UML que contenga clases. Puede ser conveniente aplicar estereotipos a los elementos del modelo.  

    Para obtener más información, consulte [transformaciones de generación de código predeterminado](#default).  

2. En un diagrama de clases o en **Explorador de modelos UML**, seleccione los elementos desde el que va a generar código. Puede seleccionar uno de los siguientes:  

   -   Un conjunto concreto de elementos.  

   -   Un paquete o el modelo, para generar el código a partir del contenido.  

   -   El diagrama, para seleccionar todos sus elementos.  

3. Abra el menú contextual para un elemento seleccionado y, a continuación, elija **generar código**.  

    La primera vez que usas **generar código** en un modelo determinado, aparece un cuadro de diálogo. Este cuadro de diálogo le permite editar los parámetros de generación de código del modelo.  

    Elija **Aceptar** a menos que sepa que desea cambiar estos parámetros.  

    Para devolver más adelante en este cuadro de diálogo, abra **Explorador de modelos UML**. Abra el modelado del menú contextual del proyecto y, a continuación, elija **configurar la generación de código**. Para obtener más información, consulte [personalizar el comando generar código](#custom).  

   Se generan archivos que contienen el código de C#. En el caso predeterminado, se genera un archivo para cada tipo y los archivos se generan en un proyecto de biblioteca de clases de C#. No obstante, puede personalizar este comportamiento. Para obtener más información, consulte [personalizar el comando generar código](#custom).  

   Se aplican al modelo algunas pruebas de validación para asegurarse de que se puede traducir a C#. Si se produce un error en las pruebas, se muestra un mensaje de error y no se realiza la generación de código. Si ha creado un comando de menú de validación, no se genera código para ningún elemento cuyo comando de validación produzca errores. Para obtener más información, consulte [definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md).  

##  <a name="default"></a> Transformaciones de generación de código predeterminadas  
 En esta sección se resume los resultados producidos por el **generar código** comando, a menos que personalice el comando. Para obtener más información, consulte [personalizar el comando generar código](#custom).  

- Se genera un tipo de C# para cada tipo seleccionado en el modelo de UML. Cada tipo se coloca en un archivo de código independiente bajo la **GeneratedCode** carpeta.  

- Si el tipo UML está incluido en un paquete, el tipo de C# generado se coloca dentro de un espacio de nombres y el archivo se genera en una carpeta que tiene el mismo nombre que el espacio de nombres.  

- Se genera una propiedad de C# para cada `Attribute` de una clase UML.  

- Se genera un método de C# para cada `Operation` de un tipo UML.  

- Se genera un campo de C# para cada asociación navegable en la que participa la clase.  

  Si agrega un estereotipo a cada tipo UML, puede controlar más propiedades del tipo de C# generado.  

|**Para crear este tipo de C#**|**Dibuje este tipo UML**|**Aplique este estereotipo**|  
|---------------------------------|----------------------------|-------------------------------|  
|Clase|Clase|\<None > o<br /><br /> Clase de C#|  
|Interfaz|Interfaz|\<None > o<br /><br /> Interfaz de C#|  
|Enumeración|Enumeración|\<None > o<br /><br /> C# enum|  
|delegado|Clase|Delegado de C#|  
|Struct|Clase|Struct de C#|  

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>Para establecer un estereotipo en un tipo u otro elemento  

1. Abra el menú contextual para el elemento en un diagrama o en **Explorador de modelos UML**y, a continuación, elija **propiedades**.  

2. En el **propiedades** ventana, elija la flecha desplegable en el **estereotipos** propiedad y, a continuación, seleccione la casilla correspondiente al estereotipo que desea aplicar.  

   > [!TIP]
   >  Si no aparecen los estereotipos de C#, habilite el perfil de C# para el modelo o para un paquete que contiene los elementos del modelo en los que está interesado. Seleccione el paquete o la raíz del modelo en **Explorador de modelos UML**. A continuación, en el **propiedades** ventana, elija **perfil**y, a continuación, habilite el perfil de C#.  

3. Expanda el **estereotipos** propiedad para ver las propiedades adicionales que se pueden establecer.  

   El **descripción** propiedades de tipos, atributos, operaciones y las asociaciones se escriben en `<summary>` comentarios en el código generado. Marque como comentario los elementos vinculados a los tipos que se escriben en los comentarios `<remarks>`.  

## <a name="varying-the-generated-code"></a>Modificar el código generado  
 El código generado varía según las propiedades de cada tipo, atributo u operación. Por ejemplo, si establece la **Is Abstract** propiedad de una clase en true, el `abstract` palabra clave aparecerá en la clase generada. Si establece la **multiplicidad** de un atributo en ** 0..\\ , la propiedad generada tendrá un `IEnumerable<>` tipo.  

 Además, cada estereotipo proporciona varias propiedades adicionales que puede establecer. Estos valores se traducen a las palabras clave adecuadas en el código de C#. Por ejemplo, si establece la propiedad `Is Static` en una clase, la clase de C# será `static`.  

 Para establecer estas propiedades adicionales, seleccione la clase u otro elemento en el diagrama. En la ventana Propiedades, expanda **estereotipos**y, a continuación, expanda el estereotipo de C#, como **clase de C#**.  En las clases, estas propiedades adicionales incluyen:  

- Atributos de CLR  

- Is Partial  

- Is Static  

- Is Unsafe  

- Package Visibility  

  Cada atributo y operación tiene también propiedades de estereotipo que puede establecer. Si no ve las propiedades de un atributo nuevo, ejecute **generar código**.  

##  <a name="custom"></a> Personalizar el comando generar código  
 El **generar código** comando funciona transformando los elementos del modelo mediante un conjunto de plantillas de texto. Para obtener más información acerca de las plantillas de texto, consulte [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md).  

 Las plantillas se especifican en un conjunto de *enlaces de plantilla de texto*. Un enlace de plantilla de texto especifica qué plantilla se debe aplicar, dónde se debe colocar la salida generada y otros parámetros de la **generar código** comando.  

 Al ejecutar el **generar código** comando en un modelo determinado, se adjunta un conjunto predeterminado de los enlaces de plantilla a la raíz del modelo. Estos enlaces se aplican a todos los elementos en el modelo.  

 Sin embargo, puede invalidarlos y agregarlos a estos enlaces predeterminados si adjunta sus propios enlaces a los paquetes, clases u otros elementos. Un enlace se aplica a todos los elementos contenidos dentro del elemento al que se adjunta. Por ejemplo, si desea que todos los tipos dentro de un paquete determinado se transformen mediante un conjunto diferente de plantillas o se generen en una carpeta diferente, puede adjuntar los enlaces de plantilla al paquete.  

 Para inspeccionar los enlaces de plantilla asociados a un elemento de modelo, elija el botón de puntos suspensivos **[...]**  en el **Text Template Bindings** propiedad en la ventana Propiedades.  

 El **generar código** comando aplica las plantillas a cada elemento del modelo que ha seleccionado. Para cada elemento, el conjunto de plantillas aplicado es el conjunto combinado de plantillas que se adjuntan a sus contenedores, hasta la raíz del modelo, inclusive.  

 Si dos enlaces de plantilla de este conjunto tienen el mismo nombre, el enlace del contenedor menor invalida el del contenedor mayor. Por ejemplo, la raíz del modelo tiene un enlace con el nombre **plantilla de clase**. Para que tenga su propia plantilla aplicada al contenido de un paquete determinado, definir su propio enlace de plantilla que tiene el nombre **plantilla de clase**.  

 Se puede aplicar más de una plantilla a un elemento modelo. Puede generar más de un archivo a partir de cada elemento del modelo.  

> [!NOTE]
>  Los enlaces adjuntos a la raíz del modelo sirven como valores predeterminados para todos los elementos del modelo. Para ver estos enlaces predeterminados, abra **Explorador de modelos UML**. Abra el menú contextual del proyecto de modelado y luego elija **configurar la generación de código**. También puede seleccionar la raíz del modelo en el Explorador de modelos UML. En la ventana Propiedades, elija **[...]**  en el **Text Template Bindings** propiedad. Los enlaces no aparecerán hasta que haya usado el **generar código** comando al menos una vez. Los enlaces de plantilla no se pueden adjuntar a un diagrama.  

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>Para adjuntar los enlaces de plantilla de texto a un paquete u otro elemento del modelo  

1. En **Explorador de modelos UML**, abra el menú contextual de un elemento de modelo y, a continuación, elija **propiedades**. Generalmente, adjuntaría los enlaces de plantilla de texto a un paquete o a la raíz del modelo.  

2. En el **propiedades** ventana, elija el botón de puntos suspensivos (**[...]** ) en el **Text Template Bindings** propiedad.  

    El **Text Template Bindings** aparece el cuadro de diálogo.  

3. Elija **agregar** para crear un nuevo enlace de plantilla de texto.  

    \- o -  

    Elija un enlace existente para editarlo.  

    Cada enlace de plantilla define cómo se debería aplicar una plantilla especificada al elemento del modelo que seleccionó y otros elementos del modelo que contiene.  

4. En el cuadro de diálogo, establezca las propiedades del enlace de plantilla de texto.  


   |    **Property**    |                                                                                                                                                                                                                                                                                                                    **Descripción**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        Name        |                                                                                                                                                                                                                                                  Nombre correspondiente a este enlace. Para invalidar un enlace heredado de un paquete contenedor o modelo, use el mismo nombre que el enlace que desea invalidar.                                                                                                                                                                                                                                                  |
   |     Overwrite      |                                                                                                                                                                                                                                                                                                      Si es true, se sobrescribe cualquier código existente.                                                                                                                                                                                                                                                                                                       |
   |    Nombre de destino     | Nombre del archivo que se generó.<br /><br /> Puede insertar las expresiones en esta cadena como `{Name}` o `{Owner.Name}`. Por ejemplo, podría escribir: `{Owner.Name}_{Name}`. La expresión se evalúa en el elemento del modelo. Puede usar las propiedades de los elementos, pero no los métodos. Para buscar qué propiedades se pueden usar, examine las propiedades de tipos en **Microsoft.VisualStudio.Uml.\\ ***. \*\*Importante:* \* `{Name}` o `{Owner.Name}` puede usarse únicamente en el **nombre de destino** propiedad. Para cambiar el nombre de la clase generada, tiene que modificar la plantilla. Para obtener más información, consulte [escribir una plantilla de texto](#writing). |
   |    Ruta de acceso del proyecto    |                                                                      Especifica la ruta de acceso al proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que contendrá los archivos de salida de la transformación. Use valores con tipo para crear un nuevo proyecto. Elija el botón de puntos suspensivos (**[...]** ) para seleccionar un proyecto existente.<br /><br /> Se creará un nuevo proyecto si no existe uno. Será un proyecto de biblioteca de clases de C#.<br /><br /> Para ello, debe escribir directamente el proyecto. Puede incluir macros de variable de entorno como %ProgramFiles% o %LocalAppData%.                                                                       |
   |  Directorio de destino  |                                                                                          Carpeta en la que se genera el archivo de destino. La ruta de acceso es relativa a la carpeta de proyecto.<br /><br /> Puede usar la expresión `{PackageStructure}` para insertar una ruta de acceso que corresponda a los nombres de los paquetes contenedores. El valor predeterminado es `\GeneratedCode\{PackageStructure}`. También puede incluir variables de entorno como %TEMP% o %HomePath%. **Importante:** `{PackageStructure}` puede usarse únicamente en el **directorio de destino** propiedad.                                                                                          |
   | Ruta de acceso del archivo de plantilla |                                                                                                                                                           Plantilla que realizará la transformación.<br /><br /> Puede usar las plantillas proporcionadas o crear otras propias. Puede buscar las plantillas proporcionadas en la siguiente ubicación:<br /><br /> …\Archivos de programa\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |


5. Puede adjuntar tantos enlaces a un elemento como desee.  

##  <a name="writing"></a> Escribir una plantilla de texto  
 Puede escribir a sus propias plantillas de texto. Las plantillas de texto pueden generar código de programa o cualquier otro tipo de archivo de texto.  

 Recomendamos comenzar por modificar las copias de las plantillas estándar. Puede copiar las plantillas de las ubicaciones siguientes:  

 …\Archivos de programa\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\  

 Para entender las plantillas de texto, consulte los siguientes temas.  

- Una plantilla de texto es un prototipo del archivo resultante y contiene el texto resultante y el código de programa que lee el modelo. Para obtener más información, consulte [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md).  

- Para navegar por el modelo de UML en el código de programa, tiene que usar la API de UML. Para obtener más información, consulte [navegar por el modelo UML](../modeling/navigate-the-uml-model.md) y [referencia de API de extensibilidad del modelado UML](../modeling/api-reference-for-uml-modeling-extensibility.md).  

  Para usar las plantillas con el **generar código** comando, debe incluir la directiva de modelado. Por ejemplo:  

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`  

  El atributo `ElementType` define el tipo de elemento UML al que se aplica esta plantilla.  

  En la plantilla, `this` pertenece a una clase temporal que tiene las siguientes propiedades:  

- `Element` = <xref:Microsoft.VisualStudio.Uml.Classes.IElement> de UML al que se aplica la plantilla.  

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>  

- `Host`: <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  

- `ModelBus`: <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>. Para obtener más información, consulte [integrar modelos UML con otros modelos y herramientas](../modeling/integrate-uml-models-with-other-models-and-tools.md).  

- `ProfileName` = "C#Profile"  

- `ServiceProvider`: <xref:System.IServiceProvider>  

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.  

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. Este es el almacén del SDK de visualización y modelado en el que se implementa el UML ModelStore. Para obtener el UML <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore>, use `this.Element.GetModelStore()`.  

  Puede encontrar útiles los siguientes puntos mientras escribe una plantilla de texto. Esta información se describe detalladamente en [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md).  

- Puede establecer la extensión de nombre de archivo del resultado en la directiva `Output`. Se requiere una directiva `Output` en cada plantilla de texto.  

- La plantilla hace referencia automáticamente a algunos ensamblados. Estos ensamblados incluyen, por ejemplo, System.dll y Microsoft.VisualStudio.Uml.Interfaces.dll.  

   Para usar otros ensamblados en el código generador del programa, debe usar una directiva `Assembly`. Por ejemplo:  

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`  

- Algunos espacios de nombres como `System` se importan automáticamente al código de programa. Para otros espacios de nombres, puede usar la directiva `Import` de la misma manera que usaría una instrucción `using`. Por ejemplo:  

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`  

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`  

- Use la directiva `Include` para hacer referencia al texto de otro archivo.  

- Las partes de la plantilla encerradas entre corchetes `<# ... #>` son ejecutados por el **generar código** comando. Las partes de la plantilla que están fuera de los corchetes se copian en el archivo de resultados. Es importante distinguir entre el código generador y el texto generado. El texto generado puede estar en cualquier lenguaje.  

- `<#= Expressions #>` se evalúa y se convierte en cadenas.  

## <a name="see-also"></a>Vea también  
 [Diagrama de clases de UML: Referencia](../modeling/uml-class-diagrams-reference.md)   
 [Diagrama de clases de UML: Directrices](../modeling/uml-class-diagrams-guidelines.md)   
 [Generar archivos a partir de un modelo UML](../modeling/generate-files-from-a-uml-model.md)
