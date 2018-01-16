---
title: Plantillas de Visual Studio para proyectos y archivos | Microsoft Docs
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3959b01fdfc0ff77bdd5a3ffa0c96366b9da87d7
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2018
---
# <a name="project-and-item-templates"></a>Plantillas de proyecto y elemento

Las plantillas de proyectos y elementos proporcionan códigos auxiliares reutilizables que ofrecen a los usuarios códigos y estructuras básicos que pueden personalizar para sus propios fines.

## <a name="visual-studio-templates"></a>plantillas de Visual Studio

Al instalar Visual Studio, se instalan una serie de plantillas de proyecto y elemento predefinidas. Por ejemplo, las plantillas de Visual Basic y C# **Aplicación de Windows Forms** y **Biblioteca de clases** que se muestran en el cuadro de diálogo **Nuevo proyecto** son plantillas de proyecto. Las plantillas de elemento se muestran en el cuadro de diálogo **Agregar nuevo elemento** e incluyen elementos tales como archivos de código, archivos XML, páginas HTML y hojas de estilo.

Estas plantillas proporcionan a los usuarios un punto de partida para empezar a crear proyectos o ampliar proyectos actuales. Las plantillas de proyecto proporcionan los archivos necesarios para un tipo de proyecto determinado, incluyen referencias de ensamblado estándar y establecen propiedades de proyecto y opciones de compilador predeterminadas. Las plantillas de elemento pueden abarcar desde un único archivo vacío con una determinada extensión de archivo hasta un elemento de varios archivos con, por ejemplo, archivos de código fuente con código auxiliar, archivos de información de diseñador y recursos incrustados.

Además de las plantillas instaladas en los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento**, puede crear sus propias plantillas o descargar y usar plantillas creadas por la comunidad. Para obtener más información, vea [Cómo: Crear plantillas de proyectos](../ide/how-to-create-project-templates.md) y [Cómo: Crear plantillas de elementos](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Contenido de una plantilla

Todas las plantillas de proyecto y elemento, ya estén instaladas en Visual Studio o las haya creado usted, funcionan según los mismos principios y tienen un contenido similar. Todas las plantillas contienen los siguientes elementos:

- Los archivos que se van a crear al usar la plantilla. Esto incluye archivos de código fuente, recursos incrustados, archivos de proyecto, etc.

- Un archivo .vstemplate. Este archivo contiene los metadatos que facilitan la información que necesita para mostrar la plantilla en los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento** y para crear un proyecto o elemento a partir de la plantilla. Para obtener más información sobre los archivos .vstemplate, vea [Parámetros de plantilla](../ide/template-parameters.md).

Cuando estos archivos se comprimen en un archivo .zip y se colocan en la carpeta correcta, Visual Studio los muestra de forma automática en estas ubicaciones:

- Las plantillas de proyecto aparecen en el cuadro de diálogo **Nuevo proyecto**.

- Las plantillas de elementos aparecen en el cuadro de diálogo **Agregar nuevo elemento**.

Para obtener más información sobre las carpetas de plantillas, vea [Cómo: Buscar y organizar plantillas](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="starter-kits"></a>Starter Kits

Starter Kits son plantillas mejoradas que se pueden compartir con otros integrantes de la comunidad. Un Starter Kit incluye ejemplos de código de compilación, documentación y otros recursos para ayudar a los usuarios a obtener información sobre las nuevas herramientas y técnicas de programación y, al mismo tiempo, crear aplicaciones útiles y prácticas. El contenido y los procedimientos básicos de los Starter Kits son idénticos a los de las plantillas. Para obtener más información, vea [Cómo: Crear Starter Kits](../ide/how-to-create-starter-kits.md).

## <a name="see-also"></a>Vea también

[Cómo: Crear plantillas de proyectos](../ide/how-to-create-project-templates.md)  
[Cómo: Crear plantillas de elementos](../ide/how-to-create-item-templates.md)  
[Parámetros de plantilla](../ide/template-parameters.md)  
[Personalización de plantillas](../ide/customizing-project-and-item-templates.md)  
[Paquetes NuGet en plantillas de Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)