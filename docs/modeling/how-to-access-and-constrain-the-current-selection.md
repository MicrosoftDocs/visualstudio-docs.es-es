---
title: 'Cómo: Tener acceso y restringir una selección'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1f5aaa106e00f9b10eb88892bcc978b92a01c79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545696"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Cómo: Tener acceso y restringir una selección

Al escribir un controlador de comandos o gestos para su lenguaje específico del dominio, puede determinar en qué elemento hizo clic con el botón derecho del usuario. También puede impedir que se seleccionen algunas formas o campos. Por ejemplo, puede organizar que cuando el usuario hace clic en un elemento Decorator de icono, en su lugar se selecciona la forma que lo contiene. Restringir la selección de esta manera reduce el número de controladores que se deben escribir. También facilita al usuario, que puede hacer clic en cualquier parte de la forma sin tener que evitar el elemento Decorator.

## <a name="access-the-current-selection-from-a-command-handler"></a>Obtener acceso a la selección actual desde un controlador de comandos

La clase de conjunto de comandos para un lenguaje específico del dominio contiene los controladores de comandos de los comandos personalizados. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase, de la que se deriva la clase de conjunto de comandos para un lenguaje específico del dominio, proporciona algunos miembros para tener acceso a la selección actual.

Dependiendo del comando, es posible que el controlador de comandos necesite la selección en el diseñador de modelos, en el explorador de modelos o en la ventana activa.

### <a name="to-access-selection-information"></a>Para tener acceso a la información de selección

1. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase define los siguientes miembros que se pueden utilizar para tener acceso a la selección actual.

    |Member|Descripción|
    |-|-|
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Devuelve `true` si alguno de los elementos seleccionados en el diseñador de modelos es una forma de compartimiento; de lo contrario, `false` .|
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Devuelve `true` si el diagrama está seleccionado en el diseñador de modelos; de lo contrario, `false` .|
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Devuelve `true` si hay exactamente un elemento seleccionado en el diseñador de modelos; de lo contrario, `false` .|
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Devuelve `true` si hay exactamente un elemento seleccionado en la ventana activa; de lo contrario, `false` .|
    |Propiedad<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Obtiene una colección de solo lectura de los elementos seleccionados en el diseñador de modelos.|
    |Propiedad<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Obtiene una colección de solo lectura de los elementos seleccionados en la ventana activa.|
    |Propiedad<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Obtiene el elemento primario de la selección en el diseñador de modelos.|
    |Propiedad<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Obtiene el elemento primario de la selección en la ventana activa.|

2. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> propiedad de la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase proporciona acceso al <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> objeto que representa la ventana del diseñador de modelos y proporciona acceso adicional a los elementos seleccionados en el diseñador de modelos.

3. Además, el código generado define una propiedad de ventana de herramientas del explorador y una propiedad de selección del explorador en la clase de conjunto de comandos para el lenguaje específico del dominio.

    - La propiedad de la ventana de herramientas del explorador devuelve una instancia de la clase de ventana de herramientas del explorador para el lenguaje específico del dominio. La clase de ventana de herramientas del explorador se deriva de la <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> clase y representa el explorador de modelos para el lenguaje específico del dominio.

    - La `ExplorerSelection` propiedad devuelve el elemento seleccionado en la ventana Explorador de modelos para el lenguaje específico del dominio.

## <a name="determine-which-window-is-active"></a>Determinar qué ventana está activa

La <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> interfaz contiene los miembros que proporcionan acceso al estado de selección actual en el shell. Puede obtener un <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> objeto de la clase de paquete o la clase de conjunto de comandos para el lenguaje específico del dominio a través de la `MonitorSelection` propiedad definida en la clase base de cada. La clase de paquete se deriva de la <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> clase y la clase de conjunto de comandos se deriva de la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Para determinar desde un controlador de comandos qué tipo de ventana está activa

1. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> propiedad de la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase devuelve un <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> objeto que proporciona acceso al estado de selección actual en el shell.

2. La <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> propiedad de la <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> interfaz obtiene el contenedor de selección activo, que puede ser diferente de la ventana activa.

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

## <a name="constrain-the-selection"></a>Restringir la selección

Al agregar reglas de selección, puede controlar qué elementos se seleccionan cuando el usuario selecciona un elemento en el modelo. Por ejemplo, para permitir que el usuario trate un número de elementos como una sola unidad, puede usar una regla de selección.

### <a name="to-create-a-selection-rule"></a>Para crear una regla de selección

1. Crear un archivo de código personalizado en el proyecto DSL

2. Defina una clase de regla de selección que se derive de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> clase.

3. Invalide el <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> método de la clase de regla de selección para aplicar los criterios de selección.

4. Agregue una definición de clase parcial para la clase ClassDiagram al archivo de código personalizado.

     La `ClassDiagram` clase se deriva de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> clase y se define en el archivo de código generado, Diagram.CS, en el proyecto de DSL.

5. Invalide la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> propiedad de la `ClassDiagram` clase para devolver la regla de selección personalizada.

     La implementación predeterminada de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> propiedad obtiene un objeto de regla de selección que no modifica la selección.

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

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>