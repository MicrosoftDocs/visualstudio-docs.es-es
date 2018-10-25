---
title: Definir un controlador de gestos en un diagrama de modelado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, double-click
- UML - extending, drag and drop
ms.assetid: e5e1d70a-3539-4321-a3b1-89e86e4d6430
caps.latest.revision: 36
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 26a60151d89ffaa89338601c4992f9c2f41b099a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812977"
---
# <a name="define-a-gesture-handler-on-a-modeling-diagram"></a>Definir un controlador de gestos en un diagrama de modelado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, puede definir comandos que se ejecuten cuando el usuario haga doble clic o arrastre elementos hasta un diagrama de UML. Puede empaquetar estas extensiones en una extensión de integración de Visual Studio ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) y distribuirla a otros usuarios de Visual Studio.  
  
 Si ya hay un comportamiento integrado por el tipo de diagrama y el tipo de elemento que desea arrastrar, quizás no pueda agregar o invalidar este comportamiento.  
  
## <a name="requirements"></a>Requisitos  
 Vea [Requisitos](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="creating-a-gesture-handler"></a>Crear un controlador de gestos  
 Para definir un controlador de gestos para un diseñador UML, debe crear una clase que defina el comportamiento del controlador de gestos e insertarla en una extensión de integración de Visual Studio (VSIX). Las extensiones VSIX actúan como contenedores que instalan el controlador. Hay dos métodos para definir un controlador de gestos:  
  
-   **Cree un controlador de gestos en VSIX propio utilizando una plantilla de proyecto.** Este es el método más rápido. Utilícelo si no desea combinar el controlador con otros tipos de extensión, como extensiones de validación, elementos de cuadro de herramientas o comandos de menú.  
  
-   **Crear el controlador de gestos independiente y proyectos VSIX.** Use este método si desea combinar varios tipos de extensiones en la misma VSIX. Por ejemplo, si el controlador de gestos espera que el modelo respete restricciones concretas, podría insertarlo en la misma VSIX como método de validación.  
  
#### <a name="to-create-a-gesture-handler-in-its-own-vsix"></a>Para crear un controlador de gestos en un VSIX propio  
  
1. En el cuadro de diálogo **Nuevo proyecto** , en **Proyectos de modelado**, seleccione **Extensión de gesto**.  
  
2. Abra el archivo **.cs** en el nuevo proyecto y modifique la clase `GestureExtension` para implementar el controlador de gestos.  
  
    Para obtener más información, vea [Implementar el controlador de gestos](#Implementing).  
  
3. Pruebe el controlador de gestos presionando F5. Para obtener más información, vea [Ejecutar el controlador de gestos](#Executing).  
  
4. Instalar el controlador de gestos en otro equipo copiando el archivo **bin\\\*\\\*.vsix** que compila el proyecto. Para obtener más información, vea [Instalar y desinstalar una extensión](#Installing).  
  
   A continuación se muestra el procedimiento alternativo:  
  
#### <a name="to-create-a-separate-class-library-dll-project-for-the-gesture-handler"></a>Para crear un proyecto de biblioteca de clases (DLL) independiente para el controlador de gestos  
  
1. Cree un proyecto de biblioteca de clases en una nueva solución [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o en una solución existente.  
  
   1.  En el menú **Archivo** , elija **Nuevo**, **Proyecto**.  
  
   2.  En **Plantillas instaladas**, expanda **Visual C#** o **Visual Basic**y, a continuación, en la columna central, elija **Biblioteca de clases**.  
  
2. Agregue las referencias siguientes al proyecto.  
  
    `Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
    `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]`  
  
    `Microsoft.VisualStudio.ArchitectureTools.Extensibility`  
  
    `Microsoft.VisualStudio.Uml.Interfaces`  
  
    `System.ComponentModel.Composition`  
  
    `System.Windows.Forms`  
  
    `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` - solo lo necesita si está ampliando diagramas de capas. Para obtener más información, consulte [ampliar diagramas de capas](../modeling/extend-layer-diagrams.md).  
  
3. Agregue un archivo de clase al proyecto y establezca su contenido en el código siguiente.  
  
   > [!NOTE]
   >  Cambie el nombre de clase y de espacio de nombres como desee.  
  
   ```  
   using System.ComponentModel.Composition;  
   using System.Linq;  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Modeling.Diagrams;  
   using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;  
   using Microsoft.VisualStudio.Modeling;  
   using Microsoft.VisualStudio.Uml.Classes;  
   // ADD other UML namespaces if required  
  
   namespace MyGestureHandler // CHANGE  
   {  
     // DELETE any of these attributes if the handler  
     // should not work with some types of diagram.  
     [ClassDesignerExtension]  
     [ActivityDesignerExtension]  
     [ComponentDesignerExtension]  
     [SequenceDesignerExtension]  
     [UseCaseDesignerExtension]  
     // [LayerDesignerExtension]  
  
     // Gesture handlers must export IGestureExtension:  
     [Export(typeof(IGestureExtension))]  
     // CHANGE class name  
     public class MyGesture1 : IGestureExtension  
     {  
       [Import]  
       public IDiagramContext DiagramContext { get; set; }  
  
       /// <summary>  
       /// Called when the user double-clicks on the diagram  
       /// </summary>  
       /// <param name="targetElement"></param>  
       /// <param name="diagramPointEventArgs"></param>  
       public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)  
       {  
         // CHANGE THIS CODE FOR YOUR APPLICATION.  
  
         // Get the target shape, if any. Null if the target is the diagram.  
         IShape targetIShape = targetElement.CreateIShape();  
  
         // Do something...  
       }  
  
       /// <summary>  
       /// Called repeatedly when the user drags from anywhere on the screen.  
       /// Return value should indicate whether a drop here is allowed.  
       /// </summary>  
       /// <param name="targetMergeElement">References the element to be dropped on.</param>  
       /// <param name="diagramDragEventArgs">References the element to be dropped.</param>  
       /// <returns></returns>  
       public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)  
       {  
         // CHANGE THIS CODE FOR YOUR APPLICATION.  
  
         // Get the target element, if any. Null if the target is the diagram.  
         IShape targetIShape = targetMergeElement.CreateIShape();  
  
         // This example allows drag of any UML elements.  
         return GetModelElementsFromDragEvent(diagramDragEventArgs).Count() > 0;  
       }  
  
       /// <summary>  
       /// Execute the action to be performed on the drop.  
       /// </summary>  
       /// <param name="targetDropElement"></param>  
       /// <param name="diagramDragEventArgs"></param>  
       public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
       {  
         // CHANGE THIS CODE FOR YOUR APPLICATION.  
       }  
  
       /// <summary>  
       /// Retrieves UML IElements from drag arguments.  
       /// Works for drags from UML diagrams.  
       /// </summary>  
       private IEnumerable<IElement> GetModelElementsFromDragEvent  
               (DiagramDragEventArgs dragEvent)  
       {  
         //ElementGroupPrototype is the container for  
         //dragged and copied elements and toolbox items.  
         ElementGroupPrototype prototype =  
            dragEvent.Data.  
            GetData(typeof(ElementGroupPrototype))  
                 as ElementGroupPrototype;  
         // Locate the originals in the implementation store.  
         IElementDirectory implementationDirectory =  
            dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;  
  
         return prototype.ProtoElements.Select(  
           prototypeElement =>  
           {  
             ModelElement element = implementationDirectory  
               .FindElement(prototypeElement.ElementId);  
             ShapeElement shapeElement = element as ShapeElement;  
             if (shapeElement != null)  
             {  
               // Dragged from a diagram.  
               return shapeElement.ModelElement as IElement;  
             }  
             else  
             {  
               // Dragged from UML Model Explorer.  
               return element as IElement;  
             }  
           });  
       }  
  
     }  
   }  
  
   ```  
  
    Para obtener más información sobre qué incluir en los métodos, vea [Implementar el controlador de gestos](#Implementing).  
  
   Debe agregar el comando de menú a un proyecto VSIX, que actúa como contenedor para instalar el comando. Si lo desea, puede incluir otros componentes en el mismo VSIX.  
  
#### <a name="to-add-a-separate-gesture-handler-to-a-vsix-project"></a>Para agregar un controlador de gestos independiente a un proyecto VSIX  
  
1.  No necesita este procedimiento si ha creado el controlador de gestos con un VSIX propio.  
  
2.  Cree un proyecto VSIX, a menos que la solución ya tenga uno.  
  
    1.  En el **Explorador de soluciones**, en el menú contextual de la solución, elija **Agregar**, **Nuevo proyecto**.  
  
    2.  En **Plantillas instaladas**, expanda **Visual C#** o **Visual Basic**y, a continuación, seleccione **Extensibilidad**. En la columna central, elija **Proyecto VSIX**.  
  
3.  Establezca el proyecto VSIX como proyecto de inicio de la solución.  
  
    -   En el Explorador de soluciones, en el menú contextual del proyecto VSIX, elija **Establecer como proyecto de inicio**.  
  
4.  En **source.extension.vsixmanifest**, agregue el proyecto de biblioteca de clases del controlador de gestos como un componente MEF:  
  
    1.  En la pestaña **Metadatos** , establezca un nombre para VSIX.  
  
    2.  En la pestaña **Destinos de instalación** , establezca las versiones de Visual Studio como destinos.  
  
    3.  En la pestaña **Activos** , elija **Nuevo**y, en el cuadro de diálogo, establezca:  
  
         **Tipo** = **Componente MEF**  
  
         **Origen** = **Un proyecto de la solución actual**  
  
         **Proyecto** = *Su proyecto de biblioteca de clases*  
  
##  <a name="Executing"></a> Ejecutar el controlador de gestos  
 Para fines de prueba, ejecute el controlador de gestos en modo de depuración.  
  
#### <a name="to-test-the-gesture-handler"></a>Para probar el controlador de gestos  
  
1. Presione **F5**o bien, en el menú **Depurar** , haga clic en **Iniciar depuración**.  
  
    Se iniciará una instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
    **Solución de problemas**: si no se inicia un nuevo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :  
  
   -   Si tiene más de un proyecto, asegúrese de que el proyecto VSIX está configurado como proyecto de inicio de la solución.  
  
   -   En el Explorador de soluciones, en el menú contextual del proyecto de inicio o único, elija Propiedades. En el editor de propiedades del proyecto, elija la pestaña **Depurar** . Asegúrese de que la cadena del campo Programa externo de inicio** es el nombre de ruta de acceso completo de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], normalmente:  
  
        `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  
  
2. En la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra o cree un proyecto de modelado, y abra o cree un diagrama de modelado. Use un diagrama perteneciente a uno de los tipos enumerados en los atributos de la clase del controlador de gestos.  
  
3. Haga doble clic en cualquier parte del diagrama. Se debe llamar al controlador de doble clic.  
  
4. Arrastre un elemento desde el Explorador de UML al diagrama. Se debe llamar al controlador de arrastre.  
  
   **Solución de problemas**: si el controlador de gestos no funciona, asegúrese de lo siguiente:  
  
-   El proyecto de controlador de gestos se muestra como un componente MEF en la pestaña **Activos** de **source.extensions.manifest** en el proyecto VSIX.  
  
-   Los parámetros de todos los atributos `Import` y `Export` son válidos.  
  
-   El método `CanDragDrop` no devuelve `false`.  
  
-   El tipo de diagrama del modelo que está usando (clase UML, secuencia, etc.) se muestra como uno de los atributos de la clase del controlador de gestos [ClassDesignerExtension], [SequenceDesignerExtension], etc.  
  
-   No hay ninguna funcionalidad integrada ya definida para este tipo de elemento de destino y colocado.  
  
##  <a name="Implementing"></a> Implementar el controlador de gestos  
  
### <a name="the-gesture-handler-methods"></a>Los métodos del controlador de gestos  
 La clase del controlador de gestos implementa y exporta <xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement.IGestureExtension>. Los métodos que necesita definir son los siguientes:  
  
|||  
|-|-|  
|`bool CanDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Devuelve `true` para permitir que el elemento de origen al que se hace referencia en `dragEvent` se coloque en este destino.<br /><br /> Este método no debe realizar cambios al modelo. Debe funcionar rápidamente, ya que se usa para determinar el estado de la flecha a medida que el usuario mueve el mouse.|  
|`void OnDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Actualiza el modelo en función del objeto de origen al que se hace referencia en `dragEvent`y el destino.<br /><br /> Se le llama cuando el usuario suelta el mouse después de arrastrar.|  
|`void OnDoubleClick (ShapeElement target, DiagramPointEventArgs pointEvent)`|`target` es la forma en la que el usuario hizo doble clic.|  
  
 Puede escribir controladores capaces de admitir no solo elementos de UML sino también una gran variedad de otros elementos, como archivos, nodos de una vista de clases .NET, etc. El usuario puede arrastrar cualquiera de estos elementos a un diagrama UML, siempre que escriba un método `OnDragDrop` que pueda descodificar el formato serializado de los elementos. Los métodos de descodificación varían entre los tipos de elementos.  
  
 Los parámetros de estos métodos son:  
  
-   `ShapeElement target`. La forma o el diagrama en el que el usuario ha arrastrado algo.  
  
     `ShapeElement` es una clase de la implementación subyacente a las herramientas de modelado UML. Para reducir el riesgo de provocar un estado incoherente en el modelo y diagramas UML, se recomienda no utilizar los métodos de esta clase directamente. En su lugar, encapsule el elemento en un `IShape`y, a continuación, use los métodos descritos en [mostrar un modelo UML en diagramas](../modeling/display-a-uml-model-on-diagrams.md).  
  
    -   Para obtener un objeto `IShape`:  
  
        ```  
        IShape targetIShape = target.CreateIShape(target);  
        ```  
  
    -   Para obtener el elemento del modelo que es el destino de la operación de arrastre o doble clic:  
  
        ```  
        IElement target = targetIShape.Element;  
        ```  
  
         Puede convertirlo en un tipo de elemento más específico.  
  
    -   Para obtener el almacén de modelos UML que contiene el modelo UML:  
  
        ```  
        IModelStore modelStore =   
          targetIShape.Element.GetModelStore();   
        ```  
  
    -   Para obtener acceso al host y al proveedor de servicios:  
  
        ```  
        target.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE  
        ```  
  
-   `DiagramDragEventArgs eventArgs`. Este parámetro lleva el formato serializado del objeto de origen de una operación de arrastre:  
  
    ```  
    System.Windows.Forms.IDataObject data = eventArgs.Data;    
    ```  
  
     Puede arrastrar elementos de muchos tipos diferentes a un diagrama, de diferentes partes de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], o del escritorio de Windows. Los diferentes tipos de elemento se codifican de maneras diferentes en `IDataObject`. Para extraer los elementos de él, consulte la documentación para saber cuál es el tipo de objeto adecuado.  
  
     Si el objeto de origen es un elemento UML arrastrado desde el Explorador de modelos UML o desde otro diagrama UML, consulte [elementos del modelo UML obtener a partir de IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).  
  
### <a name="writing-the-code-of-the-methods"></a>Escribir el código de los métodos  
 Para más información sobre cómo se escribe código para leer y actualizar el modelo, vea [Programming with the UML API](../modeling/programming-with-the-uml-api.md).  
  
 Para obtener información sobre el acceso a información del modelo en una operación de arrastre, vea [elementos del modelo UML obtener a partir de IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).  
  
 Si está trabajando con un diagrama de secuencia, vea también [diagramas de secuencia UML editar mediante la API de UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
 Además de los parámetros de los métodos, también puede declarar una propiedad importada en la clase que proporcione acceso al diagrama y modelo actuales.  
  
```  
[Import] public IDiagramContext DiagramContext { get; set; }  
```  
  
 La declaración de `IDiagramContext` le permite escribir en los métodos código que tiene acceso al diagrama, la selección actual y el modelo:  
  
```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>)  
{ IElement element = shape.Element; ... }  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IDiagram diagram in modelStore.Diagrams) {...}  
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}  
```  
  
 Para obtener más información, consulte [navegar por el modelo UML](../modeling/navigate-the-uml-model.md).  
  
##  <a name="Installing"></a> Instalar y desinstalar una extensión  
 Puede instalar una extensión de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] en su propio equipo y en otros equipos.  
  
#### <a name="to-install-an-extension"></a>Para instalar una extensión  
  
1.  En el equipo, busque el archivo **.vsix** compilado en el proyecto VSIX.  
  
    1.  En el **Explorador de soluciones**, en el menú contextual del proyecto VSIX, elija **Abrir carpeta en el Explorador de Windows**.  
  
    2.  Busque el archivo **bin\\\*\\**_convertirá_**.vsix**  
  
2.  Copie el archivo **.vsix** en el equipo de destino en el que desea instalar la extensión. Puede tratarse de su propio equipo o de otro.  
  
     El equipo de destino debe tener una de las ediciones de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] que especificó en **source.extension.vsixmanifest**.  
  
3.  En el equipo de destino, abra el archivo **.vsix** .  
  
     El**Instalador de extensiones de Visual Studio** se abre e instala la extensión.  
  
4.  Inicie o reinicie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-uninstall-an-extension"></a>Para desinstalar una extensión  
  
1. En el menú **Herramientas** , elija **Extensiones y actualizaciones**.  
  
2. Expanda **Extensiones instaladas**.  
  
3. Seleccione la extensión y, a continuación, elija **Desinstalar**.  
  
   En contadas ocasiones, una extensión defectuosa no se carga y crea un informe en la ventana de error, aunque no aparece en el Administrador de extensiones. En ese caso, puede quitar la extensión eliminando el archivo de:  
  
   *% LocalAppData %* **\Local\Microsoft\VisualStudio\\\Extensions [versión]**  
  
##  <a name="DragExample"></a> Ejemplo  
 En el siguiente ejemplo se muestra cómo crear las líneas de vida de un diagrama de secuencia, basándose en los elementos y puertos de un componente, arrastrado desde un diagrama de componentes.  
  
 Para probarlo, presione F5. Se abre una instancia experimental de Visual Studio. En esta instancia, abra un modelo UML y cree un componente en un diagrama de componentes. Agregue algunas interfaces y elementos internos a este componente. Seleccione las interfaces y los elementos. A continuación, arrastre las interfaces y los elementos a un diagrama de secuencia. (Arrastre desde el diagrama de componentes hasta la pestaña correspondiente al diagrama de secuencia y, a continuación, hacia abajo en el diagrama de secuencia.) Aparecerá una línea de vida para cada interfaz y elemento.  
  
 Para obtener más información sobre cómo enlazar interacciones a los diagramas de secuencia, vea [diagramas de secuencia UML editar mediante la API de UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
```  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.Uml.Interactions;  
using Microsoft.VisualStudio.Uml.CompositeStructures;  
using Microsoft.VisualStudio.Uml.Components;  
  
/// <summary>  
/// Creates lifelines from component ports and parts.  
/// </summary>  
[Export(typeof(IGestureExtension))]  
[SequenceDesignerExtension]  
public class CreateLifelinesFromComponentParts : IGestureExtension  
{  
  [Import]  
  public IDiagramContext Context { get; set; }  
  
  /// <summary>  
  /// Called by the modeling framework when  
  /// the user drops something on a target.  
  /// </summary>  
  /// <param name="target">The target shape or diagram </param>  
  /// <param name="dragEvent">The item being dragged</param>  
  public void OnDragDrop(ShapeElement target,  
           DiagramDragEventArgs dragEvent)  
  {  
    ISequenceDiagram diagram = Context.CurrentDiagram  
            as ISequenceDiagram;  
    IInteraction interaction = diagram.Interaction;  
    if (interaction == null)  
    {  
      // Sequence diagram is empty: create an interaction.  
      interaction = diagram.ModelStore.Root.CreateInteraction();  
      interaction.Name = Context.CurrentDiagram.Name;  
      diagram.Bind(interaction);  
    }  
    foreach (IConnectableElement connectable in  
       GetConnectablesFromDrag(dragEvent))  
    {  
      ILifeline lifeline = interaction.CreateLifeline();  
      lifeline.Represents = connectable;  
      lifeline.Name = connectable.Name;  
    }  
  }  
  
  /// <summary>  
  /// Called by the modeling framework to determine whether  
  /// the user can drop something on a target.  
  /// Must not change anything.  
  /// </summary>  
  /// <param name="target">The target shape or diagram</param>  
  /// <param name="dragEvent">The item being dragged</param>  
  /// <returns>true if this item can be dropped on this target</returns>  
  public bool CanDragDrop(ShapeElement target,  
           DiagramDragEventArgs dragEvent)  
  {  
    IEnumerable<IConnectableElement> connectables = GetConnectablesFromDrag(dragEvent);  
    return connectables.Count() > 0;  
  }  
  
  ///<summary>  
  /// Get dragged parts and ports of an IComponent.  
  ///</summary>  
  private IEnumerable<IConnectableElement>  
    GetConnectablesFromDrag(DiagramDragEventArgs dragEvent)  
  {  
    foreach (IElement element in  
      GetModelElementsFromDragEvent(dragEvent))  
    {  
      IConnectableElement part = element as IConnectableElement;  
      if (part != null)  
      {  
        yield return part;  
      }  
    }  
  }  
  
  /// <summary>  
  /// Retrieves UML IElements from drag arguments.  
  /// Works for drags from UML diagrams.  
  /// </summary>  
  private IEnumerable<IElement> GetModelElementsFromDragEvent  
          (DiagramDragEventArgs dragEvent)  
  {  
    //ElementGroupPrototype is the container for  
    //dragged and copied elements and toolbox items.  
    ElementGroupPrototype prototype =  
       dragEvent.Data.  
       GetData(typeof(ElementGroupPrototype))  
            as ElementGroupPrototype;  
    // Locate the originals in the implementation store.  
    IElementDirectory implementationDirectory =  
       dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;  
  
    return prototype.ProtoElements.Select(  
      prototypeElement =>  
      {  
        ModelElement element = implementationDirectory  
          .FindElement(prototypeElement.ElementId);  
        ShapeElement shapeElement = element as ShapeElement;  
        if (shapeElement != null)  
        {  
          // Dragged from a diagram.  
          return shapeElement.ModelElement as IElement;  
        }  
        else  
        {  
          // Dragged from UML Model Explorer.  
          return element as IElement;  
        }  
      });  
  }  
  
  public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)  
  {  
  }  
}  
  
```  
  
 El código de `GetModelElementsFromDragEvent()` se describe en [elementos del modelo UML obtener a partir de IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).  
  
## <a name="see-also"></a>Vea también  
 [Definir e instalar una extensión de modelado](../modeling/define-and-install-a-modeling-extension.md)   
 [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Programar con la API de UML](../modeling/programming-with-the-uml-api.md)



