---
title: Personalizar el almacenamiento de archivo y la serialización XML | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
ms.assetid: 76c53ef1-e3b9-45da-b425-1bddb3c01395
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ee8a3b5a5510ef5b8a104e3a55ace3af9ce7d318
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592901"
---
# <a name="customizing-file-storage-and-xml-serialization"></a>Personalizar el almacenamiento de archivos y la serialización XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [personalizar el almacenamiento de archivos y serialización XML](https://docs.microsoft.com/visualstudio/modeling/customizing-file-storage-and-xml-serialization).  
  
Cuando el usuario guarda una instancia, o *modelo*, de un lenguaje específico de dominio (DSL) en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], se crea o actualiza un archivo XML. Puede volver a cargar el archivo para volver a crear el modelo en el Store.  
  
 Puede personalizar el esquema de serialización mediante el ajuste de la configuración en **comportamiento de serialización Xml** en el Explorador de DSL. Hay un nodo bajo **comportamiento de serialización Xml** para cada clase de dominio, la propiedad y la relación. Las relaciones se encuentran en sus clases de origen. También existen los nodos correspondientes a la forma, conector y las clases del diagrama.  
  
 También puede escribir código de programa para la personalización más avanzada.  
  
> [!NOTE]
>  Si desea guardar el modelo en un formato determinado, pero no es necesario volver a cargarlo desde ese formulario, considere el uso de plantillas de texto para generar la salida del modelo, en lugar de un esquema de serialización personalizada. Para obtener más información, consulte [generar código desde un lenguaje específico de dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
## <a name="model-and-diagram-files"></a>Archivos de diagrama y modelo  
 Normalmente, cada modelo se guarda en dos archivos:  
  
-   El archivo de modelo tiene un nombre como **Model1.mydsl**. Almacena los elementos del modelo y las relaciones y sus propiedades. La extensión de archivo como **.mydsl** viene determinada por la **FileExtension** propiedad de la **Editor** nodo en la definición de DSL.  
  
-   El archivo de diagrama tiene un nombre como **Model1.mydsl.diagram**. Almacena las formas, conectores y sus posiciones, colores, espesores de línea y otros detalles de la apariencia del diagrama. Si el usuario elimina un **. Diagram** archivo, no se pierde la información esencial en el modelo. Se pierde solo el diseño del diagrama. Cuando se abre el archivo de modelo, de forma predeterminada un conjunto de formas y conectores que se va a crear.  
  
#### <a name="to-change-the-file-extension-of-a-dsl"></a>Para cambiar la extensión de archivo de un DSL  
  
1.  Abra la definición de DSL. En el Explorador de DSL, haga clic en el nodo del Editor.  
  
2.  En la ventana Propiedades, edite el **FileExtension** propiedad. No incluya la inicial "." de la extensión de nombre de archivo.  
  
3.  En el Explorador de soluciones, cambie el nombre de los archivos de plantilla de dos elementos en **DslPackage\ProjectItemTemplates**. Estos archivos tienen nombres que siguen este formato:  
  
     `myDsl.diagram`  
  
     `myDsl.myDsl`  
  
## <a name="the-default-serialization-scheme"></a>El esquema de serialización predeterminado  
 Para crear un ejemplo de este tema, se utilizó la siguiente definición de DSL.  
  
 ![Diagrama de definición de DSL &#45; modelo de árbol genealógico](../modeling/media/familyt-person.png "FamilyT_Person")  
  
 Este DSL se usó para crear un modelo que tiene el aspecto siguiente en la pantalla.  
  
 ![Diagrama de árbol genealógico, cuadro de herramientas y el explorador](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
 Este modelo se ha guardado y, a continuación, vuelva a abrir en el editor de texto XML:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">  
  <people>  
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">  
      <children>  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />  
      </children>  
    </person>  
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />  
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />  
  </people>  
</familyTreeModel>  
  
```  
  
 Tenga en cuenta los siguientes aspectos sobre el modelo serializado:  
  
-   Cada nodo XML tiene un nombre que es el mismo que un nombre de clase de dominio, salvo que la primera letra es minúscula. Por ejemplo, `familyTreeModel` y `person`.  
  
-   Propiedades de dominio como el nombre y el año de nacimiento se serializan como atributos en los nodos XML. Nuevamente, el carácter inicial del nombre de propiedad se convierte a minúsculas.  
  
-   Cada relación se serializa como un nodo XML anidado en el extremo de origen de la relación. El nodo tiene el mismo nombre que la propiedad de rol de origen, pero con un carácter en minúscula inicial.  
  
     Por ejemplo, en la definición de DSL, un rol que se denomina **personas** con origen en el **FamilyTree** clase.  En el XML, se representa mediante el nodo denominado `people` anidado dentro de la `familyTreeModel` nodo.  
  
-   El extremo de destino de cada relación de incrustación se serializa como un nodo anidado en la relación. Por ejemplo, el `people` nodo contiene varias `person` nodos.  
  
-   El extremo de destino de cada relación de referencia se serializa como un *moniker*, que codifica una referencia al elemento de destino.  
  
     Por ejemplo, en un `person` nodo, puede haber un `children` relación. Este nodo contiene los monikers, como:  
  
    ```  
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
    ```  
  
## <a name="understanding-monikers"></a>Monikers de descripción  
 Monikers se usan para representar referencias cruzadas entre las distintas partes de los archivos de modelo y el diagrama. También se usan en el `.diagram` que haga referencia a nodos en el archivo de modelo. Hay dos formas de moniker:  
  
-   *Monikers ID* entrecomillar el GUID del elemento de destino. Por ejemplo:  
  
    ```  
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />  
  
    ```  
  
-   *Calificado monikers claves* identificar el elemento de destino por el valor de una propiedad de dominio designada denominada clave de moniker. El moniker del elemento de destino viene precedido por el moniker de su elemento primario en el árbol de relaciones de incrustación.  
  
     Los ejemplos siguientes se realizan desde un DSL en el que existe es una clase de dominio llamada Album, que tiene una relación de incrustación a un dominio con nombre de canción de la clase:  
  
    ```  
    <albumMoniker title="/My Favorites/Jazz after Teatime" />  
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
  
    ```  
  
     Monikers de claves completos que se usará si la clase de destino tiene una propiedad de dominio para el que la opción **es la clave de Moniker** está establecido en `true` en **comportamiento de serialización Xml**. En el ejemplo, se establece esta opción para las propiedades de dominio denominadas "Title" en las clases de dominio "Álbum" y "Canción".  
  
 Monikers de clave completos son fáciles de leer que monikers de identificador. Si piensa que el XML de los archivos de modelo para ser leídos por personas, considere el uso de monikers de claves completos. Sin embargo, es posible que el usuario puede establecer más de un elemento a tener la misma clave de moniker. Claves duplicadas podrían provocar que el archivo no volver a cargar correctamente. Por lo tanto, si define una clase de dominio que se hace referencia mediante monikers de clave completos, debe considerar formas de evitar que el usuario al guardar un archivo con monikers duplicados.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Para establecer una clase de dominio para hacer referencia a los monikers de Id.  
  
1.  Asegúrese de que **es la clave de Moniker** es `false` para cada propiedad de dominio en la clase y sus clases base.  
  
    1.  En el Explorador de DSL, expanda **Behavior\Class datos de serialización de Xml\\**_\<la clase de dominio >_**\Element datos**.  
  
    2.  Compruebe que **es la clave de Moniker** es `false` para cada propiedad de dominio.  
  
    3.  Si la clase de dominio tiene una clase base, repita el procedimiento de esa clase.  
  
2.  Establecer **serializar Id**  =  `true` para la clase de dominio.  
  
     Esta propiedad se puede encontrar en **comportamiento de serialización Xml**.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Para establecer una clase de dominio para hacer referencia a los monikers de clave completos  
  
-   Establecer **es la clave de Moniker** para una propiedad de dominio de una clase de dominio existente. El tipo de la propiedad debe ser `string`.  
  
    1.  En el Explorador de DSL, expanda **Behavior\Class datos de serialización de Xml\\**_\<la clase de dominio >_**\Element datos**y, a continuación, seleccione el propiedad de dominio.  
  
    2.  En la ventana Propiedades, establezca **es la clave de Moniker** a `true`.  
  
-   \- o -  
  
     Crear una nueva clase de dominio mediante la **la clase de dominio denominado** herramienta.  
  
     Esta herramienta crea una nueva clase que tiene una propiedad de dominio denominada Name. El **es el nombre del elemento** y **es la clave de Moniker** se inicializan las propiedades de esta propiedad de dominio en `true`.  
  
-   \- o -  
  
     Crear una relación de herencia de la clase de dominio a otra clase que tiene una propiedad de clave de moniker.  
  
### <a name="avoiding-duplicate-monikers"></a>Evitar los Monikers duplicados  
 Si usa los monikers de clave completos, es posible que dos elementos de modelo de un usuario podrían tener el mismo valor en la propiedad de clave. Por ejemplo, si su DSL tiene una persona que tiene una propiedad de nombre de clase, el usuario puede establecer los nombres de dos elementos iguales. Aunque el modelo se pudo guardar en archivo, podría no volver a cargar correctamente.  
  
 Existen varios métodos que ayudan a evitar esta situación:  
  
-   Establecer **es el nombre del elemento**  =  `true` para la propiedad de dominio de clave. Seleccione la propiedad de dominio en el diagrama de definición de DSL y, a continuación, establezca el valor en la ventana Propiedades.  
  
     Cuando el usuario crea una nueva instancia de la clase, este valor hace que la propiedad de dominio que se asigne automáticamente un valor diferente. El comportamiento predeterminado, agrega un número al final del nombre de clase. Esto no impide que el usuario cambia el nombre a un duplicado, pero resulta útil en el caso cuando el usuario no establece el valor antes de guardar el modelo.  
  
-   Habilitar la validación para el DSL. En el Explorador de DSL, seleccione Editor\Validation y establezca el **usa...**  propiedades a `true`.  
  
     Hay un método de validación generado automáticamente que se comprueba para las ambigüedades. El método está en el `Load` categoría de validación. Esto garantiza que el usuario se le avisará que podría no ser posible volver a abrir el archivo.  
  
     Para obtener más información, consulte [validación en los lenguajes específicos de dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
### <a name="moniker-paths-and-qualifiers"></a>Las rutas de acceso de moniker y calificadores  
 Un moniker de la clave completo termina con la clave de moniker y tiene como prefijo el moniker de su entidad primaria en el árbol de incrustación. Por ejemplo, si el moniker de un álbum es:  
  
```  
<albumMoniker title="/My Favorites/Jazz after Teatime" />  
  
```  
  
 A continuación, podría ser una de las canciones del álbum:  
  
```  
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
```  
  
 Sin embargo, si álbumes se hace referencia al Id. en su lugar, a continuación, los monikers sería como sigue:  
  
```  
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />  
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />  
```  
  
 Tenga en cuenta que, dado un GUID es único, nunca viene precedida por el moniker de su elemento primario.  
  
 Si sabe que una propiedad concreta de dominio siempre tendrá un valor único dentro de un modelo, puede establecer **es el calificador de Moniker** a `true` para esa propiedad. Esto provocará que se usará como calificador, sin utilizar el moniker del elemento primario. Por ejemplo, si establece ambos **es el calificador de Moniker** y **es la clave de Moniker** para la propiedad de dominio de título de la clase de álbum, nombre o el identificador del modelo no se usa en los monikers de álbum y su incrustado elementos secundarios:  
  
```  
<albumMoniker name="Jazz after Teatime" />  
<songMoniker title="/Jazz after Teatime/Hot tea" />  
  
```  
  
## <a name="customizing-the-structure-of-the-xml"></a>Personalización de la estructura de XML  
 Para realizar las siguientes personalizaciones, expanda el **comportamiento de serialización Xml** nodo en el Explorador de DSL. En una clase de dominio, expanda el nodo de datos de elemento para ver la lista de propiedades y relaciones que se obtienen en esta clase. Seleccione una relación y ajuste las opciones en la ventana Propiedades.  
  
-   Establecer **omite el elemento** en true para omitir el nodo de rol de origen, dejando solo en la lista de elementos de destino. No debe establecer esta opción si no hay más de una relación entre las clases de origen y de destino.  
  
    ```  
  
    <familyTreeModel ...>  
      <!-- The following node is omitted by using Omit Element: -->  
      <!-- <people> -->  
        <person name="Henry VIII" .../>  
        <person name="Elizabeth I" .../>  
      <!-- </people> -->  
    </familyTreeModel>  
  
    ```  
  
-   Establecer **usar el formulario completo** para incrustar los nodos de destino en los nodos que representan las instancias de relación. Esta opción se establece automáticamente al agregar las propiedades de dominio a una relación de dominio.  
  
    ```  
  
    <familyTreeModel ...>  
      <people>  
        <!-- The following node is inserted by using Use Full Form: -->  
        <familyTreeModelHasPeople myRelationshipProperty="x1">  
          <person name="Henry VIII" .../>  
        </familyTreeModelHasPeople>  
        <familyTreeModelHasPeople myRelationshipProperty="x2">  
          <person name="Elizabeth I" .../>  
        </familyTreeModelHasPeople>  
      </people>  
    </familyTreeModel>  
  
    ```  
  
-   Establecer **representación** = **elemento** tener una propiedad de dominio que se guarda como un elemento en lugar de como un valor de atributo.  
  
    ```  
    <person name="Elizabeth I" birthYear="1533">  
      <deathYear>1603</deathYear>  
    </person>  
    ```  
  
-   Para cambiar el orden en que se serializan los atributos y relaciones, haga clic en un elemento bajo el elemento de datos y usar el **Subir** o **Bajar** comandos de menú.  
  
## <a name="major-customization-using-program-code"></a>Principal personalización mediante código de programa  
 Puede reemplazar partes o todos los algoritmos de serialización.  
  
 Se recomienda que revise atentamente el código en **Dsl\Generated Code\Serializer.cs** y **SerializationHelper.cs**.  
  
#### <a name="to-customize-the-serialization-of-a-particular-class"></a>Para personalizar la serialización de una clase determinada  
  
1.  Establecer **Is Custom** en el nodo de esa clase en **comportamiento de serialización Xml**.  
  
2.  Transformar todas las plantillas, compile la solución e investigar los errores de compilación resultante. Comentarios cerca de cada error explican qué código debe proporcionar.  
  
#### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Para proporcionar su propia serialización para el modelo completo  
  
1.  Invalidar métodos en Dsl\GeneratedCode\SerializationHelper.cs  
  
## <a name="options-in-xml-serialization-behavior"></a>Opciones de comportamiento de serialización Xml  
 En el Explorador de DSL, el nodo de comportamiento de serialización Xml contiene un nodo secundario para cada clase de dominio, relación, forma, conector y clase de diagrama. En cada uno de esos nodos es una lista de propiedades y relaciones con origen en ese elemento. Las relaciones se representan en sí mismas y en sus clases de origen.  
  
 En la tabla siguiente resume las opciones que se pueden establecer en esta sección de la definición de DSL. En cada caso, seleccione un elemento en el Explorador de DSL y establezca las opciones en la ventana Propiedades.  
  
### <a name="xml-class-data"></a>Datos XML (clase)  
 Estos elementos se encuentran en el Explorador de DSL en **Behavior\Class datos de serialización de Xml**.  
  
|||  
|-|-|  
|Property|Descripción|  
|Tiene el esquema de elemento personalizado|Si es True, indica que la clase de dominio tiene un esquema de elemento personalizado|  
|Es personalizado|Establezca esta opción en **True** si desea escribir su propio código de serialización y deserialización para esta clase de dominio.<br /><br /> Compile la solución e investigue los errores para conocer instrucciones detalladas.|  
|Clase de dominio|Clase de dominio al que se aplica este nodo de datos de clase. Sólo lectura.|  
|Nombre del elemento|Nombre de nodo de XML para los elementos de esta clase. El valor predeterminado es una versión en minúsculas del nombre de clase de dominio.|  
|Nombre del atributo de moniker|Nombre del atributo utilizado en los elementos del moniker para contener la referencia. Si está en blanco, se usa el nombre de la propiedad de clave o identificador.<br /><br /> En este ejemplo, es "name":  `<personMoniker name="/Mike Nash"/>`|  
|Nombre de elemento de moniker|Nombre del elemento xml utilizado para los monikers que hacen referencia a elementos de esta clase.<br /><br /> El valor predeterminado es una versión en minúsculas del nombre de clase lleva el sufijo "Moniker". Por ejemplo: `personMoniker`.|  
|Nombre de tipo de moniker|Nombre del tipo xsd generado para los monikers para los elementos de esta clase. Es el esquema XSD en **Dsl\Generated código\\\*Schema.xsd**|  
|Serializar Id.|Si es True, el GUID del elemento se incluye en el archivo. Esto debe ser true si no hay ninguna propiedad que está marcado como **es la clave de Moniker** y el DSL define las relaciones de referencia a esta clase.|  
|Nombre de tipo|Nombre del tipo xml generado en xsd a partir de la clase de dominio designada.|  
|Notas|Notas informales asociadas a este elemento|  
  
### <a name="xml-property-data"></a>Datos de la propiedad de XML  
 Los nodos de propiedad de XML se encuentran en los nodos de la clase.  
  
|||  
|-|-|  
|Property|Descripción|  
|Propiedad de dominio|Propiedad a la que se aplican los datos de configuración de serialización xml. Sólo lectura.|  
|Es la clave de Moniker|Si es True, la propiedad se utiliza como clave para crear monikers que hacen referencia a las instancias de esta clase de dominio.|  
|Es el calificador de Moniker|Si es True, la propiedad se utiliza para crear el calificador en monikers. Si es false, y si no se cumple para esta clase de dominio SerializeId, monikers están calificados por el moniker del elemento primario en el árbol de incrustación.|  
|Representación|Si el atributo, la propiedad se serializa como un atributo xml; Si el elemento, es serializado como un elemento; Si omite, no es serializar.|  
|Nombre XML|Nombre usado para el atributo o elemento xml que representa la propiedad. De forma predeterminada, esto es una versión en minúsculas del nombre de propiedad del dominio.|  
|Notas|Notas informales asociadas a este elemento|  
  
### <a name="xml-role-data"></a>Datos de las funciones de XML  
 Nodos de datos de rol se encuentran en los nodos de la clase de origen.  
  
|Property|Descripción|  
|--------------|-----------------|  
|Tiene Moniker personalizado|Establézcalo en true si desea proporcionar su propio código para generar y resolver los monikers que atraviesan esta relación.<br /><br /> Para obtener instrucciones detalladas, compile la solución y, a continuación, haga doble clic en los mensajes de error.|  
|Relación de dominio|Especifica la relación para que estas opciones se aplican. Sólo lectura.|  
|Omite el elemento|Si es true, se omite el nodo XML que se corresponde con el rol de origen desde el esquema.<br /><br /> Si hay más de una relación entre las clases de origen y destino, este nodo de rol se distingue entre los vínculos que pertenecen a las dos relaciones. Por lo tanto, se recomienda no establezca esta opción en este caso.|  
|Nombre de elemento de rol|Especifica el nombre del elemento XML que se deriva de la función de origen. El valor predeterminado es el nombre de propiedad de rol.|  
|Usar el formulario completo|Si es true, cada elemento de destino o moniker se incluyen en un nodo XML que representa la relación. Esto se debe establecer en true si la relación tiene sus propias propiedades de dominio.|  
  
## <a name="see-also"></a>Vea también  
 [Navegar y actualizar un modelo en el código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)



