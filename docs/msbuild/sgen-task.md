---
title: SGen (Tarea) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: e4ba336071a8b9e311ffe67330677cb25ff92751
ms.lasthandoff: 02/22/2017

---
# <a name="sgen-task"></a>SGen (Tarea)
Crea un ensamblado de serialización XML para los tipos del ensamblado especificado. Esta tarea ajusta la herramienta Generador de serializador XML (Sgen.exe). Para obtener más información, consulte [Herramienta Generador de serializador XML (Sgen.exe)](http://msdn.microsoft.com/Library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `SGen`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`BuildAssemblyName`|Parámetro `String` requerido.<br /><br /> Ensamblado para el que se debe generar código de serialización.|  
|`BuildAssemblyPath`|Parámetro `String` requerido.<br /><br /> Ruta de acceso al ensamblado para el que se debe generar código de serialización.|  
|`DelaySign`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, especifica que quiere un ensamblado completamente firmado. Si `false`, especifica que solo quiere colocar la clave pública en el ensamblado.<br /><br /> Este parámetro no tiene ningún efecto a menos que se utilice con el parámetro `KeyFile` o `KeyContainer`.|  
|`KeyContainer`|Parámetro `String` opcional.<br /><br /> Especifica un contenedor que contiene un par de claves. De este modo, el ensamblado se firmará mediante la inserción de una clave pública en el manifiesto del ensamblado. La tarea firmará después el ensamblado final con la clave privada.|  
|`KeyFile`|Parámetro `String` opcional.<br /><br /> Especifica un par de claves o una clave pública que se usará para firmar un ensamblado. El compilador inserta la clave pública en el manifiesto del ensamblado y firma después el ensamblado final con la clave privada.|  
|`Platform`|Parámetro `String` opcional.<br /><br /> Obtiene o establece la plataforma de compilador utilizada para generar el ensamblado de salida. Este parámetro puede tener un valor de `x86`, `x64` o `anycpu`. El valor predeterminado es `anycpu`.|  
|`References`|Parámetro `String[]` opcional.<br /><br /> Especifica los ensamblados a los que hacen referencia los tipos que requieren serialización XML.|  
|`SdkToolsPath`|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso a las herramientas del SDK, tales como resgen.exe.|  
|`SerializationAssembly`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene el ensamblado de serialización generado.|  
|`SerializationAssemblyName`|Parámetro `String` opcional.<br /><br /> Especifica el nombre del ensamblado de serialización generado.|  
|`ShouldGenerateSerializer`|Parámetro `Boolean` requerido.<br /><br /> Si es `true`, la tarea SGen debe generar un ensamblado de serialización.|  
|`Timeout`|Parámetro `Int32` opcional.<br /><br /> Especifica el tiempo en milisegundos después del cual se termina la tarea ejecutable. El valor predeterminado es `Int.MaxValue`, que indica que no hay período de tiempo de espera.|  
|`ToolPath`|Parámetro `String` opcional.<br /><br /> Especifica la ubicación desde donde la tarea cargará el archivo ejecutable subyacente (sgen.exe). Si no se especifica este parámetro, la tarea usa la ruta de instalación del SDK que se corresponde con la versión de la plataforma que está ejecutando [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`Types`|Parámetro `String[]` opcional.<br /><br /> Obtiene o establece una lista de tipos específicos para los que generar código de serialización. SGen generará el código de serialización solo para esos tipos.|  
|`UseProxyTypes`|Parámetro `Boolean` requerido.<br /><br /> Si es `true`, la tarea SGen genera código de serialización únicamente para los tipos de proxy de servicios web XML.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.ToolTask>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [ToolTaskExtension (Clase base)](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)
