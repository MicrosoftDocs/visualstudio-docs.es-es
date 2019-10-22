---
title: Actualizar un modelo UML a partir de un subproceso en segundo plano | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e6626faa09f1e38506c2d205d13caa9a3707fc0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659464"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>Actualizar un modelo UML a partir de un subproceso en segundo plano
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En ocasiones, puede resultar útil realizar cambios en un modelo a través de un subproceso en segundo plano. Por ejemplo, si está cargando información desde un recurso externo que es lento, puede usar un subproceso en segundo plano para supervisar las actualizaciones. De este modo, el usuario podrá ver cada actualización tan pronto como se produzca.

 Sin embargo, debe tener en cuenta que el almacén UML no es seguro para subprocesos. Las siguientes consideraciones son importantes:

- Todas las actualizaciones de un modelo o diagrama deben realizarse en el subproceso de la interfaz de usuario. El subproceso en segundo plano debe usar <xref:System.Windows.Forms.Control.Invoke%2A> o `Dispatcher.`<xref:System.Windows.Threading.Dispatcher.Invoke%2A> para hacer que sea el subproceso de la interfaz de usuario el que realmente realice las actualizaciones.

- Si agrupa una serie de cambios en una única transacción, le recomendamos que impida que el usuario edite el modelo mientras la transacción esté en curso. De lo contrario, cualquier modificación que pudiera hacer el usuario pasaría a formar parte de la misma transacción. Para evitar que el usuario realice cambios, muestre un cuadro de diálogo modal. Si lo desea, puede incluir un botón Cancelar en el cuadro de diálogo. El usuario puede ver los cambios cuando se producen.

## <a name="example"></a>Ejemplo
 En este ejemplo se usa un subproceso en segundo plano para realizar diversos cambios en un modelo. Se usa un cuadro de diálogo para excluir al usuario mientras el subproceso está en ejecución. En este sencillo ejemplo, no se incluye el botón Cancelar en el cuadro de diálogo. Sin embargo, sería fácil agregar esa característica.

#### <a name="to-run-the-example"></a>Para ejecutar el ejemplo

1. Cree un controlador de comandos en C# un proyecto como se describe en [definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

2. Asegúrese de que el proyecto contiene referencias a estos ensamblados:

   - Microsoft.VisualStudio.ArchitectureTools.Extensibility

   - Microsoft.VisualStudio.Modeling.Sdk.[versión]

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[versión]

   - Microsoft.VisualStudio.Uml.Interfaces

   - System.ComponentModel.Composition

   - System.Windows.Forms

3. Agregue al proyecto un Windows Form con el nombre **ProgressForm**. Debe aparece un mensaje en el que se indique que las actualizaciones están en curso. No es necesario que contengan ningún otro control.

4. Agregue un archivo C# que contenga el código que se muestra después del paso 7.

5. Compile y ejecute el proyecto.

    Se iniciará una nueva instancia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en modo experimental.

6. Cree o abra un diagrama de clases UML en la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

7. Haga clic con el botón secundario en cualquier lugar del diagrama de clases UML y, a continuación, haga clic en **agregar varias clases UML**.

   Aparecerán varios cuadros de clases nuevos en el diagrama, uno detrás de otro, en intervalos de medio segundo.

```csharp
using System;
using System.ComponentModel;
using System.ComponentModel.Composition;
using System.Threading;
using System.Windows.Forms;

using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.Uml.Classes;

namespace BackgroundThreadProgressUI // CHANGE TO YOUR NAMESPACE
{
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  class UmlClassAdderCommand : ICommandExtension
  {

    [Import]
    IDiagramContext context { get; set; }

    [Import]
    ILinkedUndoContext linkedUndoContext { get; set; }

    // Called when the user runs the command.
    public void Execute(IMenuCommand command)
    {
      // The form that will exclude the user.
      ProgressForm form = new ProgressForm();

      // System.ComponentModel.BackgroundWorker is a
      // convenient way to run a background thread.
      BackgroundWorker worker = new BackgroundWorker();
      worker.WorkerSupportsCancellation = true;

      worker.DoWork += delegate(object sender, DoWorkEventArgs args)
      {
        // This block will be executed in a background thread.

        IClassDiagram diagram = context.CurrentDiagram as IClassDiagram;
        IModelStore store = diagram.ModelStore;
        const int CLASSES_TO_CREATE = 15;

        // Group all the changes together.
        using (ILinkedUndoTransaction transaction = linkedUndoContext.BeginTransaction("Background Updates"))
        {
          for (int i = 1; i < CLASSES_TO_CREATE; i++)
          {
            if (worker.CancellationPending)
               return; // No commit - undo all.

            // Create model elements using the UI thread by using
            // the Invoke method on the progress form. Always
            // modify the model and diagrams from a UI thread.
            form.Invoke((MethodInvoker)(delegate
            {
              IClass newClass = store.Root.CreateClass();
              newClass.Name = string.Format("NewClass{0}", i);
              diagram.Display(newClass);
            }));

            // Sleep briefly so that we can watch the updates.
            Thread.Sleep(500);
          }

          // Commit the transaction or it will be rolled back.
          transaction.Commit();
        }
      };

      // Close the form when the thread completes.
      worker.RunWorkerCompleted += delegate(object sender, RunWorkerCompletedEventArgs args)
      {
        form.Close();
      };

      // Start the thread before showing the modal progress dialog.
      worker.RunWorkerAsync();

      // Show the form modally, parented on VS.
      // Prevents the user from making changes while in progress.
      form.ShowDialog();
    }

    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled = command.Visible = true;
    }

    public string Text
    {
      get { return "Add several classes"; }
    }
  }
}
```

#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>Para permitir que el usuario pueda cancelar el subproceso del ejemplo

1. Agregue un botón de cancelación en el cuadro de diálogo de progreso.

2. Agregue el código siguiente al cuadro de diálogo de progreso:

     `public event MethodInvoker Cancel;`

     `private void CancelButton_Click(object sender, EventArgs e)`

     `{`

     `Cancel();`

     `}`

3. En el método Execute (), inserte esta línea tras la construcción del formulario:

     `form.Cancel += delegate() { worker.CancelAsync(); };`

### <a name="other-methods-of-accessing-the-ui-thread"></a>Otros métodos para obtener acceso al subproceso de la interfaz de usuario
 Si no desea crear un cuadro de diálogo, puede obtener acceso al control que muestra el diagrama:

 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`

 Puede usar `uiThreadHolder.Invoke()` para realizar operaciones en el subproceso de la interfaz de usuario.

## <a name="see-also"></a>Vea también
 [Definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [definir un controlador de gestos en un diagrama de modelado](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)
