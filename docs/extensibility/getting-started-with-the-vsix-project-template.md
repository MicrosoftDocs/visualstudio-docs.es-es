---
title: Introducción a la plantilla de proyecto VSIX | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8bb85e507e62bf7dd13288cbd08d7bf9d06973e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342465"
---
# <a name="get-started-with-the-vsix-project-template"></a>Introducción a la plantilla de proyecto de VSIX

Puede usar la plantilla de proyecto de VSIX para crear una extensión o para una extensión existente para la implementación del paquete. La plantilla de proyecto de VSIX tiene las versiones de Visual Basic y Visual C# y se instala como parte del SDK de Visual Studio.

 La plantilla de proyecto de VSIX solo consta de un *source.extension.vsixmanifest* archivo, que contiene información acerca de la extensión y los recursos se incluye.

 Para buscar la plantilla de proyecto VSIX, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Implementar una plantilla de proyecto personalizado mediante la plantilla de proyecto de VSIX

 Los pasos siguientes muestran cómo usar el proyecto VSIX para empaquetar una plantilla de proyecto que se puede compartir con otros desarrolladores o cargar en la Galería de Visual Studio.

1. Crear una plantilla de proyecto.

    1. Abra el proyecto desde el que se va a crear una plantilla. Este proyecto puede ser de cualquier tipo de proyecto.

    2. En el menú **Proyecto**, haga clic en **Exportar plantilla**. Complete los pasos del asistente.

         Un *.zip* archivo se crea en *%USERPROFILE%\My Documents\Visual Studio {versión} \My Exported plantillas\\* .

2. Crear un proyecto VSIX vacío.

     Seleccione **Archivo** > **Nuevo** > **Proyecto**. En el cuadro de búsqueda, escriba "vsix" y seleccione el **C#** o **Visual Basic** verzi **proyecto VSIX**.

3. Agregar el *.zip* archivo al proyecto. Establezca su **Copy to Output Directory** propiedad `Copy Always`.

4. En **el Explorador de soluciones**, haga doble clic en el *source.extension.vsixmanifest* archivo para abrirlo en el **el Diseñador de manifiestos VSIX**y, a continuación, realice los cambios siguientes:

    - Establecer el **Product Name** campo **mi plantilla de proyecto**.

    - Establecer el **Id. de producto** campo **MyProjectTemplate - 1**.

    - Establecer el **autor** campo **Fabrikam**.

    - Establecer el **descripción** campo **mi plantilla de proyecto**.

    - En el **activos** sección, agregue un **Microsoft.VisualStudio.ProjectTemplate** tipo y establecer su ruta de acceso en el nombre de la *.zip* archivo.

5. Guarde y cierre el *source.extension.vsixmanifest* archivo.

6. Compile el proyecto.

7. En el directorio de resultados, haga doble clic en el *.vsix* archivo.

8. Un **instalador de VSIX** aparece el cuadro de mensaje. Siga las instrucciones para instalar la extensión.

9. Cierre Visual Studio y vuelva a abrirlo.

::: moniker range="vs-2017"

10. Seleccione **extensiones y actualizaciones** (en el **herramientas** menú) y seleccione el **plantillas** categoría. Debe ser una de las extensiones disponibles **mi plantilla de proyecto**.

::: moniker-end

::: moniker range=">=vs-2019"

10. Seleccione **administrar extensiones** (en el **extensiones** menú) y seleccione el **plantillas** categoría. Debe ser una de las extensiones disponibles **mi plantilla de proyecto**.

::: moniker-end

11. La plantilla de proyecto nuevo aparece en la **nuevo proyecto** cuadro de diálogo en el mismo lugar que la plantilla de proyecto original. Por ejemplo, si ha creado una plantilla denominada **VB consola** desde una aplicación de consola de Visual Basic, **VB consola** aparece en el mismo panel, como Visual Basic **aplicación de consola**plantilla.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Para especificar la ubicación de la plantilla en el cuadro de diálogo nuevo proyecto

1. Las carpetas de plantillas se encuentran en el *{ruta de instalación de Visual Studio} \Common7\IDE\ProjectTemplates* y *{ruta de instalación de Visual Studio} \Common7\IDE\ItemTemplates* directorios. Los nombres de las secciones de nivel superior de la **nuevo proyecto** cuadro de diálogo no coinciden exactamente con los nombres de las carpetas de plantilla. Si difieren, use el nombre de la carpeta de plantillas.

    Cambiar el *.vsix* extensión al archivo *.zip*y, a continuación, abra el archivo.

2. Cree una carpeta con el mismo nombre que la sección de la **nuevo proyecto** la plantilla debe aparecer en el cuadro de diálogo.

3. Si la plantilla que se va a aparecer en una subsección, cree una subcarpeta del mismo nombre.

4. Mover la plantilla *.zip* archivo a la carpeta nueva.

5. Cambiar el *.zip* extensión *.vsix*.

6. Abra el manifiesto VSIX.

7. En el manifiesto de VSIX, actualice el **activos** ruta de acceso de la plantilla de forma que apunte a la raíz del árbol del directorio que contiene el archivo de plantilla. Por ejemplo, si la plantilla está en *\CSharp\Windows*, la referencia debe apuntar a *\CSharp*.
