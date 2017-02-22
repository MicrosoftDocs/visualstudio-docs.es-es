---
title: "Elementos del Shell aislado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Shell de Visual Studio, modo aislado"
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Elementos del Shell aislado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede modificar la configuración del registro, configuración de tiempo de ejecución y punto de entrada de la aplicación de la aplicación de shell aislado y sus .vsct, .pkgdef, and.pkgundef archivos.  
  
## Configuración del registro  
 El .pkgdef y los archivos de .pkgundef modifican la configuración del registro para la aplicación de shell aislado. Cuando se ejecuta la aplicación, la configuración del registro se define en la secuencia siguiente:  
  
 Cuando se ejecuta la aplicación, la configuración del registro se define en la secuencia siguiente:  
  
1.  Se crea la clave del registro para la aplicación.  
  
2.  El registro se actualiza desde el archivo .pkgdef de la aplicación definiendo las entradas y claves especificadas.  
  
3.  Para cada paquete que forma parte de la aplicación, se actualiza el registro desde el archivo .pkgdef de ese paquete. Cada paquete se define en el archivo .pkgdef de la aplicación mediante el \\Packages\\$ $RootKey {*vsPackageGuid*} clave para el paquete.  
  
4.  El registro se actualiza desde el AppEnvConfig.pkgdef y BaseConfig.pkgdef en el *ruta de instalación del SDK de Visual Studio*\\Common7\\IDE\\ShellExtensions\\Platform directory. Estos archivos forman parte de Visual Studio y también parte del paquete redistribuible de Visual Studio Shell \(modo aislado\).  
  
5.  Quitando las entradas y claves especificadas, se actualiza el registro desde el archivo .pkgundef de la aplicación.  
  
## Configuración de tiempo de ejecución  
 Cuando un usuario inicia la aplicación de shell aislado, llama el punto de entrada de inicio del shell de Visual Studio. Configuración de la aplicación se define cuando se inicia la aplicación, como sigue:  
  
1.  El shell de Visual Studio comprueba el registro de aplicación para las teclas específicas. Si se especifica el valor de una clave en la llamada al punto de entrada de inicio, ese valor reemplaza el valor del registro.  
  
2.  Si el registro ni la entrada de punto parámetro especifica el valor de configuración, se utiliza el valor predeterminado para la configuración.  
  
 Cuando un usuario inicia la aplicación desde la línea de comandos, todos los conmutadores de línea de comandos se pasan al shell de Visual Studio, que se trata de la misma manera que para Devenv. Para obtener más información acerca de los modificadores de Devenv, consulte [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md) y [Modificadores de línea de comandos devenv para el desarrollo de VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Para obtener más información acerca de cómo se registra un paquete para los conmutadores de línea de comandos, consulte [Agregando modificadores de línea de comandos](../extensibility/adding-command-line-switches.md).  
  
## El punto de entrada de inicio  
 El archivo Appenvstub.dll contiene puntos de entrada para acceder al shell aislado. Cuando se inicia la aplicación, llama el punto de entrada de inicio de Appenvstub.dll.  
  
 Puede cambiar el comportamiento de la aplicación cambiando el valor del último parámetro que se pasa al punto de entrada de inicio. Para obtener más información, consulta [Parámetros de punto de entrada de Shell aislado \(C\+\+\)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## El archivo. Archivo de Vsct  
 El archivo .vsct permite especificar qué elementos de interfaz de usuario de Visual Studio estándares están disponibles en la aplicación. Para obtener más información, consulta [. Archivos de Vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## El archivo. Archivo Pkgundef  
 Cuando la aplicación se instala en un equipo en el que ya está instalado Visual Studio, se realiza una copia de las entradas del registro de Visual Studio para la aplicación. De forma predeterminada, la aplicación utiliza VSPackages que ya están instalados en el equipo. El archivo .pkgundef permite excluir las entradas del registro para quitar los elementos específicos de la shell de Visual Studio o las extensiones de la aplicación. Para obtener más información, consulta [. Archivos de Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 El archivo .pkgundef permite excluir las entradas del registro para quitar los elementos específicos de la shell de Visual Studio o las extensiones de la aplicación. Para obtener más información, consulta [. Archivos de Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 El conjunto de GUID que puede excluir de paquete se enumeran en [GUID del paquete de características de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## El archivo. Archivo pkgdef  
 El archivo .pkgdef le permite definir entradas del registro para la aplicación que se establecen cuando se instala la aplicación. Para obtener una descripción del archivo .pkgdef y una lista de entradas del registro que utiliza el shell de Visual Studio, consulte [. Archivos pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## Cadenas de sustitución  
 Se muestran las cadenas de sustitución que se usan en los archivos .pkgdef y .pkgundef en [Cadenas de sustitución que se usan en. Pkgdef y. Archivos de Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## Otras opciones  
 Si la aplicación de shell aislado depende de Microsoft.VisualStudio.GraphModel.dll, debe agregar la siguiente redirección de enlace al archivo .config de la aplicación de Shell aislado:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```