---
title: Elementos del shell aislado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a95b7da718f050357f6ecd79c90c389dd6085d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204610"
---
# <a name="elements-of-the-isolated-shell"></a>Elementos de Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede modificar la configuración del registro, la configuración de tiempo de ejecución y el punto de entrada de la aplicación de Shell aislado, así como los archivos. Vsct,. pkgdef y. pkgundef.  
  
## <a name="registry-settings"></a>Configuración del Registro  
 Los archivos. pkgdef y. pkgundef modifican la configuración del registro de la aplicación de Shell aislado. Cuando se ejecuta la aplicación, la configuración del registro se define en la secuencia siguiente:  
  
 Cuando se ejecuta la aplicación, la configuración del registro se define en la secuencia siguiente:  
  
1. Se crea la clave del registro de la aplicación.  
  
2. El registro se actualiza a partir del archivo. pkgdef de la aplicación mediante la definición de las claves y entradas especificadas.  
  
3. Para cada paquete que forma parte de la aplicación, el registro se actualiza a partir del archivo. pkgdef de ese paquete. Cada paquete se define en el archivo. pkgdef de la aplicación mediante la clave $RootKey $ \Packages \\ {*vsPackageGuid*} para el paquete.  
  
4. El registro se actualiza desde AppEnvConfig. pkgdef y BaseConfig. pkgdef en el directorio \Common7\IDE\ShellExtensions\Platform de la *ruta de instalación de Visual Studio SDK*. Estos archivos forman parte de Visual Studio y también forman parte del paquete redistribuible de Visual Studio Shell (modo aislado).  
  
5. El registro se actualiza desde el archivo. pkgundef de la aplicación mediante la eliminación de las claves y entradas especificadas.  
  
## <a name="run-time-settings"></a>Configuración en tiempo de ejecución  
 Cuando un usuario inicia la aplicación de Shell aislado, llama al punto de entrada de inicio de Visual Studio Shell. La configuración de la aplicación se define cuando se inicia la aplicación, como se indica a continuación:  
  
1. Visual Studio Shell comprueba el registro de la aplicación en busca de claves específicas. Si el valor de una clave se especifica en la llamada al punto de entrada de inicio, ese valor reemplaza el valor del registro.  
  
2. Si no se especifica el valor de un valor en el registro ni en el parámetro de punto de entrada, se usa el valor predeterminado de la configuración.  
  
   Cuando un usuario inicia la aplicación desde la línea de comandos, todos los modificadores de línea de comandos se pasan al shell de Visual Studio, que los trata de la misma manera que lo hace devenv. Para obtener más información sobre los modificadores de devenv, vea [modificadores de línea de comandos de devenv](../ide/reference/devenv-command-line-switches.md) y [modificadores de la línea de comandos de devenv para el desarrollo de VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Para obtener más información sobre cómo se registra un paquete para los modificadores de la línea de comandos, vea [agregar modificadores de línea de comandos](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>El punto de entrada inicial  
 El archivo Appenvstub.dll contiene puntos de entrada para tener acceso al shell aislado. Cuando se inicia la aplicación, llama al punto de entrada de inicio de Appenvstub.dll.  
  
 Puede cambiar el comportamiento de la aplicación cambiando el valor del último parámetro que se pasa al punto de entrada de inicio. Para obtener más información, vea [parámetros de punto de entrada de Shell aislado (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>El. Archivo Vsct  
 El archivo. Vsct permite especificar qué elementos de interfaz de usuario de Visual Studio estándar están disponibles en la aplicación. Para obtener más información, vea [. Archivos Vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>El. Archivo Pkgundef  
 Cuando la aplicación se instala en un equipo en el que Visual Studio ya está instalado, se realiza una copia de las entradas del registro de Visual Studio para la aplicación. De forma predeterminada, la aplicación usa VSPackages que ya están instalados en el equipo. El archivo. pkgundef permite excluir las entradas del registro para quitar elementos concretos del shell o las extensiones de Visual Studio de la aplicación. Para obtener más información, vea [. Archivos Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 El archivo. pkgundef permite excluir las entradas del registro para quitar elementos concretos del shell o las extensiones de Visual Studio de la aplicación. Para obtener más información, vea [. Archivos Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 El conjunto de GUID de paquete que puede excluir se muestra en [GUID de paquete de características de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>El. Archivo Pkgdef  
 El archivo. pkgdef permite definir entradas del registro para la aplicación que se establecen cuando se instala la aplicación. Para obtener una descripción del archivo. pkgdef y una lista de entradas del registro que usa Visual Studio Shell, vea [. Archivos Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Cadenas de sustitución  
 Las cadenas de sustitución usadas en los archivos. pkgdef y. pkgundef se enumeran en [cadenas de sustitución usadas en. Pkgdef y. Archivos Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Otras configuraciones  
 Si la aplicación de Shell aislado depende de Microsoft.VisualStudio.GraphModel.dll, debe agregar el siguiente redireccionamiento de enlace al archivo. config de la aplicación de Shell aislado:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
