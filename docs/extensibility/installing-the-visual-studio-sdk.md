---
title: Instalar el SDK de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 722c32c139d2f560fa6d10aba9fd8bac610f9f20
ms.lasthandoff: 03/07/2017

---
# <a name="installing-the-visual-studio-sdk"></a>Instalar el SDK de Visual Studio
El SDK de Visual Studio es una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalar el SDK de Visual Studio como parte de una instalación de Visual Studio  
 Si desea incluir el VSSDK en la instalación de Visual Studio, debe instalar la **desarrollo de extensiones de Visual Studio** carga de trabajo en **otros conjuntos de herramientas**. Esto instalará el SDK de Visual Studio, así como los requisitos previos necesarios. Puede ajustar aún más la instalación seleccionando o anule su selección de componentes desde el resumen de la vista. 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalar el SDK de Visual Studio después de instalar Visual Studio  
 Si decide instalar el SDK de Visual Studio después de completar la instalación de Visual Studio, vuelva a ejecutar el programa de instalación de Visual Studio y seleccione la **desarrollo de extensiones de Visual Studio** carga de trabajo.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalar el SDK de Visual Studio desde una solución  
 Si abre una solución sin instalar primero el VSSDK con un proyecto de extensibilidad, se le pedirá mediante una barra de información resaltada sobre el Explorador de soluciones. Debería ser similar al siguiente:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalar el SDK de Visual Studio desde la línea de comandos  
Como con cualquier carga de trabajo de Visual Studio o un componente, también puede instalar el producto desde la línea de comandos. Consulte [utilizar parámetros de línea de comandos para instalar Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) para obtener más información sobre los modificadores de línea de comandos apropiada y cómo determinar los identificadores de carga de trabajo o un componente.
  
 Tenga en cuenta que debe utilizar al instalador de Visual Studio que coincida con la versión instalada de Visual Studio. Por ejemplo, si tiene instalado en el equipo de Visual Studio Enterprise, debe ejecutar al instalador de Visual Studio Enterprise (vs_enterprise.exe).
