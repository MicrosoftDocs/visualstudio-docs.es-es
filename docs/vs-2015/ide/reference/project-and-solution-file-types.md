---
title: Tipos de archivos de proyecto y solución | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- File Properties.CopyToOutputDirectory
- File Properties.CustomToolNamespace
- File Properties.FileName
- File Properties.FullPath
- File Properties.BuildAction
- File Properties.CustomTool
- FileProperties
helpviewer_keywords:
- suo files
- file types, Visual Studio
- file extensions
- solutions, solution files
- solution files
- .sln files
- Visual Studio, file types and extensions
- extensions, file types
- sln files
- .suo files
- file extensions, Visual Studio
- file types
ms.assetid: 0ba5007b-465d-4efa-b1e4-f0ee68527649
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 59f9fb1f628da6bc4d958fdca3843adebe61b798
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662144"
---
# <a name="project-and-solution-file-types"></a>Tipos de archivos de proyecto y solución
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] es compatible con muchos tipos de archivo. En una instalación concreta, los componentes instalados determinan los tipos de archivo compatibles. En este tema se incluyen los tipos de archivo de solución y proyecto compatibles en algunas instalaciones típicas. Para obtener información acerca de otros tipos de archivo, busque las extensiones de nombre de archivo de cada tipo.

## <a name="solution-files-sln-and-suo"></a>Archivos de solución (.sln y .suo)
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usa dos tipos de archivo (.sln y .suo) para almacenar la configuración específica de las soluciones. Estos archivos, denominados colectivamente "archivos de solución", proporcionan al Explorador de soluciones la información que necesita para mostrar una interfaz gráfica para administrar los archivos. Le permiten concentrarse en sus proyectos y objetivos finales en lugar de concentrarse en el entorno en sí cada vez que vuelve a las tareas de desarrollo.

|Comprobación de actualización|NOMBRE|Descripción|
|---------------|----------|-----------------|
|.sln|Solución de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]|Organiza proyectos, elementos de proyecto y elementos de solución en la solución.|
|.suo|Opciones de usuario de la solución|Hace un seguimiento de las personalizaciones de nivel de usuario que ha realizado en Visual Studio, como los puntos de interrupción.|

## <a name="project-files"></a>Archivos de proyecto
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usa varios formatos de archivo para almacenar información específica de los proyectos. Para obtener más información, vea los temas de Ayuda siguientes:

 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]
 [Tipos de archivos creados para proyectos de Visual C++](https://msdn.microsoft.com/library/2b0ee2e0-ae81-4185-9bb9-11da3c99a283)

 [Creación y administración de proyectos de Visual C++](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)

 [Unicode](https://msdn.microsoft.com/library/1002004b-4113-4380-bf63-e1570934b793)

## <a name="see-also"></a>Consulte también
 [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)
