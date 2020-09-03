---
title: Creación de plantillas de proyectos y elementos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], projects
- item templates, about item templates
- templates [Visual Studio], item
- Visual Studio templates, item
- Visual Studio templates, about templates
- project templates [Visual Studio], about project templates
- Visual Studio templates, project
- templates [Visual Studio], about templates
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 995696dafce64cdcb1fbb11d0788bbe13453c440
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619297"
---
# <a name="creating-project-and-item-templates"></a>Creación de plantillas de proyectos y elementos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] las plantillas de proyecto y elemento proporcionan códigos auxiliares reutilizables que proporcionan a los usuarios código y estructura básicos que pueden usar para sus propios fines.

## <a name="visual-studio-templates"></a>Plantillas de Visual Studio
 Al instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], se instala una serie de plantillas de proyecto y elemento predefinidas. Las plantillas Aplicación de Windows Forms y Biblioteca de clases de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] y [!INCLUDE[csprcs](../includes/csprcs-md.md)] disponibles en el cuadro de diálogo **Nuevo proyecto** son ejemplos de plantillas de proyecto. Las plantillas de elemento instaladas están disponibles en el cuadro de diálogo **Agregar nuevo elemento** e incluyen elementos tales como archivos de código, archivos XML, páginas HTML y hojas de estilos.

 Estas plantillas proporcionan a los usuarios un punto de partida para empezar a crear proyectos o ampliar proyectos actuales. Las plantillas de proyecto proporcionan los archivos necesarios para un tipo de proyecto determinado, incluyen referencias de ensamblado estándar y establecen propiedades de proyecto y opciones de compilador predeterminadas. Las plantillas de elemento pueden abarcar desde un único archivo vacío con la extensión de nombre de archivo correcta hasta un elemento de varios archivos con, por ejemplo, archivos de código fuente con código auxiliar, archivos de información de diseñador y recursos incrustados.

 Además de las plantillas instaladas en los cuadros de diálogo **nuevo proyecto** y **Agregar nuevo elemento** , puede crear sus propias plantillas o descargar y usar plantillas creadas por la comunidad. Para obtener más información, vea [Cómo: crear plantillas de proyecto](../ide/how-to-create-project-templates.md) y [Cómo: crear plantillas de elementos](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Contenido de una plantilla
 Todas las plantillas de proyecto y elemento, ya estén instaladas en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o hayan sido creadas por usted, funcionan según los mismos principios y tienen un contenido similar. Todas las plantillas contienen los siguientes elementos:

- Los archivos que se van a crear al usar la plantilla. Esto incluye archivos de código fuente, recursos incrustados, archivos de proyecto, etc.

- Un archivo .vstemplate. Este archivo contiene los metadatos que facilitan a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la información que necesita para mostrar la plantilla en los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento** y crear un proyecto o elemento a partir de la plantilla. Para obtener más información sobre los archivos. vstemplate, vea [parámetros de plantilla](../ide/template-parameters.md).

  Cuando estos archivos se comprimen en un archivo .zip y se colocan en la carpeta correcta, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] los muestra de forma automática. Las plantillas de proyecto aparecen en la sección **Mis plantillas** de los cuadros de diálogo **Nuevo proyecto** y las plantillas de elemento aparecen en el cuadro de diálogo **Agregar nuevo elemento**. Para obtener más información sobre las carpetas de plantillas, vea [Cómo: buscar y organizar plantillas](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="starter-kits"></a>Starter Kits
 Starter Kits son plantillas mejoradas que se pueden compartir con otros integrantes de la comunidad. Un Starter Kit incluye ejemplos de código de compilación, documentación y otros recursos para ayudar a los usuarios a obtener información sobre las nuevas herramientas y técnicas de programación y, al mismo tiempo, crear aplicaciones útiles y prácticas. El contenido y los procedimientos básicos de los Starter Kits son idénticos a los de las plantillas. Para obtener más información, vea [Cómo: Crear Starter Kits](../ide/how-to-create-starter-kits.md).

## <a name="see-also"></a>Consulte también
 [Cómo: crear plantillas](../ide/how-to-create-project-templates.md) [de proyecto cómo: crear plantillas de elementos parámetros de](../ide/how-to-create-item-templates.md) [plantilla](../ide/template-parameters.md) [personalizar plantillas](../ide/customizing-project-and-item-templates.md) [Cómo: crear Starter kits](../ide/how-to-create-starter-kits.md)
