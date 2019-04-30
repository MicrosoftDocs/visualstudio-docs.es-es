---
title: Seguimiento del trabajo mediante Visual Studio Online o Team Foundation Server | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 41981ad6-673e-492e-b739-9863b14157b1
caps.latest.revision: 26
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 036c0ced92fd4da85989883ab5725455ed172db4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63416294"
---
# <a name="making-coded-ui-tests-wait-for-specific-events-during-playback"></a>Hacer que la prueba de IU codificada espere por eventos concretos durante la reproducción
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En una reproducción de prueba de UI codificada, puede indicar a la prueba que espere a que se produzcan ciertos eventos, como que se muestre una ventana, que se oculte la barra de progreso, etc. Para ello, use el método UITestControl.WaitForControlXXX() adecuado, tal y como se describe en la siguiente tabla. Para obtener un ejemplo de una prueba automatizada de IU que espera a que se habilite un control mediante el método <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>, vea [Tutorial: Crear, editar y mantener una prueba automatizada de IU](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
 **Requisitos**  
  
 Visual Studio Enterprise  
  
> [!TIP]
> También puede agregar retrasos antes de las acciones con el editor de pruebas de IU codificadas. Para obtener más información, vea [Cómo: Insertar un retraso antes de una acción de la interfaz de usuario mediante el Editor de pruebas de IU codificadas](http://msdn.microsoft.com/library/509f8ef7-e105-4049-b11b-d64549e055b0).  
  
 **Métodos de UITestControl.WaitForControlXXX()**  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>  
  
 Espera a que el control esté listo para aceptar entradas de mouse y de teclado. El motor llama implícitamente a esta API en todas las acciones para esperar a que el control esté listo antes de realizar cualquier operación. Sin embargo, en algunos escenarios más rebuscados, es posible que tenga que hacer una llamada explícita.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>  
  
 Espera a que el control esté habilitado cuando el asistente está realizando una validación asincrónica de la entrada a través de llamadas al servidor. Por ejemplo, puede usar este método para esperar a que el botón **Siguiente** del asistente se habilite. Para obtener un ejemplo de este método, vea [Tutorial: Crear, editar y mantener una prueba automatizada de IU](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
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
> El Editor de pruebas de IU codificadas permite modificar fácilmente este tipo de pruebas. Con el Editor de pruebas de IU codificadas puede buscar, ver y modificar métodos de prueba. También puede editar acciones de interfaz de usuario y los controles asociados en la asignación de controles de IU. Para obtener más información, consulte [Editar pruebas de IU codificadas mediante el editor de pruebas de IU codificadas](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
 **Orientación**  
  
 Para obtener más información, consulte [pruebas para entrega continua con Visual Studio 2012 – capítulo 5: Automatizar pruebas del sistema](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
## <a name="see-also"></a>Vea también  
 [Usar UI Automation para probar el código](../test/use-ui-automation-to-test-your-code.md)   
 [Crear pruebas de IU codificadas](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Tutorial: Crear, modificar y mantener una prueba de IU codificada](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)   
 [Anatomía de una prueba de IU codificada](../test/anatomy-of-a-coded-ui-test.md)   
 [Configuraciones y plataformas compatibles con las pruebas de IU codificadas y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Cómo: Insertar un retraso antes de una acción de la interfaz de usuario mediante el Editor de pruebas de IU codificadas](http://msdn.microsoft.com/library/509f8ef7-e105-4049-b11b-d64549e055b0)
