---
title: "La instancia Experimental | Microsoft Docs"
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
  - "compilaciones experimentales"
  - "VSPackages, compilaciones experimentales"
  - "VSIP, compilaciones experimentales"
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 36
caps.handback.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
---
# La instancia Experimental
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para proteger el entorno de desarrollo de Visual Studio desde aplicaciones no probados que puede cambiar, el VSSDK proporciona un espacio experimental que puede utilizar para experimentar. Desarrollar nuevas aplicaciones con Visual Studio como de costumbre, pero ejecutarlos empleando esta instancia experimental.  
  
 Cada aplicación que tiene un paquete VSIX inicia la instancia experimental de Visual Studio en modo de depuración.  
  
 Si desea iniciar la instancia experimental de Visual Studio fuera de una solución específica, ejecute el siguiente comando en la ventana de comandos:  
  
 "*\< ruta de instalación de visual studio \>*\\Common7\\IDE\\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  La instancia experimental se escribe en el registro bajo la `<version number>Exp` y `<version number>Exp_Config` nodos. Por ejemplo es el área de registro experimental de Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` y `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Se recomienda ejecutar la extensión en la instancia experimental, mientras se está desarrollando. Al implementar la extensión, se ejecuta en la instancia de desarrollo. Para obtener más información acerca del registro de aplicaciones, consulte [Registrar VSPackages](../extensibility/internals/registering-vspackages.md).