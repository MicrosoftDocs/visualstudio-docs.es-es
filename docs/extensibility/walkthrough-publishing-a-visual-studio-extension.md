---
title: "Tutorial: Publicar una extensión de Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 574af4ff2b3858201c13121475de02a763572f6b
ms.openlocfilehash: fcfb0724b89d60553d6686a0705ab1e9459014ce
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Tutorial: Publicar una extensión de Visual Studio
Este tutorial muestra cómo publicar una extensión de Visual Studio en la Galería de Visual Studio. Cuando se agrega la extensión a la galería, los desarrolladores pueden usar **extensiones y actualizaciones** para buscar extensiones nuevas y actualizadas.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el Visual Studio SDK. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="create-a-visual-studio-extension"></a>Crear una extensión de Visual Studio  
 En este caso usaremos una extensión de VSPackage predeterminada, pero los mismos pasos son válidos para cada tipo de extensión.  
  
1.  Crear un VSPackage en C# llamado `TestPublishing` que tiene un comando de menú. Para obtener más información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="test-the-extension"></a>Probar la extensión  
 Antes de distribuir la extensión, compilar y probar para asegurarse de que está instalado correctamente en la instancia experimental de Visual Studio.  
  
1.  En Visual Studio, inicie la depuración. Para abrir una instancia experimental de Visual Studio.  
  
2.  En la instancia experimental, vaya a la **herramientas** menú y haga clic en **Administrador de extensiones**. La extensión TestPublishing debería aparecer en el panel central y habilitarse.  
  
3.  En el **herramientas** menú, asegúrese de que ve el comando de prueba.  
  
## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Publicar la extensión en la Galería de Visual Studio  
 Ahora puede publicar la extensión en la Galería de Visual Studio.  
  
1.  Asegúrese de que ha creado la versión de la extensión y que esté actualizado.  
  
2.  En el explorador web, abra el sitio web de la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) .  
  
3.  En la esquina superior derecha, haga clic en **SIGN IN**.  
  
4.  Para ello, use la cuenta de Microsoft. Si no tiene una cuenta de Microsoft, puede crear uno en este momento.  
  
5.  Haga clic en **Cargar**.  
  
6.  En **paso 1: tipo de extensión**, seleccione **herramienta** y, a continuación, haga clic en **siguiente**.  
  
7.  En **paso 2: cargar**, puede cargar directamente en la Galería de Visual Studio o agregar un vínculo a su propio sitio Web. En este caso seleccione **me gustaría cargar mi herramienta**. El **seleccione su control** aparece el cuadro. Haga clic en **examinar** y, a continuación, seleccione TestPublish.vsix en la carpeta \bin\Release del proyecto. Haga clic en **Siguiente**.  
  
8.  En **paso 3: información básica**, se muestran los campos del archivo source.extension.vsixmanifest. Seleccione un valor de **categoría** y agregue **etiquetas** para ayudar a los usuarios a encontrar la extensión. Puede agregar un resumen y una descripción (la descripción debe ser al menos 280 caracteres) más detallada. Deje **tipo de extensión** como **no es una extensión de Microsoft** y **categoría de costo** como **prueba**.  
  
9. Lea el acuerdo de contribución en la parte inferior de la página y compruebe **acepto**.  
  
10. Haga clic en **crear contribución**. Aparecerá la página que tendrá la extensión en la Galería de Visual Studio, con un mensaje de que la página todavía no se ha publicado.  
  
11. Haga clic en **Publicar**.  
  
12. Buscar en la Galería de Visual Studio para la extensión. Debe aparecer la lista de la extensión de TestPublish.  
  
## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Instale la extensión desde la Galería de Visual Studio  
 Ahora que se ha publicado la extensión, instale en Visual Studio y probarla.  
  
1.  En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones**.  
  
2.  Haga clic en **en línea** y, a continuación, busque TestPublish. Debe aparecer la lista de la extensión de TestPublish.  
  
3.  Haga clic en **Descargar**. Después de descargar la extensión, haga clic en **Instalar**.  
  
4.  Para completar la instalación, reinicie Visual Studio.  
  
## <a name="removing-the-extension"></a>Quitar la extensión  
 Puede quitar la extensión de la Galería de Visual Studio y de su equipo.  
  
#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Para quitar la extensión de la Galería de Visual Studio  
  
1.  Abra la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) sitio Web.  
  
2.  En el centro, haga clic en **extensiones My**. Se muestra la lista de TestPublish.  
  
3.  Haga clic en **eliminar**.  
  
#### <a name="to-remove-the-extension-from-your-computer"></a>Para quitar la extensión de su equipo  
  
1.  En el menú **Herramientas** de Visual Studio, haga clic en **Administrador de extensiones**.  
  
2.  Seleccione TestPublish y, a continuación, haga clic en **desinstalar**.  
  
3.  Para completar la desinstalación, reinicie Visual Studio.

