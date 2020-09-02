---
title: Cómo sustituir parámetros en una plantilla | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fe49c928ca3de318410eba56afeae6f4329efed3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670658"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Cómo: Sustituir parámetros en una plantilla
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede reemplazar parámetros de plantilla (como los nombres de clase y los espacios de nombres) al crear un archivo basado en una plantilla. Para obtener una lista completa de los parámetros de plantilla, vea [parámetros de plantilla](../ide/template-parameters.md).

## <a name="procedure"></a>Procedimiento
 Puede reemplazar parámetros de los archivos de una plantilla cada vez que se cree un proyecto basado en esa plantilla. En este procedimiento se explica cómo crear una plantilla que reemplace el nombre de un espacio de nombres por el nombre del proyecto seguro al crear un proyecto nuevo con la plantilla.

#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Para usar un parámetro que sustituya el nombre del espacio de nombres por el nombre del proyecto

1. Inserte el parámetro en uno o varios archivos de código en la plantilla. Por ejemplo:

    ```
    namespace $safeprojectname$
    ```

    > [!NOTE]
    > Los parámetros de plantilla se escriben con el formato $*parámetro*$.

2. En el archivo .vstemplate de la plantilla, busque el elemento `ProjectItem` que incluye este archivo.

3. Establezca el atributo `ReplaceParameters` en `true` para el elemento `ProjectItem`. Por ejemplo:

    ```
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Consulte también
 [Crear plantillas de proyecto y elemento plantillas de](../ide/creating-project-and-item-templates.md) [plantilla](../ide/template-parameters.md) de [Visual Studio referencia de esquema de plantilla](../extensibility/visual-studio-template-schema-reference.md) [elemento ProjectItem (plantillas de elementos de Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
