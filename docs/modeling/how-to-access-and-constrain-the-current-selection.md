---
title: 'Cómo: Tener acceso y restringir una selección'
description: Obtenga información sobre cómo puede determinar en qué elemento hizo clic el usuario al escribir un comando o un controlador de gestos para el lenguaje específico del dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 28d0f99743535965b3cf203d461fac5d0193607c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386610"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Cómo: Tener acceso y restringir una selección

Al escribir un controlador de comandos o gestos para el lenguaje específico del dominio, puede determinar en qué elemento hizo clic el usuario con el botón derecho. También puede evitar que se seleccionen algunas formas o campos. Por ejemplo, puede organizar que cuando el usuario hace clic en un decorador de iconos, la forma que lo contiene se selecciona en su lugar. Restringir la selección de esta manera reduce el número de controladores que tiene que escribir. También facilita al usuario, que puede hacer clic en cualquier lugar de la forma sin tener que evitar el decorador.

## <a name="access-the-current-selection-from-a-command-handler"></a>Acceso a la selección actual desde un controlador de comandos

La clase de conjunto de comandos para un lenguaje específico del dominio contiene los controladores de comandos para los comandos personalizados. La clase , de la que deriva la clase de conjunto de comandos para un lenguaje específico de dominio, proporciona algunos miembros para acceder <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> a la selección actual.

Dependiendo del comando, el controlador de comandos puede necesitar la selección en el diseñador de modelos, el explorador de modelos o la ventana activa.

### <a name="to-access-selection-information"></a>Para acceder a la información de selección

1. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase define los siguientes miembros que se pueden usar para tener acceso a la selección actual.

    |Miembro|Descripción|
    |-|-|
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Devuelve `true` si alguno de los elementos seleccionados en el diseñador de modelos es una forma de compartimiento; de lo contrario, `false` .|
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Devuelve `true` si el diagrama está seleccionado en el diseñador de modelos; de lo contrario, `false` .|
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Devuelve `true` si se selecciona exactamente un elemento en el diseñador de modelos; de lo contrario, `false` .|
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Devuelve `true` si se selecciona exactamente un elemento en la ventana activa; de lo contrario, `false` .|
    |Propiedad <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Obtiene una colección de solo lectura de los elementos seleccionados en el diseñador de modelos.|
    |Propiedad <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Obtiene una colección de solo lectura de los elementos seleccionados en la ventana activa.|
    |Propiedad <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Obtiene el elemento principal de la selección en el diseñador de modelos.|
    |Propiedad <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Obtiene el elemento principal de la selección en la ventana activa.|

2. La propiedad de la clase proporciona acceso al objeto que representa la ventana del diseñador de modelos y proporciona acceso adicional a los elementos seleccionados <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> en el diseñador de <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> modelos.

3. Además, el código generado define una propiedad de ventana de herramientas del explorador y una propiedad de selección de explorador en la clase de conjunto de comandos para el lenguaje específico del dominio.

    - La propiedad de ventana de herramientas del explorador devuelve una instancia de la clase de ventana de herramientas del explorador para el lenguaje específico del dominio. La clase de ventana de herramientas del explorador deriva de <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> la clase y representa el explorador de modelos para el lenguaje específico del dominio.

    - La `ExplorerSelection` propiedad devuelve el elemento seleccionado en la ventana del explorador de modelos para el lenguaje específico del dominio.

## <a name="determine-which-window-is-active"></a>Determinar qué ventana está activa

La <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> interfaz contiene miembros que proporcionan acceso al estado de selección actual en el shell. Puede obtener un objeto de la clase de paquete o la clase de conjunto de comandos para el lenguaje específico del dominio a través de la propiedad definida en la <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> clase base de cada `MonitorSelection` uno. La clase de paquete se deriva de la clase y la clase de conjunto de <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> comandos se deriva de la clase <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> .

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Para determinar desde un controlador de comandos qué tipo de ventana está activo

1. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> propiedad de la clase devuelve un objeto que proporciona acceso al estado de selección actual en el <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> shell.

2. La <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> propiedad de la interfaz obtiene el contenedor de selección <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> activo, que puede ser diferente de la ventana activa.

3. Agregue las siguientes propiedades a la clase de conjunto de comandos para el lenguaje específico del dominio a fin de determinar qué tipo de ventana está activo.

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

Al agregar reglas de selección, puede controlar qué elementos se seleccionan cuando el usuario selecciona un elemento en el modelo. Por ejemplo, para permitir que el usuario trate varios elementos como una sola unidad, puede usar una regla de selección.

### <a name="to-create-a-selection-rule"></a>Para crear una regla de selección

1. Creación de un archivo de código personalizado en el proyecto DSL

2. Defina una clase de regla de selección que se derive de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> clase .

3. Invalide <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> el método de la clase de regla de selección para aplicar los criterios de selección.

4. Agregue una definición de clase parcial para la clase ClassDiagram al archivo de código personalizado.

     La clase se deriva de la clase y se define en el archivo de código `ClassDiagram` <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> generado, Diagram.cs, en el proyecto DSL.

5. Invalide <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> la propiedad de la clase para devolver la regla de selección `ClassDiagram` personalizada.

     La implementación predeterminada de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> propiedad obtiene un objeto de regla de selección que no modifica la selección.

### <a name="example"></a>Ejemplo

El siguiente archivo de código crea una regla de selección que expande la selección para incluir todas las instancias de cada una de las formas de dominio que se seleccionaron inicialmente.

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