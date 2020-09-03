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
ms.openlocfilehash: 5238274d66296a21e15b47d1a090ab01c1a1299d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201974"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Tutorial: Publicación de una extensión de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Nota**: la galería de Visual Studio se está reemplazando por el Visual Studio Marketplace. Consulte la versión más reciente de este tema para obtener más información.

En este tutorial se muestra cómo publicar una extensión de Visual Studio en la galería de Visual Studio. Al agregar la extensión a la galería, los desarrolladores pueden usar **extensiones y actualizaciones** para buscar extensiones nuevas y actualizadas.

## <a name="prerequisites"></a>Prerrequisitos
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Crear una extensión de Visual Studio
 En este caso, usaremos una extensión VSPackage predeterminada, pero los mismos pasos son válidos para cada tipo de extensión.

1. Cree un VSPackage en C# denominado `TestPublishing` que tenga un comando de menú. Para obtener más información, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="test-the-extension"></a>Prueba de la extensión
 Antes de distribuir la extensión, compilarla y probarla para asegurarse de que se ha instalado correctamente en la instancia experimental de Visual Studio.

1. En Visual Studio, inicie la depuración. para abrir una instancia experimental de Visual Studio.

2. En la instancia experimental, vaya al menú **herramientas** y haga clic en **Administrador de extensiones**. La extensión TestPublishing debe aparecer en el panel central y estar habilitada.

3. En el menú **herramientas** , asegúrese de que ve el comando prueba.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Publicación de la extensión en la galería de Visual Studio
 Ahora puede publicar la extensión en la galería de Visual Studio.

1. Asegúrese de que ha creado la versión de lanzamiento de la extensión y de que está actualizada.

2. En un explorador Web, abra el sitio Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

3. En la esquina superior derecha, haga clic en **iniciar sesión**.

4. Para ello, use la cuenta de Microsoft. Si no tiene un cuenta de Microsoft, puede crear uno en este momento.

5. Haga clic en **Cargar**.

6. En **paso 1: tipo de extensión**, seleccione **herramienta** y, a continuación, haga clic en **siguiente**.

7. En **paso 2: cargar**, puede optar por cargar directamente en la galería de Visual Studio o simplemente agregar un vínculo a su propio sitio Web. En este caso, seleccione **me gustaría cargar mi herramienta**. Aparecerá el cuadro **Seleccione el control** . Haga clic en **examinar** y, a continuación, seleccione TestPublish. vsix en la carpeta \bin\Release del proyecto. Haga clic en **Next**.

8. En el **paso 3: información básica**, se muestran los campos del archivo source. Extension. vsixmanifest. Seleccione una **categoría** adecuada y agregue **etiquetas** para ayudar a los usuarios a encontrar la extensión. Puede que desee agregar un resumen y una descripción más detallados (la descripción debe tener al menos 280 caracteres). Deje **tipo de extensión** como **no es una extensión de Microsoft y una** categoría de **costo** como **evaluación**.

9. Lea el acuerdo de contribución en la parte inferior de la página y compruebe **que acepto**.

10. Haga clic en **crear contribución**. Se muestra la página que tendrá la extensión en la galería de Visual Studio, con un mensaje que indica que la página aún no se ha publicado.

11. Haga clic en **Publicar**.

12. Busque la extensión en la galería de Visual Studio. Debe aparecer la lista de la extensión TestPublish.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Instalación de la extensión desde la galería de Visual Studio
 Ahora que se ha publicado la extensión, instálela en Visual Studio y pruébelo en ella.

1. En Visual Studio, en el menú **herramientas** , haga clic en **extensiones y actualizaciones**.

2. Haga clic en **en línea** y busque TestPublish. Debe aparecer la lista de la extensión TestPublish.

3. Haga clic en **Descargar**. Después de descargar la extensión, haga clic en **Instalar**.

4. Para completar la instalación, reinicie Visual Studio.

## <a name="removing-the-extension"></a>Quitar la extensión
 Puede quitar la extensión de la galería de Visual Studio y del equipo.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Para quitar la extensión de la galería de Visual Studio

1. Abra el sitio web de [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

2. En la esquina superior derecha, haga clic en **mi extenions**. Se muestra la lista de TestPublish.

3. Haga clic en **Eliminar**.

#### <a name="to-remove-the-extension-from-your-computer"></a>Para quitar la extensión del equipo

1. En el menú **Herramientas** de Visual Studio, haga clic en **Administrador de extensiones**.

2. Seleccione TestPublish y, a continuación, haga clic en **desinstalar**.

3. Para completar la desinstalación, reinicie Visual Studio.
