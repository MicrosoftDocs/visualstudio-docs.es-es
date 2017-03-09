---
title: "The application cannot start. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A0001"
  - "vs.message.VB_E_IDACANTBOOT"
ms.assetid: ffc123a0-99e1-4e9d-8f6e-34aa357bf98f
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The application cannot start.
Un error inesperado ha impedido que Visual Studio se inicie.  Este error aparece cuando se produce uno de los siguientes elementos:  
  
-   El entorno de desarrollo integrado \(IDE\) no pudo cargar Msxml3.dll.  
  
-   El IDE no pudo cargar Mso.dll.  
  
-   El IDE no pudo cargar DTE.olb.  
  
-   La clave de licencia para Visual Studio no se creó durante la instalación.  
  
-   Bloqueo de script está activo y no permite la ejecución de código de scripting.  
  
-   El programa de instalación de .NET Framework, componente necesario para Visual Studio, no pudo generar una imagen nativa válida para mscorlib.dll.  
  
-   El virus Klez está presente en el equipo.  
  
 Use los procedimientos siguientes para corregir este error.  
  
> [!WARNING]
>  Algunas de estas soluciones requieren que se modifique la clave del Registro.  Si usa el Editor del Registro de forma incorrecta, puede originar problemas graves que podrían requerir la reinstalación del sistema operativo.  Microsoft no puede garantizar que pueda solucionar los problemas derivados del uso incorrecto del Editor del Registro.  Use el Editor del Registro bajo su propia responsabilidad.  
  
 El IDE no pudo cargar Msxml3.dll.  
 En julio de 2001, la versión Beta de MSXML 4.0 Technology Preview dejó el equipo en un estado que causa este comportamiento.  Para reparar el registro de Msxml3.dll, siga estos pasos:  
  
### Desinstalar Msxml4.dll  
  
1.  En el menú **Inicio**, elija **Ejecutar**.  
  
2.  En el cuadro de texto **Abrir**, escriba `regsvr32 /u c:\winnt\system32\msxml4.dll` y haga clic en **Aceptar**.  
  
### Descargue e instale la actualización de seguridad para MSXML  
  
1.  Descargue la última actualización de seguridad para la versión de MSXML instalada en el equipo desde [http:\/\/www.microsoft.com\/windows\/ie\/downloads\/critical\/q317244\/download.asp](http://www.microsoft.com/windows/ie/downloads/critical/q317244/download.asp).  
  
2.  Ejecute el archivo .exe de la actualización de seguridad.  
  
### Descargue y aplique los valores del Registro actualizados  
  
1.  Descargue los valores del registro actualizados de [http:\/\/download.microsoft.com\/download\/VisualStudioNET\/fix\/1.0\/WIN98MeXP\/Fixxml4.exe](http://download.microsoft.com/download/VisualStudioNET/fix/1.0/WIN98MeXP/Fixxml4.exe).  
  
2.  Haga doble clic en fixxml4.exe y descomprima los archivos.  
  
3.  Busque Fixxml4.reg y haga doble clic en el archivo para actualizar los valores del Registro.  
  
 El IDE no pudo cargar Mso.dll.  
 Use la lista siguiente para corregir problemas con Mso.dll.  
  
### Microsoft Office  
  
-   Desinstale cualquier versión Beta de Microsoft Office XP del equipo.  
  
-   Repare Office XP en Agregar o quitar programas.  
  
-   En el Editor del Registro, compruebe la clave del Registro siguiente:  
  
     `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0\Path] "MSO"="C:\Program Files\Common Files\Microsoft Shared\Office10\MSO.DLL"`  
  
 El IDE no pudo cargar DTE.olb.  
 Para corregir este error:  
  
### Registrar Dte.olb  
  
1.  En el menú **Inicio**, elija **Ejecutar**.  
  
2.  En el cuadro de texto **Abrir**, escriba `regsvr32 C:\Program Files\Common Files\Microsoft Shared\MSEnv\DTE.OLB` y haga clic en **Aceptar**.  
  
 La clave de licencia para Visual Studio no se creó durante la instalación.  
 Si la pantalla de presentación de Visual Studio no contiene una lista de los productos instalados y no incluye información sobre la persona que instaló el producto, falta la clave de licencia.  Además, si Visual Studio no aparece en el cuadro de diálogo Agregar o quitar programas, falta la clave de licencia.  
  
 Para solucionar este problema:  
  
### Crear una clave de licencia para Visual Studio  
  
-   Quite completamente Visual Studio del equipo y vuelva a instalar el producto.  
  
 Bloqueo de script está activo y no permite la ejecución de código de scripting.  
 Si una aplicación de terceros tiene habilitado el bloqueo de scripts, el IDE aparecerá y desaparecerá.  
  
-   Para corregir este problema, compruebe que la característica de bloqueo de scripts funciona correctamente.  
  
 El programa de instalación de .NET Framework, componente necesario para Visual Studio, no pudo generar una imagen nativa válida para mscorlib.dll.  
 Si la pantalla de presentación de Visual Studio aparece brevemente y después desaparece, puede que falte una imagen nativa válida para el archivo Mscorlib.dll.  Este archivo se crea durante la instalación de .NET Framework en el directorio \\%windir%\\assembly\\NativeImages1\_v1.0.3705\\mscorlib.  
  
 Para corregir este problema:  
  
### Crear un archivo Mscorlib.dll válido  
  
1.  Desinstale y reinstale .NET Framework.  
  
 El virus Klez está presente en el equipo.  
 Si el equipo está infectado con este virus, puede que aparezca el error "No se puede iniciar la aplicación".  Se recomienda que actualice el software antivirus y después analice el equipo en busca de virus.