---
title: La instancia Experimental | Documentos de Microsoft
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
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b529ba3a0ea8b38a27d06e03ce15106cbd7512a5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787996"
---
# <a name="the-experimental-instance"></a>Instancia experimental
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para proteger el entorno de desarrollo de Visual Studio desde aplicaciones no probados que puede cambiarlo, VSSDK proporciona un espacio experimental que puede usar para experimentar. Desarrollar nuevas aplicaciones con Visual Studio como de costumbre, pero ejecutar mediante el uso de esta instancia experimental.  
  
 Cada aplicación que tiene un paquete VSIX inicia la instancia experimental de Visual Studio en modo de depuración.  
  
 Si desea iniciar la instancia experimental de Visual Studio fuera de una solución específica, ejecute el comando siguiente en la ventana de comandos:  
  
 "*\<Ruta de instalación de visual studio >* \Common7\IDE\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  La instancia experimental se escribe en el registro bajo la `<version number>Exp` y `<version number>Exp_Config` nodos. Por ejemplo es el área del registro experimental de Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` y `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Se recomienda ejecutar la extensión en la instancia experimental, mientras se está desarrollando. Al implementar la extensión, se ejecuta en la instancia de desarrollo. Para obtener más información sobre el registro de aplicaciones, consulte [VSPackages registrar](../extensibility/internals/registering-vspackages.md).

