---
title: CreateItem (Tarea) | Microsoft Docs
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
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7db76f3ec603c493cef38536b6fb54b74ac6c43b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180913"
---
# <a name="createitem-task"></a>CreateItem (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Rellena las colecciones de elementos con los elementos de entrada. Esto permite copiar los elementos de una lista en otra.  
  
> [!NOTE]
>  Esta tarea está en desuso. A partir de .NET Framework 3.5, los grupos de elementos se pueden colocar dentro de elementos [Target](../msbuild/target-element-msbuild.md). Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).  
  
## <a name="attributes"></a>Atributos  
 En la siguiente tabla se describen los parámetros de la tarea `CreateItem` .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AdditionalMetadata`|Parámetro de matriz `String` opcional.<br /><br /> Especifica los metadatos adicionales que se adjuntarán a los elementos de salida.  Especifique el nombre y valor de los metadatos para el elemento empleando la siguiente sintaxis:<br /><br /> *nombreDeMetadatos*  `=` *valorDeMetadatos*<br /><br /> En caso de múltiples pares de nombre/valor de metadatos, se deberán separar con un punto y coma. Si el nombre o el valor contiene un punto y coma o cualquier otro carácter especial, deben ser de escape. Para obtener más información, vea [Cómo: Utilizar caracteres de escape especiales en MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|  
|`Exclude`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los elementos que se excluirán de la colección de elementos de salida. Este parámetro puede contener las especificaciones del comodín. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md) y [Cómo: Excluir archivos de la compilación](../msbuild/how-to-exclude-files-from-the-build.md).|  
|`Include`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]`obligatorio.<br /><br /> Especifica los elementos que se incluirán en la colección de elementos de salida. Este parámetro puede contener las especificaciones del comodín.|  
|`PreserveExistingMetadata`|Parámetro `Boolean` opcional.<br /><br /> Si es `True`, solo se aplican los metadatos adicionales si no existen ya.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se crea una nueva colección de elementos denominada `MySourceItemsWithMetadata` a partir de la colección de elementos `MySourceItems`. La tarea `CreateItem` rellena la nueva colección de elementos con los elementos de `MySourceItems`. A continuación, agrega una entrada de metadatos adicional denominada `MyMetadata` con un valor de `Hello` en cada elemento de la nueva colección.  
  
 Una vez ejecutada la tarea, la colección de elementos `MySourceItemsWithMetadata` contiene los elementos `file1.resx` y `file2.resx`, ambos con entradas de metadatos para `MyMetadata`. La colección de elementos `MySourceItems` se queda sin modificar.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceItems Include="file1.resx;file2.resx" />  
    </ItemGroup>  
  
    <Target Name="NewItems">  
        <CreateItem  
            Include="@(MySourceItems)"  
            AdditionalMetadata="MyMetadata=Hello">  
           <Output  
               TaskParameter="Include"  
               ItemName="MySourceItemsWithMetadata"/>  
        </CreateItem>  
  
    </Target>  
  
</Project>  
```  
  
 En la siguiente tabla se describe el valor del elemento de salida después de la ejecución de la tarea. Los metadatos del elemento se muestran entre paréntesis después del elemento.  
  
|Colección de elementos.|Contenido|  
|---------------------|--------------|  
|`MySourceItemsWithMetadata`|`file1.resx` (`MyMetadata="Hello"`)<br /><br /> `file2.resx` (`MyMetadata="Hello"`)|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)



