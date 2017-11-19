---
title: "Origen de datos para el Control en tiempo de ejecución | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9647f1f399b0d6516fe6475e6245c6834a0ea2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-runtime-details"></a>Detalles de tiempo de ejecución del Control de origen
Cuando el usuario agrega un archivo en el proyecto de control de código fuente, o a través de un controlador de automatización, como un asistente, se agrega un proyecto al control de código fuente. Un proyecto no especifica por sí mismo que está bajo control de código fuente; admite el control de código fuente, pero deben agregarse manualmente a él.  
  
## <a name="registering-with-a-source-control-package"></a>El registro con un paquete de Control de código fuente  
 Cuando se agrega un archivo en el proyecto al control de código fuente, el entorno llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> para proporcionar cuatro cadenas opacas que se usan como cookies por el sistema de control de código fuente. Almacenar estas cadenas en el archivo de proyecto. Estas cadenas se deben pasar al código auxiliar de Control de origen (el componente de Visual Studio que administra los paquetes de control de origen) en el inicio del tipo de proyecto mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Esto a su vez carga el paquete de control de origen que corresponda y reenvía la llamada a su implementación de `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)