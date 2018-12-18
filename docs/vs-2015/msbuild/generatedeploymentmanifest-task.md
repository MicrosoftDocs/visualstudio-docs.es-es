---
title: GenerateDeploymentManifest (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
ms.assetid: 0734ebda-734d-49c4-9642-8d9d919d45fd
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ad0b9919c5c567662d78573573f1bf046c93552
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261896"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Genera un manifiesto de implementación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Un manifiesto de implementación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] describe la implementación de una aplicación definiendo una identidad única para la implementación, identificando opciones de la implementación, como el modo de instalación o el modo en línea, especificando la configuración y la ubicación de actualización de la aplicación y señalando el manifiesto de la aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] correspondiente.  
  
## <a name="parameters"></a>Parámetros  
 En la tabla siguiente se describen los parámetros de la tarea `GenerateDeploymentManifest`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AssemblyName`|Parámetro `String` opcional.<br /><br /> Especifica el campo `Name` de la identidad del ensamblado para el manifiesto generado. Si no se especifica este parámetro, el nombre se deduce de los parámetros `EntryPoint` o `InputManifest`. Si no se puede deducir el nombre, la tarea muestra un error.|  
|`AssemblyVersion`|Parámetro `String` opcional.<br /><br /> Especifica el campo `Version` de la identidad del ensamblado para el manifiesto generado. Si no se especifica este parámetro, la tarea utiliza el valor "1.0.0.0".|  
|`CreateDesktopShortcut`|Parámetro `Boolean` opcional.<br /><br /> Si es true, se crea un icono en el escritorio durante la instalación de la aplicación ClickOnce.|  
|`DeploymentUrl`|Parámetro `String` opcional.<br /><br /> Especifica la ubicación de actualización para la aplicación. Si no se especifica este parámetro, no se definirá ninguna ubicación de actualización para la aplicación. Sin embargo, si el parámetro `UpdateEnabled` es `true`, se debe especificar la ubicación de actualización. El valor especificado debe ser una dirección URL o ruta de acceso UNC completa.|  
|`Description`|Parámetro `String` opcional.<br /><br /> Especifica una descripción opcional para la aplicación.|  
|`DisallowUrlActivation`|Parámetro `Boolean` opcional.<br /><br /> Especifica si la aplicación debe ejecutarse automáticamente cuando se abre mediante una dirección URL. Si este parámetro es `true`, la aplicación solo se puede iniciar desde el menú Inicio. El valor predeterminado de este parámetro es `false`. Este valor solo se aplica cuando el valor del parámetro `Install` es `true`.|  
|`EntryPoint`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Indica el punto de entrada para el manifiesto del ensamblado generado. En un manifiesto de implementación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], este valor especifica el manifiesto de aplicación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].<br /><br /> En [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)], la [tarea GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md) requería un parámetro `EntryPoint` para generar un manifiesto de aplicación. (Los manifiestos de ensamblado o nativos no necesitan el parámetro `EntryPoint`). Este requisito se exigía con el siguiente error de compilación: "MSB3185: No se especificó EntryPoint para el manifiesto".<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] no emite este error cuando no se especifica el parámetro de tarea `EntryPoint`. En su lugar, la etiqueta \<customHostSpecified> se inserta como etiqueta secundaria de \<entryPoint>; por ejemplo:<br /><br /> `<entryPoint xmlns="urn:schemas-`<br /><br /> `microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Puede agregar dependencias de DLL al manifiesto de aplicación siguiendo estos pasos:<br /><br /> 1.  Resuelva las referencias del ensamblado con una llamada a <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>.<br />2.  Pase el resultado de la tarea anterior y el propio ensamblado a <xref:Microsoft.Build.Tasks.ResolveManifestFiles>.<br />3.  Pase las dependencias a través del parámetro `Dependencies` a <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>.|  
|`ErrorReportUrl`|Opcional [String] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parámetro.<br /><br /> Especifica la dirección URL de la página web que se muestra en los cuadros de diálogo durante las instalaciones ClickOnce.|  
|`InputManifest`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Indica un documento XML de entrada que sirve de base para el generador de manifiestos. De este modo, los datos estructurados, como las definiciones personalizadas del manifiesto, pueden reflejarse en el manifiesto de salida. El elemento raíz del documento XML debe ser un nodo de ensamblado en el espacio de nombres asmv1.|  
|`Install`|Parámetro `Boolean` opcional.<br /><br /> Especifica si la aplicación es una aplicación instalada o se trata de una aplicación que únicamente está disponible en línea. Si este parámetro es `true`, la aplicación se instalará en el menú Inicio del usuario y se podrá eliminar a través del cuadro de diálogo Agregar o quitar programas. Si este parámetro es `false`, la aplicación está destinada para su uso en línea desde una página web. El valor predeterminado de este parámetro es `true`.|  
|`MapFileExtensions`|Parámetro `Boolean` opcional.<br /><br /> Especifica si se utiliza la asignación de extensión de nombre de archivo .deploy. Si este parámetro es `true`, todos los archivos de programa se publican con la extensión de nombre de archivo .deploy. Esta opción es útil para la seguridad de los servidores web, ya que limita el número de extensiones de nombre que deben desbloquearse para habilitar la implementación de la aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. El valor predeterminado de este parámetro es `false`.|  
|`MaxTargetPath`|Parámetro `String` opcional.<br /><br /> Especifica la longitud máxima permitida de la ruta de acceso de un archivo en una implementación de aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Si se especifica este parámetro, se comprobará si la longitud de cada ruta de archivo de la aplicación rebasa este límite. Cualquier elemento que supere el límite provocará una advertencia de compilación. Si no se especifica esta entrada o es cero, no se realiza ninguna comprobación.|  
|`MinimumRequiredVersion`|Parámetro `String` opcional.<br /><br /> Especifica si el usuario puede omitir la actualización. Si el usuario tiene una versión anterior a la versión mínima requerida, no podrá omitir la actualización. Este valor solo se aplica cuando el valor del parámetro `Install` es `true`.|  
|`OutputManifest`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el nombre del archivo de manifiesto de salida generado. Si no se especifica este parámetro, el nombre del archivo de salida se deduce de la identidad del manifiesto generado.|  
|`Platform`|Parámetro `String` opcional.<br /><br /> Especifica la plataforma de destino de la aplicación. Este parámetro puede tener los valores siguientes:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> El valor predeterminado es `AnyCPU`.|  
|`Product`|Parámetro `String` opcional.<br /><br /> Especifica el nombre de la aplicación. Si no se especifica este parámetro, el nombre se deduce de la identidad del manifiesto generado. Este nombre se utiliza para el nombre del acceso directo del menú Inicio y forma parte del nombre que aparece en el cuadro de diálogo Agregar o quitar programas.|  
|`Publisher`|Parámetro `String` opcional.<br /><br /> Especifica el publicador de la aplicación. Si no se especifica este parámetro, el nombre se deduce del usuario registrado o de la identidad del manifiesto generado. Este nombre se utiliza para el nombre de la carpeta del menú Inicio y forma parte del nombre que aparece en el cuadro de diálogo Agregar o quitar programas.|  
|`SuiteNamel`|Parámetro `String` opcional.<br /><br /> Especifica el nombre de la carpeta del menú Inicio donde se ubica la aplicación después de la implementación ClickOnce.|  
|`SupportUrl`|Parámetro `String` opcional.<br /><br /> Especifica el vínculo que aparece en el cuadro de diálogo Agregar o quitar programas para la aplicación. El valor especificado debe ser una dirección URL o ruta de acceso UNC completa.|  
|`TargetCulture`|Parámetro `String` opcional.<br /><br /> Identifica la referencia cultural de la aplicación y especifica el campo `Language` de la identidad del ensamblado para el manifiesto generado. Si no se especifica este parámetro, se supone que la aplicación es invariable en cuanto a la referencia cultural.|  
|`TrustUrlParameters`|Parámetro `Boolean` opcional.<br /><br /> Especifica si los parámetros de cadena de consulta de dirección URL deben ponerse a disposición de la aplicación. El valor predeterminado de este parámetro es `false`, lo que indica que los parámetros no estarán disponibles para la aplicación.|  
|`UpdateEnabled`|Parámetro `Boolean` opcional.<br /><br /> Indica si se permite actualizar la aplicación. El valor predeterminado de este parámetro es `false`. Este parámetro solo se aplica cuando el valor del parámetro `Install` es `true`.|  
|`UpdateInterval`|Parámetro `Int32` opcional.<br /><br /> Especifica el intervalo de actualización de la aplicación. El valor predeterminado de este parámetro es cero. Este parámetro solo se aplica cuando los valores de los parámetros `Install` y `UpdateEnabled` son ambos `true`.|  
|`UpdateMode`|Parámetro `String` opcional.<br /><br /> Especifica si las actualizaciones deben comprobarse en primer plano antes de que se inicie la aplicación o en segundo plano mientras la aplicación se está ejecutando. Este parámetro puede tener los valores siguientes:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> El valor predeterminado de este parámetro es `Background`. Este parámetro solo se aplica cuando los valores de los parámetros `Install` y `UpdateEnabled` son ambos `true`.|  
|`UpdateUnit`|Parámetro `String` opcional.<br /><br /> Especifica las unidades del parámetro `UpdateInterval`. Este parámetro puede tener los valores siguientes:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Este parámetro solo se aplica cuando los valores de los parámetros `Install` y `UpdateEnabled` son ambos `true`.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.GenerateManifestBase>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de los parámetros de la clase Task, vea [Task Base (Clase)](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [GenerateApplicationManifest (Tarea)](../msbuild/generateapplicationmanifest-task.md)   
 [SignFile (Tarea)](../msbuild/signfile-task.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)



