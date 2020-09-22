---
title: Instancia experimental | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ee3c1ef0aed082a0e4e0fb519c744fda376fc8e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842535"
---
# <a name="the-experimental-instance"></a>Instancia experimental
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para proteger el entorno de desarrollo de Visual Studio de aplicaciones no comprobadas que puedan cambiarlo, el VSSDK proporciona un espacio experimental que puede usar para experimentar. Las aplicaciones nuevas se desarrollan con Visual Studio como de costumbre, pero se ejecutan mediante esta instancia experimental.  
  
 Todas las aplicaciones que tienen un paquete VSIX inician la instancia experimental de Visual Studio en modo de depuración.  
  
 Si desea iniciar la instancia experimental de Visual Studio fuera de una solución específica, ejecute el siguiente comando en la ventana de comandos:  
  
 " *\<Visual studio installation path>* \Common7\IDE\devenv.exe"/RootSuffix exp  
  
> [!NOTE]
> La instancia experimental se escribe en el registro en los `<version number>Exp` `<version number>Exp_Config` nodos y. Por ejemplo, el área del registro experimental de Visual Studio 2015 es  
>   
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` y `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Se recomienda ejecutar la extensión en la instancia experimental mientras se está desarrollando. Al implementar la extensión, se ejecuta en la instancia de desarrollo. Para obtener más información acerca del registro de aplicaciones, vea [registrar VSPackages](../extensibility/internals/registering-vspackages.md).
