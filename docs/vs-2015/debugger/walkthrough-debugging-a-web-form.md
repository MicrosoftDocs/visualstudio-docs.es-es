---
title: 'Tutorial: Depurar un formulario Web Forms | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7024a9abc58117bf28ed78de107b1c17ddad601f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747257"
---
# <a name="walkthrough-debugging-a-web-form"></a>Tutorial: Depurar un formulario Web Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los pasos de este tutorial muestran cómo depurar aplicaciones web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], también conocidas como formularios Web Forms. Muestra cómo iniciar y detener la ejecución, establecer puntos de interrupción y examinar variables en el **inspección** ventana.  
  
> [!NOTE]
>  Para completar este tutorial, debe tener privilegios de administrador en el equipo servidor. De forma predeterminada, el proceso de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], aspnet_wp.exe o w3wp.exe, se ejecuta como un proceso de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Para depurar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], debe tener privilegios de administrador en el equipo en el que se ejecute [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Para obtener más información, consulte [requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
 Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-the-web-form"></a>Para crear el formulario Web Forms  
  
1.  Si hay alguna solución abierta, ciérrela.  
  
2.  En el **archivo** menú, haga clic en **New**y, a continuación, haga clic en **sitio Web**.  
  
     El **nuevo sitio Web** aparece el cuadro de diálogo.  
  
3.  En el **plantillas** panel, haga clic en **sitio Web de ASP.NET**.  
  
4.  En el **ubicación** línea, haga clic en **HTTP** en la lista y, en el cuadro de texto, escriba **http://localhost/WebSite**.  
  
5.  En el **lenguaje** lista, haga clic en **Visual C#** o **Visual Basic**.  
  
6.  Haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crea un nuevo proyecto y muestra el código fuente HTML predeterminado. También crea un nuevo directorio virtual denominado **sitio Web** en **sitio Web predeterminado** en IIS.  
  
7.  Haga clic en el **diseño** ficha en el margen inferior.  
  
8.  Haga clic en el **cuadro de herramientas** pestaña en el margen izquierdo o selecciónela en la **vista** menú.  
  
     Se abrirá el **Cuadro de herramientas** .  
  
9. En el **cuadro de herramientas**, haga clic en el **botón** controlar y agregarlo a la superficie de diseño principal, Default.aspx.  
  
10. En el **cuadro de herramientas**, haga clic en el **Textbox** control y arrastre el control a la superficie de diseño principal, Default.aspx.  
  
11. Haga doble clic en el control de botón que colocó.  
  
     Esto le llevará a la página de códigos: Default.aspx.cs para C# o Default.aspx.vb para [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. El cursor debe estar en la función `Button1_Click` .  
  
12. Agregue a la función `Button1_Click` las siguientes líneas de código:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. En el menú **Compilar** , haga clic en **Compilar solución**.  
  
     El proyecto se debe compilar sin errores.  
  
     Ahora está listo para comenzar la depuración.  
  
### <a name="to-debug-the-web-form"></a>Para crear el formulario Web Forms  
  
1.  En la ventana de Default.aspx.cs o Default.aspx.vb, haga clic en el margen izquierdo en la misma línea que el texto que ha agregado:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Aparecerá un punto rojo y el texto de la línea se resaltará en rojo. El punto rojo representa un punto de interrupción. Cuando ejecute la aplicación en el depurador, este interrumpirá la ejecución del código en la posición donde encuentre un punto de interrupción. Esto le permite ver el estado de la aplicación y depurarla. Para obtener más información, consulte [puntos de interrupción](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  En el menú **Depurar**, haga clic en **Iniciar depuración**.  
  
3.  El **depuración no habilitada** aparece el cuadro de diálogo. Seleccione **modificar el archivo Web.config para habilitar la depuración** opción y haga clic en **Aceptar**.  
  
     Internet Explorer iniciará y mostrará la página que acaba de diseñar.  
  
4.  En Internet Explorer, haga clic en el botón.  
  
     En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], esto le lleva a la línea en la que estableció el punto de interrupción en la página de códigos Default.aspx.cs o Default.aspx.vb. Esta línea debe aparecer resaltada en amarillo. Ahora puede ver las variables de la aplicación y controlar su ejecución. La aplicación deja de ejecutarse y espera a que el usuario le facilite un comando.  
  
5.  En el **depurar** menú, haga clic en **Windows**, a continuación, haga clic en **inspección**y, a continuación, haga clic en **Inspección1**.  
  
6.  En el **inspección** ventana, escriba **TextBox1.Text**.  
  
     El **inspección** ventana muestra el valor de la variable `TextBox1.Text`:  
  
    ```  
    ""  
    ```  
  
7.  En el **depurar** menú, haga clic en **paso a paso por**.  
  
     El valor de `TextBox1.Text` cambia en el **inspección** ventana leer:  
  
    ```  
    "Button was clicked!"  
    ```  
  
8.  En el **depurar** menú, haga clic en **continuar**.  
  
9. En Internet Explorer, haga clic en el botón otra vez.  
  
     La ejecución se volverá a detener en el punto de interrupción.  
  
10. En la ventana de Default.aspx.cs o Default.aspx.vb, haga clic en el punto rojo situado en el margen izquierdo.  
  
     Esto quita el punto de interrupción.  
  
11. En el **depurar** menú, haga clic en **Detener depuración**.  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>Para asociar el formulario Web Forms para la depuración  
  
1.  En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede adjuntar el depurador a un proceso en ejecución. Para lograr una depuración más efectiva, compile el archivo ejecutable como una versión de depuración con archivos de símbolos (PDB).  
  
2.  En la ventana de Default.aspx.cs o Default.aspx.vb, haga clic en el margen izquierdo para establecer de nuevo un punto de interrupción en la línea que ha agregado:   
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3.  En el **depurar** menú, haga clic en **iniciar sin depurar**.  
  
     El formulario Web Forms empieza a ejecutarse en Internet Explorer, pero el depurador no está asociado.  
  
4.  Establezca una asociación al proceso de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Para obtener más información, consulte [depurar aplicaciones Web implementadas](../debugger/debugging-deployed-web-applications.md).  
  
5.  En Internet Explorer, haga clic en el botón del formulario.  
  
     En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], debe alcanzar el punto de interrupción de Default.aspx.cs, Default.aspx.vb o Default.aspx.  
  
6.  Cuando haya terminado la depuración, en el **depurar** menú, haga clic en **Detener depuración**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones de ASP.NET y AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)



