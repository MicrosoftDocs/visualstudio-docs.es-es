---
title: Plantilla de proyecto VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc2600a6c72e13ba7d894dab84f0b8a171d5a43e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322840"
---
# <a name="vsix-project-template"></a>Plantilla de proyecto VSIX

Puede usar la plantilla de proyecto de VSIX para ajustar una o varias extensiones de Visual Studio en un proyecto de VSIX y, a continuación, publicar el paquete en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/) sitio Web.

 Implementación de VSIX es compatible con los VSPackages, ensamblados, componentes MEF, plantillas de proyecto, plantillas de elementos, controles de cuadro de herramientas y tipos de extensión personalizados.

> [!NOTE]
> Para usar proyectos VSIX, debe instalar el SDK de Visual Studio. Para obtener más información sobre el SDK de Visual Studio, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Dónde encontrar la plantilla de proyecto VSIX

La plantilla de proyecto de VSIX está disponible en el **nuevo proyecto** cuadro de diálogo buscando "vsix".  Hay tanto un C# y versión de Visual Basic.

> [!TIP]
> Debe asegurarse de que .NET Framework 4.5 o versiones posteriores, se especifica en el cuadro de lista desplegable en la parte superior de la **nuevo proyecto** cuadro de diálogo.

## <a name="uses-of-the-vsix-project-template"></a>Usos de la plantilla de proyecto VSIX

La plantilla de proyecto VSIX tiene dos usos principales:

- Para implementar plantillas de proyecto, plantillas de elementos y las extensiones.

- Para ajustar los resultados de varias extensiones en un paquete de distribución.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Empaquetar una extensión en un proyecto VSIX vacío

Puede empaquetar una extensión existente o una extensión que no tenga ya VSIX admiten incluyéndolo en un proyecto VSIX vacío. La extensión que se ajustará debe ser de un tipo que es compatible con la [esquema VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Para empaquetar una extensión mediante el uso de un proyecto de VSIX

1. Compile los proyectos que componen la extensión.

2. Crear un proyecto de VSIX con el **proyecto VSIX** plantilla.

    *Source.Extension.vsixmanifest* se abre en **Diseñador de manifiestos**.

3. En el **activos** ficha, elija la **New** botón.

    El **Agregar nuevo activo** aparece el cuadro de diálogo.

4. En el **tipo** lista, elija el tipo de extensión que se va a agregar.

5. Para agregar un elemento de extensión o contenido que se incluye en la solución actual (por ejemplo, una plantilla de elemento o un ensamblado compilado), realice los pasos siguientes:

   1. En el **origen** elija **un proyecto de la solución actual**.

   2. En el **proyecto** lista, elija el nombre de la extensión.

   3. En el **insertar en esta carpeta** , escriba el nombre de una carpeta en la que se va a incrustar el recurso y, a continuación, elija el **Aceptar** botón.

6. Para agregar una extensión o un elemento de contenido que no se incluye en la solución actual, realice los pasos siguientes:

   1. En el **origen** cuadro de lista, elija **archivo en filesystem**.

   2. En el **ruta** campo, escriba la ruta de acceso completa al archivo de extensión compilado o comprimidos o usar el **examinar** botón para examinar el archivo.

   3. En el **insertar en esta carpeta** , escriba el nombre de una carpeta en la que se va a incrustar el recurso y, a continuación, elija el **Aceptar** botón.

7. Si desea que el paquete para incluir extensiones adicionales, agregue de la misma manera.

8. Compile la solución.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compila un *.vsix* archivo que contiene un archivo de manifiesto de VSIX en un archivo [Content_Types] *.xml* archivo y todos los recursos de extensión que ha agregado al proyecto.

## <a name="see-also"></a>Vea también

- [Referencia de esquema 2.0 de extensión VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Búsqueda y uso de extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)