---
title: Crear plantillas de proyecto
description: Aprenda a usar el Asistente para exportar plantillas y otros métodos para crear plantillas de proyecto en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 9030a88e67c90fab870613d71d0fe63992166222
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597189"
---
# <a name="how-to-create-project-templates"></a>Cómo: Crear plantillas de proyectos

En este tema se muestra cómo crear una plantilla con el **Asistente para exportar plantillas**, que empaqueta su plantilla en un archivo *.zip*.

## <a name="use-the-export-template-wizard"></a>Uso del Asistente para exportar plantillas

1. Crear un proyecto.

    > [!NOTE]
    > Use solo caracteres de identificador válidos al asignar un nombre al proyecto que será el origen de una plantilla. En caso contrario, se pueden producir errores de compilación en los proyectos creados a partir de la plantilla. Para obtener más información sobre los caracteres de identificador válidos, vea [Nombres de elementos declarados (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) o [Identificadores de C++](/cpp/cpp/identifiers-cpp). También puede usar [parámetros de plantilla](../ide/template-parameters.md) para utilizar nombres "seguros" para las clases y los espacios de nombres.

2. Modifique el proyecto hasta que esté listo para exportarse como una plantilla. Por ejemplo, le recomendamos que edite los archivos de código para indicar dónde debe aplicarse el reemplazo de parámetros. Vea [Cómo: Sustituir parámetros en una plantilla](../ide/how-to-substitute-parameters-in-a-template.md).

3. En el menú **Proyecto**, elija **Exportar plantilla**.

   Se abre el **Asistente para exportar plantillas**.

4. En la página **Elegir tipo de plantilla**, seleccione **Plantilla de proyecto**. Seleccione el proyecto que quiera exportar a una plantilla y, después, **Siguiente**.

::: moniker range="vs-2017"

5. En la página **Seleccionar opciones de plantilla**, escriba un nombre y, si quiere, una descripción, un icono y una imagen de vista previa para su plantilla. Estos elementos aparecerán en el cuadro de diálogo **Nuevo proyecto**. Elija **Finalizar**.

   El proyecto se exporta a un archivo *.zip* y se coloca en la ubicación de salida especificada y, si se selecciona, se importa a Visual Studio.

Para encontrar una plantilla en el cuadro de diálogo **Nuevo proyecto**, expanda la opción **Instalado** y, después, la categoría que corresponde al elemento `ProjectType` del archivo *.vstemplate*. Por ejemplo, un archivo *.vstemplate* que contiene `<ProjectType>CSharp</ProjectType>` aparece de forma predeterminada en **Instalado** > **Visual C#**. Para organizar una plantilla en un subdirectorio del tipo de proyecto solo tiene que crear una carpeta en el directorio correspondiente y colocar ahí el archivo *.zip* de la plantilla. Para obtener más información, vea [Cómo: Localizar y organizar plantillas](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

5. En la página **Seleccionar opciones de plantilla**, escriba un nombre y, si quiere, una descripción, un icono y una imagen de vista previa para su plantilla. Estos elementos aparecerán en el cuadro de diálogo en que se crea un proyecto. Elija **Finalizar**.

   El proyecto se exporta a un archivo *.zip* y se coloca en la ubicación de salida especificada y, si se selecciona, se importa a Visual Studio.

Para buscar la plantilla en el cuadro de diálogo en que se crea un proyecto, búsquela por nombre o desplácese por la lista. (El filtrado basado en el lenguaje o el tipo de proyecto no es posible actualmente para las plantillas de usuario).

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>Otras formas de crear plantillas de proyectos

Puede crear plantillas de proyectos manualmente incluyendo en una carpeta los archivos que componen el proyecto y creando un archivo XML *.vstemplate* con los metadatos adecuados. Para obtener más información, vea [Cómo: Crear plantillas web manualmente](../ide/how-to-manually-create-web-templates.md).

Si tiene Visual Studio SDK instalado, puede ajustar la plantilla terminada en un archivo VSIX para su implementación con la plantilla **Proyecto VSIX**. Para obtener más información, vea [Introducción a la plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Vea también

- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Cómo: Crear plantillas de elemento](../ide/how-to-create-item-templates.md)
- [Introducción a la plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
