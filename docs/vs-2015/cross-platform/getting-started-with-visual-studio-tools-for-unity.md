---
title: Introducción a Visual Studio Tools para Unity | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
caps.latest.revision: 12
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: 9ed6cb4127ba57c6b9b84a32996968dbf9fac4fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762724"
---
# <a name="getting-started-with-visual-studio-tools-for-unity"></a>Introducción a Visual Studio Tools para Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
En esta sección, aprenderá a instalar Visual Studio Tools para Unity y a configurar el proyecto de Unity para trabajar con Visual Studio.  
  
> [!IMPORTANT]
>  Unity 5.2 agrega compatibilidad integrada con Visual Studio Tools para Unity 2.1, lo que simplifica la configuración del proyecto. Para aprovechar estas características, necesitará la versión 5.2.0 de Unity o superior en Windows y Visual Studio Tools para Unity, versión 2.1 o posterior.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para usar Visual Studio Tools necesitará lo siguiente:  
  
-   Una versión de **Visual Studio** que admita extensiones como, por ejemplo, Visual Studio Community, Professional, Premium o Enterprise. Puede descargar Visual Studio Community de manera gratuita.  
  
     [Descargar la Comunidad de Visual Studio](http://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   Necesitará la versión 4.0.0 de**Unity** o superior, así como la versión 5.2.0 de **Unity** o superior Para aprovechar las ventajas de las características de compatibilidad integrada de Visual Studio Tools para Unity versión 21 o posterior.  
  
     [Descargar Unity](https://unity3d.com/get-unity/download)  
  
## <a name="install-visual-studio-tools-for-unity"></a>Instalar Visual Studio Tools para Unity  
 Descargue e instale Visual Studio Tools para Unity desde la Galería de Visual Studio. Deberá instalar el paquete adecuado para su versión de Visual Studio. Asegúrese de instalar Visual Studio Tools para Unity, versión 2.1 o posterior, para aprovechar las ventajas de las características de compatibilidad integrada para VSTU en Unity 5.2 o posterior.  
  
-   Para Visual Studio 2015 Community, Visual Studio 2015 Professional o Visual Studio 2015 Enterprise:  
  
     [Descargar Visual Studio 2015 Tools para Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)  
  
-   Para Visual Studio Community 2013, Visual Studio Professional 2013 o Visual Studio Premium 2013:  
  
     [Descargar Visual Studio 2013 Tools para Unity](https://visualstudiogallery.msdn.microsoft.com/20b80b8c-659b-45ef-96c1-437828fe7cf2)  
  
-   Para Visual Studio Professional 2012 Visual Studio Premium 2012:  
  
     [Descargar Visual Studio 2012 Tools para Unity](https://visualstudiogallery.msdn.microsoft.com/7ab11d2a-f413-4ed6-b3de-ff1d05157714)  
  
-   Para Visual Studio Professional 2010 Visual Studio Premium 2010:  
  
     [Descargar Visual Studio 2010 Tools para Unity](https://visualstudiogallery.msdn.microsoft.com/6e536faa-ce73-494a-a746-6a14753015f1)  
  
> [!NOTE]
>  Las versiones Express de Visual Studio no admiten extensiones como Visual Studio Tools para Unity. Visual Studio Community es una versión gratuita de Visual Studio que admite Visual Studio Tools para Unity y otras extensiones. Para la mayoría de los usuarios, Visual Studio Community es una mejor opción que la versión Express.  
  
## <a name="your-first-unity-project-with-visual-studio-tools-for-unity"></a>Su primer proyecto de Unity con Visual Studio Tools para Unity  
 Ahora que tiene todo lo necesario, está preparado para crear su primer proyecto Unity con Visual Studio. La configuración del proyecto de Unity varía dependiendo de las versiones de Unity y Visual Studio Tools para Unity que estén instaladas. Siga los pasos que se describen a continuación para saber cuál es la versión de Visual Studio Tools para Unity que tiene instalada.  
  
### <a name="unity-52-and-higher-requires-vstu-21-or-higher"></a>Unity 5.2 y versiones posteriores (requiere VSTU 2.1 o posterior)  
 A partir de Unity 5.2, ya no necesitará el el unitypackage de Visual Studio Tools en los proyectos. Si el proyecto importa este unitypackage, Unity 5.2 lo omitirá y Visual Studio Tools para Unity se cargará directamente desde su ubicación de instalación.  
  
#### <a name="1---create-a-unity-project"></a>1. Crear un proyecto Unity  
 Si ya tiene experiencia con Unity, puede crear un nuevo proyecto o cargar uno propio. Si se carga un proyecto que importó el unitypackage de Visual Studio Tools para usar Visual Studio Tools para Unity con una versión anterior de Unity, se recomienda quitarlo mediante la eliminación del directorio UnityVS.  
  
 De lo contrario, si no está familiarizado con Unity, empiece poco a poco con un tutorial básico. Visite la página Unity Learn, donde podrá acceder a tutoriales con ejemplos de proyectos para empezar y lecciones para aprender a crear su propio juego con Unity. La página Unity Learn tiene tutoriales fáciles de seguir para diversos juegos.  
  
 [Tutoriales: Página de aprendizaje de Unity](http://unity3d.com/learn/tutorials/modules)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2. Configure el Editor de Unity para que utilice Visual Studio Tools para Unity  
 Para habilitar el proyecto para usar Visual Studio Tools para Unity, simplemente establezca Visual Studio como su editor de script externo. En el Editor de Unity, en el menú principal, elija **Editar, Preferencias**; a continuación, en el cuadro de diálogo **Preferencias de Unity** , elija **Herramientas externas**. A continuación, establezca la propiedad **External Script Editor** a la versión de Visual Studio que desea usar (Visual Studio Tools para Unity debe estar instalado para esta versión de Visual Studio) y asegúrese de que la propiedad **Editor Attaching** está establecida.  
  
 Para asegurarse de que la compatibilidad integrada de Visual Studio Tools para Unity está ahora habilitada, vea el cuadro de diálogo **Acerca de Unity** . In the Unity editor, on the main menu, choose **Ayuda, Acerca de Unity.** Si Visual Studio Tools para Unity está instalado y configurado correctamente, se mostrará un mensaje en la esquina inferior izquierda del cuadro de diálogo **Acerca de Unity** .  
  
 Por último, asegúrese de que ha establecido un destino de compilación a través de la página **Configuración de generación** y de que la opción **Depuración de scripts** esté habilitada.  
  
 ![Establezca la configuración de compilación de Unity para la depuración.](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-the-unity-editor"></a>3. Inicie Visual Studio desde el Editor de Unity  
 A partir de Unity 5.2, el menú de extensión **Visual Studio Tools** ya no es necesario para iniciar Visual Studio o para configurar Visual Studio Tools para Unity. En su lugar, una vez que Visual Studio está configurado como editor de script externo, elija el archivo de script desde el editor de Unity y el código se abrirá en Visual Studio.  
  
### <a name="previous-versions-of-unity-pre-52"></a>Versiones anteriores de Unity (anteriores a la versión 5.2)  
 Antes de Unity 5.2, no había compatibilidad integrada para Visual Studio Tools para Unity. En su lugar, cada proyecto tenía que importar el unitypackage de Visual Studio Tools y configurar otras opciones de proyecto para poder usar Visual Studio Tools para Unity.  
  
#### <a name="1---create-a-unity-project"></a>1. Crear un proyecto Unity  
 Si ya tiene experiencia con Unity, puede crear un nuevo proyecto o cargar uno propio. Si comienza un nuevo proyecto, importe el unitypackage de Visual Studio Tools al crearlo.  
  
 De lo contrario, si no está familiarizado con Unity, empiece poco a poco con un tutorial básico. Visite la página Unity Learn, donde podrá acceder a tutoriales con ejemplos de proyectos para empezar y lecciones para aprender a crear su propio juego con Unity. La página Unity Learn tiene tutoriales fáciles de seguir para diversos juegos.  
  
 [Tutoriales: Página de aprendizaje de Unity](http://unity3d.com/learn/tutorials/modules)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2. Configure el Editor de Unity para que utilice Visual Studio Tools para Unity  
 Si se va a basar en un proyecto de Unity existente o si no importó unitypackage de Visual Studio Tools cuando creó el proyecto, deberá importar unitypackage ahora. En el menú principal del Editor de Unity elija **Activos, Importar paquete, Visual Studio Tools 2015** (debería ver una opción para la versión de Visual Studio que haya instalado).  
  
 ![Importar el paquete VSTU en el proyecto de Unity.](../cross-platform/media/vstu-configure-unity-import-vstu.png "vstu_configure_unity_import_vstu")  
  
 Por último, asegúrese de que ha establecido un destino de compilación a través de la página **Configuración de generación** y de que la opción **Depuración de scripts** esté habilitada.  
  
 ![Establezca la configuración de compilación de Unity para la depuración.](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-unity-editor"></a>3. Inicie Visual Studio desde el Editor de Unity  
 El último paso consiste en iniciar Visual Studio desde Unity. Esto crea una solución de Visual Studio para el proyecto y, a continuación, la abre en Visual Studio.  
  
 En el menú principal del Editor de Unity, elija **Visual Studio Tools, Abrir en Visual Studio**.  
  
 ![Abra el proyecto de Unity en Visual Studio.](../cross-platform/media/vstu-configure-open-in-visual-studio.png "vstu_configure_open_in_visual_studio")  
  
## <a name="next-steps"></a>Pasos siguientes  
 Para obtener información sobre el uso y la depuración de su proyecto Unity en Visual Studio, vea [Uso de Visual Studio Tools para Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md).  
  
## <a name="see-also"></a>Vea también  
 [Página principal de Unity](http://unity3d.com)

