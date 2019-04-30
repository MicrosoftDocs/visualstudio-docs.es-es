---
title: Editar diagramas de secuencia UML mediante la API de UML | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c619ae6efd1de48319bf9c0398ee8ab4e3cd57ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442953"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>Modificar diagramas de secuencia usando la API de UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una interacción es una secuencia de mensajes entre un conjunto de líneas de vida. Las interacciones se muestran en un diagrama de secuencia UML.  
  
 Para obtener todos los detalles sobre la API, vea <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>.  
  
 Para obtener una introducción más general a la escritura de comandos y controladores de gestos para diagramas UML, vea [definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="basic-code"></a>Código básico  
  
### <a name="namespace-imports"></a>Importaciones de espacio de nombres  
 Debe incluir estas instrucciones `using`:  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
   // for basic UML types such as IPackage  
using Microsoft.VisualStudio.Uml.Interactions;  
   // for interaction types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // to create elements and use additional functions  
```  
  
 Si está creando comandos de menú y controladores de gestos, también necesitará:  
  
```  
using System.ComponentModel.Composition;   
   // for Import and Export  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   // for ICommandExtension  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   // for diagrams and context  
```  
  
 Para obtener más información, consulte [definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="getting-the-context"></a>Obtener el contexto  
 Si está editando una interacción que forma parte de un controlador de comandos o gestos en un diagrama de secuencia, puede obtener una referencia al contexto. Por ejemplo:  
  
```  
[SequenceDesignerExtension]  
[Export(typeof(ICommandExtension))]    
public class MySequenceDiagramCommand : ICommandExtension  
{  
    [Import]  
    public IDiagramContext Context { get; set; }  
    public void QueryStatus (IMenuCommand command)  
    {  
      ISequenceDiagram sequenceDiagram =   
          Context.CurrentDiagram as ISequenceDiagram;  
         ...  
```  
  
### <a name="generated-and-uml-sequence-diagrams"></a>Diagramas de secuencia UML y generados  
 Existen dos tipos de diagramas de secuencia: aquellos que se crean manualmente en un proyecto de modelado de UML y aquellos que se generan desde el código del programa. Use la propiedad `UmlMode` para detectar de qué tipo de diagrama de secuencia dispone.  
  
> [!NOTE]
> Esta propiedad solo devuelve false con los diagramas de secuencia generados desde el código con Visual Studio 2013 y versiones anteriores. Esto incluye diagramas de secuencia generados por código y migrados desde VS 2013 y versiones anteriores. Esta versión de Visual Studio no admite la generación de nuevos diagramas de secuencia.  
  
 Por ejemplo, si desea crear un comando de menú que solo esté visible en diagramas de secuencia UML, el método `QueryStatus()` podría incluir la siguiente instrucción:  
  
```  
command.Enabled = command.Visible =   
      sequenceDiagram != null && sequenceDiagram.UmlMode;  
```  
  
 En un diagrama de secuencia generado, las líneas de vida, los mensajes y el resto de elementos son muy similares a los de un diagrama de secuencia UML. En un modelo UML, el almacén de modelos tiene una raíz, que es el modelo que posee todos los demás elementos, pero existe una interacción generada en su propio almacén de modelos, que tiene una raíz nula:  
  
```  
IModel rootModel = sequenceDiagram.ModelStore.Root;  
    // !sequenceDiagram.UmlMode == (rootModel == null)  
```  
  
## <a name="to-create-and-display-an-interaction"></a>Para crear y mostrar una interacción  
 Cree la interacción como un elemento secundario de un paquete o modelo.  
  
 Por ejemplo, si va a desarrollar un comando que podría ejecutarse en un diagrama de secuencia vacío, siempre debería comprobar primero si existe la interacción.  
  
```  
public void Execute (IMenuCommand command)  
{  
    ISequenceDiagram sequenceDiagram =   
         Context.CurrentDiagram as ISequenceDiagram;  
    if (sequenceDiagram == null) return;  
    // Get the diagram's interaction:  
    IInteraction interaction = sequenceDiagram.Interaction;  
    // A new sequence diagram might have no interaction:  
    if (interaction == null)  
    {  
       // Get the home package or model of the diagram:  
       IPackage parentPackage = sequenceDiagram.GetObject<IPackage>();  
       interaction = parentPackage.CreateInteraction();  
       // Display the interaction on the sequence diagram:  
       sequenceDiagram.Bind(interaction);  
    }   
```  
  
## <a name="updating-an-interaction-and-its-layout"></a>Actualizar una interacción y su diseño  
 Cuando actualice una interacción, finalice siempre la operación con uno de los métodos siguientes para actualizar el diseño:  
  
- `ISequenceDiagram.UpdateShapePositions()` ajusta las posiciones de las formas que se hayan insertado o movido recientemente y sus formas vecinas.  
  
- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])` vuelve a dibujar el diagrama entero. Puede usar el parámetro para especificar la reubicación de las líneas de vida, los mensajes o ambos.  
  
  Esto es especialmente importante al insertar nuevos elementos o mover los elementos existentes, ya que no estarán en las posiciones correctas en el diagrama hasta que se realice una de estas operaciones. Tan solo necesita llamar una vez a una de estas operaciones al final de una serie de cambios.  
  
  Para evitar confundir al usuario que realiza una acción de deshacer después de su comando, use una `ILinkedUndoTransaction` para delimitar los cambios y las operaciones finales `Layout()` o `UpdateShapePositions()`. Por ejemplo:  
  
```  
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))  
{  
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);  
  Diagram.UpdateShapePositions();  
  transaction.Commit();  
}  
```  
  
 Para usar una `ILinkedUndoTransaction`, haga esta declaración en su clase:  
  
```  
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }  
```  
  
 Para obtener más información, consulte [actualizaciones del modelo UML vínculo mediante transacciones](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
## <a name="building-an-interaction"></a>Compilar una interacción  
  
### <a name="to-create-lifelines"></a>Para crear líneas de vida  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
```  
  
 Una línea de vida representa un elemento que se puede conectar, es decir, una instancia de un tipo. Por ejemplo, si la interacción se usa para mostrar cómo un componente delega los mensajes entrantes en sus elementos internos, las líneas de vida pueden representar los puertos y los elementos del componente:  
  
```  
foreach (IConnectableElement part in   
            component.Parts  
           .Concat<IConnectableElement>(component.OwnedPorts))  
{  
   ILifeline lifeline = interaction.CreateLifeline();  
   lifeline.Represents = part;  
}  
```  
  
 Por otro lado, si en la interacción se muestra un conjunto arbitrario de objetos, puede crear una propiedad u otros `IConnectableElement` en la propia interacción:  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
IProperty property1 = interaction.CreateProperty();  
property1.Type = model.CreateInterface();  
property1.Type.Name = "Type 1";  
lifeline.Represents = property1;  
```  
  
 Otra alternativa consiste en establecer el nombre y el tipo de una línea de vida sin vincularla a un elemento conectable:  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
lifeline.Name = "c1";  
lifeline.SetInstanceType("Customer");  
System.Diagnostics.Debug.Assert(  
           lifeline.GetDisplayName() == "c1:Customer"  );  
```  
  
### <a name="to-create-messages"></a>Para crear mensajes  
 Para crear un mensaje, debe identificar los puntos de inserción en las líneas de vida de origen y de destino. Por ejemplo:  
  
```  
interaction.CreateMessage( sourceInsertionPoint,   
                           targetInsertionPoint,   
                           MessageKind.Complete,   
                           MessageSort.ASynchCall)  
```  
  
 Para crear un mensaje que tenga un origen o un destino no definidos:  
  
```  
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);  
```  
  
 Hay varios mensajes que se pueden usar para identificar puntos de inserción en todos los puntos clave de una línea de vida:  
  
|Método de ILifeline|Úselo para insertar en este punto|  
|-------------------------|------------------------------------|  
|`FindInsertionPointAtTop()`|La parte superior de la línea de vida.|  
|`FindInsertionPointAtBottom()`|La parte inferior de la línea de vida.|  
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|Un punto inmediatamente posterior al mensaje especificado.|  
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|El punto puede estar en la línea de vida o en un bloque de especificación de ejecución primario.|  
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|Un punto que siga a un uso de interacción.|  
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|Un punto que siga a un fragmento combinado.|  
|`FindInsertionPoint(IExecutionSpecification block)`|La parte superior de un bloque de ejecución.|  
|`FindInsertionPoint(IInteractionOperand fragment)`|La parte superior de un operando de un fragmento combinado.|  
  
 Al crear mensajes, tenga cuidado de no definir un mensaje que se cruce con otro mensaje.  
  
### <a name="to-create-combined-fragments-and-interaction-uses"></a>Para crear fragmentos combinados y usos de interacción  
 Puede crear fragmentos combinados y usos de la interacción: solo tiene que especificar un punto de inserción en cada línea de vida que el elemento deba cubrir. Tenga cuidado de no especificar un conjunto de puntos que se crucen con un mensaje o fragmento existente.  
  
```  
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,   
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
Interaction.CreateInteractionUse(  
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
```  
  
 También puede crear un fragmento combinado que cubra un conjunto de mensajes existente. Todos los mensajes deben tener su origen en la misma línea de vida o bloque de ejecución.  
  
```  
ICombinedFragment cf = Interaction.CreateCombinedFragment(  
  InteractionOperatorKind.Loop,  
  Interaction.Lifelines.First().GetAllOutgoingMessages());  
```  
  
 Un fragmento combinado siempre se crea con un solo operando. Para crear un operando nuevo, debe especificar un operando existente y si desea insertar el nuevo operando antes o después de él:  
  
```  
// Create an additional operand before the first  
cf.CreateInteractionOperand(cf.Operands.First(), false);  
// Create an additional operand after the last:  
cf.CreateInteractionOperand(cf.Operands.Last(), true);  
```  
  
## <a name="troubleshooting"></a>Solución de problemas  
 Las formas aparecerán en posiciones incorrectas si los cambios no se completan con una operación `UpdateShapePositions()` o `Layout()`.  
  
 La mayoría del resto de problemas se producen por puntos de inserción desalineados, que hacen que los nuevos mensajes o fragmentos se crucen con otros. Los síntomas pueden ser que no se lleve a cabo ningún cambio o se produzca una excepción. La excepción podría no producirse hasta que se realice la operación `UpdateShapePositions()` o `Layout()`.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>   
 [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definir un personalizado en un elemento de cuadro de herramientas de modelado](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Programar con la API de UML](../modeling/programming-with-the-uml-api.md)
