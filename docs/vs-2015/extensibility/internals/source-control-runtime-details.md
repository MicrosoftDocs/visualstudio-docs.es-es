---
title: Detalles de tiempo de ejecución del Control de origen | Documentos de Microsoft
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
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3db90aaaccefb940c9cdea773b5b18f41f60d5d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756590"
---
# <a name="source-control-runtime-details"></a>Detalles de tiempo de ejecución del control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cuando el usuario agrega un archivo en el proyecto de control de código fuente, o a través de un controlador de automatización, como un asistente, se agrega un proyecto al control de código fuente. Un proyecto no especifica por sí mismo que está bajo control de código fuente; admite el control de código fuente, pero deben agregarse manualmente a él.  
  
## <a name="registering-with-a-source-control-package"></a>Registro con un paquete de Control de código fuente  
 Cuando se agrega un archivo en el proyecto de control de código fuente, el entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> para proporcionar cuatro cadenas opacas que sirven como cookies por el sistema de control de código fuente. Store estas cadenas en el archivo de proyecto. Estas cadenas se deben pasar al código auxiliar de Control de origen (el componente de Visual Studio que administra los paquetes de control de origen) en el inicio del tipo de proyecto mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Esto a su vez carga el paquete de control de origen adecuado y reenvía la llamada a su implementación de `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)

