---
title: Depurar con el depurador Just In Time | Microsoft Docs
ms.date: 09/24/18
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fbdf32377db26cdb3696187248bd9b8becb8de24
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831555"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Depurar con el depurador Just In Time en Visual Studio

Depuración Just-In-Time puede iniciar Visual Studio automáticamente cuando una aplicación que se ejecuta fuera de los errores de Visual Studio o se bloquea. Con Just-In-Time de depuración, puede probar aplicaciones fuera de Visual Studio y abra Visual Studio para comenzar la depuración cuando se produce un problema.

Depuración Just-In-Time funciona para aplicaciones de escritorio de Windows. No funciona para aplicaciones universales de Windows o de código administrado que se hospeda en una aplicación nativa, por ejemplo los visualizadores.

> [!TIP]
> Si solo desea detener el cuadro de diálogo de depurador Just In Time de encendido, pero no tiene instalado Visual Studio, vea [deshabilita el depurador Just In Time](../debugger/just-in-time-debugging-in-visual-studio.md). Si tenía una vez instalado Visual Studio, es posible que deba [Just-In-Time de deshabilitar la depuración desde el registro de Windows](#disable-just-in-time-debugging-from-the-windows-registry). 

##  <a name="BKMK_Enabling"></a> Habilitar o deshabilitar la depuración en Visual Studio Just-In-Time

>[!NOTE]
>Para habilitar o deshabilitar la depuración Just-In-Time, debe ejecutar Visual Studio como administrador. Habilitación o deshabilitación de Just-In-Time depuración establece una clave del registro, y es posible que se requieren privilegios de administrador para modificar dicha clave. Para abrir Visual Studio como administrador, haga clic en la aplicación de Visual Studio y elija **ejecutar como administrador**. 

Puede configurar la depuración de Visual Studio Just-In-Time **herramientas** > **opciones** (o **depurar** > **opciones**) cuadro de diálogo. 

**Para habilitar o deshabilitar la depuración Just-In-Time:**

1. En el **herramientas** o **depurar** menú, seleccione **opciones** > **depuración**  >   **Just-In-Time**.

   ![Habilitar o deshabilitar la depuración JIT](../debugger/media/dbg-jit-enable-or-disable.png "habilitar o deshabilitar la depuración JIT")

1. En el **Just habilitar la depuración para estos tipos de código** , seleccione los tipos de código que desee para depurar la depuración Just-In-Time: **Managed**, **nativo**, o **Script**.
   
1. Seleccione **Aceptar**.

Si se habilita Just-In-Time depurador, pero no se abre cuando se bloquea una aplicación o errores, vea [depuración Just solucionar](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Deshabilitar la depuración desde el registro de Windows Just-In-Time

La depuración Just-In-Time todavía puede habilitarse aunque ya no esté instalado Visual Studio en el equipo. Si ya no está instalado Visual Studio, puede deshabilitar editando el registro de Windows la depuración Just-In-Time.

**Para deshabilitar la depuración Just-In-Time mediante la edición del Registro:**

1.  Desde el Windows **iniciar** menú, ejecute el **Editor del registro** (*regedit.exe*).

2.  En el **Editor del registro** ventana, busque y elimine las entradas del registro siguientes:

    -   **HKEY_LOCAL_MACHINE\Software\Microsoft\\. NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Clave del registro JIT](../debugger/media/dbg-jit-registry.png "clave del registro JIT")

3.  Si el equipo se está ejecutando un sistema operativo de 64 bits, también elimina las entradas del registro siguientes:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Asegúrese de no eliminar o cambiar cualquier otra clave del registro.

5.  Cerrar la **Editor del registro** ventana.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Habilitar Just-In-Time de depuración de un formulario de Windows

De forma predeterminada, las aplicaciones de formulario de Windows tienen un controlador de excepciones de nivel superior que permite que la aplicación se seguirá ejecutando si se recupera. Si una aplicación de Windows Forms produce una excepción no controlada, muestra el cuadro de diálogo siguiente:

![Excepción no controlada del formulario de Windows](../debugger/media/windowsformsunhandledexception.png "excepción no controlada del formulario de Windows")

Para habilitar la depuración en lugar de control de errores de formulario de Windows estándar Just-In-Time, agregue estos valores:

-  En el `system.windows.forms` sección de la *machine.config* o  *\<nombre de la aplicación >. exe.config* de archivos, establezca el `jitDebugging` valor `true`:
    
    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```
    
-  En una aplicación de formulario de Windows de C++, también establece `DebuggableAttribute` a `true` en un *.config* archivo o en el código. Si compila con la opción [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) y sin la opción [/Og](/cpp/build/reference/og-global-optimizations), el compilador establece este atributo automáticamente. Si desea depurar una compilación de versión no optimizada, sin embargo, debe establecer `DebuggableAttribute` agregando la siguiente línea en la aplicación *AssemblyInfo.cpp* archivo:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```
   
   Para obtener más información, vea <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="BKMK_Using_JIT"></a>Usar Just-In-Time de depuración
 En este ejemplo le guiará a través de cuando una aplicación produce un error de depuración Just-In-Time.

 - Debe tener Visual Studio instalado para seguir estos pasos. Si no tiene Visual Studio, puede descargar la versión gratuita [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).
   
 - Asegúrese de que Just-In-Time de depuración es [habilitado](#BKMK_Enabling) en **herramientas** > **opciones** > **depuración**  >  **Just-In-Time**.

En este ejemplo, podrá realizar un C# aplicación de consola en Visual Studio inicia un [NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. En Visual Studio, cree un C# aplicación de consola (**archivo** > **New** > **proyecto** > **Visual C#**   >  **Aplicación de consola**) denominado *ThrowsNullException*. Para obtener más información sobre cómo crear proyectos en Visual Studio, consulte [Tutorial: Creación de una aplicación sencilla](/visualstudio/get-started/csharp/tutorial-wpf)
   
1. Cuando se abre el proyecto en Visual Studio, abra el *Program.cs* archivo. Reemplace el método Main() por el código siguiente, que imprime una línea en la consola y, a continuación, genera una excepción NullReferenceException:
   
   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```
   
1. Para compilar la solución, elija el **depurar** (valor predeterminado) o **versión** configuración y, a continuación, seleccione **compilar** > **volver a generar solución** . 
   
   >[!NOTE]
   >- Elija **depurar** configuración para la experiencia de depuración completa. 
   >- Si selecciona [versión](../debugger/how-to-set-debug-and-release-configurations.md) configuración, debe desactivar la opción [solo mi código](../debugger/just-my-code.md) para que funcione este procedimiento. En **herramientas** > **opciones** > **depuración**, anule la selección de **habilitar solo mi código**.
   Para más información sobre las configuraciones de compilación, consulte [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).
   
1. Abra la aplicación compilada *ThrowsNullException.exe* en su C# carpeta del proyecto (*...\ThrowsNullException\ThrowsNullException\bin\Debug* o *...\ThrowsNullException\ ThrowsNullException\bin\Release*). 
   
   Debería ver la ventana de comandos siguiente:
   
   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")
   
1. El **elija Just In Time depurador** abre el cuadro de diálogo.
   
   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")
   
   En **depuradores disponibles**, seleccione **nueva instancia de \<su versión o edición de Visual Studio preferida >**, si aún no está seleccionada. 
   
1. Seleccione **Aceptar**.
   
   El proyecto ThrowsNullException se abre en una nueva instancia de Visual Studio, con la ejecución se detendrá en la línea que produjo la excepción:
   
   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

Puede iniciar la depuración en este momento. Si se depura una aplicación real, deberá averiguar por qué el código que produce la excepción.

> [!CAUTION]
> Si la aplicación contiene código no seguro, aparece un cuadro de diálogo de advertencia de seguridad, lo que le permite decidir si desea continuar con la depuración. Antes de continuar la depuración, decida si confía en el código. ¿Escribió el código usted mismo? Si la aplicación se ejecuta en un equipo remoto, ¿reconoce el nombre del proceso? Si la aplicación se ejecuta localmente, considere la posibilidad de código malintencionado que se ejecuta en el equipo. Si decide que el código es de confianza, seleccione **Aceptar**. En caso contrario, haga clic en **Cancelar**.

## <a name="jit_errors"></a> Just-In-Time de la solución de problemas de depuración 

Si Just-In-Time de depuración no se inicia cuando se bloquea una aplicación, incluso si está habilitado en Visual Studio:

- En el control de errores en el equipo podría estar asumiendo el informe de errores de Windows. 
  
  Para corregir este problema, utilice el Editor del registro para agregar un **valor DWORD** de **deshabilitado**, con **datos del valor** de **1**, a las siguientes claves del registro:
  
  

  - **Informe de errores de HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows**
    
  - (Para equipos de 64 bits): **Informe de errores de HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows**
  
  Para obtener más información, consulte [. La configuración de WER](https://docs.microsoft.com/windows/desktop/wer/wer-settings).
  
- Un problema conocido de Windows puedan estar causando Just-In-Time depurador para producir un error. 
  
  La solución consiste en Agregar un **valor DWORD** de **automática**, con **datos del valor** de **1**, a las siguientes claves del registro:
  
  
  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**
    
  - (Para equipos de 64 bits): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Es posible que vea los siguientes mensajes de error durante Just-In-Time de depuración:

- **No se puede adjuntar al proceso de bloqueo. El programa especificado no es un programa para Windows o MS-DOS.**

    El depurador intentó asociar a un proceso que se ejecutan en otro usuario.

    Para solucionar este problema, en Visual Studio, abra **depurar** > **asociar al proceso**y busque el proceso que desee depurar en el **procesos disponibles** lista. Si no conoce el nombre del proceso, busque el identificador de proceso en el **Just In Time de Visual Studio Debugger** cuadro de diálogo. Seleccione el proceso en el **procesos disponibles** lista y seleccione **adjuntar**. Seleccione **n** Just-In-Time de descartar el cuadro de diálogo de depurador.

- **No se pudo iniciar el depurador porque no hay usuarios conectados.**

    No hay ningún usuario haya iniciado sesión en la consola, por lo que no hay ninguna sesión de usuario para mostrar Just-In-Time cuadro de diálogo de depuración.

    Para solucionar este problema, inicie una sesión en el equipo.

- **No se ha registrado la clase.**

    El depurador intentó crear una clase COM que no está registrada, probablemente debido a un problema de instalación.

    Para corregir este problema, utilice al instalador de Visual Studio para reinstalar o reparar la instalación de Visual Studio.

## <a name="see-also"></a>Vea también
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Opciones, depuración, Just-In-Time cuadro de diálogo](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
