---
title: Plantillas para proyectos y archivos
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 04aa647d378e956c7a2394b7c3fc2a187a7c5963
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049291"
---
# <a name="project-and-item-templates"></a>Plantillas de proyecto y elemento

Las plantillas de proyectos y elementos proporcionan códigos auxiliares reutilizables que ofrecen a los usuarios códigos y estructuras básicos que pueden personalizar para sus propios fines.

## <a name="visual-studio-templates"></a>plantillas de Visual Studio

Al instalar Visual Studio, se instalan una serie de plantillas de proyecto y elemento predefinidas. Por ejemplo, las plantillas de Visual Basic y C# **Aplicación de Windows Forms** y **Biblioteca de clases** que se muestran en el cuadro de diálogo **Nuevo proyecto** son plantillas de proyecto. Las plantillas de elemento se muestran en el cuadro de diálogo **Agregar nuevo elemento** e incluyen elementos tales como archivos de código, archivos XML, páginas HTML y hojas de estilo.

Estas plantillas proporcionan a los usuarios un punto de partida para empezar a crear proyectos o ampliar proyectos actuales. Las plantillas de proyecto proporcionan los archivos necesarios para un tipo de proyecto determinado, incluyen referencias de ensamblado estándar y establecen propiedades de proyecto y opciones de compilador predeterminadas. Las plantillas de elemento pueden abarcar desde un único archivo vacío con una determinada extensión de archivo hasta varios archivos de código fuente con código auxiliar, archivos de información de diseñador y recursos incrustados.

Puede usar las plantillas instaladas en los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento**, crear sus propias plantillas o descargar y utilizar plantillas creadas por la comunidad. Para obtener más información, vea [Cómo: Crear plantillas de proyecto](../ide/how-to-create-project-templates.md) y [Cómo: Crear plantillas de elemento](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Contenido de una plantilla

Todas las plantillas de proyecto y elemento, ya estén instaladas en Visual Studio o las haya creado usted, funcionan según los mismos principios y tienen un contenido similar. Todas las plantillas contienen los siguientes elementos:

- Los archivos que se van a crear al usar la plantilla. Estos archivos incluyen archivos de código fuente, recursos incrustados, archivos de proyecto, etc.

- Un archivo *.vstemplate* que contiene los metadatos que necesita para mostrar la plantilla en los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento** y crear un proyecto o elemento a partir de la plantilla. Para obtener más información sobre los archivos *.vstemplate*, vea [Parámetros de plantilla](../ide/template-parameters.md).

Cuando estos archivos se comprimen en un archivo *.zip* y se colocan en la carpeta correcta, Visual Studio los muestra de forma automática en estas ubicaciones:

- Las plantillas de proyecto aparecen en el cuadro de diálogo **Nuevo proyecto**.

- Las plantillas de elementos aparecen en el cuadro de diálogo **Agregar nuevo elemento**.

Para obtener más información sobre las carpetas de plantillas, vea [Cómo: Localizar y organizar plantillas](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Vea también

- [Cómo: Crear plantillas de proyecto](../ide/how-to-create-project-templates.md)
- [Cómo: Crear plantillas de elemento](../ide/how-to-create-item-templates.md)
- [Parámetros de plantilla](../ide/template-parameters.md)
- [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)
- [Paquetes NuGet en plantillas de Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)