---
title: Instalar el SDK de Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 259646e0dbee4831db83a7098954d1c5144d8ead
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129087"
---
# <a name="installing-the-visual-studio-sdk"></a>Instalar el SDK de Visual Studio
El SDK de Visual Studio es una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalar el SDK de Visual Studio como parte de una instalación de Visual Studio  
 Si desea incluir el VSSDK en la instalación de Visual Studio, debe instalar la **desarrollo de extensión de Visual Studio** cargas de trabajo en **otros conjuntos de herramientas**. Este modo se instalará el SDK de Visual Studio, así como los requisitos previos necesarios. Puede ajustar aún más la instalación, seleccione o anule su selección de componentes desde el resumen de la vista. 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalar el SDK de Visual Studio después de instalar Visual Studio  
 Si decide instalar el SDK de Visual Studio después de completar la instalación de Visual Studio, vuelva a ejecutar el programa de instalación de Visual Studio y seleccione la **desarrollo de extensión de Visual Studio** carga de trabajo.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalar el SDK de Visual Studio desde una solución  
 Si abre una solución con un proyecto de extensibilidad sin instalar primero el VSSDK, se le pedirá por una barra de información resaltada sobre el Explorador de soluciones. Debe tener un aspecto similar al siguiente:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalar el SDK de Visual Studio desde la línea de comandos  
Como con cualquier carga de trabajo de Visual Studio o un componente, también puede instalar el **desarrollo de extensión de Visual Studio** cargas de trabajo (Id.: Microsoft.VisualStudio.Workload.VisualStudioExtension) desde la línea de comandos. Vea [usar parámetros de línea de comandos para instalar Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) para obtener más información sobre los modificadores de línea de comandos adecuada e instrucciones generales acerca de cómo determinar los identificadores de carga de trabajo o un componente.
  
 Tenga en cuenta que debe usar al instalador de Visual Studio que coincida con la versión instalada de Visual Studio. Por ejemplo, si tiene instalado en el equipo de Visual Studio Enterprise, debe ejecutar el programa de instalación de Visual Studio Enterprise (vs_enterprise.exe).