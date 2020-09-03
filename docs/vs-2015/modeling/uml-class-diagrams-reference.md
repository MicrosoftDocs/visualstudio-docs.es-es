---
title: 'Diagramas de clases de UML: referencia | Microsoft Docs'
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
ms.openlocfilehash: 06e83e254cad77d4ede9716a18a51f6476fb51ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850180"
---
# <a name="uml-class-diagrams-reference"></a>Diagramas de clases de UML: Referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En los diagramas de clases de UML se describen el objeto y las estructuras de información que se usan en la aplicación, tanto de forma interna como en la comunicación con los usuarios. Esta información se describe sin hacer referencia a ninguna implementación concreta. Las clases y relaciones se pueden implementar de muchas maneras, por ejemplo, en tablas de bases de datos, en nodos XML o en composiciones de objetos de software.

> [!NOTE]
> En este tema se analizan los diagramas de clases de UML. Hay otro tipo de diagrama de clases, el diagrama de clases de .NET, que se usa para visualizar el código de programa. Para obtener más información, vea [diseñar y ver clases y tipos](https://msdn.microsoft.com/library/ab7aty24.aspx).

 Para crear un diagrama de clases de UML, en el menú **arquitectura** , elija **nuevo diagrama de UML o de capas**. Para obtener más información sobre cómo dibujar diagramas de clases UML, vea [diagramas de clases UML: instrucciones](../modeling/uml-class-diagrams-guidelines.md). Para obtener más información sobre cómo crear y dibujar diagramas de modelado, vea [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-class-diagrams"></a>Lectura de diagramas de clases
 En la tabla de esta sección se describen los elementos que se pueden ver en un diagrama de clases UML. Para obtener información sobre las propiedades de estos elementos, vea los temas siguientes:

- [Propiedades de los tipos de diagramas de clases de UML](../modeling/properties-of-types-on-uml-class-diagrams.md)

- [Propiedades de los atributos de diagramas de clases de UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Propiedades de las operaciones de diagramas de clases de UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Propiedades de las asociaciones de diagramas de clases de UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)

  ![Tres clases mostrando relaciones y propiedades](../modeling/media/uml-classovreading.png "UML_ClassOvReading")

| **Forma** |       **Element**        |                                                                                                                                                             **Descripción**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **Clase**         |                                                           Definición de objetos que comparten determinadas características estructurales y de comportamiento. Para obtener más información, vea [propiedades de tipos en diagramas de clases de UML](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1     |        Clasificador        |                                                                                                             Nombre general de una clase, interfaz o enumeración. Los componentes, casos de uso y actores también son clasificadores.                                                                                                             |
|     2     | Control de contraer o expandir |                                                                                         Si no puede ver los detalles de un clasificador, haga clic en el botón de expansión situado en la parte superior izquierda del clasificador. También tendrá que hacer clic en el icono [+] de cada segmento.                                                                                         |
|     3     |      **Atributo**       |   Valor con tipo que se asocia a cada instancia de un clasificador.<br /><br /> Para agregar un atributo, haga clic en la sección **atributos** y, a continuación, presione **entrar**. Escriba la firma del atributo. Para obtener más información, vea [propiedades de los atributos de diagramas de clases de UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **operación**       | Método o función que pueden realizar las instancias de un clasificador. Para agregar una operación, haga clic en la sección **operaciones** y, a continuación, presione **entrar**. Escriba la firma de la operación. Para obtener más información, vea [propiedades de las operaciones en diagramas de clases de UML](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **Asociación**      |                                                                  Relación entre los miembros de dos clasificadores. Para obtener más información, vea [propiedades de las asociaciones de diagramas de clases de UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5a     |     **Agregación**      |                                                                                                    Asociación que representa una relación de propiedad compartida. La propiedad **Aggregation** del rol Owner está establecida en **Shared**.                                                                                                     |
|    5b     |     **Composición**      |                                                                                                      Asociación que representa una relación parte/todo. La propiedad **Aggregation** del rol Owner está establecida en **composite**.                                                                                                      |
|     6     |   **Nombre de asociación**   |                                                                                                                                         Nombre de una asociación. Puede dejarse vacío.                                                                                                                                          |
|     7     |      **Nombre de rol**       |                       Nombre de un rol, es decir, un extremo de una asociación. Puede usarse para hacer referencia al objeto asociado. En la ilustración anterior, cualquier pedido `O`, tiene `O.ChosenMenu` como menú asociado.<br /><br /> Cada rol tiene sus propias propiedades, que se muestran bajo las propiedades de la asociación.                       |
|     8     |     **Multiplicidad**     |                                         Indica cuántos de los objetos de este extremo se pueden vincular a cada objeto del otro. En el ejemplo, cada pedido debe vincularse exactamente a un solo menú.<br /><br /> **\\**\* significa que no hay ningún límite superior para el número de vínculos que se pueden realizar.                                         |
|     9     |    **Generalización**    |  El clasificador *específico* hereda parte de su definición del clasificador *General* . El clasificador general se encuentra en el extremo del conector de la flecha. El clasificador específico hereda los atributos, las asociaciones y las operaciones.<br /><br /> Utilice la herramienta **herencia** para crear una generalización entre dos clasificadores.   |

 ![Paquete que contiene interfaz y enumeración](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")

|Forma|Elemento|Descripción|
|-----------|-------------|-----------------|
|10|**Interfaz**|Definición de una parte del comportamiento externamente visible de un objeto. Para obtener más información, vea [propiedades de tipos en diagramas de clases de UML](../modeling/properties-of-types-on-uml-class-diagrams.md).|
|11|**Enumeración**|Clasificador que se compone de un conjunto de valores literales.|
|12|**Paquete**|Grupo de clasificadores, asociaciones, acciones, líneas de vida, componentes y otros paquetes. En un diagrama de clases lógicas se muestra que los paquetes y clasificadores de miembros están incluidos dentro del paquete.<br /><br /> Los nombres están dentro del ámbito de los paquetes para que **Class1** dentro de **package1** sea distinto de **Class1** fuera de ese paquete. El nombre del paquete aparece como parte de las propiedades de **nombre completo** de su contenido.<br /><br /> Puede establecer la propiedad **paquete vinculado** de cualquier diagrama UML para que haga referencia a un paquete. Todos los elementos que cree en ese diagrama formarán parte del paquete. Aparecerán en el paquete, en el **Explorador de modelos UML**.|
|13|**Importar**|Relación entre paquetes que indica que un paquete incluye todas las definiciones de otro.|
|14|**Dependencia**|La definición o implementación del clasificador dependiente podría cambiar si el clasificador situado en el extremo con la punta de flecha se modifica.|

 ![Realización mostrada con conector y círculo](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")

|Forma|**Element**|Descripción|
|-----------|-----------------|-----------------|
|15|**Resolución**|La clase implementa las operaciones y los atributos definidos por la interfaz.<br /><br /> Utilice la herramienta **herencia** para crear una realización entre una clase y una interfaz.|
|16|**Resolución**|Presentación alternativa de la misma relación. La etiqueta del símbolo circular identifica la interfaz.<br /><br /> Para crear esta presentación, seleccione una relación de realización existente. Aparecerá una etiqueta de acción cerca de la asociación. Haga clic en la etiqueta de acción y, a continuación, haga clic en **Mostrar como círculo**.|

## <a name="see-also"></a>Consulte también
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md) [diagramas de clases UML: instrucciones](../modeling/uml-class-diagrams-guidelines.md) [propiedades de tipos en diagramas de clases de UML](../modeling/properties-of-types-on-uml-class-diagrams.md) [propiedades de los atributos de diagramas de clases de UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [propiedades de las operaciones de diagramas de clases de UML](../modeling/properties-of-operations-on-uml-class-diagrams.md) [propiedades de las asociaciones de diagramas de clases de UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)
