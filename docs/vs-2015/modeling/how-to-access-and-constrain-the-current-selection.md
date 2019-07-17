---
title: Procedimiento Tener acceso y restringir la selección actual | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
ms.assetid: 2990981e-dfae-416f-b0d0-7197f1242dfa
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c3f6d0d481b91f7c475a37d33d43d47aff69ac8d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181740"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Procedimiento Acceder a la selección actual y restringirla
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al escribir un controlador de comandos o gestos para su lenguaje específico de dominio, puede determinar qué elemento haga el usuario. También puede impedir que algunas formas o campos que se seleccione. Por ejemplo, puede organizar que cuando el usuario hace clic en un elemento decorator de icono, en su lugar, se selecciona la forma que lo contiene. Restringir la selección de esta manera reduce el número de controladores que se deben escribir. También resulta más fácil para el usuario, quien puede haga clic en la forma sin tener que evitar el decorador.  
  
## <a name="accessing-the-current-selection-from-a-command-handler"></a>Acceso a la selección actual desde un controlador de comandos  
 La clase de conjunto de comandos para un lenguaje específico de dominio contiene los controladores de comandos para los comandos personalizados. El <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> (clase), desde el que se deriva la clase de conjunto de comandos para un lenguaje específico de dominio proporciona algunos miembros para acceder a la selección actual.  
  
 Según el comando, el controlador de comandos que la selección en el Diseñador de modelos, el Explorador de modelos o la ventana activa.  
  
#### <a name="to-access-selection-information"></a>Para obtener acceso a información sobre la selección  
  
1. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase define los siguientes miembros que pueden utilizarse para tener acceso a la selección actual.  
  
    |Member|DESCRIPCIÓN|  
    |------------|-----------------|  
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Devuelve `true` si alguno de los elementos seleccionados en el Diseñador de modelos es una forma de compartimiento; en caso contrario, `false`.|  
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Devuelve `true` si el diagrama está seleccionado en el Diseñador de modelos; de lo contrario, `false`.|  
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Devuelve `true` si exactamente un elemento está seleccionado en el Diseñador de modelos; en caso contrario, `false`.|  
    |Método <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Devuelve `true` si exactamente un elemento está seleccionado en la ventana activa; en caso contrario, `false`.|  
    |Propiedad<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Obtiene una colección de solo lectura de los elementos seleccionados en el Diseñador de modelos.|  
    |Propiedad<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Obtiene una colección de solo lectura de los elementos seleccionados en la ventana activa.|  
    |Propiedad<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Obtiene el elemento primario de la selección en el Diseñador de modelos.|  
    |Propiedad<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Obtiene el elemento primario de la selección en la ventana activa.|  
  
2. El <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> propiedad de la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase proporciona acceso a la <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> objeto que representa la ventana del Diseñador de modelos y proporciona acceso adicional de los elementos seleccionados en el Diseñador de modelos.  
  
3. Además, el código generado define una propiedad de ventana de herramienta de explorador y una propiedad de selección del explorador en el comando set (clase) para el lenguaje específico del dominio.  
  
    - La propiedad de ventana de herramienta de explorador devuelve una instancia de la clase de ventana de herramienta de explorador del lenguaje específico de dominio. Deriva de la clase de ventana de herramienta de explorador el <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> clase y representa el Explorador de modelos para el lenguaje específico del dominio.  
  
    - El `ExplorerSelection` propiedad devuelve el elemento seleccionado en la ventana del explorador de modelos para el lenguaje específico del dominio.  
  
## <a name="determining-which-window-is-active"></a>Determinar qué ventana está activa  
 El <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> contiene la interfaz define los miembros que proporcionan acceso al estado de selección actual en el shell. Puede obtener un <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> objeto de la clase de paquete o la clase de conjunto de comandos para el lenguaje específico de dominio a través de la `MonitorSelection` definida en la clase base de cada propiedad. La clase de paquete que se deriva de la <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> deriva la clase y la clase de conjunto de comandos la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase.  
  
#### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Para determinar desde un controlador de comandos, ¿qué tipo de ventana está activa  
  
1. El <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> propiedad de la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> clase devuelve una <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> objeto que proporciona acceso al estado de selección actual en el shell.  
  
2. El <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> propiedad de la <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> interfaz obtiene el contenedor de selección activa, que puede ser diferente de la ventana activa.  
  
3. Agregue que las siguientes propiedades para el comando set (clase) para los lenguajes específicos de dominio para determinar qué tipo de ventana está activa.  
  
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
 Mediante la adición de reglas de selección, puede controlar qué elementos se seleccionan cuando el usuario selecciona un elemento en el modelo. Por ejemplo, para permitir al usuario tratar a un número de elementos como una sola unidad, puede usar una regla de selección.  
  
#### <a name="to-create-a-selection-rule"></a>Para crear una regla de selección  
  
1. Cree un archivo de código personalizado en el proyecto DSL  
  
2. Defina una clase de regla de selección que se deriva el <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> clase.  
  
3. Invalidar el <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> método de la clase de regla de selección para aplicar los criterios de selección.  
  
4. Agregue una definición de clase parcial para la clase ClassDiagram al archivo de código personalizado.  
  
     El `ClassDiagram` clase se deriva de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> clase y se define en el archivo de código generado, Diagram.cs, en el proyecto DSL.  
  
5. Invalidar el <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> propiedad de la `ClassDiagram` clase para devolver la regla de selección personalizada.  
  
     La implementación predeterminada de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> propiedad obtiene un objeto de regla de selección que no modifica la selección.  
  
### <a name="example"></a>Ejemplo  
 El archivo de código siguiente crea una regla de selección que se expande la selección para incluir todas las instancias de cada una de las formas de dominio que se seleccionó inicialmente.  
  
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
