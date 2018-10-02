---
title: Clase base Task | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b2b269d718871c58cb082ce09ed50ce70736b55
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576188"
---
# <a name="task-base-class"></a>Base de tarea (Clase)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [tarea Base clase](https://docs.microsoft.com/visualstudio/msbuild/task-base-class).  
  
  
Muchas tareas heredan en última instancia de la clase <xref:Microsoft.Build.Utilities.Task>. Esta clase agrega varios parámetros a las tareas que derivan de ellos. Estos parámetros se muestran en este documento.  
  
## <a name="parameters"></a>Parámetros  
 En la tabla siguiente se describen los parámetros de esta clase base.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parámetro <xref:Microsoft.Build.Framework.IBuildEngine> opcional.<br /><br /> Especifica la interfaz del motor de compilación disponible para las tareas. El motor de compilación establece automáticamente este parámetro para permitir que las tareas vuelvan a llamarlo.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parámetro <xref:Microsoft.Build.Framework.IBuildEngine2> opcional.<br /><br /> Especifica la interfaz del motor de compilación disponible para las tareas. El motor de compilación establece automáticamente este parámetro para permitir que las tareas vuelvan a llamarlo.<br /><br /> Esta es una propiedad que permite que los autores de las tareas que heredan de esta clase no tengan que convertir el valor de `IBuildEngine` a `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parámetro <xref:Microsoft.Build.Framework.IBuildEngine3> opcional.<br /><br /> Especifica la interfaz del motor de compilación proporcionado por el host.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parámetro <xref:Microsoft.Build.Framework.ITaskHost> opcional.<br /><br /> Especifica la instancia del objeto host (puede ser null). El motor de compilación establece esta propiedad si el IDE del host tiene un objeto host asociado a esta tarea concreta.|  
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Parámetro de solo lectura <xref:Microsoft.Build.Utilities.TaskLoggingHelper> opcional.<br /><br /> Objeto del asistente de registro.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)



