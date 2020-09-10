---
title: Introducción al servicio de lenguaje y extensiones de editor
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94ccda92a0ad5508b8e14ec267f32c50b64e55c0
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742890"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Introducción al servicio de lenguaje y extensiones de editor

Puede usar las extensiones de editor para agregar características del servicio de lenguaje como esquematización, coincidencia de llaves, IntelliSense y bombillas a su propio lenguaje de programación o a cualquier tipo de contenido. También puede personalizar la apariencia y el comportamiento del editor de Visual Studio, por ejemplo, colores de texto, márgenes, elementos gráficos y otros elementos visuales. También puede definir su propio tipo de contenido y especificar la apariencia y el comportamiento de las vistas de texto en las que aparece el contenido.

 Para empezar a escribir extensiones de editor, use las plantillas de proyecto de editor que se instalan como parte del SDK de Visual Studio. El SDK de Visual Studio es un conjunto de herramientas descargables que facilitan el desarrollo de extensiones de Visual Studio, ya sea mediante VSPackages o mediante el Managed Extensibility Framework (MEF).

> [!NOTE]
> Para obtener más información sobre el SDK de Visual Studio, vea [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Le recomendamos que obtenga información sobre los siguientes conceptos y tecnologías antes de escribir sus propias extensiones de editor.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Las extensiones de Windows Presentation Foundation (WPF) y de editor

 La interfaz de usuario (UI) del editor de Visual Studio se implementa mediante el Windows Presentation Foundation (WPF). WPF proporciona una experiencia visual enriquecida y un modelo de programación coherente que separa los aspectos visuales del código de la lógica de negocios. Puede usar muchos elementos y características de WPF al crear extensiones de editor. Para obtener más información, vea [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Extensiones de Managed Extensibility Framework (MEF) y del editor

 El editor de Visual Studio usa el Managed Extensibility Framework (MEF) para administrar sus componentes y extensiones. MEF también permite a los desarrolladores crear fácilmente extensiones para una aplicación host como Visual Studio. En este marco, se define una extensión de acuerdo con un contrato MEF y se exporta como una parte del componente MEF. La aplicación host administra las partes del componente al buscarlas, registrarlas y asegurarse de que se aplican al contexto correcto.

> [!NOTE]
> Para obtener más información sobre MEF en el editor, vea [Managed Extensibility Framework en el editor](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Extensiones y puntos de extensión del editor de Visual Studio

 Los puntos de extensión de editor son partes de componentes de MEF que puede personalizar y ampliar. En algunos casos, puede extender el punto de extensión implementando una interfaz y exportándolo junto con los metadatos correctos. En otros casos, basta con declarar una extensión y exportarla como un tipo determinado.

 A continuación se muestran algunos de los tipos básicos de extensiones de editor:

- Márgenes y barras de desplazamiento

- Etiquetas

- Elementos gráficos

- Opciones

- IntelliSense

  Para obtener más información acerca de los puntos de extensión de editor, consulte [puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Implementar extensiones de editor

 En Visual Studio, implemente extensiones de editor agregando un archivo de metadatos denominado *source. Extension. vsixmanifest* a la solución, compilando la solución y agregando después una copia de los archivos binarios y el manifiesto en una carpeta conocida por Visual Studio. El archivo de manifiesto define los hechos básicos de la extensión (por ejemplo, el nombre, el autor, la versión y el tipo de contenido). Para obtener más información sobre el archivo de manifiesto VSIX y cómo implementar extensiones, vea [envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Cuando se instala una extensión en un equipo, se incluyen los archivos binarios y el manifiesto en una subcarpeta de la carpeta que Visual Studio conoce.

> [!WARNING]
> No tiene que preocuparse de los detalles de los manifiestos y las ubicaciones de implementación si usa una de las plantillas de extensibilidad del editor que se incluyen en Visual Studio. Las plantillas contienen todo lo necesario para registrar e implementar una extensión.

## <a name="run-extensions-in-the-experimental-instance"></a>Ejecutar extensiones en la instancia experimental

 Puede aislar su versión de trabajo de Visual Studio mientras desarrolla una extensión mediante su implementación en la siguiente carpeta experimental (en Windows Vista y Windows 7):

 *{% LOCALAPPDATA%} \VisualStudio\10.0Exp\Extensions \\ {Company} \\ {ExtensionID}*

 donde *% LOCALAPPDATA%* es el nombre del usuario que ha iniciado sesión, *Company* es el nombre de la compañía propietaria de la extensión y *ExtensionID* es el identificador de la extensión.

 Cuando se implementa una extensión en la ubicación experimental, se ejecuta en modo de depuración. Se inicia una segunda instancia de Visual Studio y se denomina **Microsoft Visual Studio instancia experimental**.

## <a name="manage-extensions"></a>Administración de extensiones

 Las extensiones de Visual Studio se muestran en **extensiones y actualizaciones** (en el menú **herramientas** ). Si está probando una extensión en la instancia experimental, se muestra en **extensiones y actualizaciones** en la instancia experimental, pero no aparece en la instancia de desarrollo.

 Para obtener más información, vea [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Usar plantillas para crear extensiones de editor

 Puede usar plantillas de editor para crear extensiones de MEF que personalicen clasificadores, elementos gráficos y márgenes. Hay plantillas para proyectos de C# y Visual Basic. Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 También puede usar la plantilla de Proyecto VSIX para crear extensiones. Esta plantilla proporciona solo los elementos necesarios para implementar cualquier tipo de extensión e incluye el archivo *source. Extension. vsixmanifest* , las referencias de ensamblado necesarias y un archivo de proyecto que incluye las tareas de compilación que permiten implementar la extensión. Para obtener más información, consulte [Plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).

 También puede crear componentes de MEF de editor a partir de una extensión de paquete de Visual Studio. Vea los siguientes tutoriales para obtener más información:

- [Tutorial: usar un comando de Shell con una extensión de editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Tutorial: usar una tecla de método abreviado con una extensión de editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Vea también

- [Puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
