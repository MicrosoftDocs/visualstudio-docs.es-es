---
title: "Cómo: obtener acceso y restringir la selección actual | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 81036e04abc9eac2cbed2879839e95cce52166fc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Cómo: Tener acceso y restringir una selección
Cuando se escribe un controlador de comandos o gestos para su lenguaje específico de dominio, puede determinar qué elemento con el botón secundario del usuario. También puede evitar algunas formas o campos que se seleccione. Por ejemplo, puede organizar que cuando el usuario hace clic en un elemento decorator de icono, en su lugar, se selecciona la forma que lo contiene. Restringir la selección de esta manera, reduce el número de controladores que se deben escribir. También resulta más fácil para el usuario, lo que hacer clic en cualquier parte en la forma sin tener que evitar el decorador.  
  
## <a name="accessing-the-current-selection-from-a-command-handler"></a>Obtiene acceso a la selección actual desde un controlador de comandos.  
 La clase de conjunto de comandos para un lenguaje específico de dominio contiene los controladores de comandos para los comandos personalizados. El <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> (clase), del que se deriva la clase de conjunto de comandos para un lenguaje específico de dominio, proporciona unos pocos miembros para tener acceso a la selección actual.  
  
 Dependiendo del comando, el controlador de comandos que tenga la selección en el Diseñador de modelos, el Explorador de modelos o en la ventana activa.  
  
#### <a name="to-access-selection-information"></a>Para obtener acceso a información sobre la selección  
  
1.  La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase define los miembros siguientes que pueden utilizarse para tener acceso a la selección actual.  
  
    |Miembro|Descripción|  
    |------------|-----------------|  
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Devuelve `true` si alguno de los elementos seleccionados en el Diseñador de modelos es una forma de compartimiento; en caso contrario, `false`.|  
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Devuelve `true` si el diagrama está seleccionada en el Diseñador de modelos; en caso contrario, `false`.|  
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Devuelve `true` si exactamente un elemento está seleccionado en el Diseñador de modelos; en caso contrario, `false`.|  
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Devuelve `true` si exactamente un elemento está seleccionado en la ventana activa; en caso contrario, `false`.|  
    |Propiedad <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Obtiene una colección de solo lectura de los elementos seleccionados en el Diseñador de modelos.|  
    |Propiedad <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Obtiene una colección de solo lectura de los elementos seleccionados en la ventana activa.|  
    |Propiedad <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Obtiene el elemento primario de la selección en el Diseñador de modelos.|  
    |Propiedad <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Obtiene el elemento primario de la selección de la ventana activa.|  
  
2.  El <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> propiedad de la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase proporciona acceso a la <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> objeto que representa la ventana del Diseñador de modelos y proporciona acceso adicional con los elementos seleccionados en el Diseñador de modelos.  
  
3.  Además, el código generado define una propiedad de ventana de herramienta de explorador y una propiedad de selección de explorador en el comando set (clase) para el lenguaje específico de dominio.  
  
    -   La propiedad de ventana de herramienta de explorador devuelve una instancia de la clase de ventana de herramienta de explorador para el lenguaje específico de dominio. La clase de ventana de herramienta de explorador que se deriva de la <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> clase y representa el Explorador de modelos para el lenguaje específico de dominio.  
  
    -   El `ExplorerSelection` propiedad devuelve el elemento seleccionado en la ventana del explorador de modelo para el lenguaje específico de dominio.  
  
## <a name="determining-which-window-is-active"></a>Determinar qué ventana está activa  
 El <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> contiene interfaz define los miembros que proporcionan acceso al estado de selección actual en el shell. Puede obtener un <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> objeto de la clase de paquete o la clase de conjunto de comandos para el lenguaje específico de dominio a través de la `MonitorSelection` propiedad definida en la clase base de cada uno. Deriva de la clase de paquete de la <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> clase y la clase de conjunto de comandos que se deriva de la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase.  
  
#### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Para determinar desde un controlador de comandos qué tipo de ventana está activo  
  
1.  El <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> propiedad de la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase devuelve una <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> objeto que proporciona acceso al estado de selección actual en el shell.  
  
2.  El <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> propiedad de la <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> interfaz obtiene el contenedor de selección activa, que puede ser diferente de la ventana activa.  
  
3.  Agregue que las siguientes propiedades para el comando set (clase) para su lenguaje específico de dominio para determinar qué tipo de ventana está activa.  
  
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
  
## <a name="constraining-the-selection"></a>Restringir la selección  
 Mediante la adición de reglas de selección, puede controlar qué elementos se seleccionan cuando el usuario selecciona un elemento en el modelo. Por ejemplo, para permitir que el usuario pueda tratar a un número de elementos como una sola unidad, puede usar una regla de selección.  
  
#### <a name="to-create-a-selection-rule"></a>Para crear una regla de selección  
  
1.  Cree un archivo de código personalizado en el proyecto DSL  
  
2.  Defina una clase de regla de selección que se deriva de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> clase.  
  
3.  Invalidar el <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> método de la clase de regla de selección para aplicar los criterios de selección.  
  
4.  Agregar una definición de clase parcial para la clase ClassDiagram al archivo de código personalizado.  
  
     El `ClassDiagram` clase se deriva de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> clase y se define en el archivo de código generado, Diagram.cs, en el proyecto DSL.  
  
5.  Invalidar el <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> propiedad de la `ClassDiagram` clase para devolver la regla de selección personalizada.  
  
     La implementación predeterminada de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> propiedad obtiene un objeto de regla de selección que no modifica la selección.  
  
### <a name="example"></a>Ejemplo  
 El archivo de código siguiente crea una regla de selección que se expande la selección para incluir todas las instancias de cada una de las formas de dominio que inicialmente se seleccionan.  
  
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
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>