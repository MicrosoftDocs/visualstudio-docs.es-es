---
title: "C&#243;mo: Sustituir par&#225;metros en una plantilla | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "parámetros de plantilla, sustituir"
  - "plantillas de Visual Studio, utilizar parámetros"
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Sustituir par&#225;metros en una plantilla
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede reemplazar parámetros de plantilla \(como los nombres de clase y los espacios de nombres\) al crear un archivo basado en una plantilla.  Para obtener una lista completa de parámetros de plantilla, consulte [Parámetros de plantilla](../ide/template-parameters.md).  
  
## Procedimiento  
 Puede reemplazar parámetros de los archivos de una plantilla cada vez que se cree un proyecto basado en esa plantilla.  En este procedimiento se explica cómo crear una plantilla que reemplace el nombre de un espacio de nombres por el nombre del proyecto seguro al crear un proyecto nuevo con la plantilla.  
  
#### Para usar un parámetro que sustituya el nombre del espacio de nombres por el nombre del proyecto  
  
1.  Inserte el parámetro en uno o varios archivos de código en la plantilla.  Por ejemplo:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  Los parámetros de plantilla se escriben con el formato $*parámetro*$.  
  
2.  En el archivo .vstemplate de la plantilla, busque el elemento `ProjectItem` que incluye este archivo.  
  
3.  Establezca el atributo `ReplaceParameters` en `true` para el elemento `ProjectItem`.  Por ejemplo:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## Vea también  
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem \(Elemento, Plantillas de elementos de Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md)