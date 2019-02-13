---
title: Adición de parámetros de nombre a las plantillas de proyecto y de elemento
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cf9a990be3f5e87180967a4f9f274ec79fbc357e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55943342"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Filtrar Sustituir parámetros en una plantilla

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