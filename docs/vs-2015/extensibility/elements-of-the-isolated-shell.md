---
title: Elementos del Shell aislado | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c051425f2d3ae131362c2d95494ed0edbef5353e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246056"
---
# <a name="elements-of-the-isolated-shell"></a>Elementos del Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede modificar la configuración del registro, configuración de tiempo de ejecución y punto de entrada de la aplicación de la aplicación de shell aislado y su .vsct, .pkgdef, and.pkgundef archivos.  
  
## <a name="registry-settings"></a>Configuración de registro  
 El .pkgdef y los archivos .pkgundef modifican la configuración del registro para la aplicación de shell aislado. Cuando se ejecuta la aplicación, la configuración del registro se define en la siguiente secuencia:  
  
 Cuando se ejecuta la aplicación, la configuración del registro se define en la siguiente secuencia:  
  
1.  Se crea la clave del registro para la aplicación.  
  
2.  El registro se actualiza desde el archivo .pkgdef de la aplicación mediante la definición de las entradas y las claves especificadas.  
  
3.  Para cada paquete que forma parte de la aplicación, se actualiza el registro desde el archivo .pkgdef de ese paquete. Cada paquete se define en el archivo .pkgdef de la aplicación mediante el \Packages $ $RootKey\\{*vsPackageGuid*} clave para el paquete.  
  
4.  El registro se actualiza desde el AppEnvConfig.pkgdef y BaseConfig.pkgdef en el *ruta de instalación del SDK de Visual Studio*\Common7\IDE\ShellExtensions\Platform directory. Estos archivos forman parte de Visual Studio y también parte del paquete redistribuible de Visual Studio Shell (modo aislado).  
  
5.  El registro se actualiza desde el archivo .pkgundef de la aplicación mediante la eliminación de entradas y las claves especificadas.  
  
## <a name="run-time-settings"></a>Configuración de tiempo de ejecución  
 Cuando un usuario inicia la aplicación de shell aislado, llama el punto de entrada de inicio de Visual Studio shell. Configuración de la aplicación se define cuando se inicia la aplicación, como se indica a continuación:  
  
1.  El shell de Visual Studio comprueba el registro de aplicación para determinadas claves. Si se especifica la configuración de una clave en la llamada al punto de entrada de inicio, ese valor reemplaza el valor en el registro.  
  
2.  Si el registro ni la entrada de punto de parámetro especifica el valor de una configuración y luego se usa el valor predeterminado para la configuración.  
  
 Cuando un usuario inicia la aplicación desde la línea de comandos, todos los modificadores de línea de comandos se pasan en el shell de Visual Studio, que se trata de la misma manera que hace de Devenv. Para obtener más información acerca de los modificadores de Devenv, consulte [modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md) y [modificadores de línea de comandos para Devenv para el desarrollo de VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Para obtener más información acerca de cómo se registra un paquete para los modificadores de línea de comandos, consulte [agregar modificadores de línea de comandos](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>El punto de entrada de inicio  
 El archivo Appenvstub.dll contiene puntos de entrada para tener acceso a la shell aislado. Cuando se inicia la aplicación, llama el punto de entrada de inicio de Appenvstub.dll.  
  
 Puede cambiar el comportamiento de la aplicación cambiando el valor del último parámetro que se pasa al punto de entrada de inicio. Para obtener más información, consulte [aislado Shell entrada punto parámetros (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>El archivo. Archivo de Vsct  
 El archivo .vsct le permite especificar qué elementos de interfaz de usuario de Visual Studio estándares están disponibles en la aplicación. Para obtener más información, consulte [. Archivos Vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>El archivo. Archivo Pkgundef  
 Cuando la aplicación se instala en un equipo en el que ya está instalado Visual Studio, se realiza una copia de las entradas del registro de Visual Studio para la aplicación. De forma predeterminada, la aplicación utiliza los VSPackages que ya están instalados en el equipo. El archivo .pkgundef le permite excluir las entradas del registro con el fin de quitar los elementos específicos del shell de Visual Studio o las extensiones de la aplicación. Para obtener más información, consulte [. Archivos Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 El archivo .pkgundef le permite excluir las entradas del registro con el fin de quitar los elementos específicos del shell de Visual Studio o las extensiones de la aplicación. Para obtener más información, consulte [. Archivos Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 El conjunto de GUID que se pueden excluir del paquete se enumeran en [paquete GUID de características de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>El archivo. Archivo pkgdef  
 El archivo .pkgdef le permite definir las entradas del registro para la aplicación que se establecen cuando se instala la aplicación. Para obtener una descripción del archivo .pkgdef y una lista de entradas del registro que utiliza el shell de Visual Studio, consulte [. Archivos pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Cadenas de sustitución  
 Se enumeran las cadenas de sustitución utilizadas en los archivos .pkgdef y .pkgundef en [utilizan las cadenas de sustitución de. Pkgdef y. Archivos Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Otras configuraciones  
 Si la aplicación de shell aislado depende Microsoft.VisualStudio.GraphModel.dll, deberá agregar la siguiente redirección de enlace al archivo .config de la aplicación Shell aislado:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```

