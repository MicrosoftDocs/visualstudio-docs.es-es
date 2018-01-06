---
title: "Introducción al servicio de lenguaje y las extensiones de Editor | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5f7b7440ff2f42eba1d138872071d4e51d2402c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Introducción al servicio de lenguaje y las extensiones de Editor
Puede utilizar extensiones de editor para agregar características del servicio de lenguaje como la esquematización, coincidencia de llaves, IntelliSense y las bombillas a su propio lenguaje de programación o a cualquier tipo de contenido. También puede personalizar la apariencia y el comportamiento del editor de Visual Studio, por ejemplo texto colorear, márgenes, elementos gráficos y otros elementos visuales. También puede definir su propio tipo de contenido y especificar la apariencia y el comportamiento de las vistas de texto en el que aparece el contenido.  
  
 Para empezar a escribir las extensiones de editor, use las plantillas de proyecto de editor que se instalan como parte del SDK de Visual Studio. El SDK de Visual Studio es un conjunto de herramientas que resulten más fáciles de desarrollar extensiones de Visual Studio, ya sea mediante el uso de VSPackages o mediante Managed Extensibility Framework (MEF) que se pueden descargar.  
  
> [!NOTE]
>  Para obtener más información sobre el SDK de Visual Studio, vea [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
 Es recomendable conocer los siguientes conceptos y tecnologías antes de escribir sus propias extensiones de editor.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) y extensiones de Editor  
 La interfaz de usuario del editor de Visual Studio (UI) se implementa mediante el uso de Windows Presentation Foundation (WPF). WPF proporciona una experiencia visual enriquecida y un modelo de programación coherente que separa los aspectos visuales del código de la lógica de negocios. Puede usar muchos elementos WPF y las características al crear extensiones de editor. Para obtener más información, consulte [Windows Presentation Foundation](/dotnet/framework/wpf/index).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) y extensiones de Editor  
 El editor de Visual Studio usa Managed Extensibility Framework (MEF) para administrar sus componentes y extensiones. MEF también permite a los desarrolladores más fácil crear extensiones para una aplicación host como Visual Studio. En este marco de trabajo, definir una extensión de acuerdo con un contrato MEF y exportarlo como un componente MEF. La aplicación host administra los componentes buscándolas, registrarlos y asegurándose de que se apliquen en el contexto correcto.  
  
> [!NOTE]
>  Para obtener más información sobre la MEF en el editor, consulte [Managed Extensibility Framework en el Editor de](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Puntos de extensión del Editor de Visual Studio y extensiones  
 Puntos de extensión del Editor son componentes de MEF que puede personalizar y extender. En algunos casos se amplía el punto de extensión mediante la implementación de una interfaz y exportarlo junto con los metadatos correctos. En otros casos simplemente declare una extensión y exportarlo como un tipo determinado.  
  
 Éstos son algunos de los tipos básicos de extensiones de editor:  
  
-   Los márgenes y las barras de desplazamiento  
  
-   Etiquetas  
  
-   Opciones gráficas  
  
-   Opciones  
  
-   IntelliSense  
  
 Para obtener más información acerca de los puntos de extensión del editor, vea [servicio de lenguaje y puntos de extensión del Editor de](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Implementar extensiones de Editor  
 En Visual Studio, que se implementen extensiones de editor agregando un archivo de metadatos denominado source.extension.vsixmanifest a la solución, compilar la solución y, a continuación, agregar una copia de los archivos binarios y el manifiesto en una carpeta que se conoce a Visual Studio. El archivo de manifiesto define los hechos básicos acerca de la extensión (por ejemplo, nombre, autor, versión y tipo de contenido). Para obtener más información sobre el archivo de manifiesto de VSIX y cómo implementar extensiones, consulte [trasvase extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Al instalar una extensión en un equipo, incluyen los archivos binarios y el manifiesto en una subcarpeta de la carpeta que se conoce a Visual Studio.  
  
> [!WARNING]
>  No tiene que preocuparse sobre los detalles de los manifiestos y ubicaciones de implementación si utiliza una de las plantillas de extensibilidad de editor que se incluyen en Visual Studio. Las plantillas contienen toda la información necesaria para registrar e implementar una extensión.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Ejecuta las extensiones en la instancia Experimental  
 Puede aislar su versión de trabajo de Visual Studio mientras desarrolla una extensión mediante la implementación en la siguiente carpeta experimental (en Windows Vista y Windows 7):  
  
 *% LOCALAPPDATA %*\VisualStudio\10.0Exp\Extensions\\*empresa*\\*ExtensionID*  
  
 donde *% LOCALAPPDATA %* es el nombre del usuario ha iniciado sesión, *empresa* es el nombre de la compañía que posee la extensión y *ExtensionID* es el identificador de la extensión.  
  
 Al implementar una extensión en la ubicación experimental, se ejecuta en modo de depuración. Una segunda instancia de Visual Studio se inicia y se denomina **Microsoft Visual Studio: instancia Experimental**.  
  
## <a name="managing-extensions"></a>Administrar extensiones  
 Las extensiones de Visual Studio se enumeran en **extensiones y actualizaciones** (en el **herramientas** menú). Si va a probar una extensión en la instancia experimental, se incluye en **extensiones y actualizaciones** en la instancia experimental, pero no aparece en la instancia de desarrollo.  
  
 Para más información, vea [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Usar plantillas para crear extensiones de Editor  
 Puede utilizar plantillas de editor para crear extensiones MEF que personalicen clasificadores, opciones gráficas y los márgenes. Hay plantillas para proyectos de C# y Visual Basic. Para obtener más información, consulte [crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 También puede usar la plantilla de proyecto de VSIX para crear extensiones. Esta plantilla proporciona solo los elementos necesarios para implementar cualquier tipo de extensión e incluyen el archivo source.extension.vsixmanifest, las referencias de ensamblado necesarias y un archivo de proyecto que incluye las tareas de compilación que le permiten implementar la extensión. Para obtener más información, consulte [plantilla de proyecto de VSIX](../extensibility/vsix-project-template.md).  
  
 También puede crear editor componentes MEF desde una extensión de paquete de Visual Studio. Vea los siguientes tutoriales para obtener más información:  
  
-   [Tutorial: uso de un comando de shell con una extensión del editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Tutorial: uso de una tecla de método abreviado con una extensión del editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Vea también  
 [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)