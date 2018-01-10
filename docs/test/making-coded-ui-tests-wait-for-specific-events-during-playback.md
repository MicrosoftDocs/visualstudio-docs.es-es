---
title: Seguimiento del trabajo mediante Visual Studio Online o Team Foundation Server | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 4a6c7ae9f0438d440471bc9e049b539e96e63e13
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="making-coded-ui-tests-wait-for-specific-events-during-playback"></a>Hacer que la prueba de IU codificada espere por eventos concretos durante la reproducción
En una reproducción de prueba de UI codificada, puede indicar a la prueba que espere a que se produzcan ciertos eventos, como que se muestre una ventana, que se oculte la barra de progreso, etc. Para ello, use el método UITestControl.WaitForControlXXX() adecuado, tal y como se describe en la siguiente tabla. Para ver un ejemplo de una prueba de IU codificada que espera a que un control se habilite con el método <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>, vea [Tutorial: Crear, modificar y mantener una prueba de IU codificada](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
 **Requisitos**  
  
 Visual Studio Enterprise  
  
> [!TIP]
>  También puede agregar retrasos antes de las acciones con el editor de pruebas de IU codificadas. Para obtener más información, consulte [Cómo insertar un retraso antes de una acción de IU mediante el editor de pruebas de IU codificadas](http://msdn.microsoft.com/Library/509f8ef7-e105-4049-b11b-d64549e055b0).  
  
 **Métodos de UITestControl.WaitForControlXXX()**  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>  
  
 Espera a que el control esté listo para aceptar entradas de mouse y de teclado. El motor llama implícitamente a esta API en todas las acciones para esperar a que el control esté listo antes de realizar cualquier operación. Sin embargo, en algunos escenarios más rebuscados, es posible que tenga que hacer una llamada explícita.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>  
  
 Espera a que el control esté habilitado cuando el asistente está realizando una validación asincrónica de la entrada a través de llamadas al servidor. Por ejemplo, puede usar este método para esperar a que el botón **Siguiente** del asistente se habilite. Para ver un ejemplo de este método, consulte [Tutorial: Crear, modificar y mantener una prueba de IU codificada](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>  
  
 Espera a que el control aparezca en la interfaz de usuario. Por ejemplo, tiene previsto que se abra un cuadro de diálogo de error después de que la aplicación haya validado los parámetros. El tiempo necesario para la validación es variable. Puede usar este método para esperar a que el cuadro de diálogo de error se abra.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>  
  
 Espera a que el control desaparezca de la interfaz de usuario. Por ejemplo, puede esperar a que la barra de progreso desaparezca.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>  
  
 Espera a que la propiedad especificada del control tenga un valor determinado. Por ejemplo, puede esperar a que el texto de estado cambie a **Listo**.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>  
  
 Espera a que la propiedad especificada del control tenga un valor contrario al especificado. Por ejemplo, cuando espera a que el cuadro de edición no sea de solo lectura, esto es, que sea editable.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>  
  
 Espera que el predicado especificado devuelva `true`. Esto se puede usar en operaciones de espera complejas (como condiciones OR) en un control determinado. Por ejemplo, puede esperar a que el texto de estado sea **Correcto** o **Error**, tal y como se muestra en el siguiente código:  
  
```csharp  
  
// Define the method to evaluate the condition   
private static bool IsStatusDone(UITestControl control)   
{   
    WinText statusText = control as WinText;   
    return statusText.DisplayText == "Succeeded" || statusText.DisplayText == "Failed";   
}   
  
// In test method, wait till the method evaluates to true   
statusText.WaitForControlCondition(IsStatusDone);  
  
```  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForCondition%2A>  
  
 Todos los métodos anteriores son métodos de instancia de UITestControl. Este método es un método estático. Este método también espera a que el predicado especificado sea `true` pero se puede usar en operaciones de espera complejas (como condiciones OR) en varios controles. Por ejemplo, puede esperar a que el texto de estado sea **Correcto** o a que aparezca un mensaje de error, como se muestra en el siguiente código:  
  
```csharp  
  
// Define the method to evaluate the condition   
private static bool IsStatusDoneOrError(UITestControl[] controls)   
{   
    WinText statusText = controls[0] as WinText;   
    WinWindow errorDialog = controls[1] as WinWindow;   
    return statusText.DisplayText == "Succeeded" || errorDialog.Exists;   
}   
  
// In test method, wait till the method evaluates to true   
UITestControl.WaitForCondition<UITestControl[]>(new UITestControl[] { statusText, errorDialog }, IsStatusDoneOrError);  
  
```  
  
 Todos estos métodos tienen el siguiente comportamiento:  
  
 Los métodos devuelven true si la espera es correcta y false si se produjo un error.  
  
 El tiempo de espera implícito de la operación de espera se especifica mediante la propiedad <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A>. El valor predeterminado de esta propiedad es 60000 milisegundos (un minuto).  
  
 Los métodos tienen una sobrecarga para tener el tiempo de espera explícito en milisegundos. Sin embargo, cuando la operación de espera da como resultado una búsqueda implícita del control, o si la aplicación está ocupada, el tiempo de espera real podría ser mayor que el tiempo de espera especificado.  
  
 Las funciones anteriores son eficaces y flexibles y deberían satisfacer casi todas las condiciones. Sin embargo, en caso de que estos métodos no satisfagan sus necesidades y tenga que codificar <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A> o <xref:System.Threading.Thread.Sleep%2A> en su código, le recomendamos que use Playback.Wait() en lugar de la API Thread.Sleep(). Las razones para esto son las siguientes:  
  
 Puede usar la propiedad <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A> para modificar la duración de la suspensión. Esta variable es 1 de forma predeterminada, pero puede aumentarla o disminuirla para cambiar el tiempo de espera de todo el código. Por ejemplo, si está realizando pruebas expresamente en una red lenta o algún otro caso de bajo rendimiento, puede cambiar esta variable a un valor de 1,5 en un solo lugar (o incluso en el archivo de configuración) para incorporar un 50 % de espera extra en todos los lugares.  
  
 Playback.Wait() llama internamente a Thread.Sleep() (tras el cálculo anterior) en fragmentos más pequeños en un bucle for mientras busca la operación cancel\break del usuario. En otras palabras, Playback.Wait() permite cancelar la reproducción antes de que la espera finalice, mientras que la suspensión no lo haría o generaría una excepción.  
  
> [!TIP]
>  El Editor de pruebas de IU codificadas permite modificar fácilmente este tipo de pruebas. Con el Editor de pruebas de IU codificadas puede buscar, ver y modificar métodos de prueba. También puede editar acciones de interfaz de usuario y los controles asociados en la asignación de controles de IU. Para obtener más información, consulte [Editar pruebas de IU codificadas mediante el editor de pruebas de IU codificadas](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
 **Orientación**  
  
 Para obtener información adicional, vea [Pruebas para entrega continua con Visual Studio 2012 – Capítulo 5: Automatización de las pruebas del sistema](http://go.microsoft.com/fwlink/?LinkID=255196).  
  
## <a name="see-also"></a>Vea también  
 [Usar UI Automation para probar el código](../test/use-ui-automation-to-test-your-code.md)   
 [Crear pruebas de IU codificadas](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Tutorial: Crear, modificar y mantener una prueba de IU codificada](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)   
 [Anatomía de una prueba de IU codificada](../test/anatomy-of-a-coded-ui-test.md)   
 [Configuraciones y plataformas compatibles con las pruebas de IU codificadas y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Cómo: Insertar un retraso antes de una acción de IU mediante el editor de pruebas de IU programadas](http://msdn.microsoft.com/Library/509f8ef7-e105-4049-b11b-d64549e055b0)
