---
title: Adición de parámetros de nombre a las plantillas de proyecto y de elemento
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 3c8b6e0570567e8eb696fda61fe9db7bbd4a2f1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283949"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Cómo: Sustituir parámetros en una plantilla

Los parámetros de plantilla le permiten reemplazar identificadores, como nombres de clase y espacios de nombres, cuando se crea un archivo a partir de una plantilla. Puede agregar parámetros de plantilla a una plantilla o bien crear sus propias plantillas con dichos parámetros.

Los parámetros de plantilla se escriben con el formato $*parámetro*$. Para obtener una lista completa de parámetros de plantilla, vea [Parámetros de plantilla](../ide/template-parameters.md).

En la sección siguiente se muestra cómo modificar una plantilla para reemplazar el nombre de un espacio de nombres con el nombre del proyecto "seguro".

## <a name="example---namespace-name"></a>Ejemplo: nombre del espacio de nombres

1. Inserte el parámetro en uno o varios archivos de código en la plantilla. Por ejemplo:

    ```csharp
    namespace $safeprojectname$
    ```

1. En el archivo *vstemplate* de la plantilla, busque el elemento `ProjectItem` que incluye este archivo.

1. Establezca el atributo `ReplaceParameters` en `true` para el elemento `ProjectItem`:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Vea también

- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Parámetros de plantilla](../ide/template-parameters.md)
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem (Elemento, Plantillas de elementos de Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
