---
redirect_url: shell/elements-of-the-isolated-shell
title: Elementos de Shell aislado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15c32ccd3634529c63eb95eb698c3239b6c0e37e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="elements-of-the-isolated-shell"></a>Elementos de Shell aislado
Puede modificar la configuración del registro, configuración de tiempo de ejecución y punto de entrada de la aplicación de la aplicación de shell aislado y sus .vsct, .pkgdef, and.pkgundef archivos.  
  
## <a name="registry-settings"></a>Configuración de registro  
 El .pkgdef y los archivos de .pkgundef modifican la configuración del registro para la aplicación de shell aislado. Cuando se ejecuta la aplicación, la configuración del registro se define en la siguiente secuencia:  
  
 Cuando se ejecuta la aplicación, la configuración del registro se define en la siguiente secuencia:  
  
1.  Se crea la clave del registro para la aplicación.  
  
2.  El registro se actualiza desde el archivo .pkgdef de la aplicación mediante la definición de las entradas y las claves especificadas.  
  
3.  Para cada paquete que forma parte de la aplicación, se actualiza el registro desde el archivo .pkgdef de ese paquete. Cada paquete se define en el archivo .pkgdef de la aplicación mediante el \Packages $ $RootKey\\{*vsPackageGuid*} clave para el paquete.  
  
4.  El registro se actualiza desde el AppEnvConfig.pkgdef y BaseConfig.pkgdef en el *ruta de instalación del SDK de Visual Studio*\Common7\IDE\ShellExtensions\Platform directory. Estos archivos son parte de Visual Studio y formar parte del paquete redistribuible de Visual Studio Shell (modo aislado).  
  
5.  El registro se actualiza desde el archivo .pkgundef de la aplicación mediante la eliminación de las entradas y las claves especificadas.  
  
## <a name="run-time-settings"></a>Configuración de tiempo de ejecución  
 Cuando un usuario inicia la aplicación de shell aislado, llama el punto de entrada de inicio del shell de Visual Studio. Configuración de la aplicación se define cuando se inicia la aplicación, como se indica a continuación:  
  
1.  El shell de Visual Studio busca en el registro de aplicación para determinadas claves. Si se especifica el valor de una clave en la llamada al punto de entrada de inicio, ese valor reemplaza el valor en el registro.  
  
2.  Si el registro ni la entrada del punto parámetro especifica el valor de una configuración, a continuación, se utiliza el valor predeterminado para la configuración.  
  
 Cuando un usuario inicia la aplicación desde la línea de comandos, todos los modificadores de línea de comandos se pasan en el shell de Visual Studio, que se trata de la misma manera que realiza para Devenv. Para obtener más información acerca de los modificadores de Devenv, vea [Devenv Command Line Switches](../ide/reference/devenv-command-line-switches.md) y [modificadores de línea de comandos de Devenv para el desarrollo de VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Para obtener más información acerca de cómo se registra un paquete para los modificadores de línea de comandos, consulte [agregar modificadores de línea de comandos](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>El punto de entrada de inicio  
 El archivo Appenvstub.dll contiene puntos de entrada para tener acceso a la shell aislado. Cuando se inicia la aplicación, llama el punto de entrada de inicio de Appenvstub.dll.  
  
 Puede cambiar el comportamiento de la aplicación cambiando el valor del último parámetro que se pasa al punto de entrada de inicio. Para obtener más información, consulte [parámetros de punto de entrada de Shell aislado (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>El archivo. Archivo de Vsct  
 El archivo .vsct le permite especificar qué elementos de interfaz de usuario de Visual Studio estándares están disponibles en la aplicación. Para obtener más información, consulte [. Archivos Vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>El archivo. Archivo Pkgundef  
 Cuando la aplicación se instala en un equipo en el que ya está instalado Visual Studio, se crea una copia de las entradas del registro de Visual Studio para la aplicación. De forma predeterminada, la aplicación utiliza VSPackages que ya están instalados en el equipo. El archivo .pkgundef permite excluir las entradas del registro con el fin de quitar los elementos específicos del shell de Visual Studio o las extensiones de la aplicación. Para obtener más información, consulte [. Archivos de Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 El archivo .pkgundef permite excluir las entradas del registro con el fin de quitar los elementos específicos del shell de Visual Studio o las extensiones de la aplicación. Para obtener más información, consulte [. Archivos de Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 El conjunto de GUID que se pueden excluir de paquete se enumeran en [paquete GUID de características de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>El archivo. Pkgdef del archivo  
 El archivo .pkgdef le permite definir las entradas del registro para la aplicación que se establecen cuando se instala la aplicación. Para obtener una descripción del archivo .pkgdef y una lista de entradas del registro que utiliza el shell de Visual Studio, vea [. Archivos pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Cadenas de sustitución  
 Se muestran las cadenas de sustitución que se usa en los archivos .pkgdef y .pkgundef en [utilizan las cadenas de sustitución de. Pkgdef del y. Archivos de Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Otros valores de configuración  
 Si la aplicación de shell aislado depende de Microsoft.VisualStudio.GraphModel.dll, debe agregar la siguiente redirección de enlace al archivo .config de la aplicación de Shell aislado:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```