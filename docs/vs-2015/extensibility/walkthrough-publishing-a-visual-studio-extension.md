---
title: Publicar una extensión | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0d32428c7a7b1f481771aacaf3e2b0dadfde5db6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002428"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Tutorial: Publicar una extensión de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Nota**: La Galería de Visual Studio se está reemplazando por Visual Studio Marketplace. Consulte la versión más reciente de este tema para obtener más información.


En este tutorial se muestra cómo publicar una extensión de Visual Studio en la Galería de Visual Studio. Cuando se agrega la extensión a la galería, los desarrolladores pueden usar **extensiones y actualizaciones** para buscar allí extensiones nuevas y actualizadas.

## <a name="prerequisites"></a>Requisitos previos
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Crear una extensión de Visual Studio
 En este caso usaremos una extensión predeterminada de VSPackage, pero los mismos pasos son válidos para cada tipo de extensión.

1.  Crear un VSPackage en C# llamado `TestPublishing` que tiene un comando de menú. Para obtener más información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="test-the-extension"></a>Probar la extensión
 Antes de distribuir la extensión, compilar y probar para asegurarse de que está instalado correctamente en la instancia experimental de Visual Studio.

1.  En Visual Studio, inicie la depuración. Para abrir una instancia experimental de Visual Studio.

2.  En la instancia experimental, vaya a la **herramientas** menú y haga clic en **Administrador de extensiones**. La extensión TestPublishing debe aparecer en el panel central y habilitarse.

3.  En el **herramientas** menú, asegúrese de que ve el comando de prueba.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Publicar la extensión en la Galería de Visual Studio
 Ahora puede publicar la extensión en la Galería de Visual Studio.

1.  Asegúrese de que ha creado la versión de lanzamiento de la extensión y que está actualizada.

2.  En un explorador web, abra el [Visual Studio Marketplace](https://marketplace.visualstudio.com/) sitio Web.

3.  En la esquina superior derecha, haga clic en **sesión**.

4.  Para ello, use la cuenta de Microsoft. Si no tiene una cuenta de Microsoft, puede crear uno en este momento.

5.  Haga clic en **Cargar**.

6.  En **paso 1: Tipo de extensión**, seleccione **herramienta** y, a continuación, haga clic en **siguiente**.

7.  En **paso 2: Cargar**, puede elegir cargar directamente a la Galería de Visual Studio o agregar un vínculo a su propio sitio Web. En este caso seleccione **gustaría cargar mi herramienta**. El **seleccione el control** aparece el cuadro. Haga clic en **examinar** y, a continuación, seleccione TestPublish.vsix en la carpeta \bin\Release del proyecto. Haga clic en **Siguiente**.

8.  En **paso 3: Información básica**, se muestran los campos del archivo source.extension.vsixmanifest. Seleccione un **categoría** y agregue **etiquetas** para ayudar a los usuarios encontrar la extensión. Es posible que desea agregar un resumen y (la descripción debe ser al menos de 280 caracteres de longitud) una descripción más detallada. Deje **tipo de extensión** como **no es una extensión de Microsoft** y **categoría de costo** como **prueba**.

9. Lea el acuerdo de contribución en la parte inferior de la página y comprobar **acepto**.

10. Haga clic en **crear contribución**. Esto muestra la página que tendrá la extensión en la Galería de Visual Studio, con un mensaje que la página aún no se ha publicado.

11. Haga clic en **Publicar**.

12. Buscar en la Galería de Visual Studio para la extensión. Debería aparecer la lista para la extensión TestPublish.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Instale la extensión desde la Galería de Visual Studio
 Ahora que se ha publicado la extensión, instalarlo en Visual Studio y pruébela.

1.  En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones**.

2.  Haga clic en **Online** y, a continuación, busque TestPublish. Debería aparecer la lista para la extensión TestPublish.

3.  Haga clic en **Descargar**. Después de descargar la extensión, haga clic en **Instalar**.

4.  Para completar la instalación, reinicie Visual Studio.

## <a name="removing-the-extension"></a>Quitar la extensión
 Puede quitar la extensión desde la Galería de Visual Studio y desde el equipo.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Para quitar la extensión de la Galería de Visual Studio

1.  Abra el [Visual Studio Marketplace](https://marketplace.visualstudio.com/) sitio Web.

2.  En la esquina superior derecha, haga clic en **darán mi**. Se muestra la lista de TestPublish.

3.  Haga clic en **Eliminar**.

#### <a name="to-remove-the-extension-from-your-computer"></a>Para quitar la extensión de su equipo

1.  En el menú **Herramientas** de Visual Studio, haga clic en **Administrador de extensiones**.

2.  Seleccione TestPublish y, a continuación, haga clic en **desinstalar**.

3.  Para completar la desinstalación, reinicie Visual Studio.
