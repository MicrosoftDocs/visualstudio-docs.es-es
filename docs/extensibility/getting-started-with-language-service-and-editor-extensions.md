---
title: Introducción al servicio de lenguaje y las extensiones de Editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 54b4d1b3b1dca44acc092cb3a9a639c196ce8e50
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010069"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Introducción a las extensiones de editor y el servicio de lenguaje
Puede usar las extensiones de editor para agregar características del servicio de lenguaje como la esquematización, coincidencia de llaves, IntelliSense y bombillas a su propio lenguaje de programación o a cualquier tipo de contenido. También puede personalizar la apariencia y comportamiento del editor de Visual Studio, por ejemplo el color, los márgenes, los elementos gráficos y otros elementos visuales de texto. También puede definir su propio tipo de contenido y especificar la apariencia y comportamiento de las vistas de texto en el que aparece su contenido.  
  
 Para empezar a escribir las extensiones de editor, use las plantillas de proyecto del editor que se instalan como parte del SDK de Visual Studio. El SDK de Visual Studio es un conjunto de herramientas que facilitan el desarrollo de extensiones de Visual Studio mediante paquetes VSPackage o mediante el uso de Managed Extensibility Framework (MEF) descargable.  
  
> [!NOTE]
>  Para obtener más información sobre el SDK de Visual Studio, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
 Se recomienda que conozca los siguientes conceptos y tecnologías antes de escribir sus propias extensiones de editor.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Las extensiones de editor y Windows Presentation Foundation (WPF)  
 La interfaz de usuario del editor de Visual Studio (UI) se implementa mediante el uso de Windows Presentation Foundation (WPF). WPF proporciona una experiencia visual enriquecida y un modelo de programación coherente que separa los aspectos visuales del código de la lógica de negocios. Puede usar muchos elementos de WPF y características al crear extensiones de editor. Para obtener más información, consulte [Windows Presentation Foundation](/dotnet/framework/wpf/index).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Las extensiones de editor y Managed Extensibility Framework (MEF)  
 El editor de Visual Studio usa Managed Extensibility Framework (MEF) para administrar sus componentes y extensiones. MEF también permite a los desarrolladores más fácil crear extensiones para una aplicación host como Visual Studio. En este marco de trabajo, definir una extensión según un contrato MEF y exportarlo como un componente MEF. La aplicación host administra las partes componentes encontrarlos, registrarlos y asegurándose de que se apliquen en el contexto correcto.  
  
> [!NOTE]
>  Para obtener más información acerca de MEF en el editor, vea [Managed Extensibility Framework en el editor de](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Extensiones y puntos de extensión de editor de visual Studio  
 Puntos de extensión del Editor son componentes de MEF que puede personalizar y ampliar. En algunos casos extender el punto de extensión implementando una interfaz y exportarlo junto con los metadatos correctos. En otros casos simplemente declare una extensión y exportarlo como un tipo determinado.  
  
 Los siguientes son algunos de los tipos básicos de las extensiones de editor:  
  
- Márgenes y barras de desplazamiento  
  
- Etiquetas  
  
- Elementos gráficos  
  
- Opciones  
  
- IntelliSense  
  
  Para obtener más información acerca de los puntos de extensión del editor, vea [puntos de extensión de editor y el servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Implementación de extensiones de editor  
 En Visual Studio, implementar extensiones de editor mediante la adición de un archivo de metadatos denominado *source.extension.vsixmanifest* a la solución, compilar la solución y, a continuación, agregar una copia de los archivos binarios y el manifiesto en una carpeta que se conoce Visual Studio. El archivo de manifiesto define los aspectos básicos sobre la extensión (por ejemplo, nombre, autor, versión y tipo de contenido). Para obtener más información sobre el archivo de manifiesto de VSIX y cómo implementar extensiones, consulte [extensiones de Visual Studio de envío](../extensibility/shipping-visual-studio-extensions.md).  
  
 Cuando se instala una extensión en un equipo, incluyen los archivos binarios y el manifiesto en una subcarpeta de la carpeta que se conoce a Visual Studio.  
  
> [!WARNING]
>  No tiene que preocuparse por los detalles de los manifiestos y las ubicaciones de implementación si utiliza una de las plantillas de extensibilidad de editor que se incluyen en Visual Studio. Las plantillas contienen todo lo necesario para registrar e implementar una extensión.  
  
## <a name="run-extensions-in-the-experimental-instance"></a>Ejecutar las extensiones en la instancia experimental  
 Puede aislar su versión de Visual Studio mientras desarrolla una extensión mediante la implementación en la siguiente carpeta experimental (en Windows Vista y Windows 7):  
  
 *{%LOCALAPPDATA%}\VisualStudio\10.0Exp\Extensions\\{Company}\\{ExtensionID}*  
  
 donde *% LOCALAPPDATA %* es el nombre del usuario ha iniciado sesión, *empresa* es el nombre de la empresa que posee la extensión, y *ExtensionID* es el identificador de la extensión.  
  
 Al implementar una extensión a la ubicación experimental, se ejecuta en modo de depuración. Una segunda instancia de Visual Studio se inicia y se denomina **Microsoft Visual Studio – instancia Experimental**.  
  
## <a name="manage-extensions"></a>Administrar extensiones  
 Se enumeran las extensiones de Visual Studio en **extensiones y actualizaciones** (en el **herramientas** menú). Si va a probar una extensión en la instancia experimental, aparece en **extensiones y actualizaciones** en la instancia experimental, pero no aparece en la instancia de desarrollo.  
  
 Para obtener más información, consulte [encontrar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="use-templates-to-create-editor-extensions"></a>Usar plantillas para crear extensiones de editor  
 Puede usar plantillas de editor para crear extensiones MEF que personalizan clasificadores, los elementos gráficos y los márgenes. Hay plantillas para proyectos de C# y Visual Basic. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 También puede usar la plantilla de proyecto de VSIX para crear extensiones. Esta plantilla proporciona solo los elementos necesarios para implementar cualquier tipo de extensión e incluyen el *source.extension.vsixmanifest* archivo, las referencias de ensamblado necesarias y un archivo de proyecto que incluye las tareas de compilación que le permiten implementar la extensión. Para obtener más información, consulte [plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).  
  
 También puede crear editor de componentes de MEF de una extensión de paquete de Visual Studio. Vea los siguientes tutoriales para obtener más información:  
  
-   [Tutorial: Uso de un comando de shell con una extensión del editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Tutorial: Uso de una tecla de método abreviado con una extensión del editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Vea también  
 [Puntos de extensión de editor y el servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)