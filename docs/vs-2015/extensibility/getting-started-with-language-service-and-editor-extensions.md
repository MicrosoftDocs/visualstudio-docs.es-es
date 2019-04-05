---
title: Introducción al servicio de lenguaje y las extensiones de Editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e247192b19e8ae2e2037281f4f89631d2ea78605
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998705"
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Introducción al servicio de lenguaje y las extensiones de editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar las extensiones de editor para agregar características del servicio de lenguaje como la esquematización, coincidencia de llaves, IntelliSense y bombillas a su propio lenguaje de programación o a cualquier tipo de contenido. También puede personalizar la apariencia y comportamiento del editor de Visual Studio, por ejemplo el color, los márgenes, los elementos gráficos y otros elementos visuales de texto. También puede definir su propio tipo de contenido y especificar la apariencia y comportamiento de las vistas de texto en el que aparece su contenido.  
  
 Para empezar a escribir las extensiones de editor, use las plantillas de proyecto del editor que se instalan como parte del SDK de Visual Studio. El SDK de Visual Studio es un conjunto de herramientas que facilitan el desarrollo de extensiones de Visual Studio mediante paquetes VSPackage o mediante el uso de Managed Extensibility Framework (MEF) descargable.  
  
> [!NOTE]
>  Para obtener más información sobre el SDK de Visual Studio, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
 Se recomienda que conozca los siguientes conceptos y tecnologías antes de escribir sus propias extensiones de editor.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>The Windows Presentation Foundation (WPF) y extensiones de Editor  
 La interfaz de usuario del editor de Visual Studio (UI) se implementa mediante el uso de Windows Presentation Foundation (WPF). WPF proporciona una experiencia visual enriquecida y un modelo de programación coherente que separa los aspectos visuales del código de la lógica de negocios. Puede usar muchos elementos de WPF y características al crear extensiones de editor. Para obtener más información, consulte [Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) y extensiones de Editor  
 El editor de Visual Studio usa Managed Extensibility Framework (MEF) para administrar sus componentes y extensiones. MEF también permite a los desarrolladores más fácil crear extensiones para una aplicación host como Visual Studio. En este marco de trabajo, definir una extensión según un contrato MEF y exportarlo como un componente MEF. La aplicación host administra las partes componentes encontrarlos, registrarlos y asegurándose de que se apliquen en el contexto correcto.  
  
> [!NOTE]
>  Para obtener más información acerca de MEF en el editor, vea [Managed Extensibility Framework en el Editor de](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Puntos de extensión del Editor de Visual Studio y extensiones  
 Puntos de extensión del Editor son componentes de MEF que puede personalizar y ampliar. En algunos casos extender el punto de extensión implementando una interfaz y exportarlo junto con los metadatos correctos. En otros casos simplemente declare una extensión y exportarlo como un tipo determinado.  
  
 Los siguientes son algunos de los tipos básicos de las extensiones de editor:  
  
- Márgenes y barras de desplazamiento  
  
- Etiquetas  
  
- Elementos gráficos  
  
- Opciones  
  
- IntelliSense  
  
  Para obtener más información acerca de los puntos de extensión del editor, vea [servicio de lenguaje y puntos de extensión del Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Implementación de extensiones de Editor  
 En Visual Studio, implementa extensiones de editor agregando un archivo de metadatos denominado source.extension.vsixmanifest a la solución, compilar la solución, y, a continuación, agregar una copia de los archivos binarios y el manifiesto en una carpeta que se conoce a Visual Studio. El archivo de manifiesto define los aspectos básicos sobre la extensión (por ejemplo, nombre, autor, versión y tipo de contenido). Para obtener más información sobre el archivo de manifiesto de VSIX y cómo implementar extensiones, consulte [envío extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Cuando se instala una extensión en un equipo, incluyen los archivos binarios y el manifiesto en una subcarpeta de la carpeta que se conoce a Visual Studio.  
  
> [!WARNING]
>  No tiene que preocuparse por los detalles de los manifiestos y las ubicaciones de implementación si utiliza una de las plantillas de extensibilidad de editor que se incluyen en Visual Studio. Las plantillas contienen todo lo necesario para registrar e implementar una extensión.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Ejecución de extensiones en la instancia Experimental  
 Puede aislar su versión de Visual Studio mientras desarrolla una extensión mediante la implementación en la siguiente carpeta experimental (en Windows Vista y Windows 7):  
  
 *%LOCALAPPDATA%* \VisualStudio\10.0Exp\Extensions\\*Company*\\*ExtensionID*  
  
 donde *% LOCALAPPDATA %* es el nombre del usuario ha iniciado sesión, *empresa* es el nombre de la empresa que posee la extensión, y *ExtensionID* es el identificador de la extensión.  
  
 Al implementar una extensión a la ubicación experimental, se ejecuta en modo de depuración. Una segunda instancia de Visual Studio se inicia y se denomina **Microsoft Visual Studio – instancia Experimental**.  
  
## <a name="managing-extensions"></a>Administración de extensiones  
 Se enumeran las extensiones de Visual Studio en **extensiones y actualizaciones** (en el **herramientas** menú). Si va a probar una extensión en la instancia experimental, aparece en **extensiones y actualizaciones** en la instancia experimental, pero no aparece en la instancia de desarrollo.  
  
 Para más información, vea [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Usar plantillas para crear extensiones de Editor  
 Puede usar plantillas de editor para crear extensiones MEF que personalizan clasificadores, los elementos gráficos y los márgenes. Hay plantillas para proyectos de C# y Visual Basic. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 También puede usar la plantilla de proyecto de VSIX para crear extensiones. Esta plantilla proporciona solo los elementos necesarios para implementar cualquier tipo de extensión e incluir el archivo source.extension.vsixmanifest, las referencias de ensamblado necesarias y un archivo de proyecto que incluye las tareas de compilación que le permiten implementar la extensión. Para obtener más información, consulte [plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).  
  
 También puede crear editor de componentes de MEF de una extensión de paquete de Visual Studio. Vea los siguientes tutoriales para obtener más información:  
  
-   [Tutorial: Uso de un comando de Shell con una extensión del Editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Tutorial: Uso de una tecla de método abreviado con una extensión del Editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Vea también  
 [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)
