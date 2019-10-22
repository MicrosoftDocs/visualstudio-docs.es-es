---
title: 'Cómo: obtener acceso y restringir la selección actual | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
ms.assetid: 2990981e-dfae-416f-b0d0-7197f1242dfa
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 00fa99ce9be158b2fe7b0bc4076817892a1b1ba9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646233"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Cómo: Tener acceso y restringir una selección
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al escribir un controlador de comandos o gestos para su lenguaje específico del dominio, puede determinar en qué elemento hizo clic con el botón derecho del usuario. También puede impedir que se seleccionen algunas formas o campos. Por ejemplo, puede organizar que cuando el usuario hace clic en un elemento Decorator de icono, en su lugar se selecciona la forma que lo contiene. Restringir la selección de esta manera reduce el número de controladores que se deben escribir. También facilita al usuario, que puede hacer clic en cualquier parte de la forma sin tener que evitar el elemento Decorator.

## <a name="accessing-the-current-selection-from-a-command-handler"></a>Obtener acceso a la selección actual desde un controlador de comandos
 La clase de conjunto de comandos para un lenguaje específico del dominio contiene los controladores de comandos de los comandos personalizados. La clase <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>, de la que se deriva la clase de conjunto de comandos para un lenguaje específico del dominio, proporciona algunos miembros para tener acceso a la selección actual.

 Dependiendo del comando, es posible que el controlador de comandos necesite la selección en el diseñador de modelos, en el explorador de modelos o en la ventana activa.

#### <a name="to-access-selection-information"></a>Para tener acceso a la información de selección

1. La clase <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> define los siguientes miembros que se pueden utilizar para tener acceso a la selección actual.

    |Miembro|Descripción|
    |------------|-----------------|
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Devuelve `true` si alguno de los elementos seleccionados en el diseñador de modelos es una forma de compartimiento. de lo contrario, `false`.|
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Devuelve `true` si el diagrama está seleccionado en el diseñador de modelos; de lo contrario, `false`.|
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Devuelve `true` si hay exactamente un elemento seleccionado en el diseñador de modelos; de lo contrario, `false`.|
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Devuelve `true` si hay exactamente un elemento seleccionado en la ventana activa; de lo contrario, `false`.|
    |Propiedad<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Obtiene una colección de solo lectura de los elementos seleccionados en el diseñador de modelos.|
    |Propiedad<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Obtiene una colección de solo lectura de los elementos seleccionados en la ventana activa.|
    |Propiedad<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Obtiene el elemento primario de la selección en el diseñador de modelos.|
    |Propiedad<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Obtiene el elemento primario de la selección en la ventana activa.|

2. La propiedad <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> de la clase <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> proporciona acceso al objeto <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> que representa la ventana del diseñador de modelos y proporciona acceso adicional a los elementos seleccionados en el diseñador de modelos.

3. Además, el código generado define una propiedad de ventana de herramientas del explorador y una propiedad de selección del explorador en la clase de conjunto de comandos para el lenguaje específico del dominio.

    - La propiedad de la ventana de herramientas del explorador devuelve una instancia de la clase de ventana de herramientas del explorador para el lenguaje específico del dominio. La clase de ventana de herramientas del explorador se deriva de la clase <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> y representa el explorador de modelos para el lenguaje específico del dominio.

    - La propiedad `ExplorerSelection` devuelve el elemento seleccionado en la ventana Explorador de modelos para el lenguaje específico del dominio.

## <a name="determining-which-window-is-active"></a>Determinar qué ventana está activa
 La interfaz <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> contiene define los miembros que proporcionan acceso al estado de selección actual en el shell. Puede obtener un objeto <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> de la clase Package o de la clase de conjunto de comandos para el lenguaje específico del dominio a través de la propiedad `MonitorSelection` definida en la clase base de cada. La clase de paquete deriva de la clase <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> y la clase de conjunto de comandos deriva de la clase <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

#### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Para determinar desde un controlador de comandos qué tipo de ventana está activa

1. La propiedad <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> de la clase <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> devuelve un objeto <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> que proporciona acceso al estado de selección actual en el shell.

2. La propiedad <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> de la interfaz <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> obtiene el contenedor de selección activo, que puede ser diferente de la ventana activa.

3. Agregue las siguientes propiedades a la clase de conjunto de comandos para el lenguaje específico del dominio para determinar el tipo de ventana que está activa.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constraining-the-selection"></a>Restricción de la selección
 Al agregar reglas de selección, puede controlar qué elementos se seleccionan cuando el usuario selecciona un elemento en el modelo. Por ejemplo, para permitir que el usuario trate un número de elementos como una sola unidad, puede usar una regla de selección.

#### <a name="to-create-a-selection-rule"></a>Para crear una regla de selección

1. Crear un archivo de código personalizado en el proyecto DSL

2. Defina una clase de regla de selección que se derive de la clase <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>.

3. Invalide el método <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> de la clase de regla de selección para aplicar los criterios de selección.

4. Agregue una definición de clase parcial para la clase ClassDiagram al archivo de código personalizado.

     La clase `ClassDiagram` se deriva de la clase <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> y se define en el archivo de código generado, Diagram.cs, en el proyecto DSL.

5. Invalide la propiedad <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> de la clase `ClassDiagram` para devolver la regla de selección personalizada.

     La implementación predeterminada de la propiedad <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> obtiene un objeto de regla de selección que no modifica la selección.

### <a name="example"></a>Ejemplo
 El siguiente archivo de código crea una regla de selección que amplía la selección para incluir todas las instancias de cada una de las formas de dominio que se seleccionaron inicialmente.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Vea también
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>
