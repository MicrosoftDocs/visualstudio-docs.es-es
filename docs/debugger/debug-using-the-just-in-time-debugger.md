---
title: Depurar con el depurador Just | Documentos de Microsoft
ms.custom: 
ms.date: 07/06/17
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
caps.latest.revision: "48"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 470e4c728d246570e6f7e38ff3b71772de5b05fd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Depurar con el depurador Just en Visual Studio
Depuración Just-In-Time inicia Visual Studio automáticamente cuando se produce una excepción o un bloqueo en una aplicación que se ejecuta fuera de Visual Studio. Esto le permite probar la aplicación cuando no se está ejecutando Visual Studio y empiece a depurar con Visual Studio cuando se produce un problema.

Depuración Just-In-Time funciona en aplicaciones de escritorio de Windows. No funciona para aplicaciones universales de Windows y no funciona para el código administrado que se hospeda en una aplicación nativa, por ejemplo los visualizadores.

> [!TIP] 
> Si desea saber cómo responder a Just-in-Time cuadro de diálogo del depurador, vea [en este tema](../debugger/just-in-time-debugging-in-visual-studio.md).

##  <a name="BKMK_Enabling"></a>Habilitar o deshabilitar Just-In-Time la depuración  
Puede habilitar o deshabilitar la depuración de Visual Studio Just-In-Time **Herramientas > opciones** cuadro de diálogo.
  
#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Para habilitar o deshabilitar la depuración Just-In-Time  
  
1.  Abra Visual Studio con privilegios de administrador (haga clic en y elija **ejecutar como administrador**).

    Habilitar o deshabilitar Just-In-Time depuración establece una clave del registro, y privilegios de administrador pueden ser necesarias para modificar dicha clave.
    
2. En el menú **Herramientas** , haga clic en **Opciones**.
  
2.  En el **opciones** cuadro de diálogo, expanda el **depuración** nodo.  
  
3.  En el **depuración** nodo, seleccione **Just-In-Time**.

    ![Habilitar o deshabilitar la depuración JIT](../debugger/media/dbg-jit-enable-or-disable.png "habilitar o deshabilitar la depuración JIT") 
  
4.  En el **Just Habilitar depuración de estos tipos de código** cuadro, active o desactive los tipos de programa pertinentes: **administrada**, **nativo**, o **Script**.    
  
5.  Haga clic en **Aceptar**.  
  
La depuración Just-In-Time todavía puede habilitarse aunque ya no esté instalado Visual Studio en el equipo. Cuando no está instalado Visual Studio, no se puede deshabilitar la depuración de Visual Studio Just-In-Time **opciones** cuadro de diálogo. En ese caso, puede deshabilitar la depuración Just-In-Time editando el Registro de Windows.  
  
#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Para deshabilitar la depuración Just-In-Time editando el Registro  
  
1.  En el **iniciar** menú, busque y ejecute`regedit.exe`  
  
2.  En el **Editor del registro** ventana, busque y elimine las entradas del registro siguientes:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\Software\Microsoft\.NETFramework\DbgManagedDebugger  

    ![Clave del registro JIT](../debugger/media/dbg-jit-registry.png "clave del registro JIT") 
  
3.  Si el equipo está ejecutando un sistema operativo de 64 bits, elimine también las entradas del registro siguientes:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger  
  
4.  Tenga cuidado de no eliminar ni cambiar accidentalmente ninguna otra clave del Registro.  
  
5.  Cerrar la **Editor del registro** ventana.   
  
#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Para habilitar la depuración Just-In-Time para un Windows Form  
  
1.  De forma predeterminada, las aplicaciones de Windows Forms tienen un controlador de excepciones de nivel superior que permite que el programa continúe ejecutándose si puede recuperar. Por ejemplo, si la aplicación de formularios Windows Forms produce una excepción no controlada, verá un cuadro de diálogo similar al siguiente:  
  
     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")  
  
     Para habilitar Just-In-Time la depuración de una aplicación de formularios Windows Forms, debe realizar los siguientes pasos adicionales:  
  
2.  Establecer el `jitDebugging` valor a `true` en el `system.windows.form` sección del archivo machine.config o  *\<nombre de aplicación >*. exe.config archivo:  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
3.  En una aplicación de Windows Forms de C++, también debe establecer `DebuggableAttribute` en un archivo .config o en el código. Si se compila con [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) y sin [/Og](/cpp/build/reference/og-global-optimizations), el compilador establece este atributo automáticamente. Sin embargo, si desea depurar una compilación de versión no optimizada, deberá establecerlo personalmente. Puede hacerlo agregando la siguiente línea al archivo AssemblyInfo.cpp de la aplicación:  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     Para obtener más información, consulta <xref:System.Diagnostics.DebuggableAttribute>.  
  
## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Usar la depuración Just-In-Time  
 En esta sección se muestra lo que sucede cuando un archivo ejecutable produce una excepción.  
  
 Debe tener Visual Studio instalado para seguir estos pasos. Si no tiene Visual Studio, puede descargar gratuitamente [Visual Studio Community Edition](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).  
  
 Asegúrese de que ese Just-In-Time de depuración es [habilitado](#BKMK_Enabling).
  
 Para los fines de esta sección, nos aseguraremos de hacer una aplicación de consola de C# en Visual Studio que se inicia un [NullReferenceException](http://msdn.microsoft.com/Library/658af786-d893-4114-a3c5-31c7d586056a).  
  
 En Visual Studio, cree una aplicación de consola de C# (**archivo > Nuevo > proyecto > Visual C# > aplicación de consola**) denominado **ThrowsNullException**. Para obtener más información sobre cómo crear proyectos en Visual Studio, vea [Tutorial: crear una aplicación sencilla](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).  
  
 Cuando se abre el proyecto en Visual Studio, abra el archivo Program.cs. Reemplace el método Main() por el código siguiente, que imprime una línea en la consola y, a continuación, genera una excepción NullReferenceException:  
  
```csharp  
static void Main(string[] args)  
{  
    Console.WriteLine("we will now throw a NullReferenceException");  
    throw new NullReferenceException("this is the exception thrown by the console app");  
}  
```  
  
> [!IMPORTANT]
>  Para este procedimiento para que funcione un [configuración release](../debugger/how-to-set-debug-and-release-configurations.md), necesita desactivar [solo mi código](../debugger/just-my-code.md). En Visual Studio, haga clic en **Herramientas > opciones**. En el **opciones** cuadro de diálogo, seleccione **depuración**. Quitar la marca de verificación de **habilitar solo mi código**.  
  
 Compile la solución (en Visual Studio, elija **generar > volver a generar solución**). Puede elegir la depuración o la configuración de lanzamiento (elija **depurar** de la experiencia de depuración completa). Para obtener más información acerca de las configuraciones de compilación, consulte [descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).  
  
 El proceso de compilación crea un archivo ejecutable ThrowsNullException.exe. Puede encontrarlo en la carpeta donde se creó el proyecto de C#: **...\ThrowsNullException\ThrowsNullException\bin\Debug** o **...\ThrowsNullException\ThrowsNullException\bin\Release**.  
  
 Haga doble clic en el ThrowsNullException.exe. Debería ver una ventana de comandos similar al siguiente:  
  
 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")  
  
 Después de unos segundos, aparece una ventana de error:  
  
 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")  
  
 No haga clic en **cancelar**! Después de unos segundos, verá dos botones, **depurar** y **cerrar programa**. Haga clic en **depurar**.  
  
> [!CAUTION]
>  Si la aplicación contiene código de confianza, aparecerá un cuadro de diálogo con una advertencia de seguridad. Este cuadro de diálogo le permite decidir si desea continuar o no con la depuración. Antes de continuar con la depuración, decida si confía en el código. ¿Escribió el código usted mismo? ¿Confía en el codificador? Si la aplicación se ejecuta en un equipo remoto, ¿reconoce el nombre del proceso? Incluso si la aplicación se ejecuta localmente, no significa necesariamente que se pueda confiar en ella. Considere la posibilidad de que código malintencionado pueda ejecutarse en el equipo. Si decide que el código que va a depurar es de confianza, haga clic en **depurar**. En caso contrario, haga clic en **no depurar**.  
  
 El **depurador de Visual Studio Just** aparecerá la ventana:  
  
 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")  
  
 En **posibles depuradores**, debería ver que la **nueva instancia de Microsoft Visual Studio <available version>**  línea está activada. Si aún no está activada, selecciónela.  
  
 En la parte inferior de la ventana, en **¿desea depurar utilizando el depurador seleccionado?**, haga clic en **Sí**.  
  
 El proyecto de ThrowsNullException se abre en una nueva instancia de Visual Studio, con la ejecución detenida en la línea que produce la excepción:  
  
 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")  
  
 Puede iniciar la depuración en este momento. Si se tratara de una aplicación real, necesitará averiguar por qué el código que produce la excepción.  
  
## <a name="just-in-time-debugging-errors"></a>Errores de la depuración Just-In-Time  
 Si no ve el cuadro de diálogo cuando el programa se bloquea, esto puede ser debido a la configuración de informe de errores de Windows en el equipo. Para obtener más información, consulte [. La configuración de WER](/windows-hardware/drivers/dashboard/windows-error-reporting-getting-started).  
  
 Es posible que aparezcan los siguientes mensajes de error asociados a la depuración Just-In-Time.  
  
-   **No se puede adjuntar al proceso de bloqueo. El programa especificado no es un programa de Windows o MS-DOS.**  
  
     Este error se produce cuando se intenta asociar a un proceso que se ejecuta como otro usuario.  
  
     Para solucionar este problema, inicie Visual Studio, abra el **adjuntar al proceso** cuadro de diálogo desde el **depurar** menú y busque el proceso que desea depurar en el **procesos disponibles**lista. Si no conoce el nombre del proceso, examine la **depurador de Visual Studio Just** cuadro de diálogo y anote el identificador del proceso. Seleccione el proceso en el **procesos disponibles** lista y haga clic en **adjuntar**. En el **depurador de Visual Studio Just** cuadro de diálogo, haga clic en **n** para descartar el cuadro de diálogo.  
  
-   **No se pudo iniciar el depurador porque ningún usuario ha iniciado sesión.**  
  
     Este error se produce cuando la depuración Just-In-Time intenta iniciar Visual Studio en un equipo en el que no hay ningún usuario que haya iniciado sesión en la consola. Como no ha iniciado sesión ningún usuario, no hay ninguna sesión de usuario que se pueda mostrar el cuadro de diálogo de depuración Just-In-Time.  
  
     Para solucionar este problema, inicie una sesión en el equipo.  
  
-   **Clase no registrada.**  
  
     Este error indica que el depurador intentó crear una clase COM que no está registrada, probablemente debido a un problema de instalación.  
  
     Para solucionar este problema, utilice el disco de instalación para reinstalar o reparar la instalación de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Just-In-Time, depuración, cuadro de diálogo Opciones](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)