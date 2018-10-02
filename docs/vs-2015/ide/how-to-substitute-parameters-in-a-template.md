---
title: Cómo sustituir parámetros en una plantilla | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e7e3fea66b23d86378ff4afb81a7d4f46f5090d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578663"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Cómo: Sustituir parámetros en una plantilla
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: sustituir parámetros en una plantilla](https://docs.microsoft.com/visualstudio/ide/how-to-substitute-parameters-in-a-template).  
  
Puede reemplazar parámetros de plantilla (como los nombres de clase y los espacios de nombres) al crear un archivo basado en una plantilla. Para obtener una lista completa de parámetros de plantilla, vea [Parámetros de plantilla](../ide/template-parameters.md).  
  
## <a name="procedure"></a>Procedimiento  
 Puede reemplazar parámetros de los archivos de una plantilla cada vez que se cree un proyecto basado en esa plantilla. En este procedimiento se explica cómo crear una plantilla que reemplace el nombre de un espacio de nombres por el nombre del proyecto seguro al crear un proyecto nuevo con la plantilla.  
  
#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Para usar un parámetro que sustituya el nombre del espacio de nombres por el nombre del proyecto  
  
1.  Inserte el parámetro en uno o varios archivos de código en la plantilla. Por ejemplo:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  Los parámetros de plantilla se escriben con el formato $*parámetro*$.  
  
2.  En el archivo .vstemplate de la plantilla, busque el elemento `ProjectItem` que incluye este archivo.  
  
3.  Establezca el atributo `ReplaceParameters` en `true` para el elemento `ProjectItem`. Por ejemplo:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem (Elemento, Plantillas de elementos de Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)



