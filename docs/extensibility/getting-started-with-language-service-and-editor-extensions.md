---
title: Introducción al servicio de lenguaje y a las extensiones de editor . Microsoft Docs
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
ms.openlocfilehash: 7894efc477e0c406cf8e85f4d3d31df4f2ef97c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711307"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Comience con el servicio de lenguaje y las extensiones del editor
Puede usar extensiones de editor para agregar características de servicio de lenguaje como esquematización, coincidencia de llaves, IntelliSense y bombillas a su propio lenguaje de programación o a cualquier tipo de contenido. También puede personalizar la apariencia y el comportamiento del editor de Visual Studio, por ejemplo, el color del texto, los márgenes, los adornos y otros elementos visuales. También puede definir su propio tipo de contenido y especificar la apariencia y el comportamiento de las vistas de texto en las que aparece el contenido.

 Para empezar a escribir extensiones de editor, use las plantillas de proyecto del editor que se instalan como parte del SDK de Visual Studio. El SDK de Visual Studio es un conjunto descargable de herramientas que facilitan el desarrollo de extensiones de Visual Studio, ya sea mediante VSPackages o mediante Managed Extensibility Framework (MEF).

> [!NOTE]
> Para obtener más información acerca del SDK de Visual Studio, vea SDK de [Visual Studio](../extensibility/visual-studio-sdk.md).

 Le recomendamos que obtenga información sobre los siguientes conceptos y tecnologías antes de escribir sus propias extensiones de editor.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) y las extensiones del editor
 La interfaz de usuario (UI) del editor de Visual Studio se implementa mediante Windows Presentation Foundation (WPF). WPFWPF proporciona una experiencia visual enriquecida y un modelo de programación coherente que separa los aspectos visuales del código de la lógica empresarial. Puede usar muchos elementos y características de WPFWPF al crear extensiones de editor. Para obtener más información, vea [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>El marco de extensibilidad administrada (MEF) y las extensiones del editor
 El editor de Visual Studio usa Managed Extensibility Framework (MEF) para administrar sus componentes y extensiones. El MEF también permite a los desarrolladores crear más fácilmente extensiones para una aplicación host como Visual Studio. En este marco, se define una extensión según un contrato MEF y se exporta como una parte de componente MEF. La aplicación host administra los componentes findingthem, registering them y asegurándose de que se aplican al contexto correcto.

> [!NOTE]
> Para obtener más información sobre el MEF en el editor, vea [Managed Extensibility Framework en el editor](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Puntos de extensión y extensiones del editor de Visual Studio
 Los puntos de extensión del editor son componentes MEF que puede personalizar y ampliar. En algunos casos, se amplía el punto de extensión implementando una interfaz y exportándola junto con los metadatos correctos. En otros casos, solo se declara una extensión y se exporta como un tipo determinado.

 Los siguientes son algunos de los tipos básicos de extensiones de editor:

- Márgenes y barras de desplazamiento

- Etiquetas

- Adornos

- Opciones

- IntelliSense

  Para obtener más información acerca de los puntos de extensión del editor, vea Servicio de lenguaje [y puntos](../extensibility/language-service-and-editor-extension-points.md)de extensión del editor .

## <a name="deploying-editor-extensions"></a>Implementación de extensiones de editor
 En Visual Studio, implementar extensiones de editor agregando un archivo de metadatos denominado *source.extension.vsixmanifest* a la solución, compilar la solución y, a continuación, agregar una copia de los archivos binarios y el manifiesto en una carpeta que es conocido por Visual Studio. El archivo de manifiesto define los hechos básicos sobre la extensión (por ejemplo, nombre, autor, versión y tipo de contenido). Para obtener más información sobre el archivo de manifiesto VSIX y cómo implementar extensiones, vea [Enviar extensiones](../extensibility/shipping-visual-studio-extensions.md)de Visual Studio .

 Al instalar una extensión en un equipo, incluya los archivos binarios y el manifiesto en una subcarpeta de carpeta que Visual Studio conoce.

> [!WARNING]
> No tiene que preocuparse por los detalles de los manifiestos y las ubicaciones de implementación si usa una de las plantillas de extensibilidad del editor que se incluyen en Visual Studio. Las plantillas contienen todo lo necesario para registrar e implementar una extensión.

## <a name="run-extensions-in-the-experimental-instance"></a>Ejecutar extensiones en la instancia experimental
 Puede aislar la versión de trabajo de Visual Studio mientras desarrolla una extensión implementándola en la siguiente carpeta experimental (en Windows Vista y Windows 7):

 *•%LOCALAPPDATA%-VisualStudio-10.0Exp-Extensiones-Empresa-ExtensionID--ExtensionID---ExtensionID-------------------------------------------------------------------------------------------------------------\\\\*

 donde *%LOCALAPPDATA%* es el nombre del usuario que ha iniciado sesión, *Company* es el nombre de la empresa propietaria de la extensión y *ExtensionID* es el identificador de la extensión.

 Al implementar una extensión en la ubicación experimental, se ejecuta en modo de depuración. Se inicia una segunda instancia de Visual Studio y se denomina **Microsoft Visual Studio - Experimental Instance**.

## <a name="manage-extensions"></a>Administración de extensiones
 Las extensiones de Visual Studio se enumeran en **Extensiones y actualizaciones** (en el menú **Herramientas).** Si está probando una extensión en la instancia experimental, aparece en **Extensiones y actualizaciones** en la instancia experimental, pero no aparece en la instancia de desarrollo.

 Para obtener más información, vea [Buscar y usar extensiones](../ide/finding-and-using-visual-studio-extensions.md)de Visual Studio .

## <a name="use-templates-to-create-editor-extensions"></a>Usar plantillas para crear extensiones de editor
 Puede usar plantillas de editor para crear extensiones MEF que personalicen clasificadores, adornos y márgenes. Hay plantillas para proyectos de Visual Basic y de C. Para obtener más información, consulte Crear una extensión con una plantilla de elemento de [editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

 También puede usar la plantilla De proyecto VSIX para crear extensiones. Esta plantilla proporciona solo los elementos necesarios para implementar cualquier tipo de extensión e incluir el archivo *source.extension.vsixmanifest,* las referencias de ensamblado necesarias y un archivo de proyecto que incluya las tareas de compilación que permiten implementar la extensión. Para obtener más información, consulte Plantilla de [proyecto VSIX](../extensibility/vsix-project-template.md).

 También puede crear componentes MEF de editor a partir de una extensión de paquete de Visual Studio. Consulte los siguientes tutoriales para obtener más información:

- [Tutorial: Uso de un comando shell con una extensión de editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Tutorial: Uso de una tecla de método abreviado con una extensión de editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Vea también
- [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)
