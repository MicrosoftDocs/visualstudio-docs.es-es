---
title: 'Tutorial: Depurar un formulario Web Forms | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: e46169728c10d696f8dd99eb6459b9fcf081cb45
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704932"
---
# <a name="walkthrough-debugging-a-web-form"></a>Tutorial: Depurar un formulario web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los pasos de este tutorial muestran cómo depurar aplicaciones web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], también conocidas como formularios Web Forms. También muestra cómo iniciar y detener la ejecución, establecer puntos de interrupción y examinar variables en la ventana **Inspección**.  
  
> [!NOTE]
> Para completar este tutorial, debe tener privilegios de administrador en el equipo servidor. De forma predeterminada, el proceso de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], aspnet_wp.exe o w3wp.exe, se ejecuta como un proceso de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Para depurar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], debe tener privilegios de administrador en el equipo en el que se ejecute [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Para obtener más información, consulte [requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
 Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-the-web-form"></a>Para crear el formulario Web Forms  
  
1. Si hay alguna solución abierta, ciérrela.  
  
2. En el menú **Archivo**, haga clic en **Nuevo** y después haga clic en **Sitio web**.  
  
     Aparece el cuadro de diálogo **Nuevo sitio web**.  
  
3. En el panel **Plantillas**, haga clic en **Sitio web ASP.NET**.  
  
4. En el **ubicación** línea, haga clic en **HTTP** en la lista y, en el cuadro de texto, escriba **http://localhost/WebSite**.  
  
5. En la lista **Lenguaje**, haga clic en **Visual C#** o en **Visual Basic**.  
  
6. Haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crea un nuevo proyecto y muestra el código fuente HTML predeterminado. También crea un nuevo directorio virtual denominado **Sitio web** bajo el **Sitio web predeterminado** de IIS.  
  
7. Haga clic en la ficha **Diseño** en el margen inferior.  
  
8. Haga clic en la ficha **Cuadro de herramientas** en el margen izquierdo o selecciónela en el menú **Ver**.  
  
     Se abrirá el **Cuadro de herramientas** .  
  
9. En el **Cuadro de herramientas**, haga clic en el control **Button** y agréguelo a la superficie de diseño principal, Default.aspx.  
  
10. En el **Cuadro de herramientas**, haga clic en el control **Textbox** y arrástrelo hasta la superficie de diseño principal, Default.aspx.  
  
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
  
1. En la ventana de Default.aspx.cs o Default.aspx.vb, haga clic en el margen izquierdo en la misma línea que el texto que ha agregado:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Aparecerá un punto rojo y el texto de la línea se resaltará en rojo. El punto rojo representa un punto de interrupción. Cuando ejecute la aplicación en el depurador, este interrumpirá la ejecución del código en la posición donde encuentre un punto de interrupción. Esto le permite ver el estado de la aplicación y depurarla. Para obtener más información, vea [Puntos de interrupción](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. En el menú **Depurar**, haga clic en **Iniciar depuración**.  
  
3. Aparece el cuadro de diálogo **Depuración no habilitada**. Seleccione la opción **Modificar el archivo Web.config para habilitar la depuración** y haga clic en **Aceptar**.  
  
     Internet Explorer iniciará y mostrará la página que acaba de diseñar.  
  
4. En Internet Explorer, haga clic en el botón.  
  
     En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], esto le lleva a la línea en la que estableció el punto de interrupción en la página de códigos Default.aspx.cs o Default.aspx.vb. Esta línea debe aparecer resaltada en amarillo. Ahora puede ver las variables de la aplicación y controlar su ejecución. La aplicación deja de ejecutarse y espera a que el usuario le facilite un comando.  
  
5. En el menú **Depurar**, haga clic en **Ventanas**, haga clic en **Inspección** y después haga clic en **Inspección1**.  
  
6. En la ventana **Inspección**, escriba **TextBox1.Text**.  
  
     La ventana **Inspección** mostrará el valor de la variable `TextBox1.Text`:  
  
    ```  
    ""  
    ```  
  
7. En el menú **Depurar**, haga clic en **Paso a paso por procedimientos**.  
  
     El valor `TextBox1.Text` se cambia en la ventana **Inspección** por lo siguiente:  
  
    ```  
    "Button was clicked!"  
    ```  
  
8. En el menú **Depurar**, haga clic en **Continuar**.  
  
9. En Internet Explorer, haga clic en el botón otra vez.  
  
     La ejecución se volverá a detener en el punto de interrupción.  
  
10. En la ventana de Default.aspx.cs o Default.aspx.vb, haga clic en el punto rojo situado en el margen izquierdo.  
  
     Esto quita el punto de interrupción.  
  
11. En el menú **Depurar**, haga clic en **Detener depuración**.  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>Para asociar el formulario Web Forms para la depuración  
  
1. En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede adjuntar el depurador a un proceso en ejecución. Para lograr una depuración más efectiva, compile el archivo ejecutable como una versión de depuración con archivos de símbolos (PDB).  
  
2. En la ventana de Default.aspx.cs o Default.aspx.vb, haga clic en el margen izquierdo para establecer de nuevo un punto de interrupción en la línea que ha agregado:   
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3. En el menú **Depurar**, haga clic en **Iniciar sin depurar**.  
  
     El formulario Web Forms empieza a ejecutarse en Internet Explorer, pero el depurador no está asociado.  
  
4. Establezca una asociación al proceso de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Para obtener más información, consulte [depurar aplicaciones Web implementadas](../debugger/debugging-deployed-web-applications.md).  
  
5. En Internet Explorer, haga clic en el botón del formulario.  
  
     En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], debe alcanzar el punto de interrupción de Default.aspx.cs, Default.aspx.vb o Default.aspx.  
  
6. Cuando finaliza la depuración, en el menú **Depurar**, haga clic en **Detener depuración**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones de ASP.NET y AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)
