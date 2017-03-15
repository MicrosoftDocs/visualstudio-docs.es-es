---
title: "Tutorial: Depurar Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Asociar al proceso (cuadro de diálogo)"
  - "Asociar al proceso (cuadro de diálogo), tutoriales"
  - "depurador, asociar a programas"
  - "depurar [Visual Studio], tutoriales"
  - "depurar [Visual Studio], Windows Forms"
  - "depurar código administrado, Windows Forms"
  - "depurar formularios Windows Forms, tutoriales"
  - "Windows Forms, depurar"
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Tutorial: Depurar Windows Forms
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un Windows Form es una de las aplicaciones administradas más comunes.  Con un Windows Form se crean aplicaciones estándar de Windows.  Puede completar este tutorial utilizando Visual Basic, C\# o C\+\+.  
  
 En primer lugar, debe cerrar las soluciones que estén abiertas.  
  
### Pasos preliminares de este tutorial  
  
-   Si tiene una solución abierta, ciérrela. \(En el menú **Archivo**, seleccione **Cerrar solución**.\)  
  
## Crear un nuevo Windows Form  
 A continuación, creará un nuevo Windows Form.  
  
#### Para crear el formulario Windows Forms para este tutorial  
  
1.  En el menú **Archivo**, elija **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto**.  
  
2.  En el panel Tipos de proyecto, abra el nodo **Visual Basic**, **Visual C\#** o **Visual C\+\+** y, a continuación,  
  
    1.  En Visual Basic o Visual C\#, seleccione el nodo **Windows** y, a continuación, **Aplicación de Windows Forms** en el panel **Plantillas**.  
  
    2.  En Visual C\+\+, seleccione el nodo **CLR** y, a continuación, **Aplicación de Windows Forms**  en el panel **Plantillas**.  
  
3.  En el panel **Plantillas**, seleccione **Aplicación Windows**.  
  
4.  En el cuadro **Nombre**, asigne un nombre único al proyecto \(por ejemplo, Walkthrough\_SimpleDebug\).  
  
5.  Haga clic en **Aceptar**.  
  
     Visual Studio crea un proyecto nuevo y muestra un formulario nuevo en el Diseñador de Windows Forms.  Para obtener más información, vea [Diseñador de Windows Forms](http://msdn.microsoft.com/es-es/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
6.  En el menú **Ver**, seleccione **Cuadro de herramientas**.  
  
     Se abrirá el Cuadro de herramientas.  Para obtener más información, vea [Cuadro de herramientas](../ide/reference/toolbox.md).  
  
7.  En el Cuadro de herramientas, haga clic en el control **Button** y arrástrelo a la superficie de diseño del formulario.  Coloque el botón en el formulario.  
  
8.  En el Cuadro de herramientas, haga clic en el control **TextBox** y arrástrelo a la superficie de diseño del formulario.  Coloque el control **TextBox** en el formulario.  
  
9. En la superficie de diseño del formulario, haga doble clic en el botón.  
  
     Esto le lleva a la página de códigos.  El cursor debe estar en `button1_Click`.  
  
10. Agregue el código siguiente a la función `button1_Click`:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. En el menú **Compilar**, seleccione **Compilar solución**.  
  
     El proyecto se debe compilar sin errores.  
  
## Depurar el formulario  
 Ahora está listo para comenzar la depuración.  
  
#### Para depurar el Windows Form creado para este tutorial  
  
1.  En la ventana de código fuente, haga clic en el margen izquierdo en la misma línea que el texto que agregó:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     Aparecerá un punto rojo y el texto de la línea se resaltará en rojo.  El punto rojo representa un punto de interrupción.  Para obtener más información, vea [Puntos de interrupción](http://msdn.microsoft.com/es-es/fe4eedc1-71aa-4928-962f-0912c334d583).  Cuando ejecute la aplicación en el depurador, este interrumpirá la ejecución del código en la posición donde encuentre un punto de interrupción.  Esto le permite ver el estado de la aplicación y depurarla.  
  
    > [!NOTE]
    >  También puede hacer clic con el botón secundario en cualquier línea de código, seleccionar **Punto de interrupción** y, a continuación, hacer clic en **Insertar punto de interrupción** para agregar un punto de interrupción en esa línea.  
  
2.  En el menú **Depurar**, elija**Iniciar**.  
  
     El Windows Form comienza su ejecución.  
  
3.  En el Windows Form, haga clic en el botón agregado.  
  
     En Visual Studio, esto le lleva a la línea en la que estableció el punto de interrupción en la página de códigos.  Esta línea debe aparecer resaltada en amarillo.  Ahora puede ver las variables de la aplicación y controlar su ejecución.  La aplicación ha detenido ahora su ejecución y espera a que se le indique una acción.  
  
4.  En el menú **Depurar**, elija **Ventanas**, después **Inspección** y, a continuación, haga clic en **Inspección1**.  
  
5.  En la ventana **Inspección1**, haga clic en una fila en blanco.  En la columna **Nombre**, escriba `textBox1.Text` \(si utiliza Visual Basic, Visual C\# o J\#\) o `textBox1->Text` \(si utiliza C\+\+\), luego presione ENTRAR.  
  
     En la ventana **Inspección1** se muestra el valor de esta variable entre comillas:  
  
    ```  
    ""  
    ```  
  
6.  En el menú **Depurar**, elija **Paso a paso por instrucciones**.  
  
     El valor de textBox1.Text cambia en la ventana **Inspección1** a:  
  
    ```  
    Button was clicked!  
    ```  
  
7.  En el menú **Depurar**, elija **Continuar** para reanudar la depuración del programa.  
  
8.  En el Windows Form, haga clic de nuevo en el botón.  
  
     Visual Studio vuelve a interrumpir la ejecución.  
  
9. Haga clic en el punto rojo que representa al punto de interrupción.  
  
     Esto quita el punto de interrupción del código.  
  
10. En el menú **Depurar**, elija **Detener depuración**.  
  
## Adjuntar la aplicación de Windows Forms para la depuración  
 En [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], puede adjuntar el depurador a un proceso en ejecución.  Si utiliza Express Edition, esta característica no es compatible.  
  
#### Para adjuntar la aplicación de Windows Forms para la depuración  
  
1.  En el proyecto creado anteriormente, haga clic en el margen izquierdo para volver a establecer un punto de interrupción en la línea agregada:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
2.  En el menú **Depurar**, seleccione **Iniciar sin depurar**.  
  
     El Windows Form comenzará su ejecución en Windows, como si se hubiera hecho doble clic en su archivo ejecutable.  El depurador no se ha asociado.  
  
3.  En el menú **Depurar**, seleccione **Asociar al proceso**. \(Este comando también está disponible en el menú **Herramientas**\).  
  
     Aparecerá el cuadro de diálogo **Asociar al proceso**.  
  
4.  En el panel **Procesos disponibles**, busque el nombre del proceso \(Walkthrough\_SimpleDebug.exe\) en la columna **Proceso** y haga clic en él.  
  
5.  Haga clic en el botón **Asociar**.  
  
6.  En el Windows Form, haga clic en el único botón.  
  
     El depurador interrumpe la ejecución del Windows Form en el punto de interrupción.  
  
## Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)