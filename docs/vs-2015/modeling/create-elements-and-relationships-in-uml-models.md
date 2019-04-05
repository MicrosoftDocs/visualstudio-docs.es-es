---
title: Crear elementos y relaciones en modelos UML | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: cae81d32-8cc7-4f7c-9f00-20119952bc51
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4b31faa7c71a0f4072d922528a1abc4d040e7dae
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "59001968"
---
# <a name="create-elements-and-relationships-in-uml-models"></a>Crear elementos y relaciones en modelos UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el código de programa de una extensión de Visual Studio, puede crear y eliminar elementos y relaciones.  
  
## <a name="create-a-model-element"></a>Crear un elemento de modelo  
  
### <a name="namespace-imports"></a>Importaciones de espacio de nombres  
 Incluya las siguientes instrucciones `using`:  
  
 Los métodos de creación se definen como métodos de extensión en este espacio de nombres:  
  
 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
### <a name="obtain-the-owner-of-the-element-you-want-to-create"></a>Obtener el propietario del elemento que se desea crear  
 Un modelo conforma un único árbol, de modo que todos los elementos, a excepción de la raíz del modelo, tienen un propietario. La raíz del modelo es de tipo `IModel`, que es un tipo de `IPackage`.  
  
 Si está creando un elemento que va a aparecer en un diagrama determinado, por ejemplo, en el diagrama actual del usuario, normalmente deberá crearlo en el paquete que está vinculado a ese diagrama. Por ejemplo:  
  
```  
IPackage linkedPackage = Context.CurrentDiagram.Element as IPackage;  
```  
  
 En esta tabla se resumen los propietarios de los elementos comunes del modelo:  
  
|Elemento que se va a crear|Propietario|  
|---------------------------|-----------|  
|`IActor, IUseCase, IComponent, IClass, IInterface, IEnumeration`<br /><br /> `IActivity, IInteraction`|`IPackage, IModel`|  
|`IAttribute, IOperation`|`IClass, IInterface`|  
|`IPart, IPort`|`IComponent`|  
|`IAction, IObjectNode`|`IActivity`|  
|`ILifeline, IMessage, ICombinedFragment`|`IInteraction`|  
  
### <a name="invoke-the-create-method-on-the-owner"></a>Invocar el método Create en el propietario  
 El nombre del método tiene el formato: `Create`*OwnedType*`()`. Por ejemplo:  
  
```  
IUseCase usecase1 = linkedPackage.CreateUseCase();  
```  
  
 Algunos tipos tienen métodos de creación más complejos, especialmente en los diagramas de secuencia. Consulte [diagramas de secuencia UML editar mediante la API de UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
 Con algunos tipos de elemento, puede usar `SetOwner(newOwner)` para cambiar el propietario de un elemento durante su vigencia.  
  
### <a name="set-the-name-and-other-properties"></a>Establecer el nombre y otras propiedades  
  
```  
usecase1.Name = "user logs in";  
```  
  
### <a name="example"></a>Ejemplo  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.Uml.Extensions;  
...  
 void InstantiateObserverPattern (IPackage package, string namePrefix)  
 {    IInterface observer = package.CreateInterface();  
      observer.Name = namePrefix + "Observer";  
      IOperation operation = observer.CreateOperation();  
      operation.Name = "Update";  
      IClass subject = package.CreateClass();  
      subject.Name = namePrefix + "Subject"; ...  
```  
  
## <a name="create-an-association"></a>Crear una asociación  
  
#### <a name="to-create-an-association"></a>Para crear una asociación  
  
1.  Obtenga el propietario de la asociación, que normalmente es el paquete o el modelo que contienen el extremo de origen de la relación.  
  
2.  Invoque el método Create necesario en el propietario.  
  
3.  Establezca las propiedades de la relación, como su nombre.  
  
     Por ejemplo:  
  
    ```  
    IAssociation association = subject.Package.CreateAssociation(subject, observer);  
    association .Name = "Observes";  
    ```  
  
4.  Establezca las propiedades de cada extremo de la relación. Siempre hay dos `MemberEnds`. Por ejemplo:  
  
    ```  
    association .MemberEnds[0].Name = "subject";   // role name  
    association .MemberEnds[1].Name = "observers"; // role name  
    association .MemberEnds[1].SetBounds("0..*");           
                // multiplicity defaults to "1"  
    association.MemberEnds[0].Aggregation = AggregationKind.Composite;  
    ```  
  
## <a name="create-a-generalization"></a>Crear una generalización  
  
```  
IGeneralization generalization =   
  subclass.CreateGeneralization(superClass);  
```  
  
## <a name="delete-an-element-relationship-or-generalization-from-the-model"></a>Eliminar un elemento, relación o generalización del modelo  
  
```  
anElement.Delete();  
```  
  
 Cuando se elimina un elemento de un modelo:  
  
-   También se eliminan todas las relaciones que tiene vinculadas.  
  
-   También se eliminan todas las formas que lo representan en un diagrama.  
  
## <a name="see-also"></a>Vea también  
 [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Mostrar un modelo UML en diagramas](../modeling/display-a-uml-model-on-diagrams.md)
