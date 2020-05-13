---
title: Introducción a la plantilla de proyecto VSIX ( Project Template) Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 773e9e6891599cd9672888d0521e94891e0d9f41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711241"
---
# <a name="get-started-with-the-vsix-project-template"></a>Comience con la plantilla de proyecto VSIX

Puede usar la plantilla de proyecto VSIX para crear una extensión o empaquetar una extensión existente para la implementación. La plantilla de proyecto VSIX tiene versiones de Visual Basic y Visual C, y se instala como parte del SDK de Visual Studio.

 La plantilla de proyecto VSIX solo consta de un archivo *source.extension.vsixmanifest,* que contiene información sobre la extensión y los activos que envía.

 Para buscar la plantilla de proyecto VSIX, debe instalar el SDK de Visual Studio. Para obtener más información, vea SDK de [Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Implementar una plantilla de proyecto personalizada mediante la plantilla de proyecto VSIX

 En los pasos siguientes se muestra cómo usar el proyecto VSIX para empaquetar una plantilla de proyecto que puede compartir con otros desarrolladores o cargar en la Galería de Visual Studio.

1. Cree una plantilla de proyecto.

    1. Abra el proyecto desde el que desea crear una plantilla. Este proyecto puede ser de cualquier tipo de proyecto.

    2. En el menú **Proyecto**, haga clic en **Exportar plantilla**. Complete los pasos del asistente.

         Se crea un archivo *.zip* en *%USERPROFILE%-Mis documentos-Visual\\Studio .versión-Mis plantillas exportadas*.

2. Cree un proyecto VSIX vacío.

     Seleccione **File (Archivo)**  > **New (Nuevo)**  > **Project (Proyecto)** . En el cuadro de búsqueda, escriba "vsix" y seleccione la versión de **C** o **Visual Basic** del **proyecto VSIX**.

3. Agregue el archivo *.zip* al proyecto. Establezca su propiedad Copiar `Copy Always`en directorio de **salida** en .

4. En el **Explorador**de soluciones , haga doble clic en el archivo *source.extension.vsixmanifest* para abrirlo en el Diseñador de **manifiestos VSIX**y, a continuación, realice los siguientes cambios:

    - Establezca el campo **Nombre del producto** en Mi plantilla de **proyecto**.

    - Establezca el campo **ID de producto en** **MyProjectTemplate - 1**.

    - Establezca el campo **Autor** en **Fabrikam**.

    - Establezca el campo **Descripción** en **Mi plantilla**de proyecto .

    - En la sección **Assets,** agregue un tipo **Microsoft.VisualStudio.ProjectTemplate** y establezca su ruta de acceso al nombre del archivo *.zip.*

5. Guarde y cierre el archivo *source.extension.vsixmanifest.*

6. Compile el proyecto.

7. En el directorio de salida, haga doble clic en el archivo *.vsix.*

8. Aparece un cuadro de mensaje **del instalador de VSIX.** Siga las instrucciones para instalar la extensión.

9. Cierre Visual Studio y vuelva a abrirlo.

::: moniker range="vs-2017"

10. Seleccione **Extensiones y actualizaciones** (en el menú **Herramientas)** y seleccione la categoría **Plantillas.** Una de las extensiones disponibles debe ser **Mi plantilla de proyecto**.

::: moniker-end

::: moniker range=">=vs-2019"

10. Seleccione **Administrar extensiones** (en el menú **Extensiones)** y seleccione la categoría **Plantillas.** Una de las extensiones disponibles debe ser **Mi plantilla de proyecto**.

::: moniker-end

11. La nueva plantilla de proyecto aparece en el cuadro de diálogo **Nuevo proyecto** en el mismo lugar que la plantilla de proyecto original. Por ejemplo, si ha creado una plantilla denominada **Consola de VB** a partir de una aplicación de consola de Visual Basic, la consola de **VB** aparece en el mismo panel que la plantilla Aplicación de **consola** de Visual Basic.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Para especificar la ubicación de la plantilla en el cuadro de diálogo Nuevo proyecto

1. Las carpetas de la plantilla se encuentran en los directorios de la ruta de instalación de *Visual Studio, Common7, IDE, ProjectTemplates* y la ruta de instalación de *Visual Studio, Common7, IDE, ItemTemplates.* Los nombres de las secciones de nivel superior en el cuadro de diálogo **Nuevo proyecto** no coinciden exactamente con los nombres de las carpetas de plantilla. Donde difieren, utilice el nombre de la carpeta de plantilla.

    Cambie la extensión de archivo *.vsix* a *.zip*y, a continuación, abra el archivo.

2. Cree una nueva carpeta con el mismo nombre que la sección del cuadro de diálogo **Nuevo proyecto** en el que debe aparecer la plantilla.

3. Si la plantilla va a aparecer en una subsección, cree una subcarpeta con el mismo nombre.

4. Mueva el archivo *.zip* de plantilla a la nueva carpeta.

5. Cambie la extensión *.zip* a *.vsix*.

6. Abra el manifiesto VSIX.

7. En el manifiesto VSIX, actualice la ruta de acceso **Asset** de la plantilla para que apunte a la raíz del árbol de directorios que contiene el archivo de plantilla. Por ejemplo, si la plantilla se encuentra en *el archivo .CSharp ,* la referencia debe apuntar a *.CSharp*.
