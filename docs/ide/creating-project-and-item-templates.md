---
title: Plantillas para proyectos y archivos
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 2cc932a2407aeb4951bab970a0edc6e2b2a5fcc9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79306912"
---
# <a name="project-and-item-templates"></a>Plantillas de proyecto y elemento

Las plantillas de proyectos y elementos proporcionan códigos auxiliares reutilizables que ofrecen a los usuarios códigos y estructuras básicos que pueden personalizar para sus propios fines.

## <a name="visual-studio-templates"></a>plantillas de Visual Studio

Al instalar Visual Studio, se instalan una serie de plantillas de proyecto y elemento predefinidas. Estas plantillas, como las plantillas **Aplicación web ASP.NET** y **Biblioteca de clases**, están disponibles para que se elijan al crear un proyecto. Las plantillas de elemento tales como archivos de código, archivos XML, páginas HTML y hojas de estilo se muestran en la ventana **Agregar nuevo elemento**.

Estas plantillas proporcionan a los usuarios un punto de partida para empezar a crear proyectos o ampliar proyectos actuales. Las plantillas de proyecto proporcionan los archivos necesarios para un tipo de proyecto determinado, incluyen referencias de ensamblado estándar y establecen propiedades de proyecto y opciones de compilador predeterminadas. Las plantillas de elemento pueden abarcar desde un único archivo vacío con una determinada extensión de archivo hasta varios archivos de código fuente con código auxiliar, archivos de información de diseñador y recursos incrustados.

Puede usar las plantillas instaladas, crear sus propias plantillas personalizadas o descargar y utilizar plantillas creadas por la comunidad. Para obtener más información, vea [Cómo: Crear plantillas de proyectos](../ide/how-to-create-project-templates.md) y [Cómo: Crear plantillas de elementos](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Contenido de una plantilla

Todas las plantillas de proyecto y elemento, ya estén instaladas en Visual Studio o las haya creado usted, funcionan según los mismos principios y tienen un contenido similar. Todas las plantillas contienen los siguientes elementos:

- Los archivos que se van a crear al usar la plantilla. Estos archivos incluyen archivos de código fuente, recursos incrustados, archivos de proyecto, etc.

::: moniker range="vs-2017"

- Un archivo *.vstemplate* que contiene los metadatos necesarios para crear un proyecto o un elemento a partir de la plantilla y para mostrar la plantilla en las ventanas **Nuevo proyecto** y **Agregar nuevo elemento**.

::: moniker-end

::: moniker range=">=vs-2019"

- Un archivo *.vstemplate* que contiene los metadatos necesarios para crear un proyecto o un elemento a partir de la plantilla y para mostrar la plantilla en la página **Crear un proyecto** y en el cuadro de diálogo **Agregar nuevo elemento**.

::: moniker-end

   Para obtener más información sobre los archivos *.vstemplate*, vea [Template tags](template-tags.md) (Etiquetas de plantilla) y [Parámetros de plantilla](../ide/template-parameters.md).

Cuando estos archivos se comprimen en un archivo *.zip* y se colocan en la carpeta correcta, Visual Studio los muestra de forma automática en estas ubicaciones:

::: moniker range="vs-2017"

- Las plantillas de proyecto aparecen en la ventana **Nuevo proyecto**.

::: moniker-end

::: moniker range=">=vs-2019"

- Las plantillas de proyecto aparecen en la página **Crear un proyecto**.

::: moniker-end

- Las plantillas de elementos aparecen en la ventana **Agregar nuevo elemento**.

Para obtener más información sobre las carpetas de plantillas, vea [Cómo: Buscar y organizar plantillas](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Vea también

- [Cómo: Crear plantillas de proyecto](../ide/how-to-create-project-templates.md)
- [Cómo: Crear plantillas de elementos](../ide/how-to-create-item-templates.md)
- [Template tags](template-tags.md) (Etiquetas de plantilla)
- [Parámetros de plantilla](../ide/template-parameters.md)
- [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)
- [Paquetes NuGet en plantillas de Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
