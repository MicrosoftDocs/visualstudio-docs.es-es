---
title: "Detalles de tiempo de ejecuci&#243;n del Control de origen | Microsoft Docs"
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
  - "control de código fuente [Visual Studio SDK], detalles de tiempo de ejecución"
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Detalles de tiempo de ejecuci&#243;n del Control de origen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Se agrega un proyecto al control de código fuente cuando el usuario agrega un archivo del proyecto al control de código fuente, o mediante un controlador de automatización, como un asistente.  Un proyecto no especifica para usted que está bajo control de código fuente; admite el control de código fuente, pero debe agregar a manualmente.  
  
## Registrarse con un paquete de control de código fuente  
 Cuando un archivo del proyecto se agrega al control de código fuente, el entorno llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> para proporcionarle cuatro cadenas opacas que se utilizarán como cookies por el sistema de control de código fuente.  almacene estas cadenas en el archivo de proyecto.  Estas cadenas se deben pasar a código auxiliar de control de código fuente \(el componente de Visual Studio que administra los paquetes de control de código fuente\) en el inicio del tipo de proyecto llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>.  Esto a su vez carga el paquete de control de código fuente adecuado y reenvía la llamada a su implementación de `IVsSccManager2::RegisterSccProject`.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Compatibilidad con Control de código fuente](../../extensibility/internals/supporting-source-control.md)