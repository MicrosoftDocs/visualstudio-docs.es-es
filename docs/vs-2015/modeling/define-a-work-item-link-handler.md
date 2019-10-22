---
title: Definir un controlador de vínculos de elementos de trabajo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 380aaa5bed1e30c549334bc004ea38e3f0bdb762
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669936"
---
# <a name="define-a-work-item-link-handler"></a>Definir un controlador de vínculos de elementos de trabajo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede crear una extensión de integración de Visual Studio que responda cuando el usuario cree o elimine un vínculo establecido entre un elemento del modelo UML y un elemento de trabajo. Por ejemplo, si el usuario decide vincular un nuevo elemento de trabajo a un elemento del modelo, el código podría inicializar los campos del elemento de trabajo a partir de los valores del modelo.

## <a name="set-up-a-uml-extension-solution"></a>Configurar una solución de extensión UML
 De este modo, podrá desarrollar controladores y distribuirlos posteriormente a otros usuarios. Es necesario configurar dos proyectos de Visual Studio:

- Un proyecto de biblioteca de clases que contenga el código del controlador de vínculos.

- Un proyecto VSIX, que actúe como contenedor a la hora de instalar el comando. Si lo desea, puede incluir otros componentes en el mismo VSIX.

#### <a name="to-set-up-the-visual-studio-solution"></a>Para configurar la solución de Visual Studio

1. Cree un proyecto de biblioteca de clases, ya sea agregándolo a una solución VSIX existente o creando una nueva solución.

    1. En el menú **Archivo** , elija **Nuevo**, **Proyecto**.

    2. En **plantillas instaladas**, expanda **Visual C#**  o **Visual Basic**y, a continuación, en la columna central, haga clic en **biblioteca de clases**.

    3. Establezca **Solución** para indicar si desea crear una nueva solución o agregar un componente a una solución VSIX que ya tiene abierta.

    4. Especifique el nombre y la ubicación del proyecto, y haga clic en Aceptar.

2. A menos que la solución ya contenga uno, cree un proyecto VSIX.

    1. En el **Explorador de soluciones**, en el menú contextual de la solución, elija **Agregar**, **Nuevo proyecto**.

    2. En **Plantillas instaladas**, expanda **Visual C#** o **Visual Basic**y, a continuación, seleccione **Extensibilidad**. En la columna central, elija **Proyecto VSIX**.

3. Establezca el proyecto VSIX como proyecto de inicio de la solución.

    - En el Explorador de soluciones, en el menú contextual del proyecto VSIX, elija **Establecer como proyecto de inicio**.

4. En **source. Extension. vsixmanifest**, en **contenido**, agregue el proyecto de biblioteca de clases como componente MEF.

    1. En la pestaña **Metadatos** , establezca un nombre para VSIX.

    2. En la pestaña **Destinos de instalación** , establezca las versiones de Visual Studio como destinos.

    3. En la pestaña **Activos** , elija **Nuevo**y, en el cuadro de diálogo, establezca:

         **Tipo** = **Componente MEF**

         **Origen** = **Un proyecto de la solución actual**

         **Proyecto** = *Su proyecto de biblioteca de clases*

## <a name="defining-the-work-item-link-handler"></a>Definir el controlador de vínculos de elementos de trabajo
 Realice todas las tareas siguientes en el proyecto de biblioteca de clases.

### <a name="project-references"></a>Referencias del proyecto
 Agregue los siguientes ensamblados [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] a las referencias del proyecto:

 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`

 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`

 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`

 `Microsoft.VisualStudio.Uml.Interfaces`

 `System.ComponentModel.Composition`

 `System.Drawing`: utilizado por el código de ejemplo

 Si no puede encontrar una de estas referencias en la pestaña **.net** del cuadro de diálogo **Agregar referencia** , use la pestaña examinar para encontrarla en la carpeta \Archivos de programa\Microsoft Visual Studio [versión] \Common7\IDE\PrivateAssemblies \\.

### <a name="import-the-work-item-namespace"></a>Importar el espacio de nombres de elemento de trabajo
 En las **referencias**del proyecto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], agregue referencias a los siguientes ensamblados:

- Microsoft.TeamFoundation.WorkItemTracking.Client.dll

- Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll

  En el código de programa, importe los siguientes espacios de nombres:

```
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;
using System.Linq;
```

### <a name="define-the-linked-work-item-event-handler"></a>Definir el controlador de eventos de elementos de trabajo vinculados
 Agregue un archivo de clase al proyecto de biblioteca de clases y establezca su contenido de la manera siguiente. Cambie los nombres de clase y espacio de nombres como desee.

```
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;
using System.Linq;

namespace WorkItems
{
  [Export(typeof(ILinkedWorkItemExtension))]
  public class MyWorkItemExtension : ILinkedWorkItemExtension
  {
    // Called before a new work item is edited by the user.
    // Use this to initialize work item fields from the model element.
    public void OnWorkItemCreated(System.Collections.Generic.IEnumerable<IElement> elementsToBeLinked, IWorkItemDocument workItemDocument)
    {
      INamedElement namedElement =
            elementsToBeLinked.First() as INamedElement;
      if (namedElement != null)
        workItemDocument.Item.Title = namedElement.Name;

    }

    // Called when any work item is linked to a model element.
    public void OnWorkItemLinked(System.Collections.Generic.IEnumerable<IElement> elements, string serverUri, int workItemId)
    {
      foreach (IElement element in elements)
        foreach (IShape shape in element.Shapes())
          shape.Color = System.Drawing.Color.Red;
    }

    // Called when a work item is unlinked from a model element.
    public void OnWorkItemRemoved(IElement element, string serverUri, int workItemId)
    {
      foreach (IShape shape in element.Shapes())
        shape.Color = System.Drawing.Color.White;
    }
  }
}
```

## <a name="testing-the-link-handler"></a>Probar el controlador de vínculos
 Para probar, ejecute el controlador de vínculos en modo de depuración.

> [!WARNING]
> Ya debe estar conectado al control de código fuente TFS (SCC) para crear o vincular a un elemento de trabajo. Si intenta abrir una conexión a un SCC TFS diferente, Visual Studio cierra automáticamente la solución actual. Asegúrese de que ya está conectado al SCC apropiado antes de intentar crear o vincular a un elemento de trabajo. En las versiones posteriores de Visual Studio, los comandos de menú no están disponibles si no está conectado a un SCC.

#### <a name="to-test-the-link-handler"></a>Para probar el controlador de vínculos

1. Presione **F5**o, en el menú **Depurar** , elija **Iniciar depuración**.

     Se iniciará una instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

     **Solución de problemas**: Si no se inicia una nueva [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], asegúrese de que el Proyecto VSIX está establecido como proyecto de inicio de la solución.

2. En la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra o cree un proyecto de modelado, y abra o cree un diagrama de modelado.

3. Cree un elemento de modelo como una clase UML y establezca su nombre.

4. Haga clic con el botón secundario en el elemento y, a continuación, haga clic en **crear elemento de trabajo**.

    - Si el submenú muestra **abrir Team Foundation Server conexión**, tendrá que cerrar el proyecto, conectarse al TFS adecuado y reiniciar este procedimiento.

    - Si el submenú muestra una lista de tipos de elemento de trabajo, haga clic en uno de ellos.

         Se abrirá un formulario de nuevo elemento de trabajo.

5. Compruebe que el título del elemento de trabajo sea igual que el elemento de modelo, si ha usado el código de ejemplo de la sección anterior. Esto indica que `OnWorkItemCreated()` ha funcionado.

6. Complete el formulario, guarde y cierre el elemento de trabajo.

7. Compruebe que el elemento de trabajo es ahora de color rojo. Esto muestra `OnWorkItemLinked()` en el código de ejemplo.

     **Solución de problemas**: Si no se han ejecutado los métodos de controlador, compruebe lo siguiente:

    - El proyecto de biblioteca de clases se muestra como un componente MEF en la lista de **contenido** de **source. Extensions. manifest** en el Proyecto VSIX.

    - Se ha adjuntado el atributo `Export` correcto a la clase del controlador y la clase implementa `ILinkedWorkItemExtension`.

    - Los parámetros de todos los atributos `Import` e `Export` son válidos.

## <a name="about-the-work-item-handler-code"></a>Acerca del código del controlador de elementos de trabajo

### <a name="listening-for-new-work-items"></a>Escuchar nuevos elementos de trabajo
 `OnWorkItemCreated` se invoca cuando el usuario decide crear un nuevo elemento de trabajo que se va a vincular a elementos del modelo. El código puede inicializar los campos de elementos de trabajo. El elemento de trabajo se presenta a continuación al usuario, que puede actualizar los campos y guardar el elemento de trabajo. El vínculo a un elemento del modelo no se crea hasta que el elemento de trabajo se ha guardado correctamente.

```
public void OnWorkItemCreated(
    IEnumerable<IElement> elementsToBeLinked,
    IWorkItemDocument workItem)
{
  INamedElement namedElement =
         elementsToBeLinked.First() as INamedElement;
  if (namedElement != null)
      workItem.Item.Title = namedElement.Name;
}
```

### <a name="listening-for-link-creation"></a>Realizar escuchas para la creación de vínculos
 `OnWorkItemLinked` se invoca inmediatamente después de crear un vínculo. Se invoca cuando el vínculo es a un nuevo elemento de trabajo o un elemento existente. Se llama una vez por cada elemento de trabajo.

```
public void OnWorkItemLinked
        (IEnumerable<IElement> elements,
         string serverUri, // TFS server
         int workItemId)
{
  foreach (IElement element in elements)
    foreach (IShape shape in element.Shapes())
         shape.Color = System.Drawing.Color.Red;
}
```

> [!NOTE]
> Para que este ejemplo funcione, debe agregar una referencia de proyecto a `System.Drawing.dll` e importar el espacio de nombres `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation`. Sin embargo, estas adiciones no son necesarias para otras implementaciones de `OnWorkItemLinked`.

### <a name="listening-for-link-removal"></a>Realizar escuchas para la eliminación de vínculos
 `OnWorkItemRemoved` se invoca una vez inmediatamente antes de que se elimine cada vínculo de elementos de trabajo. Si se elimina un elemento del modelo, se quitarán todos sus vínculos.

```
public void OnWorkItemRemoved
         (IElement element, string serverUri, int workItemId)
{...}
```

## <a name="updating-a-work-item"></a>Actualizar un elemento de trabajo
 A través de los espacios de nombres de Team Foundation, puede manipular un elemento de trabajo.

 Para usar el ejemplo siguiente, agregue estos ensamblados .NET a las referencias del proyecto:

- Microsoft.TeamFoundation.Client.dll

- Microsoft.TeamFoundation.WorkItemTracking.Client.dll

```

using Microsoft.TeamFoundation.Client;
using Microsoft.TeamFoundation.WorkItemTracking.Client;
...
public void OnWorkItemLinked
        (IEnumerable<IElement> elements,
         string serverUri, // TFS server
         int workItemId)
{
  TfsTeamProjectCollection tfs =
        TfsTeamProjectCollectionFactory
            .GetTeamProjectCollection(new Uri(serverUri));
  WorkItemStore workItemStore = new WorkItemStore(tfs);
  WorkItem item = workItemStore.GetWorkItem(workItemId);
  item.Open();
  item.Title = "something";
  item.Save();
} 
```

## <a name="accessing-the-work-item-reference-links"></a>Acceso a los vínculos de referencia de elementos de trabajo
 Puede tener acceso a los vínculos del modo siguiente:

```
//Get:
string linkString = element.GetReference(ReferenceConstants.WorkItem);
// Set:
element.AddReference(ReferenceConstants.WorkItem, linkString, true);

```

 El formato de `linkString` es:

 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`

 donde:

- El identificador URI del servidor sería:

   `http://tfServer:8080/tfs/projectCollection`

   El uso de minúsculas y mayúsculas es importante en `projectCollection`.

- `RepositoryGuid` se puede obtener de la conexión a TFS:

  ```csharp
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;
  RepositoryGuid= tpc.InstanceId;

  ```

  Para obtener más información sobre las referencias, vea [adjuntar cadenas de referencia a elementos del modelo UML](../modeling/attach-reference-strings-to-uml-model-elements.md).

## <a name="see-also"></a>Vea también

- [Microsoft. TeamFoundation. WorkItemTracking. Client. WorkItemStore](/previous-versions/visualstudio/visual-studio-2013/bb179850(v=vs.120))
- [Vincular elementos de modelo con elementos de trabajo](../modeling/link-model-elements-and-work-items.md)
- [Adjuntar cadenas de referencia a elementos de modelo UML](../modeling/attach-reference-strings-to-uml-model-elements.md)
- [Definir e instalar una extensión de modelado](../modeling/define-and-install-a-modeling-extension.md)
- [Programar con la API de UML](../modeling/programming-with-the-uml-api.md)
