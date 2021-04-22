---
title: Personalización de archivos de proyecto creados por VSTU | Microsoft Docs
description: Aprenda a personalizar los archivos del proyecto creados por Visual Studio Tools para Unity (VSTU). Revise un ejemplo de código de C#.
ms.custom: ''
ms.date: 04/19/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a4a5973863877db2d071f9be8d4689928b21a689
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879322"
---
# <a name="customize-project-files-created-by-vstu"></a>Personalizar archivos de proyecto creados por VSTU
Unity proporciona devoluciones de llamada durante la generación de archivos de proyecto. Implemente `OnGeneratedSlnSolution` los métodos y mediante para modificar el archivo de proyecto o solución cada vez que se vuelva a `OnGeneratedCSProject` [`AssetPostprocessor`](https://docs.unity3d.com/ScriptReference/AssetPostprocessor.html) generar.

## <a name="demonstrates"></a>Muestra
Cómo personalizar los archivos de proyecto de Visual Studio generados por Visual Studio Tools para Unity.

## <a name="example"></a>Ejemplo

```csharp
using System;
using UnityEditor;
using UnityEngine;

public class ProjectFilePostprocessor : AssetPostprocessor
{
  public static string OnGeneratedSlnSolution(string path, string content)
  {
    // TODO: process solution content
    return content;
  }

  public static string OnGeneratedCSProject(string path, string content)
  {
    // TODO: process project content
    return content;
  }
}
```
