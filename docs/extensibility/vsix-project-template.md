---
title: Plantilla de proyecto VSIX (VSIX Project Template) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74791a77ee1c720fb60876a1efa6bd58fa94f68b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697934"
---
# <a name="vsix-project-template"></a>Plantilla de proyecto VSIX

Puede usar la plantilla de proyecto VSIX para ajustar una o varias extensiones de Visual Studio en un proyecto VSIX y, a continuación, publicar el paquete en el sitio Web de [Visual Studio Marketplace.](https://marketplace.visualstudio.com/)

 La implementación de VSIX admite VSPackages, ensamblados, componentes MEF, plantillas de proyecto, plantillas de elementos, controles de cuadro de herramientas y tipos de extensión personalizados.

> [!NOTE]
> Para usar proyectos VSIX, debe instalar el SDK de Visual Studio. Para obtener más información acerca del SDK de Visual Studio, vea SDK de [Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Dónde encontrar la plantilla de proyecto VSIX

La plantilla Proyecto VSIX está disponible en el cuadro de diálogo **Nuevo proyecto** buscando "vsix".  Hay una versión de Visual Basic y de C.

> [!TIP]
> Debe asegurarse de que .NET Framework 4.5 o superior se especifica en el cuadro de lista desplegable en la parte superior del cuadro de diálogo **Nuevo proyecto.**

## <a name="uses-of-the-vsix-project-template"></a>Usos de la plantilla de proyecto VSIX

La plantilla de proyecto VSIX tiene dos usos principales:

- Para implementar plantillas de proyecto, plantillas de elementos y extensiones.

- Para ajustar las salidas de varias extensiones en un paquete de implementación.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Empaquetado de una extensión en un proyecto VSIX vacío

Puede empaquetar una extensión existente o una extensión que aún no tenga compatibilidad con VSIX, envolviéndola en un proyecto VSIX vacío. La extensión que se va a ajustar debe ser de un tipo compatible con el [esquema VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Para empaquetar una extensión mediante un proyecto VSIX

1. Compile los proyectos que componen la extensión.

2. Cree un proyecto VSIX mediante la plantilla **Proyecto VSIX.**

    *Source.extension.vsixmanifest* se abre en **el Diseñador de manifiestos**.

3. En la pestaña **Assets(Assets),** elija el botón **New (Nuevo).**

    Aparece el cuadro de diálogo **Agregar nuevo recurso.**

4. En la lista **Tipo,** elija el tipo de extensión que desea agregar.

5. Para agregar una extensión o un elemento de contenido que se incluye en la solución actual (por ejemplo, una plantilla de elemento o un ensamblado compilado), realice los pasos siguientes:

   1. En la lista **Origen,** elija Un proyecto en la **solución actual.**

   2. En la lista **Proyecto,** elija el nombre de la extensión.

   3. En el cuadro **Incrustar en esta carpeta,** escriba el nombre de una carpeta en la que desea incrustar el recurso y, a continuación, elija el botón **Aceptar.**

6. Para agregar una extensión o un elemento de contenido que no se incluye en la solución actual, realice los pasos siguientes:

   1. En el cuadro de lista **Origen,** elija **Archivo en el sistema de archivos**.

   2. En el campo **Ruta** de acceso, escriba la ruta de acceso completa al archivo de extensión compilado o comprimido o utilice el botón **Examinar** para buscar el archivo.

   3. En el cuadro **Incrustar en esta carpeta,** escriba el nombre de una carpeta en la que desea incrustar el recurso y, a continuación, elija el botón **Aceptar.**

7. Si desea que el paquete incluya extensiones adicionales, agréguelas de la misma manera.

8. Compile la solución.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]compila un archivo *.vsix* que contiene un archivo de manifiesto VSIX, un archivo *.xml* [Content_Types] y todos los activos de extensión que agregó al proyecto.

## <a name="see-also"></a>Vea también

- [Referencia del esquema de extensión VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Búsqueda y uso de extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
