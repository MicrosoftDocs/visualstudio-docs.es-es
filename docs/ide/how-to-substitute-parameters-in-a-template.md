---
title: Adición de parámetros de nombre a las plantillas de proyecto y de elemento en Visual Studio
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 26802b7b5293fd43eb1546290560c5300c360003
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945940"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Cómo: Sustituir parámetros en una plantilla

Los parámetros de plantilla le permiten reemplazar identificadores, como nombres de clase y espacios de nombres, cuando se crea un archivo a partir de una plantilla. Puede agregar parámetros de plantilla a una plantilla o bien crear sus propias plantillas con dichos parámetros.

Los parámetros de plantilla se escriben con el formato $*parámetro*$. Para obtener una lista completa de parámetros de plantilla, vea [Parámetros de plantilla](../ide/template-parameters.md).

En la sección siguiente se muestra cómo modificar una plantilla para reemplazar el nombre de un espacio de nombres con el nombre del proyecto "seguro".

## <a name="to-use-a-parameter-to-replace-the-namespace-name"></a>Para usar un parámetro para reemplazar el nombre de espacio de nombres

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