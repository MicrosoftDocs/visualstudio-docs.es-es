---
title: "Tipos de archivos de proyecto y solución | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 744b35962a196e0372d1bd1fa916f247a9195da6
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="project-and-solution-file-types"></a>Tipos de archivos de proyecto y solución
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es compatible con muchos tipos de archivo. En una instalación concreta, los componentes instalados determinan los tipos de archivo compatibles. En este tema se incluyen los tipos de archivo de solución y proyecto compatibles en algunas instalaciones típicas. Para obtener información acerca de otros tipos de archivo, busque las extensiones de nombre de archivo de cada tipo.  
  
## <a name="solution-files-sln-and-suo"></a>Archivos de solución (.sln y .suo)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa dos tipos de archivo (.sln y .suo) para almacenar la configuración específica de las soluciones. Estos archivos, denominados colectivamente "archivos de solución", proporcionan al Explorador de soluciones la información que necesita para mostrar una interfaz gráfica para administrar los archivos. Le permiten concentrarse en sus proyectos y objetivos finales en lugar de concentrarse en el entorno en sí cada vez que vuelve a las tareas de desarrollo.  
  
|Extensión|Nombre|Descripción|  
|---------------|----------|-----------------|  
|.sln|Solución de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]|Organiza proyectos, elementos de proyecto y elementos de solución en la solución.|  
|.suo|Opciones de usuario de la solución|Hace un seguimiento de las personalizaciones de nivel de usuario que ha realizado en Visual Studio, como los puntos de interrupción.|  
  
## <a name="project-files"></a>Archivos de proyecto  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa varios formatos de archivo para almacenar información específica de los proyectos. Para obtener más información, vea los temas de Ayuda siguientes:  
  
 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]  
 [Tipos de archivos creados para proyectos de Visual C++](/cpp/ide/file-types-created-for-visual-cpp-projects)    
 [Creación y administración de proyectos de Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects)    
 [Unicode](/cpp/mfc/unicode-in-mfc)  
  
## <a name="see-also"></a>Vea también  
 [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)