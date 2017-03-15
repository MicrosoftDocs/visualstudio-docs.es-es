---
title: "Depuraci&#243;n Just-In-Time en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "CSharp"
  - "VB"
helpviewer_keywords: 
  - "depurar [Visual Studio], Just-In-Time"
  - "depuración Just-In-Time"
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 48
caps.handback.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depuraci&#243;n Just-In-Time en Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La depuración Just\-In\-Time inicia Visual Studio automáticamente cuando se produce una excepción o un bloqueo en una aplicación que se ejecuta fuera de Visual Studio.  Esto permite probar la aplicación cuando Visual Studio no se está ejecutando y comenzar la depuración con Visual Studio cuando se produce un problema.  
  
 La depuración Just\-In\-Time no funciona para las aplicaciones de la Tienda Windows.  La depuración Just\-In\-Time no funciona para el código administrado que se hospeda en una aplicación nativa, por ejemplo los visualizadores.  
  
## Usar la depuración Just\-In\-Time  
 Cuando se instala Visual Studio, la depuración Just\-In\-Time está habilitada de forma predeterminada.  Si necesita deshabilitar o volver a habilitar la depuración Just\-In\-Time, vea [Restringir la ejecución paso a paso a Solo mi código](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Cuando la depuración Just\-In\-Time está habilitada, puede probar su aplicación fuera de Visual Studio.  Cuando se produce un bloqueo o una excepción, aparecerá un cuadro de diálogo con un mensaje que tendrá un aspecto similar al siguiente:  
  
 Se ha producido una excepción no controlada \('System.TypeInitializationException'\) en terrarium.exe \[3384\]  
  
 Cuando aparece este cuadro de diálogo, puede empezar a depurar mediante el procedimiento siguiente.  
  
#### Para comenzar la depuración Just\-In\-Time cuando se produce un error  
  
1.  En el cuadro de diálogo Depuración Just\-In\-Time, en la lista **Depuradores posibles**, haga clic en **Nueva instancia de Visual Studio 2015** o haga clic en una instancia de Visual Studio que ya esté en ejecución.  
  
2.  Para usar Visual Studio automáticamente para todos los futuros bloqueos, haga clic en **Establecer depurador seleccionado como predeterminado**.  
  
3.  Si desea elegir el tipo de código que podrá depurar, haga clic en **Seleccionar manualmente los motores de depuración**.  Si no elige esta opción, Visual Studio seleccionará automáticamente los motores de depuración adecuados para el tipo de código del programa.  
  
4.  Haga clic en **Aceptar**.  
  
5.  Si la aplicación contiene un ensamblado con código que no es de confianza, aparecerá un cuadro de diálogo con una advertencia de seguridad.  Este cuadro de diálogo le permite decidir si desea continuar o no con la depuración.  Antes de continuar con la depuración, decida si confía en el código.  ¿Escribió el código usted mismo?  ¿Confía en el codificador?  Si la aplicación se ejecuta en un equipo remoto, ¿reconoce el nombre del proceso?  Incluso si la aplicación se ejecuta localmente, no significa necesariamente que se pueda confiar en ella.  En Internet Explorer, por ejemplo, podría ejecutarse un control ActiveX malintencionado.  Considere la posibilidad de que dicho código malintencionado pueda ejecutarse en su equipo.  Si decide que el código que va a depurar es de confianza, haga clic en **Depurar**.  En caso contrario, haga clic en **No depurar**.  
  
##  <a name="BKMK_Enabling"></a> Habilitar o deshabilitar la depuración Just\-In\-Time  
 Puede habilitar o deshabilitar la depuración Just\-In\-Time en el cuadro de diálogo **Opciones**.  
  
#### Para habilitar o deshabilitar la depuración Just\-In\-Time  
  
1.  En el menú **Herramientas**, haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, seleccione la carpeta **Depuración**.  
  
3.  En la carpeta **Depuración**, seleccione la página **Just\-In\-Time**.  
  
4.  En el cuadro **Habilitar depuración Just\-In\-Time de estos tipos de código**, seleccione o quite la selección de los tipos de programa pertinentes: **Administrado**, **Nativo** o **Script**.  
  
     Para deshabilitar la depuración Just\-In\-Time, una vez habilitada, debe estar ejecutando con privilegios de Administrador.  Al habilitar la depuración Just\-In\-Time, se establece una clave del Registro y se necesitan privilegios de Administrador para modificar dicha clave.  
  
5.  Haga clic en **Aceptar**.  
  
 De forma predeterminada, las aplicaciones de Windows Forms tienen un controlador de excepciones de nivel superior que permite que el programa continúe ejecutándose si puede recuperar.  Como resultado, debe realizar los siguientes pasos adicionales para habilitar la depuración Just\-In\-Time de una aplicación de Windows Forms.  
  
#### Para habilitar la depuración Just\-In\-Time para un Windows Form  
  
1.  Establezca el valor `jitDebugging` en `true` en la sección `system.windows.form` del archivo machine.config o *application*.exe.config:  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
2.  En una aplicación de Windows Forms de C\+\+, también debe establecer `DebuggableAttribute` en un archivo .config o en el código.  Si compila con la opción [\/Zi](/visual-cpp/build/reference/z7-zi-zi-debug-information-format) y sin la opción [\/Og](/visual-cpp/build/reference/og-global-optimizations), el compilador establece este atributo automáticamente.  Sin embargo, si desea depurar una compilación de versión no optimizada, deberá establecerlo personalmente.  Puede hacerlo agregando la siguiente línea al archivo AssemblyInfo.cpp de la aplicación:  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     Para obtener más información, vea <xref:System.Diagnostics.DebuggableAttribute>.  
  
 La depuración Just\-In\-Time todavía puede habilitarse aunque ya no esté instalado Visual Studio en el equipo.  Si Visual Studio no está instalado, no se puede deshabilitar la depuración Just\-In\-Time en el cuadro de diálogo **Opciones** de Visual Studio.  En ese caso, puede deshabilitar la depuración Just\-In\-Time editando el Registro de Windows.  
  
#### Para deshabilitar la depuración Just\-In\-Time editando el Registro  
  
1.  En el menú **Inicio**, busque `regedit.exe` y ejecútelo  
  
2.  En la ventana **Editor del Registro**, busque y elimine las siguientes claves del Registro:  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
3.  Si el equipo está ejecutando un sistema operativo de 64 bits, elimine también las siguientes claves del Registro:  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
4.  Tenga cuidado de no eliminar ni cambiar accidentalmente ninguna otra clave del Registro.  
  
5.  Cierre la ventana **Editor del Registro**.  
  
## Errores de la depuración Just\-In\-Time  
 Es posible que aparezcan los siguientes mensajes de error asociados a la depuración Just\-In\-Time.  
  
-   **No se puede adjuntar al proceso de bloqueo.  El programa especificado no es un programa para Windows o MS\-DOS.**  
  
     Este error se produce cuando el usuario intenta asociarse a un proceso que se ejecuta como otro usuario en Windows 2000.  
  
     Para solucionar este problema, inicie Visual Studio, abra el cuadro de diálogo **Asociar al proceso** en el menú **Depurar** y busque el proceso que desea depurar en la lista **Procesos disponibles**.  Si desconoce el nombre del proceso, vaya al cuadro de diálogo **Depurador Just\-In\-Time de Visual Studio** y anote el identificador del proceso.  Seleccione el proceso en la lista **Procesos disponibles** y haga clic en **Asociar**.  En el cuadro de diálogo **Depurador Just\-In\-Time de Visual Studio**, haga clic en **No** para descartar el cuadro de diálogo.  
  
-   **No se pudo iniciar el depurador porque no hay usuarios conectados.**  
  
     Este error se produce cuando la depuración Just\-In\-Time intenta iniciar Visual Studio en un equipo en el que no hay ningún usuario que haya iniciado sesión en la consola.  Como no ha iniciado sesión ningún usuario, no hay ninguna sesión de usuario que se pueda mostrar el cuadro de diálogo de depuración Just\-In\-Time.  
  
     Para solucionar este problema, inicie una sesión en el equipo.  
  
-   **No se ha registrado la clase.**  
  
     Este error indica que el depurador intentó crear una clase COM que no está registrada, probablemente debido a un problema de instalación.  
  
     Para solucionar este problema, utilice el disco de instalación para reinstalar o reparar la instalación de Visual Studio.  
  
## Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Just\-In\-Time, Depuración, Opciones \(Cuadro de diálogo\)](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [Advertencia de seguridad: adjuntar a un proceso que pertenezca a una cuenta de usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)