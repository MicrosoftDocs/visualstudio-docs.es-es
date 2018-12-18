---
title: Metadatos de los elementos conocidos de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8d83c6eaf441b72bc3774f4117653826da47613
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49234057"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadatos de los elementos conocidos de MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
En la tabla siguiente se describen los metadatos asignados a cada elemento en el momento de su creación. Se utilizó la declaración del elemento siguiente en cada ejemplo para incluir el archivo `C:\MyProject\Source\Program.cs` en el proyecto.  
  
```  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Metadatos de elementos|Descripción|  
|-------------------|-----------------|  
|%(FullPath)|Contiene la ruta de acceso completa del elemento. Por ejemplo:<br /><br /> `C:\MyProject\Source\Program.cs`|  
|%(RootDir)|Contiene el directorio raíz del elemento. Por ejemplo:<br /><br /> `C:\`|  
|%(Filename)|Contiene el nombre de archivo del elemento, sin la extensión. Por ejemplo:<br /><br /> `Program`|  
|%(Extension)|Contiene la extensión de nombre de archivo del elemento. Por ejemplo:<br /><br /> `.cs`|  
|%(RelativeDir)|Contiene la ruta de acceso especificada en el atributo `Include`, hasta la última barra diagonal inversa (\\). Por ejemplo:<br /><br /> `Source\`|  
|%(Directory)|Contiene el directorio del elemento, sin el directorio raíz. Por ejemplo:<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|Si el atributo `Include` contiene el carácter comodín \*\*, este metadato especifica la parte de la ruta de acceso que reemplaza el carácter comodín. Para obtener más información sobre comodines, vea [Cómo: Seleccionar los archivos que se van a compilar](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Si la carpeta *C:\MySolution\MyProject\Source\\* contiene el archivo Program.cs y si el archivo de proyecto contiene este elemento:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> entonces el valor de `%(MyItem.RecursiveDir)` sería *MySolution\MyProject\Source\\*.|  
|%(Identity)|El elemento especificado en el atributo `Include`. Por ejemplo:<br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|Contiene la marca de tiempo correspondiente a la última modificación del elemento. Por ejemplo:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Contiene la marca de tiempo correspondiente a la creación del elemento. Por ejemplo:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Contiene la marca de tiempo correspondiente a la última vez que se tuvo acceso al elemento.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Vea también  
 [Elementos](../msbuild/msbuild-items.md)   
 [Procesamiento por lotes](../msbuild/msbuild-batching.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)



