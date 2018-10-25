---
title: Depuración Just-In-Time en Visual Studio | Documentos de Microsoft
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
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2fdbbd98833ff43e07b17f605b6c3a105eb3efe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940586"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Depuración Just-In-Time en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La depuración Just-In-Time inicia Visual Studio automáticamente cuando se produce una excepción o un bloqueo en una aplicación que se está ejecutando fuera de Visual Studio. Esto permite probar la aplicación cuando no se está ejecutando Visual Studio y comenzar la depuración con Visual Studio cuando se produce un problema.

Depuración Just-In-Time funciona para aplicaciones de escritorio de Windows. No funciona para aplicaciones universales de Windows y no funciona para código administrado que se hospeda en una aplicación nativa, por ejemplo los visualizadores.

## <a name="BKMK_Scenario"></a> ¿Hizo Just-in-Time aparece el cuadro de diálogo de depurador cuando se intenta ejecutar una aplicación?

Las acciones que debe realizar cuando ve el Visual Studio Just-in-Time cuadro de diálogo de depurador dependen de lo que está intentando hacer:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Si desea deshacerse del cuadro de diálogo y solo ejecute la aplicación normalmente

1. (Usuarios avanzados) Si tiene instalado Visual Studio (o se hubiera instalado previamente y la ha quitado), [Just-in-Time de deshabilitar la depuración](#BKMK_Enabling) e intente volver a ejecutar la aplicación.

2. Si está ejecutando una aplicación web en Internet Explorer, deshabilite la depuración de scripts.

    Deshabilitar la depuración de scripts en el cuadro de diálogo Opciones de Internet. Puede tener acceso a esta desde los **Panel de Control** / **red e Internet** / **opciones de Internet** (los pasos exactos dependen de la versión de Windows e Internet Explorer).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Vuelva a abrir la página web donde encontró el error. Si esto no resuelve el problema, póngase en contacto con el propietario de la aplicación web para corregir el problema.

4. Si está ejecutando otro tipo de aplicación de Windows, deberá ponerse en contacto con el propietario de la aplicación para corregir el error y, a continuación, vuelva a instalar la versión corregida de la aplicación.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Si desea corregir o depurar el error (usuarios avanzados)

- Debe tener [instalado Visual Studio](https://www.microsoft.com/download/details.aspx?id=48146) para ver la información detallada sobre el error y se intenta depurarla. Consulte [JIT utilizando](#BKMK_Using_JIT) para obtener instrucciones detalladas. Si no se puede resolver el error y corregir la aplicación, póngase en contacto con el propietario de la aplicación para resolver el error.
  
##  <a name="BKMK_Enabling"></a> Habilitar o deshabilitar Just-In-Time la depuración  
 Puede habilitar o deshabilitar la depuración de Visual Studio Just-In-Time **herramientas / opciones** cuadro de diálogo.  
  
#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Para habilitar o deshabilitar la depuración Just-In-Time  
  
1. Abra Visual Studio. En el menú **Herramientas** , haga clic en **Opciones**.  
  
2. En el **opciones** cuadro de diálogo, seleccione el **depuración** carpeta.  
  
3. En el **depuración** carpeta, seleccione el **Just-In-Time** página.  
  
4. En el **Just Habilitar depuración de estos tipos de código** cuadro, active o desactive los tipos de programa pertinentes: **administrada**, **nativo**, o **Script**.  
  
    Para deshabilitar la depuración Just-In-Time, una vez habilitada, debe estar ejecutando con privilegios de Administrador. Al habilitar la depuración Just-In-Time, se establece una clave del Registro y se necesitan privilegios de Administrador para modificar dicha clave.  
  
5. Haga clic en **Aceptar**.  
  
   La depuración Just-In-Time todavía puede habilitarse aunque ya no esté instalado Visual Studio en el equipo. Cuando no está instalado Visual Studio, no se puede deshabilitar la depuración de Visual Studio Just-In-Time **opciones** cuadro de diálogo. En ese caso, puede deshabilitar la depuración Just-In-Time editando el Registro de Windows.  
  
#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Para deshabilitar la depuración Just-In-Time editando el Registro  
  
1.  En el **iniciar** menú, busque y ejecute `regedit.exe`  
  
2.  En el **Editor del registro** ventana, busque y elimine las entradas del registro de seguimiento:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\Software\Microsoft\\. NETFramework\DbgManagedDebugger  
  
3.  Si el equipo se está ejecutando un sistema operativo de 64 bits, elimine también las siguientes entradas del registro:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger  
  
4.  Tenga cuidado de no eliminar ni cambiar accidentalmente ninguna otra clave del Registro.  
  
5.  Cerrar la **Editor del registro** ventana.  
  
> [!NOTE]
>  Si desea deshabilitar la depuración para una aplicación de servidor Just-In-Time y estos pasos no resuelven el problema, desactive la depuración del lado servidor en la configuración de la aplicación de IIS y vuelva a intentar.  
  
#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Para habilitar la depuración Just-In-Time para un Windows Form  
  
1.  De forma predeterminada, las aplicaciones de Windows Forms tienen un controlador de excepciones de nivel superior que permite que el programa continúe ejecutándose si puede recuperar. Por ejemplo, si la aplicación de Windows Forms produce una excepción no controlada, verá un cuadro de diálogo similar al siguiente:  
  
     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")  
  
     Para habilitar Just-In-Time la depuración de una aplicación de Windows Forms, debe realizar los siguientes pasos adicionales:  
  
2.  Establecer el `jitDebugging` valor `true` en el `system.windows.form` sección del archivo machine.config o  *\<nombre de aplicación >*. archivo exe.config:  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
3.  En una aplicación de Windows Forms de C++, también debe establecer `DebuggableAttribute` en un archivo .config o en el código. Si se compila con [/Zi](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) y sin [/Og](http://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435), el compilador establece este atributo. Sin embargo, si desea depurar una compilación de versión no optimizada, deberá establecerlo personalmente. Puede hacerlo agregando la siguiente línea al archivo AssemblyInfo.cpp de la aplicación:  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     Para obtener más información, consulta <xref:System.Diagnostics.DebuggableAttribute>.  
  
## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Usar la depuración Just-In-Time  
 En esta sección se muestra lo que sucede cuando un archivo ejecutable inicia una excepción.  
  
 Debe tener Visual Studio instalado para seguir estos pasos. Si no tiene Visual Studio, puede descargar la versión gratuita [Visual Studio 2015 Community Edition](https://www.microsoft.com/download/details.aspx?id=48146).  
  
 Cuando se instala Visual Studio, la depuración Just-In-Time está habilitada de forma predeterminada.  
  
 Para los fines de esta sección, haremos una aplicación de consola de C# en Visual Studio inicia un <xref:System.NullReferenceException>.  
  
 En Visual Studio, cree una aplicación de consola de C# (**archivo / nuevo / proyecto / Visual C# / aplicación de consola**) denominado **ThrowsNullException**. Para obtener más información sobre cómo crear proyectos en Visual Studio, consulte [Tutorial: crear una aplicación sencilla](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).  
  
 Cuando se abre el proyecto en Visual Studio, abra el archivo Program.cs. Reemplace el método Main() por el código siguiente, que imprime una línea en la consola y, a continuación, genera una excepción NullReferenceException:  
  
```csharp  
static void Main(string[] args)  
{  
    Console.WriteLine("we will now throw a NullReferenceException");  
    throw new NullReferenceException("this is the exception thrown by the console app");  
}  
```  
  
> [!IMPORTANT]
>  Para este procedimiento para que funcione un [configuración release](../debugger/how-to-set-debug-and-release-configurations.md), deberá desactivar [solo mi código](../debugger/just-my-code.md). En Visual Studio, haga clic en **herramientas / opciones**. En el **opciones** cuadro de diálogo, seleccione **depuración**. Quitar la marca de verificación de **habilitar solo mi código**.  
  
 Compile la solución (en Visual Studio, elija **compilar o recompilar solución**). Puede elegir la depuración o la configuración de lanzamiento. Para más información sobre las configuraciones de compilación, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).  
  
 El proceso de compilación crea un archivo ejecutable ThrowsNullException.exe. Puede encontrarlo en la carpeta donde creó el proyecto de C#: **...\ThrowsNullException\ThrowsNullException\bin\Debug** o **...\ThrowsNullException\ThrowsNullException\bin\Release**.  
  
 Haga doble clic en el ThrowsNullException.exe. Debería ver una ventana de comandos como ésta:  
  
 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")  
  
 Después de unos segundos, aparece una ventana de error:  
  
 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")  
  
 Haga clic en no **cancelar**! Después de unos segundos, debería ver dos botones, **depurar** y **cerrar programa**. Haga clic en **depurar**.  
  
> [!CAUTION]
>  Si la aplicación contiene código no seguro, aparece un cuadro de diálogo con una advertencia de seguridad. Este cuadro de diálogo le permite decidir si desea continuar o no con la depuración. Antes de continuar con la depuración, decida si confía en el código. ¿Escribió el código usted mismo? ¿Confía en el codificador? Si la aplicación se ejecuta en un equipo remoto, ¿reconoce el nombre del proceso? Incluso si la aplicación se ejecuta localmente, no significa necesariamente que se pueda confiar en ella. Considere la posibilidad de código malintencionado que se ejecuta en el equipo. Si decide que el código que va a depurar es de confianza, haga clic en **depurar**. En caso contrario, haga clic en **no depurar**.  
  
 El **Just In Time de Visual Studio Debugger** aparecerá la ventana:  
  
 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")  
  
 En **depuradores posibles**, debería ver que el **nueva instancia de Microsoft Visual Studio 2015** línea seleccionada. Si aún no está activada, selecciónela.  
  
 En la parte inferior de la ventana, en **desea depurar mediante el depurador seleccionado?**, haga clic en **Sí**.  
  
 El proyecto ThrowsNullException se abre en una nueva instancia de Visual Studio, con la ejecución se detendrá en la línea que produce la excepción:  
  
 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")  
  
 Puede iniciar la depuración en este momento. Si se tratara de una aplicación real, deberá averiguar por qué el código que produce la excepción.  
  
## <a name="just-in-time-debugging-errors"></a>Errores de la depuración Just-In-Time  
 Si no ve el cuadro de diálogo cuando el programa se bloquea, esto puede ser debido a la configuración de informes de errores de Windows en el equipo. Para obtener más información, consulte [. La configuración de WER](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).  
  
 Es posible que aparezcan los siguientes mensajes de error asociados a la depuración Just-In-Time.  
  
-   **No se puede asociar al proceso de bloqueo. El programa especificado no es un programa de Windows o MS-DOS.**  
  
     Este error se produce al intentar adjuntar a un proceso que se ejecuta como otro usuario.  
  
     Para solucionar este problema, inicie Visual Studio, abra el **asociar al proceso** cuadro de diálogo desde el **depurar** menú y busque el proceso que desee depurar en el **procesos disponibles**lista. Si no conoce el nombre del proceso, examine el **Just In Time de Visual Studio Debugger** cuadro de diálogo y anote el identificador de proceso. Seleccione el proceso en el **procesos disponibles** lista y haga clic en **adjuntar**. En el **depurador Just In Time de Visual Studio** cuadro de diálogo, haga clic en **No** para descartar el cuadro de diálogo.  
  
-   **No se pudo iniciar el depurador porque ningún usuario haya iniciado sesión.**  
  
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



