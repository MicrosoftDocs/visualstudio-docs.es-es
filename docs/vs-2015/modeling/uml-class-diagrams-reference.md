---
title: 'UML Class Diagrams: Reference | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da4e0e3bab904b660f3d843e105b7d256a63a1b5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297219"
---
# <a name="uml-class-diagrams-reference"></a>Diagramas de clases de UML: Referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En los diagramas de clases de UML se describen el objeto y las estructuras de información que se usan en la aplicación, tanto de forma interna como en la comunicación con los usuarios. Esta información se describe sin hacer referencia a ninguna implementación concreta. Las clases y relaciones se pueden implementar de muchas maneras, por ejemplo, en tablas de bases de datos, en nodos XML o en composiciones de objetos de software.

> [!NOTE]
> En este tema se analizan los diagramas de clases de UML. Hay otro tipo de diagrama de clases, el diagrama de clases de .NET, que se usa para visualizar el código de programa. For more information, see [Designing and Viewing Classes and Types](https://go.microsoft.com/fwlink/?LinkId=142231).

 To create a UML class diagram, on the **Architecture** menu, choose **New UML or Layer Diagram**. For more information about how to draw UML class diagrams, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md). For more information about how to create and draw modeling diagrams, see [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-class-diagrams"></a>Lectura de diagramas de clases
 En la tabla de esta sección se describen los elementos que se pueden ver en un diagrama de clases UML. Para obtener información sobre las propiedades de estos elementos, vea los temas siguientes:

- [Propiedades de los tipos de diagramas de clases de UML](../modeling/properties-of-types-on-uml-class-diagrams.md)

- [Propiedades de los atributos de diagramas de clases de UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Propiedades de las operaciones de diagramas de clases de UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Propiedades de las asociaciones de diagramas de clases de UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)

  ![Three classes showing relationships and properties](../modeling/media/uml-classovreading.png "UML_ClassOvReading")

| **Shape** |       **Element**        |                                                                                                                                                             **Descripción**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **Clase**         |                                                           Definición de objetos que comparten determinadas características estructurales y de comportamiento. For more information, see [Properties of types on UML class diagrams](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1     |        Clasificador        |                                                                                                             Nombre general de una clase, interfaz o enumeración. Los componentes, casos de uso y actores también son clasificadores.                                                                                                             |
|     2     | Control de contraer o expandir |                                                                                         Si no puede ver los detalles de un clasificador, haga clic en el botón de expansión situado en la parte superior izquierda del clasificador. También tendrá que hacer clic en el icono [+] de cada segmento.                                                                                         |
|     3     |      **Attribute**       |   Valor con tipo que se asocia a cada instancia de un clasificador.<br /><br /> To add an attribute, click the **Attributes** section and then press **ENTER**. Escriba la firma del atributo. For more information, see [Properties of attributes on UML class diagrams](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **Operation**       | Método o función que pueden realizar las instancias de un clasificador. To add an operation, click the **Operations** section and then press **ENTER**. Escriba la firma de la operación. For more information, see [Properties of operations on UML class diagrams](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **Association**      |                                                                  Relación entre los miembros de dos clasificadores. For more information, see [Properties of associations on UML class diagrams](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5a     |     **Agregación**      |                                                                                                    Asociación que representa una relación de propiedad compartida. The **Aggregation** property of the owner role is set to **Shared**.                                                                                                     |
|    5b     |     **Composition**      |                                                                                                      Asociación que representa una relación parte/todo. The **Aggregation** property of the owner role is set to **Composite**.                                                                                                      |
|     6     |   **Association Name**   |                                                                                                                                         Nombre de una asociación. Puede dejarse vacío.                                                                                                                                          |
|     7     |      **Role Name**       |                       Nombre de un rol, es decir, un extremo de una asociación. Puede usarse para hacer referencia al objeto asociado. En la ilustración anterior, cualquier pedido `O`, tiene `O.ChosenMenu` como menú asociado.<br /><br /> Cada rol tiene sus propias propiedades, que se muestran bajo las propiedades de la asociación.                       |
|     8     |     **Multiplicity**     |                                         Indica cuántos de los objetos de este extremo se pueden vincular a cada objeto del otro. En el ejemplo, cada pedido debe vincularse exactamente a un solo menú.<br /><br /> **\\** \* means that there is no upper limit to the number of links that can be made.                                         |
|     9     |    **Generalization**    |  The *specific* classifier inherits part of its definition from the *general* classifier. El clasificador general se encuentra en el extremo del conector de la flecha. El clasificador específico hereda los atributos, las asociaciones y las operaciones.<br /><br /> Use the **Inheritance** tool to create a generalization between two classifiers.   |

 ![Package containing interface and enumeration](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")

|Forma|Elemento|Descripción|
|-----------|-------------|-----------------|
|10|**Interface**|Definición de una parte del comportamiento externamente visible de un objeto. For more information, see [Properties of types on UML class diagrams](../modeling/properties-of-types-on-uml-class-diagrams.md).|
|11|**Enumeration**|Clasificador que se compone de un conjunto de valores literales.|
|12|**Paquete**|Grupo de clasificadores, asociaciones, acciones, líneas de vida, componentes y otros paquetes. En un diagrama de clases lógicas se muestra que los paquetes y clasificadores de miembros están incluidos dentro del paquete.<br /><br /> Names are scoped within packages so that **Class1** within **Package1** is distinct from **Class1** outside that package. The name of the package appears as part of the **Qualified Name** properties of its contents.<br /><br /> You can set the **Linked Package** property of any UML diagram to refer to a package. Todos los elementos que cree en ese diagrama formarán parte del paquete. They will appear under the package in **UML Model Explorer**.|
|13|**Import**|Relación entre paquetes que indica que un paquete incluye todas las definiciones de otro.|
|14|**Dependency**|La definición o implementación del clasificador dependiente podría cambiar si el clasificador situado en el extremo con la punta de flecha se modifica.|

 ![Realization shown with conector and lollipop](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")

|Forma|**Element**|Descripción|
|-----------|-----------------|-----------------|
|15|**Realization**|La clase implementa las operaciones y los atributos definidos por la interfaz.<br /><br /> Use the **Inheritance** tool to create a realization between a class and an interface.|
|16|**Realization**|Presentación alternativa de la misma relación. La etiqueta del símbolo circular identifica la interfaz.<br /><br /> Para crear esta presentación, seleccione una relación de realización existente. Aparecerá una etiqueta de acción cerca de la asociación. Click the action tag, and then click **Show as Lollipop**.|

## <a name="see-also"></a>Vea también
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md) [Properties of types on UML class diagrams](../modeling/properties-of-types-on-uml-class-diagrams.md) [Properties of attributes on UML class diagrams](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [Properties of operations on UML class diagrams](../modeling/properties-of-operations-on-uml-class-diagrams.md) [Properties of associations on UML class diagrams](../modeling/properties-of-associations-on-uml-class-diagrams.md)
