---
title: Vincular actualizaciones del modelo UML mediante transacciones | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 640217b9ee9a8cb51ed11931d0d66b2c98e0a165
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999589"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>Vincular actualizaciones del modelo UML mediante transacciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al definir una extensión para los diseñadores de UML en Visual Studio, puede agrupar diversos cambios en una única transacción denominada una *contexto de deshacer vinculada*. Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 De forma predeterminada, cada modificación que el código realiza en un modelo puede deshacerla por otro lado el usuario. Por ejemplo, si define un comando de menú que intercambia los nombres de dos clases de UML, un usuario podría invocar este comando y, a continuación, ejecutar una sola fase de reversión. Esto desharía el cambio efectuado en un nombre, pero no el efectuado en el otro, lo que dejaría el modelo en un estado imprevisto.  
  
 Para evitar esto, el código puede realizar una serie de cambios dentro de una transacción. De este modo, el usuario percibe los cambios como si se tratara de una única modificación. Si posteriormente se ejecutara el comando Deshacer, se desharía la serie completa de cambios.  
  
 Otra ventaja adicional es que el código puede deshacer un conjunto parcialmente completo de cambios iniciando una excepción o anulando la transacción.  
  
## <a name="to-group-changes-into-a-single-transaction"></a>Para agrupar los cambios en una única transacción  
 Asegúrese de que en las referencias del proyecto se incluye este ensamblado .NET:  
  
 **Microsoft.VisualStudio.Modeling.Sdk.[version].dll**  
  
 En la clase, declare una propiedad importada que tenga el tipo <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext>:  
  
 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`  
  
 `...`  
  
 `class … {`  
  
 `[Import]`  
  
 `public ILinkedUndoContext LinkedUndoContext { get; set; }`  
  
 En un método que modifique el modelo, agregue los cambios en una transacción:  
  
 `using (ILinkedUndoTransaction transaction =`  
  
 `LinkedUndoContext.BeginTransaction("my updates"))`  
  
 `{`  
  
 `// code to update model elements or shapes goes here`  
  
 `transaction.Commit();`  
  
 `}`  
  
 Tenga en cuenta lo siguiente:  
  
-   Siempre debe incluir `Commit()` al final de la transacción. Si una transacción se deshace antes de confirmarse, se revertirá. Es decir, se restaurará el estado que tenía el modelo al comienzo de la transacción.  
  
-   Si se produce una excepción que no se detecta en la transacción, se revertirá la transacción. Es una práctica habitual incluir el bloque `using` de la transacción en un bloque `try…catch`.  
  
-   Puede anidar transacciones.  
  
-   Puede proporcionar cualquier nombre, salvo un nombre en blanco, a `BeginTransaction()`.  
  
-   Estas transacciones solamente afectan al almacén de modelos de UML. Las transacciones de modelado no afectan: las variables, los almacenes externos, como los archivos y las bases de datos, los diagramas de capas y los modelos de código.  
  
## <a name="example"></a>Ejemplo  
  
```  
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
    using Microsoft.VisualStudio.Uml.Interfaces;  
    using Microsoft.VisualStudio.Uml.Classes;  
    using Microsoft.VisualStudio.Uml.Extensions;  
    using System.Linq;  
    using System.ComponentModel.Composition;  
 ...  
  [Import]  
  public ILinkedUndoContext LinkedUndoContext { get; set; }  
  
  /// <summary>  
  /// Swap the names of the currently selected elements.  
  /// </summary>  
  public void Execute(IMenuCommand command)  
  {  
    var selectedShapes =  
      Context.CurrentDiagram.GetSelectedShapes<IClassifier>();  
    if (selectedShapes.Count() < 2) return;  
    IClassifier firstElement = selectedShapes.First().Element;  
    IClassifier lastElement = selectedShapes.Last().Element;  
    string firstName = firstElement.Name;  
    // Perform changes inside a transaction so that undo  
    // works as a single change.  
    using (ILinkedUndoTransaction transaction =   
      LinkedUndoContext.BeginTransaction("Swap names"))  
    {  
        firstElement.Name = lastElement.Name;  
        lastElement.Name = firstName;  
        transaction.Commit();  
    }  
 }  
```  
  
## <a name="see-also"></a>Vea también  
 [Programación con la API de UML](../modeling/programming-with-the-uml-api.md)   
 [Definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)
