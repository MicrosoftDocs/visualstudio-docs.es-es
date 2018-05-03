---
title: Creación de plantillas de proyectos para Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a18b756b38a810915ea49e9f3208e9349afda7ef
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-project-templates"></a>Cómo: Crear plantillas de proyectos

En este tema se muestra cómo crear una plantilla con el **Asistente para exportar plantillas**, que empaqueta su plantilla en un archivo *.zip*.

## <a name="to-create-a-user-project-template-by-using-the-export-template-wizard"></a>Para crear una plantilla de proyecto de usuario mediante el Asistente para exportar plantillas

1. Cree un proyecto.

    > [!NOTE]
    > Use solo caracteres de identificador válidos al asignar un nombre al proyecto que será el origen de una plantilla. En caso contrario, se pueden producir errores de compilación en los proyectos creados a partir de la plantilla. Para obtener más información sobre los caracteres de identificador válidos, vea [Nombres de elementos declarados (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) o [Identificadores de C++](/cpp/cpp/identifiers-cpp). También puede usar [parámetros de plantilla](../ide/template-parameters.md) para utilizar nombres "seguros" para las clases y los espacios de nombres.

1. Modifique el proyecto hasta que esté listo para exportarse como una plantilla. Por ejemplo, le recomendamos que edite los archivos de código para indicar dónde debe aplicarse el reemplazo de parámetros. Vea [Cómo: Sustituir parámetros en una plantilla](../ide/how-to-substitute-parameters-in-a-template.md).

1. En el menú **Proyecto**, elija **Exportar plantilla**.

   Se abre el **Asistente para exportar plantillas**.

1. En la página **Elegir tipo de plantilla**, seleccione **Plantilla de proyecto**. Seleccione el proyecto que quiera exportar a una plantilla y, después, **Siguiente**.

1. En la página **Seleccionar opciones de plantilla**, escriba un nombre y, si quiere, una descripción, un icono y una imagen de vista previa para su plantilla. Estos elementos aparecerán en el cuadro de diálogo **Nuevo proyecto**. Elija **Finalizar**.

  El proyecto se exporta a un archivo *.zip* y se coloca en la ubicación de salida especificada y, si se selecciona, se importa a Visual Studio.

>[!NOTE]
> Para encontrar una plantilla en el cuadro de diálogo **Nuevo proyecto**, expanda la opción **Instalado** y, después, la categoría que corresponde al elemento `ProjectType` del archivo *.vstemplate*. Por ejemplo, un archivo *.vstemplate* que contiene `<ProjectType>CSharp</ProjectType>` aparece de forma predeterminada en **Instalado** > **Visual C#**. Para organizar una plantilla en un subdirectorio del tipo de proyecto solo tiene que crear una carpeta en el directorio correspondiente y colocar ahí el archivo *.zip* de la plantilla. Para más información, vea [Cómo: Localizar y organizar plantillas](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="other-ways-to-create-project-templates"></a>Otras formas de crear plantillas de proyectos

Puede crear plantillas de proyectos manualmente incluyendo en una carpeta los archivos que componen el proyecto y, después, creando un archivo XML *.vstemplate* con los metadatos adecuados. Para obtener más información, vea [Cómo: Crear plantillas web manualmente](../ide/how-to-manually-create-web-templates.md).

Si tiene Visual Studio SDK instalado, puede ajustar la plantilla terminada en un archivo VSIX para su implementación con la plantilla **Proyecto VSIX**. Para obtener más información, vea [Introducción a la plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Vea también

[Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)  
[Cómo: Crear plantillas de elementos](../ide/how-to-create-item-templates.md)  
[Introducción a la plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
