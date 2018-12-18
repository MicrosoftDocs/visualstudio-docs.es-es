---
title: La instancia Experimental | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c80c071866e46528fe7edd287e082df3af166973
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138930"
---
# <a name="the-experimental-instance"></a>La instancia Experimental
Para proteger el entorno de desarrollo de Visual Studio desde las aplicaciones no se han comprobado que puede cambiarlo, el VSSDK proporciona un espacio experimental que puede utilizar para experimentar. Desarrollar nuevas aplicaciones con Visual Studio como de costumbre, pero su ejecución mediante el uso de esta instancia experimental.  
  
 Todas las aplicaciones que tiene un paquete VSIX inicia la instancia experimental de Visual Studio en modo de depuración.  
  
 Si desea iniciar la instancia experimental de Visual Studio fuera de una solución específica, ejecute el comando siguiente en la ventana de comandos:  
  
 "*\<Ruta de instalación de visual studio >* \Common7\IDE\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  La instancia experimental se escribe en el registro bajo la `<version number>Exp` y `<version number>Exp_Config` nodos. Por ejemplo es el área del registro experimental de Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` y `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Se recomienda ejecutar la extensión en la instancia experimental mientras se está desarrollando. Al implementar la extensión, se ejecuta en la instancia de desarrollo. Para obtener más información sobre el registro de aplicaciones, consulte [VSPackages registrar](../extensibility/internals/registering-vspackages.md).